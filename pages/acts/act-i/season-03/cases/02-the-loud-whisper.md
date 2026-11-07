---
notion_id: 4019c563-0425-810a-af92-d528f2575dde
source: https://app.notion.com/p/4019c5630425810aaf92d528f2575dde?pvs=204
title: "📢 02 — The Loud Whisper"
exported_at: 2026-11-07
---

# Story

Uma operação é corretamente confidencial no estado principal.

Mas o evento emitido pelo contrato publica dados sensíveis suficientes para reconstruir o que deveria permanecer oculto.

# Mission

> **Recupere pelo evento aquilo que o state tenta esconder.**

# Canonical Vulnerability

**Sensitive Data Leakage via Events — **`leaky_events`**.**

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

**CASE 03 — SOMEONE ELSE'S FACE**

# Reference

[https://github.com/Veritas-Vaults-Network/soroban-guard-contracts](https://github.com/Veritas-Vaults-Network/soroban-guard-contracts)

## Loop jogável v2 — reconstrução a partir de eventos

**Investigar:** contrato protegido por commitment/ciphertext na área onde deveriam estar dados sensíveis; event topics/data expõem partes de relação ou payload. Exibir no Breaker OS fonte de cada campo.

**Hipótese:** os eventos formam uma superfície pública independente do storage; a emissão verbosa pode violar a política de disclosure.

**Executar:** correlacionar eventos de fixture e reconstruir um fato sensível preciso sem conseguir decifrar a área protegida. Não pedir ao jogador para “ler storage secreto”.

**Feedback/verifier:** prova de inferência com IDs de events e cálculo de correlação; mirror seguro emite dados mínimos e impede dedução da propriedade escolhida. Eventos de transação revertida não devem ser considerados publicados.

**Conseqüência:** monitoramento público revela profile/association DENIED; próximo Case examina integridade de identidade. A ferramenta cognitiva é **event correlation**, diferente de Case 01.
