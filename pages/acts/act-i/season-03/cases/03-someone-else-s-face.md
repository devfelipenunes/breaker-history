---
notion_id: 4019c563-0425-81b3-a027-e02784354352
source: https://app.notion.com/p/4019c563042581b3a027e02784354352?pvs=204
title: "🎭 03 — Someone Else's Face"
exported_at: 2026-11-07
---

# Story

O profile de risco do Breaker mudou.

ASSOCIATION: DENIED
RISK: CRITICAL

A alteração existe onchain.

Mas não foi autorizada por ele nem por uma autoridade legítima.

# Mission

> **Mude quem o sistema acredita que alguém é.**

# Canonical Vulnerability

**Unsafe Storage Write / Unauthorized Profile Mutation — **`unsafe_storage`**.**

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

**CASE 04 — THE DENIED**

# Reference

[https://github.com/Veritas-Vaults-Network/soroban-guard-contracts](https://github.com/Veritas-Vaults-Network/soroban-guard-contracts)

## Loop jogável v2 — falsificação de perfil versus autoria histórica

**Distinção obrigatória:** esta fixture demonstra que um registry inadequado permite mutação não autorizada de profile. Isso **não demonstra por si só** que esse foi o caminho utilizado na associação DENIED histórica do Breaker. A origem histórica específica depende da governança comprometida do Case 04.

**Investigar:** profile de endereço-alvo, função de mutação, auth do caller e auth do subject; comparar a intenção da operação com o slot realmente alterado.

**Executar:** alterar na fixture o profile de um target sem sua autorização e sem permissão de registry legítima. Não manipular identidades reais.

**Verifier:** detectar **target profile changed** + **required subject/authority auth absent**; mirror seguro exige sujeito correto ou autoridade de sistema com escopo. Testar mudança de outro target e tentativa legitimamente autorizada.

**Conseqüência:** o Breaker tem prova de fragilidade do modelo, mas encontra um rastro mais específico: cancelamento administrativo que não limpou pending state. A fase seguinte responde **quem tinha autoridade na cronologia real**, não apenas “é possível forjar”.
