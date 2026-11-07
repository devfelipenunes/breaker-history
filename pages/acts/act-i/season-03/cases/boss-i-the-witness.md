---
notion_id: 4019c563-0425-81bf-844c-f3a8371eb2bc
source: https://app.notion.com/p/4019c563042581bf844cf3a8371eb2bc?pvs=204
title: "👁️ BOSS I — The Witness"
exported_at: 2026-11-07
---

**Sem vulnerabilidade nova. Boss de composição e perseguição.**

# História

First Witness alcança o Breaker.

Não pede prisão.

Pede disclosure.

> **“Entregue a chave.”**

Breaker:

> “Você não precisa ver tudo.”

First Witness:

> **“Você não decide o que eu preciso.”**

A fala não vem de sadismo.

First Witness já participou de investigações em que pessoas culpadas usaram exatamente a lógica de “privacidade” para impedir uma apuração legítima.

# Missão

> **Escape sem entregar uma visão completa.**

# Gameplay

O jogador combina:

- public storage awareness;
- event leakage;
- identity/profile state;
- association-set governance.

O objetivo é atravessar uma rota onde cada ação revela o mínimo possível e invalidar a associação falsa sem entregar acesso total.

# Resultado

Breaker escapa.

A Witness Spire muda de estratégia.

Se não consegue obrigá-lo a revelar, vai construir um caso técnico.

Primeira evidência:

NULLIFIER: USED TWICE
SUBJECT: BREAKER

Ao mesmo tempo, Rhea percebe que a investigação também pode chegar até ela por ser sender da settlement original.

Os dois continuam separados.

Mas agora estão presos ao mesmo caso.

Unlock:

**CASE 05 — SPENT TWICE**

## Blueprint de experiência v2 — vitória objetiva sem bug novo

**Missão:** escapar do checkpoint de investigação sem entregar view authority global, preservando a timeline de association. O boss compõe os quatro conceitos anteriores: segredo público comprometido, event leak, profile e governance.

**Ações:** identificar rota exposta; escolher/produzir um caminho que não reutiliza credencial pública vazada; controlar o que a operação emite; apresentar apenas âncoras históricas suficientes para atravessar o checkpoint. As opções são técnicas, **não** escolhas narrativas que criam finais distintos.

**Verifier de design:** **route\_checkpoint\_reached**, **no\_full\_view\_key\_disclosure**, **no\_reuse\_of\_known\_leaked\_secret**, **no\_new\_sensitive\_event\_leak**, **timeline\_evidence\_preserved**. O fluxo e APIs ainda dependem de fixture.

**Consequência:** a fuga é real, mas provisória. First Witness não se torna vilão ou desaparece; passa à evidência de nullifier duplicado. Nenhum material da rota de fuga precisa provar inocência ainda.

**QA:** caso positivo, tentativa de entregar view key, reuso de credencial vazada, evento excessivo, e route checkpoint sem timeline precisam ser testados. Ver [10 — The Witness & Witness Spire — Blueprints Técnicos](../world/10-the-witness-witness-spire-blueprints-tecnicos.md).
