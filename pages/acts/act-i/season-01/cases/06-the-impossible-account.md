---
notion_id: 4009c563-0425-81f1-b02e-c78e46a3bba0
source: https://app.notion.com/p/4009c563042581f1b02ec78e46a3bba0?pvs=204
title: "♾️ 06 — The Impossible Account"
exported_at: 2026-11-07
---

**Visual reference:** [06 — The Impossible Account — abrir arte no Google Drive](https://drive.google.com/file/d/1C6QoWPP5MxloEZdAg_9A5TNktxATkP7s/view)

# Função narrativa

Usar matemática como evidência de que outra pessoa já explorou a infraestrutura.

# Situação

Uma conta antiga possui um saldo que não deveria ser alcançável pelas regras do sistema.

# Conceito técnico

**Aritmética com wrapping em **`u32`**: multiplicação e subtração que dão a volta em vez de falhar.**

# Missão

> **Reproduza o saldo impossível.**

# Condição de vitória

Produzir na conta do jogador o valor que o próprio contrato declara impossível (`impossible()`), usando um caminho de aritmética que dá a volta.

# Resultado

O saldo impossível leva o Breaker a consultar o **relatório histórico de proveniência** do módulo energético, previamente indexado e verificável, no qual aparece a referência técnica:

**GRID NODE: 13 / ARCHIVE DESTINATION: SECTOR 13**

# Pista

## SECTOR 13

Voss registrou esse estado impossível como vestígio de uma infraestrutura legada que continuava conectada a Sector 13.

# Próximo passo

O jogador entra em Sector 13.

# Blueprint técnico e narrativo da fase

## A conta impossível

A gravação de Voss contém um Contract ID. O contrato é um antigo módulo de créditos energéticos. Uma única conta possui um valor que não faz sentido diante das regras econômicas do sistema.

O Breaker não precisa roubar o saldo. Precisa descobrir **como aquele saldo foi produzido**.

> **Reproduza o saldo impossível.**

## Vulnerabilidade real

**Aritmética com wrapping (**`wrapping_mul`** / **`wrapping_sub`**).**

O módulo usa `u32` e operações `wrapping_*`: em vez de falhar no overflow/underflow, o resultado dá a volta módulo 2³². A conta do jogador começa em zero; `withdraw(player, amount)` subtrai com `wrapping_sub`, então um saque maior que o saldo produz um valor enorme — exatamente o tipo de número que o contrato chama de impossível. `accrue` tem o mesmo problema na multiplicação.

O alvo não é inventado pelo jogador: `impossible()` deriva o valor-sentinela de dados públicos da instância e da carteira (hash de player + contrato, offset módulo 97, `BASE_ELAPSED × FACTOR`). O contrato também expõe as variantes seguras `accrue_checked` e `withdraw_checked`, que usam `checked_*` e falham alto.

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

O jogador chama `impossible()` para obter o alvo, confere que `credit(player)` começa em zero e pede um saque maior que o saldo. `withdraw` usa `wrapping_sub`: `0 - amount` dá a volta e produz o valor-sentinela. Alternativamente, `accrue` com fatores escolhidos produz o mesmo efeito por overflow na multiplicação.

### Condição objetiva de vitória

- `credit(player) == impossible()`;
- o valor só é alcançável porque uma operação deu a volta (underflow ou overflow);
- o alvo é derivado de `player` + endereço da instância, não copiado de outra instância;
- `withdraw_checked`/`accrue_checked` recusam o mesmo caminho.

## Solução segura

```rs
let reward = stake
    .checked_mul(rate)
    .and_then(|value| value.checked_mul(elapsed))
    .expect("overflow");
let next = current.checked_sub(amount).expect("underflow");
```

A regra é usar `checked_*` em todo caminho que aceita valor de usuário; o contrato já expõe `accrue_checked` e `withdraw_checked` como a versão correta.

## A pista na tabela de roteamento

O saldo impossível representa créditos contábeis de energia, não moeda nem eletricidade transferida. Reproduzida a falha, o Breaker consulta o relatório histórico de proveniência do módulo, um índice existente antes do desafio. Esse relatório referencia **GRID NODE: 13 / ARCHIVE DESTINATION: SECTOR 13**. A tabela não foi decodificada a partir do número e não surge magicamente porque uma operação deu a volta. Não inventar apagão, vítima ou crédito financeiro.

## Referências para implementação

- [Soroban Guard — unchecked\_math](https://github.com/Veritas-Vaults-Network/soroban-guard-contracts/blob/main/docs/vulnerabilities.md)
- [Stellar example — checked arithmetic](https://developers.stellar.org/docs/build/smart-contracts/example-contracts/cross-contract-call)
- [Soroban SDK Security Advisory GHSA-96xm-fv9w-pf3f](https://github.com/stellar/rs-soroban-sdk/security/advisories/GHSA-96xm-fv9w-pf3f)

**Nota de construção:** não apresentar a lição como “Rust sempre faz wrap”. O contrato da fase deve fixar uma configuração/versão vulnerável controlada e o pós-level deve explicar o comportamento do tooling moderno.

# Roteiro in-game — Player-facing

## Scene 0 — Arrival

**Nova função dramática:** após a gravação de Voss, o Breaker quer provar que há um caminho de infraestrutura, não simplesmente repetir um exploit numérico. Uma hipótese falsa inicial associa o saldo a roubo de energia; os dados, porém, remetem ao relatório histórico de proveniência do módulo, não a um furto ou reconstrução automática de um mapa. A referência ao Sector 13 pertence à tabela da infraestrutura, não é uma mensagem arbitrariamente escondida em um número.

A conta impossível pertence a um antigo sistema de energia.

Dashboard:
**BALANCE: VALUE OUTSIDE EXPECTED RANGE**

Mara:

> **Esse número não pode existir sob este contrato.**

## Scene 1 — Inciting Evidence

Evidence:

- historical balance;
- arithmetic operation;
- Voss notes;
- repeated numeric anomaly.

## Scene 2 — Mission

> **REPRODUZA O SALDO IMPOSSÍVEL.**

## Scene 3 — Active Investigation

O jogador investiga operações matemáticas e limites.

Nenhum texto usa “overflow” inicialmente.

Outputs:
**EXPECTED RANGE**
**CURRENT VALUE**
**DELTA: INVALID**

## Scene 4 — Reactive Beats

Se o jogador reproduzir valores próximos:

**STATE VALID**

Quando cruza o comportamento inesperado:

**RANGE CHECK: NONE**

## Scene 5 — Breach

O jogador produz novamente o estado impossível.

## Scene 6 — World Reaction

O painel registra o estado impossível. O Breaker abre o relatório de proveniência histórico previamente indexado pela interface legada; o relatório mostra a rota energética sem atribuir o valor do saldo a um roubo:

**ENERGY ROUTING TABLE — LEGACY**
**GRID NODE: 13**
**ARCHIVE DESTINATION: SECTOR 13**
**STATUS: UNMAPPED**

## Scene 7 — Discovery

Voss não escreveu “13” como uma charada. Ele percebeu que a conta impossível estava ligada a um destino de infraestrutura que Meridian havia removido dos mapas modernos.

Mara consulta o destino:

**SECTOR 13 — NO SUCH SECTOR**

Breaker:

> **Isso está virando um padrão.**

## Scene 8 — Debrief

**VULNERABILITY DISCOVERED — UNSAFE ARITHMETIC / RANGE VALIDATION**

O relatório técnico explica a condição específica usada no challenge.

## Scene 9 — Transition

**NEW LEAD: SECTOR 13**

Unlock:
**CASE 07 — SECTOR 13**
