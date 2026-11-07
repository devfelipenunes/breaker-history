---
notion_id: 4019c563-0425-819c-b20a-c8462a316cb0
source: https://app.notion.com/p/4019c5630425819cb20ac8462a316cb0?pvs=204
title: "♻️ 05 — Spent Twice"
exported_at: 2026-11-07
---

# História

O sistema acusa o Breaker de double-spend em um privacy pool.

O nullifier ligado a uma note aparece duas vezes.

A prova parece suficiente.

Mas o pool não valida corretamente o estado de nullifiers já gastos.

# Missão

> **Gaste a mesma private note duas vezes.**

# Vulnerabilidade canônica / falha de invariant

**Nullifier Replay / Missing Spent-Nullifier Validation.**

Nullifiers precisam ser calculados corretamente e rejeitados após o primeiro spend.

# Aprendizado

- commitments vs nullifiers;
- por que privacy pools precisam de um spent signal público;
- privacy pode esconder ownership sem permitir double-spend;
- verificar proof não basta se o state transition estiver incompleto.

# Condição de vitória

Reutilizar um spend proof/nullifier em uma implementação vulnerável e demonstrar double-spend.

# Consequência narrativa

O Breaker demonstra, em uma reprodução isolada da implementação vulnerável, que a repetição do nullifier não basta para atribuir dois gastos independentes a ele. O exploit do challenge não é um novo gasto na operação histórica investigada.

Isso enfraquece a evidência acusatória; ainda não demonstra a legitimidade da settlement original. A prova positiva depende dos witnesses vinculados à mesma operação e da policy histórica, reunidos até o Final.

Mas descobre algo mais:

a note original está ligada à settlement enviada por Rhea.

Para reconstruir corretamente a origem sem abrir o pool inteiro, precisa de uma informação que só o sender possui.

SENDER WITNESS: REQUIRED

O Breaker procura Rhea.

Rhea:

> **“Você não consegue limpar seu nome sem mim.”**

Breaker:

> “E você não consegue limpar o seu sem mim.”

Rhea:

> **“Eu sei.”**

Aqui começa a cooperação forçada. Cada um concorda em compartilhar apenas o necessário para defender a settlement; não há consentimento geral para usar credenciais ou metadados em investigações diferentes. Rhea ainda não tem qualquer plano de entregar o Breaker.

A Witness Spire apresenta uma segunda evidência:

PROOF: VALID

Unlock:

**CASE 06 — THE PROOF THAT LIED**

# Referência

[https://github.com/NethermindEth/stellar-private-payments](https://github.com/NethermindEth/stellar-private-payments)

## Loop jogável v2 — nullifier e interpretação de prova

**Investigar:** compromisso da note, nullifier derivado no protocolo de teste, estado “spent” e duas entradas contendo o mesmo nullifier. O jogador deve identificar se a segunda operação deveria ter falhado.

**Hipótese:** a prova criptográfica de ownership pode ser válida enquanto o contrato não aplica a unicidade do nullifier no state transition.

**Executar:** em uma instância isolada do privacy pool, usar o mesmo nullifier duas vezes e confirmar que o programa vulnerável aceita a segunda utilização; mirror seguro rejeita como SPENT. Não criar novo gasto na settlement histórica do Breaker.

**Verifier:** duas execuções aceitas no vulnerável com nullifier idêntico, rejeição no seguro, estado de spend auditável. Uma repetição pública no caso histórico **não prova, sozinha, duas decisões legítimas de gasto atribuíveis ao Breaker**; pode refletir falha de implementação ou dados de acusação insuficientes.

**Relação:** sender witness de Rhea e recipient witness do Breaker são necessários para vincular a mesma settlement sem full disclosure. Cooperação é obrigatória, ainda sem confiança geral.

**Diferencial:** invariant de **double spend** (state), não falha de constraints do Caso 06.
