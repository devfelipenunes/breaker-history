---
notion_id: 4019c563-0425-81bf-844c-f3a8371eb2bc
source: https://app.notion.com/p/4019c563042581bf844cf3a8371eb2bc?pvs=204
title: "👁️ BOSS I — The Witness"
exported_at: 2026-11-07
---

Here is the result of "fetch" for the Page with URL https://app.notion.com/p/4019c563042581bf844cf3a8371eb2bc as of 2026-11-02T17:40:32.109Z:
<page url="https://app.notion.com/p/4019c563042581bf844cf3a8371eb2bc" icon="👁️">
<ancestor-path>
<parent-page url="https://app.notion.com/p/4019c563042581a2a331e66548c30494" title="04 — Cases & Bosses"/>
<ancestor-2-page url="https://app.notion.com/p/4019c56304258179bfa0fc93d15ac390" title="Season 03 — Shadows of Privacy — Moonlight"/>
<ancestor-3-page url="https://app.notion.com/p/4019c563042581469a0edc7e30a6eff9" title="ACT I — The World Is Breakable"/>
<ancestor-4-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
<properties>
{"title":"BOSS I — The Witness"}
</properties>
<iconMetadata>{"type":"emoji","emoji":"👁️"}</iconMetadata>
<content>
<callout icon="👁️" color="red_bg">
<b>Sem vulnerabilidade nova. Boss de composição e perseguição.</b>
</callout>

# História

First Witness alcança o Breaker.

Não pede prisão.

Pede disclosure.

> <b>“Entregue a chave.”</b>

Breaker:

> “Você não precisa ver tudo.”

First Witness:

> <b>“Você não decide o que eu preciso.”</b>

A fala não vem de sadismo.

First Witness já participou de investigações em que pessoas culpadas usaram exatamente a lógica de “privacidade” para impedir uma apuração legítima.

# Missão

> <b>Escape sem entregar uma visão completa.</b>

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

NULLIFIER: USED TWICE<br />SUBJECT: BREAKER

Ao mesmo tempo, Rhea percebe que a investigação também pode chegar até ela por ser sender da settlement original.

Os dois continuam separados.

Mas agora estão presos ao mesmo caso.

Unlock:

<b>CASE 05 — SPENT TWICE</b>

## Blueprint de experiência v2 — vitória objetiva sem bug novo

<b>Missão:</b> escapar do checkpoint de investigação sem entregar view authority global, preservando a timeline de association. O boss compõe os quatro conceitos anteriores: segredo público comprometido, event leak, profile e governance.

<b>Ações:</b> identificar rota exposta; escolher/produzir um caminho que não reutiliza credencial pública vazada; controlar o que a operação emite; apresentar apenas âncoras históricas suficientes para atravessar o checkpoint. As opções são técnicas, <b>não</b> escolhas narrativas que criam finais distintos.

<b>Verifier de design:</b> <b>route\_checkpoint\_reached</b>, <b>no\_full\_view\_key\_disclosure</b>, <b>no\_reuse\_of\_known\_leaked\_secret</b>, <b>no\_new\_sensitive\_event\_leak</b>, <b>timeline\_evidence\_preserved</b>. O fluxo e APIs ainda dependem de fixture.

<b>Consequência:</b> a fuga é real, mas provisória. First Witness não se torna vilão ou desaparece; passa à evidência de nullifier duplicado. Nenhum material da rota de fuga precisa provar inocência ainda.

<b>QA:</b> caso positivo, tentativa de entregar view key, reuso de credencial vazada, evento excessivo, e route checkpoint sem timeline precisam ser testados. Ver <mention url="https://app.notion.com/p/40c9c563042581df836bcef78dcb861a" />.
</content>
</page>

