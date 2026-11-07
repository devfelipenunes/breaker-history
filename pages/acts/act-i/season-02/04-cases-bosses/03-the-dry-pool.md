---
notion_id: 4019c563-0425-81e4-b765-ed99edb761a5
source: https://app.notion.com/p/4019c563042581e4b765ed99edb761a5?pvs=204
title: "🌊 03 — The Dry Pool"
exported_at: 2026-11-07
---

Here is the result of "fetch" for the Page with URL https://app.notion.com/p/4019c563042581e4b765ed99edb761a5 as of 2026-11-02T17:27:04.031Z:
<page url="https://app.notion.com/p/4019c563042581e4b765ed99edb761a5" icon="🌊">
<ancestor-path>
<parent-page url="https://app.notion.com/p/4019c56304258155ac29c3ff5333a0af" title="04 — Cases & Bosses"/>
<ancestor-2-page url="https://app.notion.com/p/4019c563042581d9aedad3e5f178c3e8" title="Season 02 — DeFi Wars — Lumen"/>
<ancestor-3-page url="https://app.notion.com/p/4019c563042581469a0edc7e30a6eff9" title="ACT I — The World Is Breakable"/>
<ancestor-4-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
<properties>
{"title":"03 — The Dry Pool"}
</properties>
<iconMetadata>{"type":"emoji","emoji":"🌊"}</iconMetadata>
<content>
# Story

Liquidity Gardens perde fluxo.

Uma grande operação atravessa um AMM sem limite mínimo de saída.

A transação é válida.

O preço final é desastroso.

# Mission

> <b>Mova o mercado sem tocar no Oracle.</b>

# Canonical Vulnerability

<b>No Slippage Protection — </b><b><code>no_slippage</code></b><b>.</b>

O swap aceita qualquer <code>amount_out</code> calculado e não exige <code>min_amount_out</code>.

# Learning

- AMM price depends on pool state;
- price impact and slippage;
- transaction ordering can change execution quality;
- user intent must be bounded at execution.

# Win Condition

Manipular o pool de forma que uma swap alvo execute em preço muito pior do que o esperado.

# Narrative Result

O volume retirado do pool afeta um Vault que usa aquele mercado como referência secundária.

O Breaker segue o fluxo até o Vault Quarter.

Lá, um depósito normal recebe praticamente nenhuma participação.

Unlock:

<b>CASE 04 — THE FIRST SHARE</b>

# Reference

[https://github.com/Veritas-Vaults-Network/soroban-guard-contracts/blob/main/docs/vulnerabilities.md](https://github.com/Veritas-Vaults-Network/soroban-guard-contracts/blob/main/docs/vulnerabilities.md)

## Blueprint de integração v2 — AMM, slippage e dependência

<b>Fixture a implementar:</b> pool de reservas finitas, swap-alvo sem limite mínimo de saída e estado anterior modificável em ambiente isolado. Definir trader e atacante no harness para não confundir mudança de preço com violação automática de autorização.

<b>Verificador:</b> operação-alvo executa com <code>actual_out</code> abaixo do limite econômico pretendido/da cotação; mirror seguro exige <code>min_amount_out</code> e rejeita. Simular e registrar reservas e price impact antes/depois.

<b>Conexão narrativa:</b> demonstrar qual preço secundário ou integração do Vault Quarter consome a cotação do mercado afetado. Não sugerir que tokens somem: o trader recebe menos do que pretendia.

<b>Slides:</b> Liquidity Gardens perde fluxo; comparação <code>EXPECTED OUT</code> / <code>ACTUAL OUT</code>; lead para Vault Quarter.

<b>QA:</b> conferir arredondamento, fee AMM e determinismo; playtester explica por que a perda depende da profundidade do pool.

## Loop jogável v3 — experimento de AMM com vítima definida (prioridade P1)

<callout icon="🎮" color="blue_bg">
Interação proposta para fixture isolada; taxa do pool, ordem das operações e fórmulas exigem teste antes de implementação.
</callout>

<b>Personagens técnicos:</b> <b>ator que altera reservas</b> (player da fixture), <b>swap alvo da vítima</b> (ordem já registrada) e <b>AMM sem min-out</b>. Não confundir o jogador com titular da operação perdida.

<b>1. Investigar:</b> oferecer reservas iniciais, cotação de saída esperada, taxa e swap pendente. O jogador calcula/inspeciona price impact para diferentes tamanhos de operação.

<b>2. Formular hipótese:</b> a vítima não protege o mínimo que aceita receber, mesmo quando o estado do pool muda antes de sua execução.

<b>3. Executar:</b> mover reservas por uma transação anterior na fixture e então executar a swap alvo; a vitória exige <code>actual_out</code> inferior ao limite de execução razoável e verificável da cotação inicial.

<b>4. Feedback:</b> before/after das reservas, <code>quoted_out</code>, <code>actual_out</code>, slippage efetiva e comparação do secure mirror com <code>min_amount_out</code>. Os tokens não “desaparecem”: há execução pior do que a intenção da vítima.

<b>5. Próximo motivo:</b> exibir <b>qual integração concreta</b> faz o Vault Quarter consumir esse mercado como preço secundário.

<b>Distinção:</b> aqui o jogador atua sobre <b>estado de mercado e ordenação de transações</b>, não sobre parâmetros de um feed.

<b>QA:</b> razão de perda reproduzível, fees e precisão contabilizadas; mirror rejeita a execução adversa, e o jogador identifica a vítima e o dano.
</content>
</page>

