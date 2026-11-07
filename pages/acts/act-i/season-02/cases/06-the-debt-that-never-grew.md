---
notion_id: 4019c563-0425-81bb-b1a5-f7d53248a3cb
source: https://app.notion.com/p/4019c563042581bbb1a5f7d53248a3cb?pvs=204
title: "📈 06 — The Debt That Never Grew"
exported_at: 2026-11-07
---

# Story

Juros existem no modelo de Lumen.

Mas um borrower consegue pedir novo crédito antes que o protocolo atualize o índice de dívida.

No momento da validação, a dívida parece menor do que realmente é.

# Mission

> **Borrow against yesterday's debt.**

# Canonical Vulnerability

**Borrow Without Accrual — **`borrow_without_accrual`**.**

# Learning

- lending uses indexed/accrued debt;
- health checks require current state;
- lazy accrual can create stale risk calculations;
- order of accounting operations matters.

# Win Condition

Obter crédito acima do limite econômico utilizando debt state anterior à atualização de juros.

# Narrative Result

O Breaker descobre que o problema não está apenas em entrar em dívida.

É possível sair com o collateral.

Unlock:

**CASE 07 — EXIT WITH DEBT**

# Reference

[https://github.com/Veritas-Vaults-Network/soroban-guard-contracts](https://github.com/Veritas-Vaults-Network/soroban-guard-contracts)

## Blueprint de integração v2 — dívida depende do tempo

**Fixture:** lending com índice de accrual por ledger/tempo, posição com dívida prévia e chamada `borrow` que calcula health com índice antigo antes da atualização. Não depender do relógio real: avançar o ledger determinísticamente no harness.

**Verifier:** comparar dívida registrada com dívida efetivamente acumulada na mesma referência temporal; o borrow inseguro excede limite econômico, enquanto a versão segura atualiza accrual **antes** do health check.

**Conexão narrativa:** a mesma posição de dívida pode retirar collateral depois do empréstimo; isso conduz ao Case 07 sem introduzir outro protocolo aleatório.

**Slides:** o tempo avança e o debt index não; após breach aparece a diferença `RECORDED DEBT` vs `ACCRUED DEBT`.

**QA:** testar limite do borrow, rounding, index e replay com mesma sequência de ledger.

## Loop jogável v3 — relógio da dívida (P1)

A dimensão nova é **tempo e índice de accrual**, não apenas diferença entre dois saldos. Modelo econômico e unidades devem ser testados em Soroban.

**1. Investigar:** linha temporal de ledgers e index snapshots, juros devidos e último accrual; a posição permite um borrow adicional.

**2. Formular hipótese:** o check de saúde compara a dívida antiga com colateral atual, então autoriza crédito acima do limite real.

**3. Executar:** avançar tempo por fixture determinística, solicitar novo borrow antes da atualização do índice e demonstrar a diferença entre limite calculado e dívida corretamente accrued.

**4. Feedback:** uma timeline mostra `LAST ACCRUAL`, `CHECK LEDGER`, `RECORDED DEBT` e `ACTUAL DEBT`; o mirror atualiza dívida antes do check.

**5. Próximo motivo:** o mesmo mercado também aceita saque de colateral sem recalcular health depois do withdrawal.

**Diferencial:** **análise de tempo e ordenação de atualizações**, contra a reconciliação de transfer do Case 05.

**QA:** não depender de hora real; replay determinístico; taxas e arredondamento coerentes; o jogador identifica por que a ordem accrual/borrow importa.
