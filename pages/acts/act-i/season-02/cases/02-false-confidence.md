---
notion_id: 4019c563-0425-815e-a749-f6cd17dbf305
source: https://app.notion.com/p/4019c5630425815ea749f6cd17dbf305?pvs=204
title: "📡 02 — False Confidence"
exported_at: 2026-11-07
---

Here is the result of "fetch" for the Page with URL https://app.notion.com/p/4019c5630425815ea749f6cd17dbf305 as of 2026-11-02T17:27:02.110Z:
<page url="https://app.notion.com/p/4019c5630425815ea749f6cd17dbf305" icon="📡">
<ancestor-path>
<parent-page url="https://app.notion.com/p/4019c56304258155ac29c3ff5333a0af" title="04 — Cases & Bosses"/>
<ancestor-2-page url="https://app.notion.com/p/4019c563042581d9aedad3e5f178c3e8" title="Season 02 — DeFi Wars — Lumen"/>
<ancestor-3-page url="https://app.notion.com/p/4019c563042581469a0edc7e30a6eff9" title="ACT I — The World Is Breakable"/>
<ancestor-4-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
<properties>
{"title":"02 — False Confidence"}
</properties>
<iconMetadata>{"type":"emoji","emoji":"📡"}</iconMetadata>
<content>
# Story

O Oracle não publica apenas preço.

Publica também o grau de confiança daquele preço.

O protocolo de risco de Lumen usa o número e ignora a incerteza.

# Mission

> <b>Make an uncertain price behave like a certain one.</b>

# Canonical Vulnerability

<b>Oracle Confidence Ignored — </b><b><code>oracle_confidence_ignored</code></b><b>.</b>

Um preço de baixa confiança é usado para collateral valuation e liquidation como se tivesse a mesma qualidade de um preço estável.

# Learning

- data feeds have quality, not only value;
- confidence intervals matter;
- liquidation thresholds must account for uncertainty;
- oracle consumption is a risk model, not just a getter.

# Win Condition

Forçar uma liquidation utilizando um preço cuja confidence deveria impedir a ação.

# Narrative Result

O Breaker encontra transações de Rhea próximas às posições vulneráveis.

Mas uma coisa não fecha:

ela não está lucrando.

Ela está reduzindo exposição.

Antes que ele consiga entender por quê, uma grande swap drena profundidade de um pool.

Unlock:

<b>CASE 03 — THE DRY POOL</b>

# Reference

[https://github.com/Veritas-Vaults-Network/soroban-guard-contracts](https://github.com/Veritas-Vaults-Network/soroban-guard-contracts)

## Blueprint de integração v2 — Confidence ≠ Freshness

<b>Fixture a implementar:</b> feed recente com intervalo/medida de incerteza definida e consumer que usa apenas o valor central para collateral/liquidation. Fixar no challenge a interpretação exata de confidence (unidades/escala) para evitar leitura ambígua.

<b>Verificador:</b> prova que a liquidation ocorre apesar de confidence fora da política, enquanto o mirror seguro bloqueia a operação ou aplica política conservadora previamente documentada. Não reutilizar stale como causa do sucesso.

<b>Conexão narrativa:</b> o registro de Rhea mostra redução de exposição, sem ganho demonstrado; a próxima evidência é uma swap grande afetando profundidade nos Liquidity Gardens. Suspeita é hipótese, não prova de autoria.

<b>Slides:</b> exibir valor semelhante com qualidade diferente; só depois mostrar a fragilidade. Debrief nomeia o uso indevido do confidence.

<b>QA:</b> jogadores distinguem preços antigos de preços presentes porém incertos; testes positivos/negativos de threshold e boundary.

## Loop jogável v3 — comparação da qualidade dos dados (prioridade P1)

<callout icon="🎮" color="blue_bg">
Especificação de gameplay; sem alterar vulnerabilidade nem resultado narrativo.
</callout>

<b>1. Investigar:</b> mostrar dois reports de preço recentes, com preço semelhante, mas intervalos/medidas de confidence diferentes. O jogador verifica a política de risco do consumidor. A unidade e semântica de confidence devem ser definidas na fixture.

<b>2. Formular hipótese:</b> um valor atual não é necessariamente adequado para liquidação quando sua incerteza ultrapassa limites.

<b>3. Executar:</b> usar o report de baixa confiança para reproduzir liquidation que deveria ser impedida pela política segura; não recorrer a feed stale, que pertence ao Case 01.

<b>4. Feedback:</b> mostrar <code>PRICE AGE: OK</code> e <code>CONFIDENCE: OUT OF POLICY</code> junto ao resultado de risco. O mirror de segurança rejeita ou aplica fallback conservador definido antecipadamente.

<b>5. Próximo motivo:</b> histórico de Rhea indica redução de risco, não lucro; uma swap grande afeta a profundidade do pool no Liquidity Gardens.

<b>Distinção:</b> investigação por <b>qualidade de fonte e política de risco</b>, não idade de dados.

<b>QA:</b> testar confidence perto do threshold, amostra segura e amostra insegura; playtester explica diferença entre Case 01 e Case 02.
</content>
</page>

