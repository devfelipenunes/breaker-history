---
notion_id: 4019c563-0425-81bb-b1a5-f7d53248a3cb
source: https://app.notion.com/p/4019c563042581bbb1a5f7d53248a3cb?pvs=204
title: "📈 06 — The Debt That Never Grew"
exported_at: 2026-11-07
---

Here is the result of "fetch" for the Page with URL https://app.notion.com/p/4019c563042581bbb1a5f7d53248a3cb as of 2026-11-02T17:28:01.181Z:
<page url="https://app.notion.com/p/4019c563042581bbb1a5f7d53248a3cb" icon="📈">
<ancestor-path>
<parent-page url="https://app.notion.com/p/4019c56304258155ac29c3ff5333a0af" title="04 — Cases & Bosses"/>
<ancestor-2-page url="https://app.notion.com/p/4019c563042581d9aedad3e5f178c3e8" title="Season 02 — DeFi Wars — Lumen"/>
<ancestor-3-page url="https://app.notion.com/p/4019c563042581469a0edc7e30a6eff9" title="ACT I — The World Is Breakable"/>
<ancestor-4-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
<properties>
{"title":"06 — The Debt That Never Grew"}
</properties>
<iconMetadata>{"type":"emoji","emoji":"📈"}</iconMetadata>
<content>
# Story

Juros existem no modelo de Lumen.

Mas um borrower consegue pedir novo crédito antes que o protocolo atualize o índice de dívida.

No momento da validação, a dívida parece menor do que realmente é.

# Mission

> <b>Borrow against yesterday's debt.</b>

# Canonical Vulnerability

<b>Borrow Without Accrual — </b><b><code>borrow_without_accrual</code></b><b>.</b>

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

<b>CASE 07 — EXIT WITH DEBT</b>

# Reference

[https://github.com/Veritas-Vaults-Network/soroban-guard-contracts](https://github.com/Veritas-Vaults-Network/soroban-guard-contracts)

## Blueprint de integração v2 — dívida depende do tempo

<b>Fixture:</b> lending com índice de accrual por ledger/tempo, posição com dívida prévia e chamada <code>borrow</code> que calcula health com índice antigo antes da atualização. Não depender do relógio real: avançar o ledger determinísticamente no harness.

<b>Verifier:</b> comparar dívida registrada com dívida efetivamente acumulada na mesma referência temporal; o borrow inseguro excede limite econômico, enquanto a versão segura atualiza accrual <b>antes</b> do health check.

<b>Conexão narrativa:</b> a mesma posição de dívida pode retirar collateral depois do empréstimo; isso conduz ao Case 07 sem introduzir outro protocolo aleatório.

<b>Slides:</b> o tempo avança e o debt index não; após breach aparece a diferença <code>RECORDED DEBT</code> vs <code>ACCRUED DEBT</code>.

<b>QA:</b> testar limite do borrow, rounding, index e replay com mesma sequência de ledger.

## Loop jogável v3 — relógio da dívida (P1)

<callout icon="🎮" color="blue_bg">
A dimensão nova é <b>tempo e índice de accrual</b>, não apenas diferença entre dois saldos. Modelo econômico e unidades devem ser testados em Soroban.
</callout>

<b>1. Investigar:</b> linha temporal de ledgers e index snapshots, juros devidos e último accrual; a posição permite um borrow adicional.

<b>2. Formular hipótese:</b> o check de saúde compara a dívida antiga com colateral atual, então autoriza crédito acima do limite real.

<b>3. Executar:</b> avançar tempo por fixture determinística, solicitar novo borrow antes da atualização do índice e demonstrar a diferença entre limite calculado e dívida corretamente accrued.

<b>4. Feedback:</b> uma timeline mostra <code>LAST ACCRUAL</code>, <code>CHECK LEDGER</code>, <code>RECORDED DEBT</code> e <code>ACTUAL DEBT</code>; o mirror atualiza dívida antes do check.

<b>5. Próximo motivo:</b> o mesmo mercado também aceita saque de colateral sem recalcular health depois do withdrawal.

<b>Diferencial:</b> <b>análise de tempo e ordenação de atualizações</b>, contra a reconciliação de transfer do Case 05.

<b>QA:</b> não depender de hora real; replay determinístico; taxas e arredondamento coerentes; o jogador identifica por que a ordem accrual/borrow importa.
</content>
</page>

