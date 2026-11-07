---
notion_id: 4019c563-0425-81b3-a027-e02784354352
source: https://app.notion.com/p/4019c563042581b3a027e02784354352?pvs=204
title: "🎭 03 — Someone Else's Face"
exported_at: 2026-11-07
---

Here is the result of "fetch" for the Page with URL https://app.notion.com/p/4019c563042581b3a027e02784354352 as of 2026-11-02T17:40:27.497Z:
<page url="https://app.notion.com/p/4019c563042581b3a027e02784354352" icon="🎭">
<ancestor-path>
<parent-page url="https://app.notion.com/p/4019c563042581a2a331e66548c30494" title="04 — Cases & Bosses"/>
<ancestor-2-page url="https://app.notion.com/p/4019c56304258179bfa0fc93d15ac390" title="Season 03 — Shadows of Privacy — Moonlight"/>
<ancestor-3-page url="https://app.notion.com/p/4019c563042581469a0edc7e30a6eff9" title="ACT I — The World Is Breakable"/>
<ancestor-4-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
<properties>
{"title":"03 — Someone Else's Face"}
</properties>
<iconMetadata>{"type":"emoji","emoji":"🎭"}</iconMetadata>
<content>
# Story

O profile de risco do Breaker mudou.

ASSOCIATION: DENIED<br />RISK: CRITICAL

A alteração existe onchain.

Mas não foi autorizada por ele nem por uma autoridade legítima.

# Mission

> <b>Mude quem o sistema acredita que alguém é.</b>

# Canonical Vulnerability

<b>Unsafe Storage Write / Unauthorized Profile Mutation — </b><b><code>unsafe_storage</code></b><b>.</b>

Um registry aceita escrever no slot/profile de outra Address sem exigir a autorização correta ou autoridade competente.

# Learning

- storage ownership;
- auth must match the subject whose state changes;
- identity metadata can be an authorization surface;
- forged state can be more dangerous than stolen credentials.

# Win Condition

Alterar o profile de um endereço alvo sem possuir a autoridade que deveria ser exigida.

# Narrative Result

O Breaker encontra quem ganhou capacidade de alterar as association sets.

Era um admin transfer cancelado.

Ou deveria ter sido.

Unlock:

<b>CASE 04 — THE DENIED</b>

# Reference

[https://github.com/Veritas-Vaults-Network/soroban-guard-contracts](https://github.com/Veritas-Vaults-Network/soroban-guard-contracts)

## Loop jogável v2 — falsificação de perfil versus autoria histórica

<callout icon="⚠️" color="yellow_bg">
<b>Distinção obrigatória:</b> esta fixture demonstra que um registry inadequado permite mutação não autorizada de profile. Isso <b>não demonstra por si só</b> que esse foi o caminho utilizado na associação DENIED histórica do Breaker. A origem histórica específica depende da governança comprometida do Case 04.
</callout>

<b>Investigar:</b> profile de endereço-alvo, função de mutação, auth do caller e auth do subject; comparar a intenção da operação com o slot realmente alterado.

<b>Executar:</b> alterar na fixture o profile de um target sem sua autorização e sem permissão de registry legítima. Não manipular identidades reais.

<b>Verifier:</b> detectar <b>target profile changed</b> + <b>required subject/authority auth absent</b>; mirror seguro exige sujeito correto ou autoridade de sistema com escopo. Testar mudança de outro target e tentativa legitimamente autorizada.

<b>Conseqüência:</b> o Breaker tem prova de fragilidade do modelo, mas encontra um rastro mais específico: cancelamento administrativo que não limpou pending state. A fase seguinte responde <b>quem tinha autoridade na cronologia real</b>, não apenas “é possível forjar”.
</content>
</page>

