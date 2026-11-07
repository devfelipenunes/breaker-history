---
notion_id: 4019c563-0425-816f-809c-f5235c1d4491
source: https://app.notion.com/p/4019c5630425816f809cf5235c1d4491?pvs=204
title: "🚪 07 — Exit With Debt"
exported_at: 2026-11-07
---

Here is the result of "fetch" for the Page with URL https://app.notion.com/p/4019c5630425816f809cf5235c1d4491 as of 2026-11-02T17:28:03.091Z:
<page url="https://app.notion.com/p/4019c5630425816f809cf5235c1d4491" icon="🚪">
<ancestor-path>
<parent-page url="https://app.notion.com/p/4019c56304258155ac29c3ff5333a0af" title="04 — Cases & Bosses"/>
<ancestor-2-page url="https://app.notion.com/p/4019c563042581d9aedad3e5f178c3e8" title="Season 02 — DeFi Wars — Lumen"/>
<ancestor-3-page url="https://app.notion.com/p/4019c563042581469a0edc7e30a6eff9" title="ACT I — The World Is Breakable"/>
<ancestor-4-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
<properties>
{"title":"07 — Exit With Debt"}
</properties>
<iconMetadata>{"type":"emoji","emoji":"🚪"}</iconMetadata>
<content>
# Story

O lending protocol valida collateral quando o usuário toma empréstimo.

Mas ao sacar collateral depois, verifica apenas se o saldo depositado é suficiente para o saque.

Não recalcula saúde da posição.

# Mission

> <b>Deixe a dívida. Leve o collateral.</b>

# Canonical Vulnerability

<b>Collateral Withdrawal Without Health Check — </b><b><code>collateral_withdraw_no_health_check</code></b><b>.</b>

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

<b>CASE 08 — ONE-LEDGER AVERAGE</b>

# Reference

[https://github.com/Veritas-Vaults-Network/soroban-guard-contracts/blob/main/docs/vulnerabilities.md](https://github.com/Veritas-Vaults-Network/soroban-guard-contracts/blob/main/docs/vulnerabilities.md)

## Blueprint de integração v2 — invariant de solvência

<b>Fixture:</b> borrower com dívida ativa, colateral e função de retirada que verifica saldo depositado, mas não recomputa health factor/LTV após a nova posição.

<b>Verifier:</b> <code>debt_outstanding > 0</code> e collateral insuficiente após withdraw, com retirada autorizada apesar da violação do invariant; versão segura calcula saúde após a mutação pretendida antes de confirmar.

<b>Revelação:</b> relatório de ativos e dívida recalculados demonstra que <b>Lumen já estava insolvente</b>, não que o Case 07 a tornou insolvente de repente. O ledger auditável revela gap maior que o dashboard.

<b>Gancho:</b> o disparador da próxima onda depende de um TWAP configurado com janela de um ledger.

<b>QA:</b> não confundir insolvência de uma posição com insolvência automaticamente comprovada de toda a cidade sem agregação do modelo econômico. Registrar o caminho da projeção agregada.

## Loop jogável v3 — auditoria de solvência agregada (P0)

<callout icon="🎮" color="blue_bg">
A exploração local e a revelação de insolvência sistêmica são <b>duas provas diferentes</b>. Um borrower insolvente, isoladamente, não demonstra que toda Lumen estava insolvente.
</callout>

<b>1. Investigar a posição:</b> dívida, preço do colateral, LTV, health factor, amount do saque e health estimado depois da retirada.

<b>2. Executar:</b> reproduzir <code>withdraw</code> que deixa dívida ativa e colateral insuficiente; o secure mirror rejeita por health após retirada.

<b>3. Prova da posição:</b> guardar <code>debt_outstanding</code>, <code>post_withdraw_collateral</code>, <code>health_after</code> e estado aprovado apesar do invariant violado.

<b>4. Auditoria da cidade:</b> a investigação agrega <b>ativos recuperáveis reais</b> versus <b>passivos exigíveis</b> de mercados selecionados no modelo de Lumen, descontando obrigações/ativos duplicados entre Vaults e lending. Identificar quem assume eventual passivo de insurance. Os fixtures agregados devem ter fonte e snapshot, não ser inferidos automaticamente do resultado do saque.

<b>5. Revelação:</b> <code>REPORTED STATUS: SOLVENT</code> vs <code>VERIFIED AGGREGATE GAP: NEGATIVE</code>. A cidade já tinha déficits ocultos; o jogador os comprova, não os cria nesta fase.

<b>6. Gancho:</b> ao rastrear a premissa de preço usada na projeção, o Breaker encontra TWAP configurado para janela de apenas um ledger.

<b>Diferencial:</b> duas camadas: <b>exploit individual</b> e <b>reconciliação econômica agregada</b>. Não transformar o cálculo agregado em outro exploit obrigatório.

<b>QA:</b> fixture de fechamento contábil com passivos/ativos por protocolo, sem dupla contagem, reconcilia os Cases 04–06 e permite verificação independente da afirmação “Lumen já estava insolvente”.
</content>
</page>

