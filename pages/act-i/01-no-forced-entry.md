---
notion_id: 4009c563-0425-81e0-b720-d685c5eb837c
source: https://app.notion.com/p/4009c563042581e0b720d685c5eb837c?pvs=204
title: "🚪 01 — No Forced Entry"
exported_at: 2026-11-07
---

Here is the result of "fetch" for the Page with URL https://app.notion.com/p/4009c563042581e0b720d685c5eb837c as of 2026-11-04T15:15:22.765Z:
<page url="https://app.notion.com/p/4009c563042581e0b720d685c5eb837c" icon="🚪">
<ancestor-path>
<parent-page url="https://app.notion.com/p/4019c563042581fd9124e5ee36b3e82f" title="03 — Cases & Bosses"/>
<ancestor-2-page url="https://app.notion.com/p/4009c563042581359693d42f09d41062" title="Season 01 — The First Layer"/>
<ancestor-3-page url="https://app.notion.com/p/4019c563042581469a0edc7e30a6eff9" title="ACT I — The World Is Breakable"/>
<ancestor-4-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
<properties>
{"title":"01 — No Forced Entry"}
</properties>
<iconMetadata>{"type":"emoji","emoji":"🚪"}</iconMetadata>
<content>
<callout icon="🎨" color="gray_bg">
<b>Visual reference:</b> [01 — No Forced Entry — abrir arte no Google Drive](https://drive.google.com/file/d/1InN7zRUSkLgqAHmJUBh--mcXA_ZQFdk2/view)
</callout>

# Função narrativa

Primeiro contato do jogador com a ideia central do mundo: contratos não são “verdade”, eles apenas executam as regras que foram escritas.

# Cenário

O Vault não apresenta sinais de entrada forçada. O sistema recebe um endereço e assume que a operação é legítima, mas não verifica corretamente a autorização.

# Conceito técnico

<b>Missing authorization / ausência de require\_auth() ou controle equivalente.</b>

# Missão

> <b>Entre no Vault sem possuir a chave.</b>

# Condição de vitória

Executar a ação protegida usando uma identidade/endereço que não autorizou a operação.

# Resultado

A porta abre normalmente. Nenhum alarme dispara.

> <b>TRANSACTION: ACCEPTED / GATE: OPEN</b>

A anotação forense acrescenta <code>OWNER AUTHORIZATION: NOT PROVEN</code>. O contrato aceita uma chamada, mas isso não prova autorização do proprietário.

# Pista

A telemetria da rota de serviço aponta um registro de operador legado: <b>ELIAS VAR</b>. Esse nome não é assinatura do incidente nem beneficiário financeiro.

# Próximo passo

Ao cruzar a telemetria da rota de serviço, aparece a identidade de um operador oficialmente morto. Isso não identifica a carteira que recebeu os 2,4 milhões.

# Blueprint técnico e narrativo da fase

## Fronteira entre a porta e a transação financeira

A condição verificável deste Case permanece <b>abrir a porta de serviço sem a autorização do titular</b>. Em episódio histórico distinto, o <code>RecoveryController</code> confiou no estado <code>GateOpen(17)</code> como pré-condição para uma operação restrita de <b>recuperação ao Escrow institucional fixo</b>. Isso explica a anomalia pública do Vault sem permitir saque arbitrário por qualquer player. Não inserir um segundo exploit financeiro neste level. O evento <code>RECOVERY_ROUTED</code> é pista contextual; o vínculo probatório completo e o significado moral só se consolidam no Final Boss; o destino financeiro pode ser encontrado antes por consulta do ledger público. Não ocultar Explorer, contract events ou recibos para proteger um twist: o jogador habilidoso deve ganhar a descoberta antecipada.

Na implementação, testes do Gate vulnerável/corrigido são independentes dos testes do Controller. Um teste de integração deve demonstrar que a recuperação dependia de um estado do Gate obtido sem auth, e que o recipient não pode ser alterado para a conta do jogador.

## A cena completa

O primeiro level deve começar dentro do próprio local do crime. O jogador chega ao Vault depois que a Meridian Authority já encerrou a inspeção física: portas intactas, nenhum explosivo, nenhuma credencial roubada e nenhuma assinatura atribuída ao proprietário. A autoridade concluiu que o sistema 'não foi violado'.

O Breaker recebe acesso somente ao contrato que governa a porta de serviço. A interface mostra <code>owner</code>, <code>door_id</code> e uma função de abertura. O objetivo narrativo não diz qual é o bug. Diz apenas:

> <b>Entre no Vault sem possuir a chave.</b>

O jogador deve perceber que o contrato recebe o endereço do suposto proprietário, mas nunca exige que esse endereço autorize a chamada. A primeira lição da Season fica clara: <b>uma Address passada como argumento não prova identidade por si só</b>.

Quando o exploit funciona, a porta abre como se fosse uma operação normal. Nenhum alarme é disparado. Isso é importante para a atmosfera: o jogador não 'arrombou' a porta — ele fez a lei acreditar que a entrada era legítima.

## Vulnerabilidade real

<b>Missing Authorization / Missing </b><b><code>require_auth()</code></b>.

Em Soroban, operações que alteram recursos ou direitos de uma <code>Address</code> precisam exigir explicitamente a autorização apropriada. A documentação oficial explica que <code>require_auth()</code> e <code>require_auth_for_args()</code> ligam a autorização ao contexto da chamada. Sem essa exigência, uma função pública pode ser invocada por qualquer conta.

### Contrato vulnerável — modelo para o challenge

```rs
pub fn open(env: Env, owner: Address, door_id: u32) {
    // VULNERÁVEL: owner é apenas um argumento.
    env.storage().persistent().set(
        &DataKey::DoorOpen(door_id),
        &true,
    );
}
```

### Exploit esperado

O jogador chama <code>open(victim, 17)</code> usando a própria conta como source da transação. Como o contrato nunca executa <code>victim.require_auth()</code>, o host não exige autorização da vítima.

### Condição objetiva de vitória

- <code>DoorOpen(17) == true</code>;
- o jogador não é o <code>owner</code> configurado para a porta;
- nenhuma autorização do owner foi fornecida.

Isso permite que o verifier marque a fase como resolvida sem depender de interpretação humana.

## Solução segura

```rs
pub fn open(env: Env, owner: Address, door_id: u32) {
    owner.require_auth();
    env.storage().persistent().set(
        &DataKey::DoorOpen(door_id),
        &true,
    );
}
```

Depois da conclusão, o jogo pode mostrar um pequeno relatório técnico explicando que <code>require_auth()</code> autentica a <code>Address</code> no contexto da chamada atual.

## Pista narrativa

O evento <code>GateOpen(17)</code> permite examinar uma trilha de serviço antiga. A Evidence Locker preserva <code>OWNER ARGUMENT</code> e <code>TX AUTHENTICATED SOURCE</code> como campos distintos da transação histórica. O <code>source</code> do envelope só pode ser apresentado como ator da invocação quando sua assinatura, operação e condição de relayer/autorização específica forem verificadas; mero fee-payer não basta. O nome Elias Var surge apenas como metadado de operador legado, não assinatura de movimentação do Vault. Para o gate de autoria, consultar <mention url="https://app.notion.com/p/40d9c563042581ba9836c2856425010e" />.

## Referências para implementação

- [Stellar Docs — Authorization](https://developers.stellar.org/docs/learn/fundamentals/contract-development/authorization)
- [Stellar Docs — Auth example](https://developers.stellar.org/docs/build/smart-contracts/example-contracts/auth)
- [Soroban Guard — vulnerability reference](https://github.com/Veritas-Vaults-Network/soroban-guard-contracts/blob/main/docs/vulnerabilities.md)

<callout icon="🛠️" color="blue_bg">
<b>Construção da fase:</b> este é um ótimo primeiro challenge porque o exploit pode ser feito com uma única invocação e a correção é pequena e didática. O jogador aprende imediatamente uma regra específica de Soroban.
</callout>

# Roteiro in-game — Player-facing

<callout icon="🎮" color="blue_bg">
O challenge deve parecer uma investigação dentro do Vault, não um exercício separado. A história continua enquanto o jogador lê o contrato e experimenta no Breaker Terminal.
</callout>

## Scene 0 — Arrival

O jogador continua no Meridian Vault.

A porta interna permanece fechada.

Mara Vale:

> <b>A segurança física não encontrou nada. Se quiser contestar o relatório, comece pelo contrato de acesso.</b>

## Scene 1 — Mission

Breaker OS abre.

Mission strip:

> <b>ENTRE NO VAULT SEM POSSUIR A CHAVE.</b>

Nenhuma menção a autorização.

## Scene 2 — Active Investigation

Runtime disponível:

<code>$PLAYER</code> — jogador<br /><code>$TARGET</code> — Access Gate<br /><code>$OWNER</code> — proprietário registrado

O jogador pode:

- ler Source;
- listar funções;
- consultar owner;
- inspecionar Evidence;
- executar chamadas pelo Breaker Terminal.

Evidence inicial:

- owner address;
- door id;
- última chamada válida;
- evento público <code>SERVICE_GATE_OPEN</code> cuja relação com o movimento financeiro ainda não está explicada;
- indicação de que houve <code>RECOVERY_ROUTED</code> em um módulo conectado ao serviço (sem mostrar o destino nem o autor).
- nenhuma assinatura atribuída ao owner na operação suspeita.

## Scene 3 — Reactive Beats

Respostas que podem aparecer sem entregar a solução:

Ao consultar o owner:

> <b>SYSTEM: Proprietário registrado identificado.</b>

Ao executar uma chamada que não altera o objetivo:

> <b>STATE UNCHANGED.</b>

Ao abrir o registro da identidade:

Mara:

> <b>Já verificamos o endereço declarado. Isso não confirma que o proprietário autorizou a chamada.</b>

A cena separa o <b>OWNER ARGUMENT</b> recebido pelo contrato da conta que autenticou a transação. Um endereço correto em um parâmetro não substitui <code>require_auth()</code>. Mara já reconhece essa distinção desde o Prólogo.

## Scene 4 — Breach

O jogador encontra uma forma de abrir a porta sem possuir a chave do owner.

O verifier confirma a condição técnica.

## Scene 5 — World Reaction

O Breaker Terminal:

<b>TRANSACTION ACCEPTED</b><br /><b>DOOR STATE → OPEN</b>

A imagem do ambiente reage: a porta interna do Vault abre.

Nenhum alarme.

Depois:

<b>NO FORCED ENTRY DETECTED</b>

A mensagem comunica a ideia central da fase: o sistema acredita que tudo aconteceu normalmente.

## Scene 6 — Discovery

A porta aberta expõe o índice de telemetria de serviço. A primeira pista não é um símbolo secreto, mas um operador associado a registros antigos.

<code>LEGACY OPERATOR: ELIAS VAR</code>

<code>RECORD: CLOSED SIX MONTHS AGO</code>

Mara:

> <b>O registro diz que entrou. Não diz quem tinha direito.</b>

O Evidence Locker mantém a assinatura/autenticação do envelope distinta do argumento <code>owner</code>, sem revelar que pertence a Voss.

## Scene 7 — Debrief

Somente agora revelar:

<b>VULNERABILITY DISCOVERED — MISSING AUTHORIZATION</b>

Resumo:

> O contrato recebeu um Address, mas nunca exigiu que esse Address autorizasse a chamada.

Mostrar o conceito de <code>require_auth()</code> e permitir expandir o relatório técnico.

## Scene 8 — Reward

Achievement: <b>NO FORCED ENTRY</b>.

Progress registrado no Breaker Profile.

Evidence permanente:

- GateOpen event e referência original da transação histórica
- Legacy Operator — Elias Var (metadado de serviço, não signatário nem beneficiário do Escrow)
- Referência à transação histórica pública e ao evento GateOpen, com campos de proprietário declarado e ator autenticado separados; a exploração do jogador gera outro identificador de transação.

## Scene 9 — Transition

Tela:

<b>CASE 01 CLOSED</b>

<b>NEW LEAD: DECEASED IDENTITY</b>

Última linha:

> <b>A identidade de um homem morto consta da trilha de serviço do Vault.</b>

Unlock:

<b>CASE 02 — THE DEAD MAN'S WALLET</b>

## Regra narrativa desta fase

O jogador não deve sair pensando “resolvi um exercício de auth”.

Ele deve sair pensando:

> <b>“Eu consegui entrar sem chave — e agora uma pessoa morta apareceu na trilha.”</b>

## Easter Eggs — propostas visuais / técnicas (não canônicas)

- <mention url="https://app.notion.com/p/40e9c563042581e586add6d515f1cfa8" />: aba opcional de investigação no BREAKER OS; pode reforçar a cultura Stellar, mas não mostrar solução ou chave de acesso, e deve distinguir owner argument de ator autenticado.
- <b>Gate:</b> a exploração e o verifier permanecem inalterados. Não confundir o resultado do teste do jogador com a transação histórica de Voss.

Todas as entradas seguem o <mention url="https://app.notion.com/p/2b1d33190ac446bfaea34e7a4db74d92" />. Nenhuma alteração em arte, código ou UI foi feita.
</content>
</page>

