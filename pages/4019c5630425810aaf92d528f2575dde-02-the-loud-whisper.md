---
notion_id: 4019c563-0425-810a-af92-d528f2575dde
source: https://app.notion.com/p/4019c5630425810aaf92d528f2575dde?pvs=204
title: "📢 02 — The Loud Whisper"
exported_at: 2026-11-07
---

Here is the result of "fetch" for the Page with URL https://app.notion.com/p/4019c5630425810aaf92d528f2575dde as of 2026-11-02T17:40:25.828Z:
<page url="https://app.notion.com/p/4019c5630425810aaf92d528f2575dde" icon="📢">
<ancestor-path>
<parent-page url="https://app.notion.com/p/4019c563042581a2a331e66548c30494" title="04 — Cases & Bosses"/>
<ancestor-2-page url="https://app.notion.com/p/4019c56304258179bfa0fc93d15ac390" title="Season 03 — Shadows of Privacy — Moonlight"/>
<ancestor-3-page url="https://app.notion.com/p/4019c563042581469a0edc7e30a6eff9" title="ACT I — The World Is Breakable"/>
<ancestor-4-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
<properties>
{"title":"02 — The Loud Whisper"}
</properties>
<iconMetadata>{"type":"emoji","emoji":"📢"}</iconMetadata>
<content>
# Story

Uma operação é corretamente confidencial no estado principal.

Mas o evento emitido pelo contrato publica dados sensíveis suficientes para reconstruir o que deveria permanecer oculto.

# Mission

> <b>Recupere pelo evento aquilo que o state tenta esconder.</b>

# Canonical Vulnerability

<b>Sensitive Data Leakage via Events — </b><b><code>leaky_events</code></b><b>.</b>

# Learning

- events are public observability surfaces;
- privacy design must include logs/events;
- a secure state model can be defeated by verbose telemetry;
- emit minimum necessary data.

# Win Condition

Reconstruir informação confidencial apenas a partir dos eventos publicados.

# Narrative Result

O Breaker percebe que Moonlight pode vazar sem “quebrar o Veil”.

Ao consultar seu próprio compliance profile, encontra algo pior:

ele foi marcado com uma associação que nunca autorizou.

Unlock:

<b>CASE 03 — SOMEONE ELSE'S FACE</b>

# Reference

[https://github.com/Veritas-Vaults-Network/soroban-guard-contracts](https://github.com/Veritas-Vaults-Network/soroban-guard-contracts)

## Loop jogável v2 — reconstrução a partir de eventos

<b>Investigar:</b> contrato protegido por commitment/ciphertext na área onde deveriam estar dados sensíveis; event topics/data expõem partes de relação ou payload. Exibir no Breaker OS fonte de cada campo.

<b>Hipótese:</b> os eventos formam uma superfície pública independente do storage; a emissão verbosa pode violar a política de disclosure.

<b>Executar:</b> correlacionar eventos de fixture e reconstruir um fato sensível preciso sem conseguir decifrar a área protegida. Não pedir ao jogador para “ler storage secreto”.

<b>Feedback/verifier:</b> prova de inferência com IDs de events e cálculo de correlação; mirror seguro emite dados mínimos e impede dedução da propriedade escolhida. Eventos de transação revertida não devem ser considerados publicados.

<b>Conseqüência:</b> monitoramento público revela profile/association DENIED; próximo Case examina integridade de identidade. A ferramenta cognitiva é <b>event correlation</b>, diferente de Case 01.
</content>
</page>

