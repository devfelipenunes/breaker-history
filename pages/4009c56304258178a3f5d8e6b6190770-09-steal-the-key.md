---
notion_id: 4009c563-0425-8178-a3f5-d8e6b6190770
source: https://app.notion.com/p/4009c56304258178a3f5d8e6b6190770?pvs=204
title: "🔑 09 — Steal the Key"
exported_at: 2026-11-07
---

Here is the result of "fetch" for the Page with URL https://app.notion.com/p/4009c56304258178a3f5d8e6b6190770 as of 2026-11-04T15:35:42.075Z:
<page url="https://app.notion.com/p/4009c56304258178a3f5d8e6b6190770" icon="🔑">
<ancestor-path>
<parent-page url="https://app.notion.com/p/4019c563042581fd9124e5ee36b3e82f" title="03 — Cases & Bosses"/>
<ancestor-2-page url="https://app.notion.com/p/4009c563042581359693d42f09d41062" title="Season 01 — The First Layer"/>
<ancestor-3-page url="https://app.notion.com/p/4019c563042581469a0edc7e30a6eff9" title="ACT I — The World Is Breakable"/>
<ancestor-4-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
<properties>
{"title":"09 — Steal the Key"}
</properties>
<iconMetadata>{"type":"emoji","emoji":"🔑"}</iconMetadata>
<content>
<callout icon="📌" color="yellow_bg">
<b>FICHA TÉCNICA ATUALIZADA — STEAL THE KEY v1.4.</b> O heist por timelock e a assinatura consciente de Mara permanecem vigentes; a transição aponta para o manifesto histórico, não para upgrade de executable. Fonte única de narrativa, cenas e slides: <mention url="https://app.notion.com/p/40d9c563042581bf886cfc339d730fd1" />. Não tratar esta ficha como prova de teste ou deploy.
</callout>

