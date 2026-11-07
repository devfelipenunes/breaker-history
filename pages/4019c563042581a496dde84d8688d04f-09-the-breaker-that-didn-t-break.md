---
notion_id: 4019c563-0425-81a4-96dd-e84d8688d04f
source: https://app.notion.com/p/4019c563042581a496dde84d8688d04f?pvs=204
title: "🛑 09 — The Breaker That Didn't Break"
exported_at: 2026-11-07
---

Here is the result of "fetch" for the Page with URL https://app.notion.com/p/4019c563042581a496dde84d8688d04f as of 2026-11-02T17:28:06.300Z:
<page url="https://app.notion.com/p/4019c563042581a496dde84d8688d04f" icon="🛑">
<ancestor-path>
<parent-page url="https://app.notion.com/p/4019c56304258155ac29c3ff5333a0af" title="04 — Cases & Bosses"/>
<ancestor-2-page url="https://app.notion.com/p/4019c563042581d9aedad3e5f178c3e8" title="Season 02 — DeFi Wars — Lumen"/>
<ancestor-3-page url="https://app.notion.com/p/4019c563042581469a0edc7e30a6eff9" title="ACT I — The World Is Breakable"/>
<ancestor-4-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
<properties>
{"title":"09 — The Breaker That Didn't Break"}
</properties>
<iconMetadata>{"type":"emoji","emoji":"🛑"}</iconMetadata>
<content>
# Story

Lumen possui uma proteção explícita contra movimentos extremos.

MAX\_PRICE\_MOVE: CONFIGURED<br />CIRCUIT\_BREAKER: ENABLED

Mas a regra nunca é aplicada no caminho crítico.

A segurança existe apenas no dashboard.

# Mission

> <b>Atravesse o limite de segurança sem parar o mercado.</b>

# Canonical Vulnerability

<b>Inactive Circuit Breaker — </b><b><code>inactive_circuit_breaker</code></b><b>.</b>

# Learning

- configuration that is read but not enforced;
- defense-in-depth must exist on execution path;
- “feature present” ≠ invariant enforced;
- emergency design requires testable behavior.

# Win Condition

Produzir price move acima do limite sem disparar pause/revert.

# Narrative Result

O Breaker entende por que Rhea tentou entrar no emergency layer.

O sistema de segurança oficial não vai parar a cascata.

Existe uma última rota: o Emergency Dispatcher.

Só que ele também está errado.

Unlock:

<b>CASE 10 — EMERGENCY AUTHORITY</b>

# Reference

[https://github.com/Veritas-Vaults-Network/soroban-guard-contracts](https://github.com/Veritas-Vaults-Network/soroban-guard-contracts)

## Blueprint de integração v2 — controle configurado vs enforce

<b>Fixture:</b> rota de execução com limite <code>MAX_PRICE_MOVE</code> e flag <code>CIRCUIT_BREAKER: ENABLED</code>, mas chamada crítica ignora a condição ou apenas registra log sem interromper a operação.

<b>Verifier:</b> movimento excede threshold configurado e a operação completa; mirror seguro pausa/reverte a execução no mesmo estado. O teste precisa capturar a diferença entre configurar e efetivamente proteger.

<b>Conexão narrativa:</b> o player entende por que Rhea tentou a emergency layer: a proteção normal não interrompe a Cascade. Isso conduz ao Emergency Dispatcher do Case 10.

<b>Slides:</b> <code>SAFETY: ENABLED</code> / <code>THRESHOLD: EXCEEDED</code> / <code>TRANSACTION: ACCEPTED</code>.

<b>QA:</b> verificar tanto o caminho crítico quanto o caminho auxiliar; não tratar existência de parâmetro como mitigação real.

## Loop jogável v3 — rastreamento do caminho crítico (P1)

<callout icon="🎮" color="blue_bg">
Não basta observar que o botão de emergência está “ON”. A ação técnica do jogador deve demonstrar a diferença entre <b>configuração declarada</b> e <b>proteção efetivamente aplicada</b>.
</callout>

<b>1. Investigar:</b> o jogador compara configuração do circuit breaker, regra de threshold, logs auxiliares e caminho real da operação de execução do mercado.

<b>2. Formular hipótese:</b> o sistema lê o parâmetro de segurança, mas não executa a condição de pause/revert no ponto onde se conclui a operação.

<b>3. Executar:</b> reproduzir um price move acima do limite e provar que swap/liquidation crítica finaliza mesmo assim; mirror seguro bloqueia a execução com a mesma entrada.

<b>4. Feedback:</b> <code>PROTECTION ENABLED</code> / <code>THRESHOLD EXCEEDED</code> / <code>OPERATION ACCEPTED</code>; trace marca onde o invariant deveria ter sido verificado.

<b>5. Gancho:</b> a rota normal de segurança não vai deter a Cascade; o Emergency Dispatcher oferece o último caminho, apesar de sua própria fragilidade.

<b>Diferencial:</b> <b>auditoria do fluxo de execução</b>, não apenas alterar janela de TWAP como no Case 08.

<b>QA:</b> casos abaixo/acima do threshold, fluxo principal e auxiliar, secure mirror e verificador independente.
</content>
</page>

