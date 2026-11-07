---
notion_id: 4019c563-0425-81fc-a09d-edd78f2490ff
source: https://app.notion.com/p/4019c563042581fca09dedd78f2490ff?pvs=204
title: "🕰️ 01 — Stale Truth"
exported_at: 2026-11-07
---

# Story

O Vault liquidado consumiu um preço antigo como se ainda fosse atual.

Rhea não precisou alterar o preço.

Alguém apenas deixou o sistema acreditar que uma verdade antiga continuava válida.

# Mission

> **Liquidate a healthy position using an old price.**

# Canonical Vulnerability

**Stale Oracle Price Acceptance — **`stale_oracle`**.**

O contrato lê o último preço disponível sem validar idade, ledger de atualização ou freshness window.

# Learning

- oracle data has a timestamp/ledger context;
- “signed price” não significa “current price”;
- consumers precisam validar freshness;
- liquidation logic is only as good as its data dependencies.

# Win Condition

Reproduzir a liquidação com um feed stale sem modificar o preço armazenado.

# Narrative Result

O jogador encontra outro feed do mesmo ativo com valor próximo, mas metadata diferente.

Um campo foi descartado:

CONFIDENCE: █████

Unlock:

**CASE 02 — FALSE CONFIDENCE**

# Reference

[https://github.com/Veritas-Vaults-Network/soroban-guard-contracts](https://github.com/Veritas-Vaults-Network/soroban-guard-contracts)

## Blueprint de integração v2 — Oracle freshness

**Fixture a implementar:** price + atualização/ledger + consumer de liquidation com política temporal insegura. O preço publicado permanece idêntico antes/depois; a diferença explorada é sua **idade** no momento da decisão. Evitar dependência de oráculos reais ou preços ao vivo.

**Verificador:** snapshot inicial de posição saudável com preço vigente; execução com feed stale produz liquidação que o mirror seguro recusa por expiração. Guardar timestamp, ledger de publicação e de consumo como prova.

**Conexão narrativa:** dois feeds referentes ao mesmo ativo mostram metadados diferentes; o segundo é recente, mas tem `CONFIDENCE` ignorada. Isso justifica Case 02 sem apresentar o nome do bug antes da vitória.

**Slides:** mostrar liquidação inexplicável → execução aceita → timestamp da fonte; relatório técnico separado. Nenhum número de preço deve contradizer o ratio de 168% do prólogo.

**Testes:** preço stale passa no vulnerável; é rejeitado no seguro; preço atualizado legítimo não cria false positive; reset/replay determinístico.

## Loop jogável v3 — auditoria temporal (prioridade P1)

Especificação de experiência proposta para integração; não representa teste concluído nem altera a condição de vitória canônica.

**1. Investigar:** mostrar posição de risco, timestamp/ledger da cotação e momento da liquidação. O jogador compara a última cotação publicada com uma referência mais recente disponível na fixture.

**2. Formular hipótese:** “A assinatura é válida, mas o consumidor aceita uma idade incompatível com a política de risco.” O nome `stale_oracle` só aparece no Breach Report após a vitória.

**3. Executar:** reproduzir no terminal uma liquidação usando a cotação antiga sem alterar seu preço; a posição seria saudável com feed atual válido. Não transformar o objetivo em apenas clicar “replay”.

**4. Feedback:** `PRICE SOURCE: SIGNED`, `AGE: OUTSIDE SAFE WINDOW` (esta pista pode ser derivada pelo jogador a partir dos dados), `LIQUIDATION: EXECUTED`. Segurança comparada: o mirror exige freshness.

**5. Próximo motivo:** um feed recente do mesmo ativo possui metadado `CONFIDENCE` que o consumidor descartou.

**Distinção:** a ferramenta cognitiva é **linha do tempo**, não comparar incerteza estatística.

**QA:** teste com feed recente passa normalmente; teste com feed stale passa no vulnerável, falha no seguro; o jogador consegue explicar por que a liquidação ocorreu.