<callout icon="🎨" color="gray_bg">
<b>Visual reference:</b> [09 — Steal the Key — abrir arte no Google Drive](https://drive.google.com/file/d/1jxFENnjZYf3W1r4-R8ta8SkNYDyIwotZ/view)
</callout>

# Função narrativa

Criar o heist da Season.

# Situação

The Spire é protegida por uma autorização legítima pertencente a um operador real.

O objetivo não é roubar a wallet física do operador. É explorar o sistema.

# Conceito técnico

<b>Admin Timelock Rewrite / ação agendada não vinculada ao payload completo.</b>

# Missão

> <b>Roube o acesso sem roubar a chave.</b>

# Condição de vitória

Usar uma autorização legítima para executar uma operação que o signatário não pretendia autorizar.

# Resultado

O jogador recebe acesso à Spire sem possuir a chave privada do operador.

# Story Item

<b>Spire Credential</b>

# Próximo passo

No topo da Spire existe um mecanismo capaz de alterar contratos da First Layer.

# Blueprint técnico e narrativo da fase

## O heist

The Spire não aceita visitantes. A entrada administrativa só abre depois que uma operação aprovada passa por um timelock. Um operador de Meridian agendou <b>duas</b> operações para a mesma janela: rotacionar a chave de serviço (<code>op_id = 1</code>) e, em seguida, abrir o hatch técnico (<code>op_id = 0</code>). O contrato mantém o vínculo entre as duas: a operação 0 tem a operação 1 como <code>predecessor</code>.

O jogador observa o processo e percebe algo: a autorização é legítima, o delay é legítimo e o operador realmente aprovou uma ação. O erro está em <b>como o contrato identifica aquilo que foi aprovado</b>.

O objetivo do Breaker não é roubar a private key do operador.

> <b>Roube o acesso sem roubar a chave.</b>

## Vulnerabilidade real

<b>Admin Timelock Rewrite Attack — operação pendente não vinculada ao payload completo.</b>

Existe uma classe de contrato vulnerável em referências Soroban em que o timelock guarda apenas uma ação pendente por <code>target</code>, ou usa uma chave incompleta, sem vincular a fila ao hash de <code>target + function + args + predecessor + salt</code>. Isso permite que uma operação legitimamente agendada seja sobrescrita ou reinterpretada com outro payload.

### Contrato vulnerável — modelo

```rs
pub enum Payload {
    OpenMaintenanceHatch,
    RotateServiceKey,
    GrantSpireAccess(Address),
}

pub fn rewrite_payload(env: Env, op_id: u32, payload: Payload) {
    // VULNERÁVEL: altera o payload de uma operação já agendada,
    // sem exigir nova aprovação do operador sobre os novos dados.
    env.storage().instance().set(&DataKey::Payload(op_id), &payload);
    env.storage().instance().set(&DataKey::Rewritten, &true);
}

pub fn execute(env: Env, op_id: u32) {
    // ... confere executed, eta e predecessor ...
    let payload: Payload = env.storage().instance().get(&DataKey::Payload(op_id)).unwrap();
    match payload {
        Payload::GrantSpireAccess(who) => {
            // A guarda olha o original, não o payload atual:
            if env.storage().instance().get(&DataKey::Original(op_id)).unwrap()
                != Payload::OpenMaintenanceHatch
            {
                panic!("payload not approved for this operation");
            }
            env.storage().instance().set(&DataKey::Access(who), &true);
        }
        // ...
    }
}
```

## Exploit esperado

1. O operador agendou <code>RotateServiceKey</code> (op 1) e <code>OpenMaintenanceHatch</code> (op 0); a op 0 tem <code>predecessor(0) == 1</code>.
2. O jogador executa a op 1 (<code>execute(1)</code>) para satisfazer o predecessor.
3. Reescreve o payload da op 0 para <code>GrantSpireAccess(player)</code>, mantendo o mesmo registro/ETA.
4. Espera/avança o ledger até o eta.
5. Executa a op 0: a guarda compara o <b>original</b> (<code>OpenMaintenanceHatch</code>) e libera o grant; <code>execute</code> marca <code>rewritten = true</code>.
6. O hatch nunca é aberto — a operação que o operador aprovou não aconteceu.

Para o sistema, o timelock foi respeitado e a operação era “do tipo aprovado”. Para o operador, aquela não foi a ação que ele autorizou.

### Condição objetiva de vitória

- existia uma operação legitimamente agendada antes do exploit;
- o predecessor da op 0 foi executado;
- o payload executado é diferente do originalmente aprovado (<code>rewritten() == true</code>);
- <code>access(player) == true</code>;
- <code>hatch_open() == false</code> — o hatch aprovado continua fechado;
- o jogador nunca apresentou autorização do operador para <code>grant_spire_access(player)</code>.

## Solução segura

A identidade da operação precisa depender de <b>todos os campos críticos</b>.

Conceitualmente:

```rs
operation_id = hash(
    target,
    function,
    args,
    predecessor,
    salt,
);
```

A execução deve reconstruir exatamente esse ID e verificar que aquela operação específica está <code>Ready</code>. Alterar <code>function</code> ou <code>args</code> gera outro ID e exige novo agendamento.

A implementação de TimelockController da OpenZeppelin para Stellar segue justamente esse modelo: a operação contém <code>target</code>, <code>function</code>, <code>args</code>, <code>predecessor</code> e <code>salt</code>, e o ID é derivado desses campos.

## Story Item

Quando o payload malicioso executa, a Spire emite uma credencial de acesso:

> <b>SPIRE CREDENTIAL // ACESSO CONCEDIDO</b>

O jogador entrou sem roubar a chave de ninguém. Ele roubou <b>o significado de uma autorização</b>.

## Referências para implementação

- [OpenZeppelin Stellar — Timelock Controller](https://docs.openzeppelin.com/stellar-contracts/governance/timelock-controller)
- [Soroban Guard — admin\_timelock\_rewrite](https://github.com/Veritas-Vaults-Network/soroban-guard-contracts)
- [Stellar Docs — Authorization](https://developers.stellar.org/docs/learn/fundamentals/contract-development/authorization)

<callout icon="🎭" color="purple_bg">
<b>Valor narrativo:</b> esta fase é um heist sem quebrar criptografia. O jogador intercepta uma autorização válida e demonstra que segurança depende tanto de <i>o que foi autorizado</i> quanto de <i>quem autorizou</i>.
</callout>

# Roteiro in-game — Player-facing

## Scene 0 — Arrival

The Spire é a primeira instalação da rota que continua oficialmente operacional.

Segurança normal. Operadores reais. Manutenção agendada.

Mara:

> <b>Isso não é uma ruína. Se você mudar alguma coisa aqui, alguém vai perceber.</b>

Antes da investigação continuar, a Meridian Authority interrompe o canal:

<b>CASE STATUS: TERMINATED</b><br /><b>EXTERNAL BREAKER ACCESS: REVOKED</b><br /><b>RETURN TO AUTHORITY CHANNEL</b>

A conexão oficial cai. Na última mensagem, a Authority registra que todos os acessos futuros serão tratados como não autorizados. Mara fica em silêncio: foi ela quem exigiu a preservação formal da evidência desde Warehouse 17 e sabe exatamente o que aquela ordem significa.

Surge um canal privado, sem selo institucional.

Mara:

> <b>Você tem uma hora. Guarde uma prova verificável. Não volte aqui depois disso.</b>

Após essa fala, exibir <code>PRIVATE CHANNEL: 01:00:00</code>. É um <b>relógio diegético roteirizado</b>, com marcos visuais de urgência; não há fail state por demorar no puzzle, cronômetro real obrigatório ou ramo narrativo alternativo.

Breaker:

> <b>Você sabe o que vão fazer com suas credenciais.</b>

Mara:

> <b>Sei. É uma escolha minha.</b>

A partir daqui, o jogador não está mais operando como auditor autorizado. Mara não lhe concede autoridade irrestrita; cria apenas uma janela de comunicação limitada.

<b>Custo institucional demonstrável:</b> para que a prova final não seja apenas um arquivo sem procedência, Mara assina um recibo de preservação de evidência com sua credencial institucional, <b>depois</b> da ordem de encerramento do caso. O canal privado não é, por si só, detectado magicamente; o recibo deixa um registro auditável de que Mara preservou um dossiê apesar da revogação. O sistema exibe: <code>EVIDENCE_RECEIPT: SIGNED</code> / <code>SIGNER: MARA VALE</code> / <code>CASE STATUS: TERMINATED</code>. A Authority poderá usar a contradição para suspender suas credenciais no epílogo.

<b>Diálogo único:</b> Mara diz: "Não concordei com tudo o que você fez. Você registrou a prova no Warehouse e interrompeu a pressão adicional em Sector 13, mas isso não torna suas ações autorizadas. Precisamos de uma prova que exista sem a sua palavra." Ela assina o recibo para tornar o caso auditável e arrisca o cargo por decisão própria, independentemente de qualquer escolha do jogador.

## Scene 1 — Inciting Evidence

Após a revogação, Mara não se torna uma operadora subordinada ao Breaker. Seu canal de uma hora transmite uma condição: sair com evidência reproduzível e não usar o acesso privado como licença para qualquer ato. O momento deve recordar a custódia documentada e a interrupção do aumento de carga em Sector 13, acontecimentos fixos do único arco.

Uma operação legítima já foi agendada — na verdade, duas, encadeadas:

<b>OP 1 — ROTATE\_SERVICE\_KEY</b><br /><b>OP 0 — OPEN\_MAINTENANCE\_HATCH</b> (predecessor: 1)

Status:<br /><b>AUTHORIZED</b><br /><b>WAITING</b><br /><b>ETA: ACTIVE WINDOW</b>

O jogador não possui a chave do operador.

## Scene 2 — Mission

> <b>ROUBE O ACESSO SEM ROUBAR A CHAVE.</b>

## Scene 3 — Active Investigation

Disponível:

- schedule record;
- operation identifier;
- target;
- payload;
- ETA;
- execution state;
- payload originalmente aprovado e hash preservado como evidência;
- câmera/registro da equipe que aguarda a manutenção real.

O jogador pode comparar aquilo que o sistema considera “a mesma operação”. A equipe na câmera não cria um NPC fixo nem um objetivo secundário; comprova que uma autorização legítima possuía um destinatário e uma consequência operacional.

## Scene 4 — Reactive Beats

Ao tentar executar cedo:

<b>OPERATION NOT READY</b>

Ao consultar auth:

<b>OPERATOR AUTHORIZATION: VALID</b>

Mara:

> <b>Então a assinatura não é a fraqueza.</b>

## Scene 5 — Breach

O jogador preserva, no dossiê, a operação e o payload originais; executa primeiro a rotação que satisfaz o predecessor, mantém a assinatura e o timing legítimos, e altera o significado/payload executável da op 0. A vulnerabilidade é que a autorização não vincula de forma íntegra todos os campos críticos; não há furto da chave do operador.

## Scene 6 — World Reaction

No horário correto:

<b>AUTHORIZED OPERATION EXECUTED</b>

Esperado:<br /><b>OPEN\_MAINTENANCE\_HATCH</b>

Executado:<br /><b>GRANT\_SPIRE\_ACCESS → \$PLAYER</b>

Hatch:<br /><b>STILL CLOSED</b>

A Spire abre normalmente. Em paralelo, a câmera mostra que o <code>OPEN_MAINTENANCE_HATCH</code> esperado não ocorreu: uma equipe encontra o hatch fechado e precisa reprogramar a inspeção. Registrar essa consequência sem acidente inventado, dano catastrófico ou personagem adicional. A tela distingue <b>sucesso técnico</b> e <b>efeito sobre terceiros</b>.

Marco narrativo: <code>PRIVATE CHANNEL: 00:08:42</code> — posição roteirizada, não tempo de execução do usuário.

## Scene 7 — Discovery

Mara:

> <b>Você não roubou a chave.</b>

Breaker:

> <b>Eu não precisei.</b>

Mara:

> <b>E a equipe continua esperando a abertura que foi autorizada. Isso também precisa constar na prova.</b>

O Breaker conserva o payload original, o executado e o recibo assinado por Mara. Ela não aprova a invasão; exige cadeia de custódia.

Acesso interno revela:<br /><b>SPIRE ARCHIVE INDEX — HISTORICAL DIAGNOSTIC MANIFEST</b>

## Scene 8 — Debrief

<b>VULNERABILITY DISCOVERED — TIMELOCK PAYLOAD REWRITE</b>

Explicar que a autorização não estava vinculada ao payload completo da operação.

## Scene 9 — Transition

Dentro da Spire, depois do recibo de Mara e sem introduzir mais um slide obrigatório, a interface destaca discretamente:<br /><b>SPIRE ARCHIVE INDEX: HISTORICAL DIAGNOSTIC MANIFEST — LOCATED</b><br /><b>ARCHIVE: LEGACY / RETENTION: OPEN</b>

Unlock:<br /><b>CASE 10 — REWRITE</b>

<b>Continuidade obrigatória:</b> Mara mantém o canal apenas até o fim de Rewrite. A contagem expira antes de o Breaker confrontar o Architect. Sua suspensão futura deriva do recibo assinado após <code>CASE TERMINATED</code>, não do monitoramento sobrenatural do canal.

## Cena aprovada — assinatura atribuível de Mara

Antes de firmar o recibo tardio, a interface de evidências mostra:

<code>CASE STATUS: CLOSED</code>  ·  <code>SIGNER: MARA VALE</code>  ·  <code>RECEIPT: ATTRIBUTABLE</code>  ·  <code>CUSTODY ACCEPTED</code>.

Mara revisa o identificador e confirma conscientemente; não precisa dizer “serei suspensa”. A operação registra hash e credential ID que reaparecem no epílogo ao suspender seu acesso institucional. Ela assume a <b>cadeia de custódia de prova</b>, não uma autorização generalizada para o Breaker mudar qualquer sistema.

<b>QA:</b> não criar escolha moral de assinar, relógio de 1 hora segue diegético, canal expira antes do Architect. O rastro do recibo é independente da interface privada.
</content>
</page>

