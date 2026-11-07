---
notion_id: 4019c563-0425-81b8-bd5b-c9a78199300f
source: https://app.notion.com/p/4019c563042581b8bd5bc9a78199300f?pvs=204
title: "🪙 05 — The Token That Arrived Short"
exported_at: 2026-11-07
---

Here is the result of "fetch" for the Page with URL https://app.notion.com/p/4019c563042581b8bd5bc9a78199300f as of 2026-11-02T17:27:59.520Z:
<page url="https://app.notion.com/p/4019c563042581b8bd5bc9a78199300f" icon="🪙">
<ancestor-path>
<parent-page url="https://app.notion.com/p/4019c56304258155ac29c3ff5333a0af" title="04 — Cases & Bosses"/>
<ancestor-2-page url="https://app.notion.com/p/4019c563042581d9aedad3e5f178c3e8" title="Season 02 — DeFi Wars — Lumen"/>
<ancestor-3-page url="https://app.notion.com/p/4019c563042581469a0edc7e30a6eff9" title="ACT I — The World Is Breakable"/>
<ancestor-4-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
<properties>
{"title":"05 — The Token That Arrived Short"}
</properties>
<iconMetadata>{"type":"emoji","emoji":"🪙"}</iconMetadata>
<content>
# Story

Os dashboards de Lumen afirmam que um Vault recebeu 100 milhões em assets.

O saldo real é menor.

O token cobra taxa durante transfer.

O Vault credita o valor solicitado, não o valor efetivamente recebido.

# Mission

> <b>Crie valor que o Vault acredita possuir.</b>

# Canonical Vulnerability

<b>Fee-on-Transfer Accounting — </b><b><code>fee_on_transfer</code></b><b>.</b>

# Learning

- accounting must use actual balance delta when token semantics are not guaranteed;
- declared amount ≠ received amount;
- composability breaks when protocols assume token behavior;
- reserve accounting can become insolvent silently.

# Win Condition

Depositar um token que entrega menos do que o parâmetro <code>amount</code>, recebendo crédito integral.

# Narrative Result

A diferença entre accounting e assets reais ajuda a explicar por que Lumen parecia saudável.

A cidade estava medindo riqueza que não possuía.

Um lending market dependente do Vault apresenta outra inconsistência:

debt index desatualizado.

Unlock:

<b>CASE 06 — THE DEBT THAT NEVER GREW</b>

# Reference

[https://github.com/Veritas-Vaults-Network/soroban-guard-contracts](https://github.com/Veritas-Vaults-Network/soroban-guard-contracts)

## Blueprint de integração v2 — token transfer semantics

<b>Fixture:</b> token de teste Soroban com taxa/transfer behavior definido e Vault que credita o <code>amount</code> solicitado sem consultar o <b>delta efetivo de saldo</b>. Não presumir que todo token Stellar funciona assim: o comportamento faz parte desta fixture.

<b>Verifier:</b> após um depósito, o <code>booked_amount</code> supera o delta de ativos realmente recebidos; secure mirror credita apenas delta recebido ou rejeita tokens não compatíveis. Testar precisão, rounding, taxa e balanços.

<b>Conexão narrativa:</b> o gap de reservas explica por que Lumen parecia mais saudável; o Vault alimenta a avaliação de um lending market que, por sua vez, usa um debt index desatualizado.

<b>Slides:</b> <code>BOOKED ≠ RECEIVED</code> e saldo real conferido; Breaker: “Lumen está contando valor que não recebeu.”

<b>QA:</b> não exagerar com números de produção não demonstrados. Evitar dizer que o exploit de laboratório sozinho causou o colapso narrativo.

## Loop jogável v3 — reconciliação de saldos (P1)

<callout icon="🎮" color="blue_bg">
Proposta player-facing. A fixture deve usar token de teste Soroban com comportamento de transferência explicitamente implementado e isolado.
</callout>

<b>1. Investigar:</b> inspeção de extrato de transfer + balanço efetivo do Vault + contabilidade interna; fornecer um depósito nominal, saldo anterior e saldo posterior.

<b>2. Formular hipótese:</b> o sistema concedeu crédito pelo <code>amount</code> solicitado, não pela diferença real dos saldos recebidos.

<b>3. Executar:</b> depositar token com fee definido na fixture e provar <code>credited_amount > received_delta</code>, com posição creditada acima dos ativos existentes. O secure mirror usa saldo real ou rejeita comportamento não suportado.

<b>4. Feedback:</b> <code>TRANSFER REQUESTED</code> / <code>ACTUAL RECEIVED</code> / <code>VAULT CREDITED</code>; distinguir saldo falso contabilizado de emissão monetária real.

<b>5. Próximo motivo:</b> a reserva superestimada é uma entrada de risco utilizada por um lending market cujo índice de dívida não foi atualizado.

<b>Diferencial:</b> <b>auditoria de reconciliação</b> em uma operação de transferência, não leitura de juros nem passagem do tempo.

<b>QA:</b> dados consistentes nos extratos, mirror seguro bloqueia discrepância, sem assumir que tokens Stellar normais cobram essa taxa.
</content>
</page>

