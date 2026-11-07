---
notion_id: 4019c563-0425-81fc-a09d-edd78f2490ff
source: https://app.notion.com/p/4019c563042581fca09dedd78f2490ff?pvs=204
title: "🕰️ 01 — Stale Truth"
exported_at: 2026-11-07
---

Here is the result of "fetch" for the Page with URL https://app.notion.com/p/4019c563042581fca09dedd78f2490ff as of 2026-11-02T17:26:59.954Z:
<page url="https://app.notion.com/p/4019c563042581fca09dedd78f2490ff" icon="🕰️">
<ancestor-path>
<parent-page url="https://app.notion.com/p/4019c56304258155ac29c3ff5333a0af" title="04 — Cases & Bosses"/>
<ancestor-2-page url="https://app.notion.com/p/4019c563042581d9aedad3e5f178c3e8" title="Season 02 — DeFi Wars — Lumen"/>
<ancestor-3-page url="https://app.notion.com/p/4019c563042581469a0edc7e30a6eff9" title="ACT I — The World Is Breakable"/>
<ancestor-4-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
<properties>
{"title":"01 — Stale Truth"}
</properties>
<iconMetadata>{"type":"emoji","emoji":"🕰️"}</iconMetadata>
<content>
# Story

O Vault liquidado consumiu um preço antigo como se ainda fosse atual.

Rhea não precisou alterar o preço.

Alguém apenas deixou o sistema acreditar que uma verdade antiga continuava válida.

# Mission

> <b>Liquidate a healthy position using an old price.</b>

# Canonical Vulnerability

<b>Stale Oracle Price Acceptance — </b><b><code>stale_oracle</code></b><b>.</b>

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

<b>CASE 02 — FALSE CONFIDENCE</b>

# Reference

[https://github.com/Veritas-Vaults-Network/soroban-guard-contracts](https://github.com/Veritas-Vaults-Network/soroban-guard-contracts)

## Blueprint de integração v2 — Oracle freshness

<b>Fixture a implementar:</b> price + atualização/ledger + consumer de liquidation com política temporal insegura. O preço publicado permanece idêntico antes/depois; a diferença explorada é sua <b>idade</b> no momento da decisão. Evitar dependência de oráculos reais ou preços ao vivo.

<b>Verificador:</b> snapshot inicial de posição saudável com preço vigente; execução com feed stale produz liquidação que o mirror seguro recusa por expiração. Guardar timestamp, ledger de publicação e de consumo como prova.

<b>Conexão narrativa:</b> dois feeds referentes ao mesmo ativo mostram metadados diferentes; o segundo é recente, mas tem <code>CONFIDENCE</code> ignorada. Isso justifica Case 02 sem apresentar o nome do bug antes da vitória.

<b>Slides:</b> mostrar liquidação inexplicável → execução aceita → timestamp da fonte; relatório técnico separado. Nenhum número de preço deve contradizer o ratio de 168% do prólogo.

<b>Testes:</b> preço stale passa no vulnerável; é rejeitado no seguro; preço atualizado legítimo não cria false positive; reset/replay determinístico.

## Loop jogável v3 — auditoria temporal (prioridade P1)

<callout icon="🎮" color="blue_bg">
Especificação de experiência proposta para integração; não representa teste concluído nem altera a condição de vitória canônica.
</callout>

<b>1. Investigar:</b> mostrar posição de risco, timestamp/ledger da cotação e momento da liquidação. O jogador compara a última cotação publicada com uma referência mais recente disponível na fixture.

<b>2. Formular hipótese:</b> “A assinatura é válida, mas o consumidor aceita uma idade incompatível com a política de risco.” O nome <code>stale_oracle</code> só aparece no Breach Report após a vitória.

<b>3. Executar:</b> reproduzir no terminal uma liquidação usando a cotação antiga sem alterar seu preço; a posição seria saudável com feed atual válido. Não transformar o objetivo em apenas clicar “replay”.

<b>4. Feedback:</b> <code>PRICE SOURCE: SIGNED</code>, <code>AGE: OUTSIDE SAFE WINDOW</code> (esta pista pode ser derivada pelo jogador a partir dos dados), <code>LIQUIDATION: EXECUTED</code>. Segurança comparada: o mirror exige freshness.

<b>5. Próximo motivo:</b> um feed recente do mesmo ativo possui metadado <code>CONFIDENCE</code> que o consumidor descartou.

<b>Distinção:</b> a ferramenta cognitiva é <b>linha do tempo</b>, não comparar incerteza estatística.

<b>QA:</b> teste com feed recente passa normalmente; teste com feed stale passa no vulnerável, falha no seguro; o jogador consegue explicar por que a liquidação ocorreu.
</content>
</page>

