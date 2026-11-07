---
notion_id: 4019c563-0425-819c-b20a-c8462a316cb0
source: https://app.notion.com/p/4019c5630425819cb20ac8462a316cb0?pvs=204
title: "♻️ 05 — Spent Twice"
exported_at: 2026-11-07
---

Here is the result of "fetch" for the Page with URL https://app.notion.com/p/4019c5630425819cb20ac8462a316cb0 as of 2026-11-02T17:41:33.176Z:
<page url="https://app.notion.com/p/4019c5630425819cb20ac8462a316cb0" icon="♻️">
<ancestor-path>
<parent-page url="https://app.notion.com/p/4019c563042581a2a331e66548c30494" title="04 — Cases & Bosses"/>
<ancestor-2-page url="https://app.notion.com/p/4019c56304258179bfa0fc93d15ac390" title="Season 03 — Shadows of Privacy — Moonlight"/>
<ancestor-3-page url="https://app.notion.com/p/4019c563042581469a0edc7e30a6eff9" title="ACT I — The World Is Breakable"/>
<ancestor-4-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
<properties>
{"title":"05 — Spent Twice"}
</properties>
<iconMetadata>{"type":"emoji","emoji":"♻️"}</iconMetadata>
<content>
# História

O sistema acusa o Breaker de double-spend em um privacy pool.

O nullifier ligado a uma note aparece duas vezes.

A prova parece suficiente.

Mas o pool não valida corretamente o estado de nullifiers já gastos.

# Missão

> <b>Gaste a mesma private note duas vezes.</b>

# Vulnerabilidade canônica / falha de invariant

<b>Nullifier Replay / Missing Spent-Nullifier Validation.</b>

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

> <b>“Você não consegue limpar seu nome sem mim.”</b>

Breaker:

> “E você não consegue limpar o seu sem mim.”

Rhea:

> <b>“Eu sei.”</b>

Aqui começa a cooperação forçada. Cada um concorda em compartilhar apenas o necessário para defender a settlement; não há consentimento geral para usar credenciais ou metadados em investigações diferentes. Rhea ainda não tem qualquer plano de entregar o Breaker.

A Witness Spire apresenta uma segunda evidência:

PROOF: VALID

Unlock:

<b>CASE 06 — THE PROOF THAT LIED</b>

# Referência

[https://github.com/NethermindEth/stellar-private-payments](https://github.com/NethermindEth/stellar-private-payments)

## Loop jogável v2 — nullifier e interpretação de prova

<b>Investigar:</b> compromisso da note, nullifier derivado no protocolo de teste, estado “spent” e duas entradas contendo o mesmo nullifier. O jogador deve identificar se a segunda operação deveria ter falhado.

<b>Hipótese:</b> a prova criptográfica de ownership pode ser válida enquanto o contrato não aplica a unicidade do nullifier no state transition.

<b>Executar:</b> em uma instância isolada do privacy pool, usar o mesmo nullifier duas vezes e confirmar que o programa vulnerável aceita a segunda utilização; mirror seguro rejeita como SPENT. Não criar novo gasto na settlement histórica do Breaker.

<b>Verifier:</b> duas execuções aceitas no vulnerável com nullifier idêntico, rejeição no seguro, estado de spend auditável. Uma repetição pública no caso histórico <b>não prova, sozinha, duas decisões legítimas de gasto atribuíveis ao Breaker</b>; pode refletir falha de implementação ou dados de acusação insuficientes.

<b>Relação:</b> sender witness de Rhea e recipient witness do Breaker são necessários para vincular a mesma settlement sem full disclosure. Cooperação é obrigatória, ainda sem confiança geral.

<b>Diferencial:</b> invariant de <b>double spend</b> (state), não falha de constraints do Caso 06.
</content>
</page>

