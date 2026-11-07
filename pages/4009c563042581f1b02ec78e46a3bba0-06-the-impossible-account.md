---
notion_id: 4009c563-0425-81f1-b02e-c78e46a3bba0
source: https://app.notion.com/p/4009c563042581f1b02ec78e46a3bba0?pvs=204
title: "♾️ 06 — The Impossible Account"
exported_at: 2026-11-07
---

Here is the result of "fetch" for the Page with URL https://app.notion.com/p/4009c563042581f1b02ec78e46a3bba0 as of 2026-11-04T15:34:14.486Z:
<page url="https://app.notion.com/p/4009c563042581f1b02ec78e46a3bba0" icon="♾️">
<ancestor-path>
<parent-page url="https://app.notion.com/p/4019c563042581fd9124e5ee36b3e82f" title="03 — Cases & Bosses"/>
<ancestor-2-page url="https://app.notion.com/p/4009c563042581359693d42f09d41062" title="Season 01 — The First Layer"/>
<ancestor-3-page url="https://app.notion.com/p/4019c563042581469a0edc7e30a6eff9" title="ACT I — The World Is Breakable"/>
<ancestor-4-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
<properties>
{"title":"06 — The Impossible Account"}
</properties>
<iconMetadata>{"type":"emoji","emoji":"♾️"}</iconMetadata>
<content>
<callout icon="🎨" color="gray_bg">
<b>Visual reference:</b> [06 — The Impossible Account — abrir arte no Google Drive](https://drive.google.com/file/d/1C6QoWPP5MxloEZdAg_9A5TNktxATkP7s/view)
</callout>

# Função narrativa

Usar matemática como evidência de que outra pessoa já explorou a infraestrutura.

# Situação

Uma conta antiga possui um saldo que não deveria ser alcançável pelas regras do sistema.

# Conceito técnico

<b>Aritmética com wrapping em </b><b><code>u32</code></b><b>: multiplicação e subtração que dão a volta em vez de falhar.</b>

# Missão

> <b>Reproduza o saldo impossível.</b>

# Condição de vitória

Produzir na conta do jogador o valor que o próprio contrato declara impossível (<code>impossible()</code>), usando um caminho de aritmética que dá a volta.

# Resultado

O saldo impossível leva o Breaker a consultar o <b>relatório histórico de proveniência</b> do módulo energético, previamente indexado e verificável, no qual aparece a referência técnica:

<b>GRID NODE: 13 / ARCHIVE DESTINATION: SECTOR 13</b>

# Pista

## SECTOR 13

Voss registrou esse estado impossível como vestígio de uma infraestrutura legada que continuava conectada a Sector 13.

# Próximo passo

O jogador entra em Sector 13.

# Blueprint técnico e narrativo da fase

## A conta impossível

A gravação de Voss contém um Contract ID. O contrato é um antigo módulo de créditos energéticos. Uma única conta possui um valor que não faz sentido diante das regras econômicas do sistema.

O Breaker não precisa roubar o saldo. Precisa descobrir <b>como aquele saldo foi produzido</b>.

> <b>Reproduza o saldo impossível.</b>

## Vulnerabilidade real

<b>Aritmética com wrapping (</b><b><code>wrapping_mul</code></b><b> / </b><b><code>wrapping_sub</code></b><b>).</b>

O módulo usa <code>u32</code> e operações <code>wrapping_*</code>: em vez de falhar no overflow/underflow, o resultado dá a volta módulo 2³². A conta do jogador começa em zero; <code>withdraw(player, amount)</code> subtrai com <code>wrapping_sub</code>, então um saque maior que o saldo produz um valor enorme — exatamente o tipo de número que o contrato chama de impossível. <code>accrue</code> tem o mesmo problema na multiplicação.

O alvo não é inventado pelo jogador: <code>impossible()</code> deriva o valor-sentinela de dados públicos da instância e da carteira (hash de player + contrato, offset módulo 97, <code>BASE_ELAPSED × FACTOR</code>). O contrato também expõe as variantes seguras <code>accrue_checked</code> e <code>withdraw_checked</code>, que usam <code>checked_*</code> e falham alto.

### Contrato vulnerável

```rs
pub fn withdraw(env: Env, player: Address, amount: u32) {
    player.require_auth();
    let current: u32 = env.storage().instance()
        .get(&DataKey::Credit(player.clone()))
        .unwrap_or(0);
    // VULNERÁVEL: underflow dá a volta em 2³² em vez de falhar.
    env.storage().instance()
        .set(&DataKey::Credit(player), &current.wrapping_sub(amount));
}

pub fn accrue(env: Env, player: Address, stake: u32, rate: u32, elapsed: u32) {
    player.require_auth();
    if stake < MIN_INPUT || rate < MIN_INPUT || elapsed == 0 {
        panic!("out of range");
    }
    // VULNERÁVEL: multiplicação com wrapping.
    let reward = stake.wrapping_mul(rate).wrapping_mul(elapsed);
    // ... credita reward com wrapping_add
}
```

### Exploit esperado

O jogador chama <code>impossible()</code> para obter o alvo, confere que <code>credit(player)</code> começa em zero e pede um saque maior que o saldo. <code>withdraw</code> usa <code>wrapping_sub</code>: <code>0 - amount</code> dá a volta e produz o valor-sentinela. Alternativamente, <code>accrue</code> com fatores escolhidos produz o mesmo efeito por overflow na multiplicação.

### Condição objetiva de vitória

- <code>credit(player) == impossible()</code>;
- o valor só é alcançável porque uma operação deu a volta (underflow ou overflow);
- o alvo é derivado de <code>player</code> + endereço da instância, não copiado de outra instância;
- <code>withdraw_checked</code>/<code>accrue_checked</code> recusam o mesmo caminho.

## Solução segura

```rs
let reward = stake
    .checked_mul(rate)
    .and_then(|value| value.checked_mul(elapsed))
    .expect("overflow");
let next = current.checked_sub(amount).expect("underflow");
```

A regra é usar <code>checked_*</code> em todo caminho que aceita valor de usuário; o contrato já expõe <code>accrue_checked</code> e <code>withdraw_checked</code> como a versão correta.

## A pista na tabela de roteamento

O saldo impossível representa créditos contábeis de energia, não moeda nem eletricidade transferida. Reproduzida a falha, o Breaker consulta o relatório histórico de proveniência do módulo, um índice existente antes do desafio. Esse relatório referencia <b>GRID NODE: 13 / ARCHIVE DESTINATION: SECTOR 13</b>. A tabela não foi decodificada a partir do número e não surge magicamente porque uma operação deu a volta. Não inventar apagão, vítima ou crédito financeiro.

## Referências para implementação

- [Soroban Guard — unchecked\_math](https://github.com/Veritas-Vaults-Network/soroban-guard-contracts/blob/main/docs/vulnerabilities.md)
- [Stellar example — checked arithmetic](https://developers.stellar.org/docs/build/smart-contracts/example-contracts/cross-contract-call)
- [Soroban SDK Security Advisory GHSA-96xm-fv9w-pf3f](https://github.com/stellar/rs-soroban-sdk/security/advisories/GHSA-96xm-fv9w-pf3f)

<callout icon="⚠️" color="yellow_bg">
<b>Nota de construção:</b> não apresentar a lição como “Rust sempre faz wrap”. O contrato da fase deve fixar uma configuração/versão vulnerável controlada e o pós-level deve explicar o comportamento do tooling moderno.
</callout>

# Roteiro in-game — Player-facing

## Scene 0 — Arrival

<b>Nova função dramática:</b> após a gravação de Voss, o Breaker quer provar que há um caminho de infraestrutura, não simplesmente repetir um exploit numérico. Uma hipótese falsa inicial associa o saldo a roubo de energia; os dados, porém, remetem ao relatório histórico de proveniência do módulo, não a um furto ou reconstrução automática de um mapa. A referência ao Sector 13 pertence à tabela da infraestrutura, não é uma mensagem arbitrariamente escondida em um número.

A conta impossível pertence a um antigo sistema de energia.

Dashboard:<br /><b>BALANCE: VALUE OUTSIDE EXPECTED RANGE</b>

Mara:

> <b>Esse número não pode existir sob este contrato.</b>

## Scene 1 — Inciting Evidence

Evidence:

- historical balance;
- arithmetic operation;
- Voss notes;
- repeated numeric anomaly.

## Scene 2 — Mission

> <b>REPRODUZA O SALDO IMPOSSÍVEL.</b>

## Scene 3 — Active Investigation

O jogador investiga operações matemáticas e limites.

Nenhum texto usa “overflow” inicialmente.

Outputs:<br /><b>EXPECTED RANGE</b><br /><b>CURRENT VALUE</b><br /><b>DELTA: INVALID</b>

## Scene 4 — Reactive Beats

Se o jogador reproduzir valores próximos:

<b>STATE VALID</b>

Quando cruza o comportamento inesperado:

<b>RANGE CHECK: NONE</b>

## Scene 5 — Breach

O jogador produz novamente o estado impossível.

## Scene 6 — World Reaction

O painel registra o estado impossível. O Breaker abre o relatório de proveniência histórico previamente indexado pela interface legada; o relatório mostra a rota energética sem atribuir o valor do saldo a um roubo:

<b>ENERGY ROUTING TABLE — LEGACY</b><br /><b>GRID NODE: 13</b><br /><b>ARCHIVE DESTINATION: SECTOR 13</b><br /><b>STATUS: UNMAPPED</b>

## Scene 7 — Discovery

Voss não escreveu “13” como uma charada. Ele percebeu que a conta impossível estava ligada a um destino de infraestrutura que Meridian havia removido dos mapas modernos.

Mara consulta o destino:

<b>SECTOR 13 — NO SUCH SECTOR</b>

Breaker:

> <b>Isso está virando um padrão.</b>

## Scene 8 — Debrief

<b>VULNERABILITY DISCOVERED — UNSAFE ARITHMETIC / RANGE VALIDATION</b>

O relatório técnico explica a condição específica usada no challenge.

## Scene 9 — Transition

<b>NEW LEAD: SECTOR 13</b>

Unlock:<br /><b>CASE 07 — SECTOR 13</b>
</content>
</page>

