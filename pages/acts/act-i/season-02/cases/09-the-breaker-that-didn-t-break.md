---
notion_id: 4019c563-0425-81a4-96dd-e84d8688d04f
source: https://app.notion.com/p/4019c563042581a496dde84d8688d04f?pvs=204
title: "🛑 09 — The Breaker That Didn't Break"
exported_at: 2026-11-07
---

# Story

Lumen possui uma proteção explícita contra movimentos extremos.

MAX\_PRICE\_MOVE: CONFIGURED
CIRCUIT\_BREAKER: ENABLED

Mas a regra nunca é aplicada no caminho crítico.

A segurança existe apenas no dashboard.

# Mission

> **Atravesse o limite de segurança sem parar o mercado.**

# Canonical Vulnerability

**Inactive Circuit Breaker — **`inactive_circuit_breaker`**.**

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

**CASE 10 — EMERGENCY AUTHORITY**

# Reference

[https://github.com/Veritas-Vaults-Network/soroban-guard-contracts](https://github.com/Veritas-Vaults-Network/soroban-guard-contracts)

## Blueprint de integração v2 — controle configurado vs enforce

**Fixture:** rota de execução com limite `MAX_PRICE_MOVE` e flag `CIRCUIT_BREAKER: ENABLED`, mas chamada crítica ignora a condição ou apenas registra log sem interromper a operação.

**Verifier:** movimento excede threshold configurado e a operação completa; mirror seguro pausa/reverte a execução no mesmo estado. O teste precisa capturar a diferença entre configurar e efetivamente proteger.

**Conexão narrativa:** o player entende por que Rhea tentou a emergency layer: a proteção normal não interrompe a Cascade. Isso conduz ao Emergency Dispatcher do Case 10.

**Slides:** `SAFETY: ENABLED` / `THRESHOLD: EXCEEDED` / `TRANSACTION: ACCEPTED`.

**QA:** verificar tanto o caminho crítico quanto o caminho auxiliar; não tratar existência de parâmetro como mitigação real.

## Loop jogável v3 — rastreamento do caminho crítico (P1)

Não basta observar que o botão de emergência está “ON”. A ação técnica do jogador deve demonstrar a diferença entre **configuração declarada** e **proteção efetivamente aplicada**.

**1. Investigar:** o jogador compara configuração do circuit breaker, regra de threshold, logs auxiliares e caminho real da operação de execução do mercado.

**2. Formular hipótese:** o sistema lê o parâmetro de segurança, mas não executa a condição de pause/revert no ponto onde se conclui a operação.

**3. Executar:** reproduzir um price move acima do limite e provar que swap/liquidation crítica finaliza mesmo assim; mirror seguro bloqueia a execução com a mesma entrada.

**4. Feedback:** `PROTECTION ENABLED` / `THRESHOLD EXCEEDED` / `OPERATION ACCEPTED`; trace marca onde o invariant deveria ter sido verificado.

**5. Gancho:** a rota normal de segurança não vai deter a Cascade; o Emergency Dispatcher oferece o último caminho, apesar de sua própria fragilidade.

**Diferencial:** **auditoria do fluxo de execução**, não apenas alterar janela de TWAP como no Case 08.

**QA:** casos abaixo/acima do threshold, fluxo principal e auxiliar, secure mirror e verificador independente.
