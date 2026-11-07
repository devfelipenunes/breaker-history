---
notion_id: 4019c563-0425-81d0-a098-c4aa5d163a67
source: https://app.notion.com/p/4019c563042581d0a098c4aa5d163a67?pvs=204
title: "🧪 03 — Mapa de Desafios & Aprendizado"
exported_at: 2026-11-07
---

Here is the result of "fetch" for the Page with URL https://app.notion.com/p/4019c563042581d0a098c4aa5d163a67 as of 2026-11-02T17:29:16.549Z:
<page url="https://app.notion.com/p/4019c563042581d0a098c4aa5d163a67" icon="🧪">
<ancestor-path>
<parent-page url="https://app.notion.com/p/4019c563042581d9aedad3e5f178c3e8" title="Season 02 — DeFi Wars — Lumen"/>
<ancestor-2-page url="https://app.notion.com/p/4019c563042581469a0edc7e30a6eff9" title="ACT I — The World Is Breakable"/>
<ancestor-3-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
<properties>
{"title":"03 — Mapa de Desafios & Aprendizado"}
</properties>
<iconMetadata>{"type":"emoji","emoji":"🧪"}</iconMetadata>
<content>
<callout icon="🧪" color="yellow_bg">
<b>Mapa canônico de aprendizagem da Season 2.</b> Os Cases já estão definidos o suficiente para prototipagem de implementação.
</callout>

# Progressão

O currículo técnico evolui de <b>dados → execução de mercado → accounting de Vault → solvência de lending → intervenção sistêmica</b>.

| Case | O que o jogador aprende | Vulnerabilidade canônica |
| --- | --- | --- |
| 01 — Stale Truth | Freshness de Oracle | <code>stale_oracle</code> |
| 02 — False Confidence | Incerteza/confidence de Oracle | <code>oracle_confidence_ignored</code> |
| 03 — The Dry Pool | Price impact / slippage de AMM | <code>no_slippage</code> |
| 04 — The First Share | Vault share accounting | <code>empty_vault_share_inflation</code> / donation accounting |
| BOSS — The Liquidator | Composição | sem vulnerabilidade nova |
| 05 — The Token That Arrived Short | Premissas de integração de token | <code>fee_on_transfer</code> |
| 06 — The Debt That Never Grew | Accrual de juros | <code>borrow_without_accrual</code> |
| 07 — Exit With Debt | Invariants de solvência / LTV | <code>collateral_withdraw_no_health_check</code> |
| 08 — One-Ledger Average | Configuração de TWAP | <code>twap_window_too_short</code> |
| 09 — The Breaker That Didn't Break | Controles de segurança | <code>inactive_circuit_breaker</code> |
| 10 — Emergency Authority | Escopo de autoridade emergencial; confirmar semântica do delay na fixture | <code>emergency_delay_bypass</code> (identificador histórico; a falha descrita é dispatcher fora do escopo) |
| FINAL — The Cascade | Risco sistêmico | sem vulnerabilidade nova |

# Arco de aprendizagem

## Início

O jogador ainda pergunta:

> <b>Qual contrato está quebrado?</b>

## Meio

Depois de The Liquidator:

> <b>E se eu corrigir o contrato e piorar o sistema?</b>

## Final

O jogador precisa raciocinar sobre:

<b>oracle → Vault → liquidation → AMM → lending → bad debt → emergency controls</b>

O Final Boss não é resolvido encontrando um bug.

É resolvido escolhendo a menor intervenção capaz de interromper a Cascade sem fingir que posições insolventes estão saudáveis.

# Regra de implementação

Todo Case de DeFi precisa de:

- vulnerable contract fixture;
- secure mirror ou remediation;
- cenário local determinístico;
- snapshot de estado antes/depois;
- invariant econômico explícito no postmortem;
- objetivo player-facing que nunca entregue o nome da vulnerabilidade.

# Fonte principal de fixtures

[https://github.com/Veritas-Vaults-Network/soroban-guard-contracts](https://github.com/Veritas-Vaults-Network/soroban-guard-contracts)

# Nota de implementação — revisão de causalidade

A sequência canônica está mantida. Para transformar esta matriz em gameplay, cada Case agora possui um <b>Blueprint de integração v2</b> em sua página original: fixture, condição verificável, secure mirror, evidência e gancho. O <b>estado econômico narrativo</b> é um conjunto de snapshots demonstráveis da cidade; não exige estado financeiro perigoso compartilhado entre contratos de laboratório.

- <mention url="https://app.notion.com/p/40c9c563042581179c72dfd4d74e26bb" /> define dependências e indicadores.
- <mention url="https://app.notion.com/p/40c9c5630425812d927ed82d191156d3" /> separa narrativa de debrief.
- <mention url="https://app.notion.com/p/40c9c5630425811da9bdc67cf66b2410" /> estabelece os invariants.
- <mention url="https://app.notion.com/p/40c9c5630425810eb872fb6544359653" /> contém gate de entrega por fase.

<b>Risco especial do Case 10:</b> o ID <code>emergency_delay_bypass</code> é histórico. Pela descrição atual, a falha verificável é dispatch fora do escopo de target/selector/args; somente código/teste podem provar que o delay também é contornado.

# Matriz v3 — diversidade de gameplay e dificuldade pretendida

| Fase | Ação dominante do player | Risco de repetição evitado | Curva proposta |
| --- | --- | --- | --- |
| 01 | Comparar timestamp/ledger e reproduzir liquidation stale | Não comparar confidence | Fácil–médio |
| 02 | Examinar múltiplos reports e política de confidence | Não repetir freshness | Fácil–médio |
| 03 | Alterar reservas de AMM, executar swap da vítima e medir perda | Não tratar queda de preço como vitória automática | Médio |
| 04 | Manipular primeiro depósito, doação e rounding de shares | Não repetir swap | Médio |
| Liquidator | Bloquear override, reconstruir cadeia de consequências | Sem bug novo e sem punição arbitrária | Difícil |
| 05 | Reconciliar transfer solicitado versus saldo recebido | Não repetir teste de índice de dívida | Médio |
| 06 | Avançar ledgers e comparar dívida accrued versus registrada | Não repetir diferença estática de saldo | Médio |
| 07 | Saque que viola health + relatório agregado sem dupla contagem | Não inferir insolvência sistêmica de um único borrower | Médio–difícil |
| 08 | Calcular TWAP sob janelas distintas | Não repetir bugs Oracle de feed | Médio |
| 09 | Seguir execução sem pause apesar do flag | Não repetir alteração de configuração | Médio |
| 10 | Comparar capability aprovada com operação realizada | Escopo de autorização ≠ bypass de delay | Difícil |
| Cascade | Diagnosticar, conter e comprovar contágio estabilizado | Sem novo bug, sem solvência mágica | Muito difícil |

<b>Status:</b> contratos e UI não inspecionados nesta revisão. As mecânicas acima são contratos de design para a equipe, não operações já implementadas. <mention url="https://app.notion.com/p/40c9c5630425811da9bdc67cf66b2410" /> e <mention url="https://app.notion.com/p/40c9c5630425812d927ed82d191156d3" /> devem ser usados em conjunto.
</content>
</page>

