---
notion_id: 40c9c563-0425-81f3-96ae-f4b2410e3f26
source: https://app.notion.com/p/40c9c563042581f396aef4b2410e3f26?pvs=204
title: "✅ 11 — Como o sender witness chega ao Final Boss?"
exported_at: 2026-11-07
---

Here is the result of "fetch" for the Page with URL https://app.notion.com/p/40c9c563042581f396aef4b2410e3f26 as of 2026-11-02T23:55:37.707Z:
<page url="https://app.notion.com/p/40c9c563042581f396aef4b2410e3f26" icon="✅">
<ancestor-path>
<parent-data-source url="collection://b4f0c5f4-39bc-45b1-8950-66bd4a990f20" name="07 — Escolhas de Acontecimentos | Writers' Room Act I"/>
<ancestor-2-database url="https://app.notion.com/p/74e79ba036bb4afd95321e9578fd6151" title="07 — Escolhas de Acontecimentos | Writers' Room Act I"/>
<ancestor-3-page url="https://app.notion.com/p/4019c563042581469a0edc7e30a6eff9" title="ACT I — The World Is Breakable"/>
<ancestor-4-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
<properties>
{"Acontecimento":"11 — Como o sender witness chega ao Final Boss?","Decisão editorial":"Aprovada e incorporada","Escolha de acontecimento":"A","Métodos":["But Therefore","Story Grid"],"Observação":"Escolha aprovada: A. Cânone narrativo integrado; requisitos de fixture ainda por testar.","Prioridade":"P1 - relevante","Temporada":"S3 — Moonlight","Tipo de furo":"Continuidade","url":"https://app.notion.com/p/40c9c563042581f396aef4b2410e3f26"}
</properties>
<iconMetadata>{"type":"emoji","emoji":"✅"}</iconMetadata>
<content>
<callout icon="✅" color="green_bg">
<b>APROVADO PELO USUÁRIO — seleção A.</b> Integração narrativa canônica; detalhes de contratos, simulações e provas continuam pendentes de validação técnica. A escolha aqui é editorial, não opção moral jogável.
</callout>

# Lacuna e pergunta dramática

Como o sender witness chega ao Final Boss?

<b>Questão:</b> Como tornar este evento justo, causal e verificável?

# Alternativas avaliadas

<b>A:</b> Antes da separação do Case 10, Rhea entrega pacote autenticado já ligado ao settlement commitment e aos public inputs da policy; o Breaker conserva sem expor raw key.

<b>B:</b> Release condicionada a novos eventos (não escolhida).

<b>C:</b> Canal novo de prova conjunta com infraestrutura extra (não escolhido).

# Versão aprovada (A)

Ao encerrar o Case 09 ou na abertura do 10, Rhea entrega ao Breaker um sender witness/proof package autenticado, criptograficamente vinculado ao commitment da settlement original e ao snapshot histórico de policy. O Breaker leva o pacote para Witness Spire sem reencontro ou nova comunicação rastreável. Rhea entrega por necessidade técnica e confiança sincera, não antecipando a decisão sobre Lumen.

# Como chega ao jogador

CENA: PACKAGE SEALED / SOURCE RHEA / COMMITMENT MATCH / HANDOFF COMPLETE; depois separação e trajetória MISSING. Final verifica vínculo e origem do pacote.

# Restrições e QA

Evitar que witness signifique private signing key ou autorização ampla. Pode conter ciphertext, proof fragment ou attestation, sem segredo reutilizável do emissor.

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

