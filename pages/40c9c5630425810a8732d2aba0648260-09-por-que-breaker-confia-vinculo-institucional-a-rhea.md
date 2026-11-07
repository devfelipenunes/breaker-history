---
notion_id: 40c9c563-0425-810a-8732-d2aba0648260
source: https://app.notion.com/p/40c9c5630425810a8732d2aba0648260?pvs=204
title: "✅ 09 — Por que Breaker confia vínculo institucional a Rhea?"
exported_at: 2026-11-07
---

Here is the result of "fetch" for the Page with URL https://app.notion.com/p/40c9c5630425810a8732d2aba0648260 as of 2026-11-02T23:55:37.676Z:
<page url="https://app.notion.com/p/40c9c5630425810a8732d2aba0648260" icon="✅">
<ancestor-path>
<parent-data-source url="collection://b4f0c5f4-39bc-45b1-8950-66bd4a990f20" name="07 — Escolhas de Acontecimentos | Writers' Room Act I"/>
<ancestor-2-database url="https://app.notion.com/p/74e79ba036bb4afd95321e9578fd6151" title="07 — Escolhas de Acontecimentos | Writers' Room Act I"/>
<ancestor-3-page url="https://app.notion.com/p/4019c563042581469a0edc7e30a6eff9" title="ACT I — The World Is Breakable"/>
<ancestor-4-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
<properties>
{"Acontecimento":"09 — Por que Breaker confia vínculo institucional a Rhea?","Decisão editorial":"Aprovada e incorporada","Escolha de acontecimento":"Combinar versões","Métodos":["But Therefore","Story Grid","Promise Progress Payoff"],"Observação":"Escolha aprovada: A + C. Cânone narrativo integrado; requisitos de fixture ainda por testar.","Prioridade":"P0 - central","Temporada":"S3 — Moonlight","Tipo de furo":"Motivação","url":"https://app.notion.com/p/40c9c5630425810a8732d2aba0648260"}
</properties>
<iconMetadata>{"type":"emoji","emoji":"✅"}</iconMetadata>
<content>
<callout icon="✅" color="green_bg">
<b>APROVADO PELO USUÁRIO — seleção A + C.</b> Integração narrativa canônica; detalhes de contratos, simulações e provas continuam pendentes de validação técnica. A escolha aqui é editorial, não opção moral jogável.
</callout>

# Lacuna e pergunta dramática

Por que Breaker confia vínculo institucional a Rhea?

<b>Questão:</b> Como tornar este evento justo, causal e verificável?

# Alternativas avaliadas

<b>A:</b> Para vincular account operacional, recipient witness e elegibilidade histórica do destinatário sob a policy de t0, uma atestação de identidade institucional é necessária.

<b>B:</b> Rhea apenas verifica elegibilidade genérica sem inconsistência (não escolhida).

<b>C:</b> A Spire aponta inconsistência entre identificadores operacionais Lumen e Moonlight, exigindo vínculo autenticado que Rhea pode validar na prova composta.

# Versão aprovada (A + C)

A Spire identifica dois identificadores aparentemente incompatíveis para o mesmo beneficiário histórico. Para demonstrar que a parcela da garantia retornou ao destinatário elegível sob policy original, o Breaker precisa conectar sua conta operacional de Lumen à credencial institucional que validava a titularidade em t0. O vínculo é apresentado à Rhea somente no contexto da construção do sender+recipient proof, com aviso de risco de correlação e proibição de reutilização para atribuição externa. O Breaker revela apenas o mínimo necessário; Rhea respeita esse limite de boa-fé naquele momento.

# Como chega ao jogador

Case 07: REQUEST: HISTORICAL BENEFICIARY BINDING / SCOPED ATTESTATION / RHEA: WITNESS REVIEW. Registro de propósito, prazo e consentimento contextual; ela não recebe private key nem poder de atuar pelo Breaker.

# Restrições e QA

No epílogo Rhea envia atestação própria verdadeira à apuração de Lumen, não reutiliza consentimento como autorização; a quebra é de finalidade e confiança, não falha criptográfica inexplicável.

# Referências

<mention url="https://app.notion.com/p/4019c56304258181a4e2ef561d8954a2" />

<mention url="https://app.notion.com/p/40c9c56304258192bfa2ee5be09a512a" />
</content>
</page>

<parent-data-source-schema url="collection://b4f0c5f4-39bc-45b1-8950-66bd4a990f20">
The SQLite table definition for this page's parent data source. Use these column names and option values to set this page's properties, create sibling pages, or query the data source.
<sqlite-table>
CREATE TABLE IF NOT EXISTS "collection://b4f0c5f4-39bc-45b1-8950-66bd4a990f20" (
	url TEXT UNIQUE,
	createdTime TEXT, -- ISO-8601 datetime string, automatically set. This is the canonical time for when the page was created.
	"Prioridade" TEXT, -- one of ["P0 - central", "P1 - relevante", "P2 - refinamento"]
	"Escolha de acontecimento" TEXT, -- one of ["Ainda não escolhi", "A", "B", "C", "D", "Combinar versões"]
	"Temporada" TEXT, -- one of ["S1 — Meridian", "S2 — Lumen", "S3 — Moonlight", "Ponte S2→S3", "Ato I"]
	"Tipo de furo" TEXT, -- one of ["Motivação", "Causalidade", "Preparação e payoff", "Continuidade", "Prova / plausibilidade"]
	"Decisão editorial" TEXT, -- one of ["Para avaliar", "Gostei - explorar", "Pronta para revisão canônica", "Aprovada e incorporada", "Descartar"]
	"Métodos" TEXT, -- JSON array with zero or more of ["But Therefore", "Promise Progress Payoff", "Story Grid", "Three Clue Rule", "Environmental", "Weave"]
	"Observação" TEXT,
	"Acontecimento" TEXT
)
</sqlite-table>
</parent-data-source-schema>

