---
notion_id: 4019c563-0425-816f-809c-f5235c1d4491
source: https://app.notion.com/p/4019c5630425816f809cf5235c1d4491?pvs=204
title: "🚪 07 — Exit With Debt"
exported_at: 2026-11-07
---

# Story

O lending protocol valida collateral quando o usuário toma empréstimo.

Mas ao sacar collateral depois, verifica apenas se o saldo depositado é suficiente para o saque.

Não recalcula saúde da posição.

# Mission

> **Deixe a dívida. Leve o collateral.**

# Canonical Vulnerability

**Collateral Withdrawal Without Health Check — **`collateral_withdraw_no_health_check`**.**

# Learning

- LTV and health factors;
- every state transition must preserve solvency invariants;
- validating borrow is insufficient if withdraw can violate the same invariant;
- protocol bad debt.

# Win Condition

Depositar collateral, tomar dívida máxima e retirar collateral mantendo debt aberta.

# Narrative Result

O Breaker finalmente consegue medir a insolvência real.

Ela é maior que a publicamente reportada.

Rhea tinha razão:

Lumen não está “entrando” em crise.

Já estava insolvente.

Mas o preço que desencadeia a próxima cascata vem de um suposto TWAP.

Unlock:

**CASE 08 — ONE-LEDGER AVERAGE**

# Reference

[https://github.com/Veritas-Vaults-Network/soroban-guard-contracts/blob/main/docs/vulnerabilities.md](https://github.com/Veritas-Vaults-Network/soroban-guard-contracts/blob/main/docs/vulnerabilities.md)

## Blueprint de integração v2 — invariant de solvência

**Fixture:** borrower com dívida ativa, colateral e função de retirada que verifica saldo depositado, mas não recomputa health factor/LTV após a nova posição.

**Verifier:** `debt_outstanding > 0` e collateral insuficiente após withdraw, com retirada autorizada apesar da violação do invariant; versão segura calcula saúde após a mutação pretendida antes de confirmar.

**Revelação:** relatório de ativos e dívida recalculados demonstra que **Lumen já estava insolvente**, não que o Case 07 a tornou insolvente de repente. O ledger auditável revela gap maior que o dashboard.

**Gancho:** o disparador da próxima onda depende de um TWAP configurado com janela de um ledger.

**QA:** não confundir insolvência de uma posição com insolvência automaticamente comprovada de toda a cidade sem agregação do modelo econômico. Registrar o caminho da projeção agregada.

## Loop jogável v3 — auditoria de solvência agregada (P0)

A exploração local e a revelação de insolvência sistêmica são **duas provas diferentes**. Um borrower insolvente, isoladamente, não demonstra que toda Lumen estava insolvente.

**1. Investigar a posição:** dívida, preço do colateral, LTV, health factor, amount do saque e health estimado depois da retirada.

**2. Executar:** reproduzir `withdraw` que deixa dívida ativa e colateral insuficiente; o secure mirror rejeita por health após retirada.

**3. Prova da posição:** guardar `debt_outstanding`, `post_withdraw_collateral`, `health_after` e estado aprovado apesar do invariant violado.

**4. Auditoria da cidade:** a investigação agrega **ativos recuperáveis reais** versus **passivos exigíveis** de mercados selecionados no modelo de Lumen, descontando obrigações/ativos duplicados entre Vaults e lending. Identificar quem assume eventual passivo de insurance. Os fixtures agregados devem ter fonte e snapshot, não ser inferidos automaticamente do resultado do saque.

**5. Revelação:** `REPORTED STATUS: SOLVENT` vs `VERIFIED AGGREGATE GAP: NEGATIVE`. A cidade já tinha déficits ocultos; o jogador os comprova, não os cria nesta fase.

**6. Gancho:** ao rastrear a premissa de preço usada na projeção, o Breaker encontra TWAP configurado para janela de apenas um ledger.

**Diferencial:** duas camadas: **exploit individual** e **reconciliação econômica agregada**. Não transformar o cálculo agregado em outro exploit obrigatório.

**QA:** fixture de fechamento contábil com passivos/ativos por protocolo, sem dupla contagem, reconcilia os Cases 04–06 e permite verificação independente da afirmação “Lumen já estava insolvente”.
