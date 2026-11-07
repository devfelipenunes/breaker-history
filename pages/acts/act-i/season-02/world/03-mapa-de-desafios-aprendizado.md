---
notion_id: 4019c563-0425-81d0-a098-c4aa5d163a67
source: https://app.notion.com/p/4019c563042581d0a098c4aa5d163a67?pvs=204
title: "🧪 03 — Mapa de Desafios & Aprendizado"
exported_at: 2026-11-07
---

**Mapa canônico de aprendizagem da Season 2.** Os Cases já estão definidos o suficiente para prototipagem de implementação.

# Progressão

O currículo técnico evolui de **dados → execução de mercado → accounting de Vault → solvência de lending → intervenção sistêmica**.

| Case | O que o jogador aprende | Vulnerabilidade canônica |
| --- | --- | --- |
| 01 — Stale Truth | Freshness de Oracle | `stale_oracle` |
| 02 — False Confidence | Incerteza/confidence de Oracle | `oracle_confidence_ignored` |
| 03 — The Dry Pool | Price impact / slippage de AMM | `no_slippage` |
| 04 — The First Share | Vault share accounting | `empty_vault_share_inflation` / donation accounting |
| BOSS — The Liquidator | Composição | sem vulnerabilidade nova |
| 05 — The Token That Arrived Short | Premissas de integração de token | `fee_on_transfer` |
| 06 — The Debt That Never Grew | Accrual de juros | `borrow_without_accrual` |
| 07 — Exit With Debt | Invariants de solvência / LTV | `collateral_withdraw_no_health_check` |
| 08 — One-Ledger Average | Configuração de TWAP | `twap_window_too_short` |
| 09 — The Breaker That Didn't Break | Controles de segurança | `inactive_circuit_breaker` |
| 10 — Emergency Authority | Escopo de autoridade emergencial; confirmar semântica do delay na fixture | `emergency_delay_bypass` (identificador histórico; a falha descrita é dispatcher fora do escopo) |
| FINAL — The Cascade | Risco sistêmico | sem vulnerabilidade nova |

# Arco de aprendizagem

## Início

O jogador ainda pergunta:

> **Qual contrato está quebrado?**

## Meio

Depois de The Liquidator:

> **E se eu corrigir o contrato e piorar o sistema?**

## Final

O jogador precisa raciocinar sobre:

**oracle → Vault → liquidation → AMM → lending → bad debt → emergency controls**

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

A sequência canônica está mantida. Para transformar esta matriz em gameplay, cada Case agora possui um **Blueprint de integração v2** em sua página original: fixture, condição verificável, secure mirror, evidência e gancho. O **estado econômico narrativo** é um conjunto de snapshots demonstráveis da cidade; não exige estado financeiro perigoso compartilhado entre contratos de laboratório.

- [07 — Lumen Economic State & Continuidade da Crise](07-lumen-economic-state-continuidade-da-crise.md) define dependências e indicadores.
- [08 — Roteiro Narrativo de Gameplay & Slides](08-roteiro-narrativo-de-gameplay-slides.md) separa narrativa de debrief.
- [09 — The Cascade & Liquidator — Blueprint Técnico](09-the-cascade-liquidator-blueprint-tecnico.md) estabelece os invariants.
- [10 — Production Tracker, QA & Playtests](../production/10-production-tracker-qa-playtests.md) contém gate de entrega por fase.

**Risco especial do Case 10:** o ID `emergency_delay_bypass` é histórico. Pela descrição atual, a falha verificável é dispatch fora do escopo de target/selector/args; somente código/teste podem provar que o delay também é contornado.

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

**Status:** contratos e UI não inspecionados nesta revisão. As mecânicas acima são contratos de design para a equipe, não operações já implementadas. [09 — The Cascade & Liquidator — Blueprint Técnico](09-the-cascade-liquidator-blueprint-tecnico.md) e [08 — Roteiro Narrativo de Gameplay & Slides](08-roteiro-narrativo-de-gameplay-slides.md) devem ser usados em conjunto.
