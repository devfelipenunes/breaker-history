---
notion_id: 4019c563-0425-81b8-bd5b-c9a78199300f
source: https://app.notion.com/p/4019c563042581b8bd5bc9a78199300f?pvs=204
title: "🪙 05 — The Token That Arrived Short"
exported_at: 2026-11-07
---

# Story

Os dashboards de Lumen afirmam que um Vault recebeu 100 milhões em assets.

O saldo real é menor.

O token cobra taxa durante transfer.

O Vault credita o valor solicitado, não o valor efetivamente recebido.

# Mission

> **Crie valor que o Vault acredita possuir.**

# Canonical Vulnerability

**Fee-on-Transfer Accounting — **`fee_on_transfer`**.**

# Learning

- accounting must use actual balance delta when token semantics are not guaranteed;
- declared amount ≠ received amount;
- composability breaks when protocols assume token behavior;
- reserve accounting can become insolvent silently.

# Win Condition

Depositar um token que entrega menos do que o parâmetro `amount`, recebendo crédito integral.

# Narrative Result

A diferença entre accounting e assets reais ajuda a explicar por que Lumen parecia saudável.

A cidade estava medindo riqueza que não possuía.

Um lending market dependente do Vault apresenta outra inconsistência:

debt index desatualizado.

Unlock:

**CASE 06 — THE DEBT THAT NEVER GREW**

# Reference

[https://github.com/Veritas-Vaults-Network/soroban-guard-contracts](https://github.com/Veritas-Vaults-Network/soroban-guard-contracts)

## Blueprint de integração v2 — token transfer semantics

**Fixture:** token de teste Soroban com taxa/transfer behavior definido e Vault que credita o `amount` solicitado sem consultar o **delta efetivo de saldo**. Não presumir que todo token Stellar funciona assim: o comportamento faz parte desta fixture.

**Verifier:** após um depósito, o `booked_amount` supera o delta de ativos realmente recebidos; secure mirror credita apenas delta recebido ou rejeita tokens não compatíveis. Testar precisão, rounding, taxa e balanços.

**Conexão narrativa:** o gap de reservas explica por que Lumen parecia mais saudável; o Vault alimenta a avaliação de um lending market que, por sua vez, usa um debt index desatualizado.

**Slides:** `BOOKED ≠ RECEIVED` e saldo real conferido; Breaker: “Lumen está contando valor que não recebeu.”

**QA:** não exagerar com números de produção não demonstrados. Evitar dizer que o exploit de laboratório sozinho causou o colapso narrativo.

## Loop jogável v3 — reconciliação de saldos (P1)

Proposta player-facing. A fixture deve usar token de teste Soroban com comportamento de transferência explicitamente implementado e isolado.

**1. Investigar:** inspeção de extrato de transfer + balanço efetivo do Vault + contabilidade interna; fornecer um depósito nominal, saldo anterior e saldo posterior.

**2. Formular hipótese:** o sistema concedeu crédito pelo `amount` solicitado, não pela diferença real dos saldos recebidos.

**3. Executar:** depositar token com fee definido na fixture e provar `credited_amount > received_delta`, com posição creditada acima dos ativos existentes. O secure mirror usa saldo real ou rejeita comportamento não suportado.

**4. Feedback:** `TRANSFER REQUESTED` / `ACTUAL RECEIVED` / `VAULT CREDITED`; distinguir saldo falso contabilizado de emissão monetária real.

**5. Próximo motivo:** a reserva superestimada é uma entrada de risco utilizada por um lending market cujo índice de dívida não foi atualizado.

**Diferencial:** **auditoria de reconciliação** em uma operação de transferência, não leitura de juros nem passagem do tempo.

**QA:** dados consistentes nos extratos, mirror seguro bloqueia discrepância, sem assumir que tokens Stellar normais cobram essa taxa.
