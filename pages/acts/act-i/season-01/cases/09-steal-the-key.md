---
notion_id: 4009c563-0425-8178-a3f5-d8e6b6190770
source: https://app.notion.com/p/4009c56304258178a3f5d8e6b6190770?pvs=204
title: "🔑 09 — Steal the Key"
exported_at: 2026-11-07
---

**FICHA TÉCNICA ATUALIZADA — STEAL THE KEY v1.4.** O heist por timelock e a assinatura consciente de Mara permanecem vigentes; a transição aponta para o manifesto histórico, não para upgrade de executable. Fonte única de narrativa, cenas e slides: [BREAKER — Season 1 | FINAL NARRATIVE v1.4 — NARRATIVE LOCK](../narrative/breaker-season-1-final-narrative-v1-4-narrative-lock.md). Não tratar esta ficha como prova de teste ou deploy.

**Visual reference:** [09 — Steal the Key — abrir arte no Google Drive](https://drive.google.com/file/d/1jxFENnjZYf3W1r4-R8ta8SkNYDyIwotZ/view)

# Função narrativa

Criar o heist da Season.

# Situação

The Spire é protegida por uma autorização legítima pertencente a um operador real.

O objetivo não é roubar a wallet física do operador. É explorar o sistema.

# Conceito técnico

**Admin Timelock Rewrite / ação agendada não vinculada ao payload completo.**

# Missão

> **Roube o acesso sem roubar a chave.**

# Condição de vitória

Usar uma autorização legítima para executar uma operação que o signatário não pretendia autorizar.

# Resultado

O jogador recebe acesso à Spire sem possuir a chave privada do operador.

# Story Item

**Spire Credential**

# Próximo passo

No topo da Spire existe um mecanismo capaz de alterar contratos da First Layer.

# Blueprint técnico e narrativo da fase

## O heist

The Spire não aceita visitantes. A entrada administrativa só abre depois que uma operação aprovada passa por um timelock. Um operador de Meridian agendou **duas** operações para a mesma janela: rotacionar a chave de serviço (`op_id = 1`) e, em seguida, abrir o hatch técnico (`op_id = 0`). O contrato mantém o vínculo entre as duas: a operação 0 tem a operação 1 como `predecessor`.

O jogador observa o processo e percebe algo: a autorização é legítima, o delay é legítimo e o operador realmente aprovou uma ação. O erro está em **como o contrato identifica aquilo que foi aprovado**.

O objetivo do Breaker não é roubar a private key do operador.

> **Roube o acesso sem roubar a chave.**

## Vulnerabilidade real

**Admin Timelock Rewrite Attack — operação pendente não vinculada ao payload completo.**

Existe uma classe de contrato vulnerável em referências Soroban em que o timelock guarda apenas uma ação pendente por `target`, ou usa uma chave incompleta, sem vincular a fila ao hash de `target + function + args + predecessor + salt`. Isso permite que uma operação legitimamente agendada seja sobrescrita ou reinterpretada com outro payload.

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

1. O operador agendou `RotateServiceKey` (op 1) e `OpenMaintenanceHatch` (op 0); a op 0 tem `predecessor(0) == 1`.
2. O jogador executa a op 1 (`execute(1)`) para satisfazer o predecessor.
3. Reescreve o payload da op 0 para `GrantSpireAccess(player)`, mantendo o mesmo registro/ETA.
4. Espera/avança o ledger até o eta.
5. Executa a op 0: a guarda compara o **original** (`OpenMaintenanceHatch`) e libera o grant; `execute` marca `rewritten = true`.
6. O hatch nunca é aberto — a operação que o operador aprovou não aconteceu.

Para o sistema, o timelock foi respeitado e a operação era “do tipo aprovado”. Para o operador, aquela não foi a ação que ele autorizou.

### Condição objetiva de vitória

- existia uma operação legitimamente agendada antes do exploit;
- o predecessor da op 0 foi executado;
- o payload executado é diferente do originalmente aprovado (`rewritten() == true`);
- `access(player) == true`;
- `hatch_open() == false` — o hatch aprovado continua fechado;
- o jogador nunca apresentou autorização do operador para `grant_spire_access(player)`.

## Solução segura

A identidade da operação precisa depender de **todos os campos críticos**.

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

A execução deve reconstruir exatamente esse ID e verificar que aquela operação específica está `Ready`. Alterar `function` ou `args` gera outro ID e exige novo agendamento.

A implementação de TimelockController da OpenZeppelin para Stellar segue justamente esse modelo: a operação contém `target`, `function`, `args`, `predecessor` e `salt`, e o ID é derivado desses campos.

## Story Item

Quando o payload malicioso executa, a Spire emite uma credencial de acesso:

> **SPIRE CREDENTIAL // ACESSO CONCEDIDO**

O jogador entrou sem roubar a chave de ninguém. Ele roubou **o significado de uma autorização**.

## Referências para implementação

- [OpenZeppelin Stellar — Timelock Controller](https://docs.openzeppelin.com/stellar-contracts/governance/timelock-controller)
- [Soroban Guard — admin\_timelock\_rewrite](https://github.com/Veritas-Vaults-Network/soroban-guard-contracts)
- [Stellar Docs — Authorization](https://developers.stellar.org/docs/learn/fundamentals/contract-development/authorization)

**Valor narrativo:** esta fase é um heist sem quebrar criptografia. O jogador intercepta uma autorização válida e demonstra que segurança depende tanto de *o que foi autorizado* quanto de *quem autorizou*.

# Roteiro in-game — Player-facing

## Scene 0 — Arrival

The Spire é a primeira instalação da rota que continua oficialmente operacional.

Segurança normal. Operadores reais. Manutenção agendada.

Mara:

> **Isso não é uma ruína. Se você mudar alguma coisa aqui, alguém vai perceber.**

Antes da investigação continuar, a Meridian Authority interrompe o canal:

**CASE STATUS: TERMINATED**
**EXTERNAL BREAKER ACCESS: REVOKED**
**RETURN TO AUTHORITY CHANNEL**

A conexão oficial cai. Na última mensagem, a Authority registra que todos os acessos futuros serão tratados como não autorizados. Mara fica em silêncio: foi ela quem exigiu a preservação formal da evidência desde Warehouse 17 e sabe exatamente o que aquela ordem significa.

Surge um canal privado, sem selo institucional.

Mara:

> **Você tem uma hora. Guarde uma prova verificável. Não volte aqui depois disso.**

Após essa fala, exibir `PRIVATE CHANNEL: 01:00:00`. É um **relógio diegético roteirizado**, com marcos visuais de urgência; não há fail state por demorar no puzzle, cronômetro real obrigatório ou ramo narrativo alternativo.

Breaker:

> **Você sabe o que vão fazer com suas credenciais.**

Mara:

> **Sei. É uma escolha minha.**

A partir daqui, o jogador não está mais operando como auditor autorizado. Mara não lhe concede autoridade irrestrita; cria apenas uma janela de comunicação limitada.

**Custo institucional demonstrável:** para que a prova final não seja apenas um arquivo sem procedência, Mara assina um recibo de preservação de evidência com sua credencial institucional, **depois** da ordem de encerramento do caso. O canal privado não é, por si só, detectado magicamente; o recibo deixa um registro auditável de que Mara preservou um dossiê apesar da revogação. O sistema exibe: `EVIDENCE_RECEIPT: SIGNED` / `SIGNER: MARA VALE` / `CASE STATUS: TERMINATED`. A Authority poderá usar a contradição para suspender suas credenciais no epílogo.

**Diálogo único:** Mara diz: "Não concordei com tudo o que você fez. Você registrou a prova no Warehouse e interrompeu a pressão adicional em Sector 13, mas isso não torna suas ações autorizadas. Precisamos de uma prova que exista sem a sua palavra." Ela assina o recibo para tornar o caso auditável e arrisca o cargo por decisão própria, independentemente de qualquer escolha do jogador.

## Scene 1 — Inciting Evidence

Após a revogação, Mara não se torna uma operadora subordinada ao Breaker. Seu canal de uma hora transmite uma condição: sair com evidência reproduzível e não usar o acesso privado como licença para qualquer ato. O momento deve recordar a custódia documentada e a interrupção do aumento de carga em Sector 13, acontecimentos fixos do único arco.

Uma operação legítima já foi agendada — na verdade, duas, encadeadas:

**OP 1 — ROTATE\_SERVICE\_KEY**
**OP 0 — OPEN\_MAINTENANCE\_HATCH** (predecessor: 1)

Status:
**AUTHORIZED**
**WAITING**
**ETA: ACTIVE WINDOW**

O jogador não possui a chave do operador.

## Scene 2 — Mission

> **ROUBE O ACESSO SEM ROUBAR A CHAVE.**

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

**OPERATION NOT READY**

Ao consultar auth:

**OPERATOR AUTHORIZATION: VALID**

Mara:

> **Então a assinatura não é a fraqueza.**

## Scene 5 — Breach

O jogador preserva, no dossiê, a operação e o payload originais; executa primeiro a rotação que satisfaz o predecessor, mantém a assinatura e o timing legítimos, e altera o significado/payload executável da op 0. A vulnerabilidade é que a autorização não vincula de forma íntegra todos os campos críticos; não há furto da chave do operador.

## Scene 6 — World Reaction

No horário correto:

**AUTHORIZED OPERATION EXECUTED**

Esperado:
**OPEN\_MAINTENANCE\_HATCH**

Executado:
**GRANT\_SPIRE\_ACCESS → \$PLAYER**

Hatch:
**STILL CLOSED**

A Spire abre normalmente. Em paralelo, a câmera mostra que o `OPEN_MAINTENANCE_HATCH` esperado não ocorreu: uma equipe encontra o hatch fechado e precisa reprogramar a inspeção. Registrar essa consequência sem acidente inventado, dano catastrófico ou personagem adicional. A tela distingue **sucesso técnico** e **efeito sobre terceiros**.

Marco narrativo: `PRIVATE CHANNEL: 00:08:42` — posição roteirizada, não tempo de execução do usuário.

## Scene 7 — Discovery

Mara:

> **Você não roubou a chave.**

Breaker:

> **Eu não precisei.**

Mara:

> **E a equipe continua esperando a abertura que foi autorizada. Isso também precisa constar na prova.**

O Breaker conserva o payload original, o executado e o recibo assinado por Mara. Ela não aprova a invasão; exige cadeia de custódia.

Acesso interno revela:
**SPIRE ARCHIVE INDEX — HISTORICAL DIAGNOSTIC MANIFEST**

## Scene 8 — Debrief

**VULNERABILITY DISCOVERED — TIMELOCK PAYLOAD REWRITE**

Explicar que a autorização não estava vinculada ao payload completo da operação.

## Scene 9 — Transition

Dentro da Spire, depois do recibo de Mara e sem introduzir mais um slide obrigatório, a interface destaca discretamente:
**SPIRE ARCHIVE INDEX: HISTORICAL DIAGNOSTIC MANIFEST — LOCATED**
**ARCHIVE: LEGACY / RETENTION: OPEN**

Unlock:
**CASE 10 — REWRITE**

**Continuidade obrigatória:** Mara mantém o canal apenas até o fim de Rewrite. A contagem expira antes de o Breaker confrontar o Architect. Sua suspensão futura deriva do recibo assinado após `CASE TERMINATED`, não do monitoramento sobrenatural do canal.

## Cena aprovada — assinatura atribuível de Mara

Antes de firmar o recibo tardio, a interface de evidências mostra:

`CASE STATUS: CLOSED`  ·  `SIGNER: MARA VALE`  ·  `RECEIPT: ATTRIBUTABLE`  ·  `CUSTODY ACCEPTED`.

Mara revisa o identificador e confirma conscientemente; não precisa dizer “serei suspensa”. A operação registra hash e credential ID que reaparecem no epílogo ao suspender seu acesso institucional. Ela assume a **cadeia de custódia de prova**, não uma autorização generalizada para o Breaker mudar qualquer sistema.

**QA:** não criar escolha moral de assinar, relógio de 1 hora segue diegético, canal expira antes do Architect. O rastro do recibo é independente da interface privada.
