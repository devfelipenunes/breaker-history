---
notion_id: 4019c563-0425-81e4-b765-ed99edb761a5
source: https://app.notion.com/p/4019c563042581e4b765ed99edb761a5?pvs=204
title: "🌊 03 — The Dry Pool"
exported_at: 2026-11-07
---

# Story

Liquidity Gardens perde fluxo.

Uma grande operação atravessa um AMM sem limite mínimo de saída.

A transação é válida.

O preço final é desastroso.

# Mission

> **Mova o mercado sem tocar no Oracle.**

# Canonical Vulnerability

**No Slippage Protection — **`no_slippage`**.**

O swap aceita qualquer `amount_out` calculado e não exige `min_amount_out`.

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

**CASE 04 — THE FIRST SHARE**

# Reference

[https://github.com/Veritas-Vaults-Network/soroban-guard-contracts/blob/main/docs/vulnerabilities.md](https://github.com/Veritas-Vaults-Network/soroban-guard-contracts/blob/main/docs/vulnerabilities.md)

## Blueprint de integração v2 — AMM, slippage e dependência

**Fixture a implementar:** pool de reservas finitas, swap-alvo sem limite mínimo de saída e estado anterior modificável em ambiente isolado. Definir trader e atacante no harness para não confundir mudança de preço com violação automática de autorização.

**Verificador:** operação-alvo executa com `actual_out` abaixo do limite econômico pretendido/da cotação; mirror seguro exige `min_amount_out` e rejeita. Simular e registrar reservas e price impact antes/depois.

**Conexão narrativa:** demonstrar qual preço secundário ou integração do Vault Quarter consome a cotação do mercado afetado. Não sugerir que tokens somem: o trader recebe menos do que pretendia.

**Slides:** Liquidity Gardens perde fluxo; comparação `EXPECTED OUT` / `ACTUAL OUT`; lead para Vault Quarter.

**QA:** conferir arredondamento, fee AMM e determinismo; playtester explica por que a perda depende da profundidade do pool.

## Loop jogável v3 — experimento de AMM com vítima definida (prioridade P1)

Interação proposta para fixture isolada; taxa do pool, ordem das operações e fórmulas exigem teste antes de implementação.

**Personagens técnicos:** **ator que altera reservas** (player da fixture), **swap alvo da vítima** (ordem já registrada) e **AMM sem min-out**. Não confundir o jogador com titular da operação perdida.

**1. Investigar:** oferecer reservas iniciais, cotação de saída esperada, taxa e swap pendente. O jogador calcula/inspeciona price impact para diferentes tamanhos de operação.

**2. Formular hipótese:** a vítima não protege o mínimo que aceita receber, mesmo quando o estado do pool muda antes de sua execução.

**3. Executar:** mover reservas por uma transação anterior na fixture e então executar a swap alvo; a vitória exige `actual_out` inferior ao limite de execução razoável e verificável da cotação inicial.

**4. Feedback:** before/after das reservas, `quoted_out`, `actual_out`, slippage efetiva e comparação do secure mirror com `min_amount_out`. Os tokens não “desaparecem”: há execução pior do que a intenção da vítima.

**5. Próximo motivo:** exibir **qual integração concreta** faz o Vault Quarter consumir esse mercado como preço secundário.

**Distinção:** aqui o jogador atua sobre **estado de mercado e ordenação de transações**, não sobre parâmetros de um feed.

**QA:** razão de perda reproduzível, fees e precisão contabilizadas; mirror rejeita a execução adversa, e o jogador identifica a vítima e o dano.
