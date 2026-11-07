---
notion_id: 4019c563-0425-81fb-b26e-f86004353e0a
source: https://app.notion.com/p/4019c563042581fbb26ef86004353e0a?pvs=204
title: "📊 08 — One-Ledger Average"
exported_at: 2026-11-07
---

Here is the result of "fetch" for the Page with URL https://app.notion.com/p/4019c563042581fbb26ef86004353e0a as of 2026-11-02T17:28:04.608Z:
<page url="https://app.notion.com/p/4019c563042581fbb26ef86004353e0a" icon="📊">
<ancestor-path>
<parent-page url="https://app.notion.com/p/4019c56304258155ac29c3ff5333a0af" title="04 — Cases & Bosses"/>
<ancestor-2-page url="https://app.notion.com/p/4019c563042581d9aedad3e5f178c3e8" title="Season 02 — DeFi Wars — Lumen"/>
<ancestor-3-page url="https://app.notion.com/p/4019c563042581469a0edc7e30a6eff9" title="ACT I — The World Is Breakable"/>
<ancestor-4-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
<properties>
{"title":"08 — One-Ledger Average"}
</properties>
<iconMetadata>{"type":"emoji","emoji":"📊"}</iconMetadata>
<content>
# Story

O sistema afirma usar um preço médio para resistir a manipulação.

A configuração do TWAP aceita uma janela de um único ledger.

Na prática, o “average” vira spot price.

# Mission

> <b>Turn an average into an instant.</b>

# Canonical Vulnerability

<b>TWAP Window Too Short — </b><b><code>twap_window_too_short</code></b><b>.</b>

# Learning

- TWAP purpose;
- manipulation resistance depends on window;
- configuration can destroy a security property without changing code;
- safe defaults and lower bounds matter.

# Win Condition

Configurar/usar uma janela mínima que faça o TWAP seguir o preço manipulável de um único ledger.

# Narrative Result

Uma variação extrema deveria acionar o circuit breaker de Lumen.

O threshold está configurado.

O código lê o valor.

Nada acontece.

Unlock:

<b>CASE 09 — THE BREAKER THAT DIDN'T BREAK</b>

# Reference

[https://github.com/Veritas-Vaults-Network/soroban-guard-contracts](https://github.com/Veritas-Vaults-Network/soroban-guard-contracts)

## Blueprint de integração v2 — configuração anula a proteção

<b>Fixture:</b> série histórica de preços e módulo TWAP com janela configurável; a janela aceita um ledger, resultando em baixa resistência à manipulação da última observação. Definir pesos e o algoritmo de média na fixture.

<b>Verifier:</b> TWAP indevidamente segue a distorção de curtíssimo prazo; mirror seguro aplica janela mínima e política de amostragem, produzindo saída divergente sob o mesmo cenário.

<b>Conexão narrativa:</b> o movimento anormal deveria cruzar o threshold do circuit breaker e impedir a ação crítica, mas a execução continua.

<b>Slides:</b> não chamar a média de insegura por ser “média” em si; apresentar a diferença entre proteção anunciada e janela efetiva.

<b>QA:</b> testar séries e boundary de um ledger versus janelas > mínimo, evitando depender de variação temporal não determinística.

## Loop jogável v3 — laboratório de janela temporal (P1)

<callout icon="🎮" color="blue_bg">
O foco é <b>configuração e séries históricas</b> — distinto de freshness, confidence e de um circuit breaker que não executa.
</callout>

<b>1. Investigar:</b> ver observações de preço em vários ledgers e política TWAP publicada. O jogador pode inspecionar como a janela escolhe observações; fórmula e ponderações precisam estar definidas na fixture.

<b>2. Formular hipótese:</b> quando a janela é um ledger, uma distorção momentânea domina a média e rompe a resistência que o protocolo anuncia.

<b>3. Executar:</b> usar a configuração mínima aceita pelo contrato e uma série determinística com breve distorção; provar que o TWAP acompanha praticamente o spot naquele momento.

<b>4. Feedback:</b> <code>WINDOW: 1 LEDGER</code>, valores de spot e TWAP com histórico curto versus janela segura, sem entregar a vulnerabilidade antes da vitória.

<b>5. Gancho:</b> o valor extremo deveria acionar controle de preço de execução; registro mostra proteção configurada porém sem pause.

<b>Diferencial:</b> <b>parametrização e cálculo estatístico</b>, não autorização e não ausência de enforcement.

<b>QA:</b> variáveis controladas, médias verificadas, parâmetros boundary; mirror seguro usa janela mínima adequada e rejeita configuração indevida.
</content>
</page>

