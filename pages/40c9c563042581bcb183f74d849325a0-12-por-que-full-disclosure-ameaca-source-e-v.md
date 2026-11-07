---
notion_id: 40c9c563-0425-81bc-b183-f74d849325a0
source: https://app.notion.com/p/40c9c563042581bcb183f74d849325a0?pvs=204
title: "✅ 12 — Por que full disclosure ameaça SOURCE E.V.?"
exported_at: 2026-11-07
---

Here is the result of "fetch" for the Page with URL https://app.notion.com/p/40c9c563042581bcb183f74d849325a0 as of 2026-11-02T23:55:37.724Z:
<page url="https://app.notion.com/p/40c9c563042581bcb183f74d849325a0" icon="✅">
<ancestor-path>
<parent-data-source url="collection://b4f0c5f4-39bc-45b1-8950-66bd4a990f20" name="07 — Escolhas de Acontecimentos | Writers' Room Act I"/>
<ancestor-2-database url="https://app.notion.com/p/74e79ba036bb4afd95321e9578fd6151" title="07 — Escolhas de Acontecimentos | Writers' Room Act I"/>
<ancestor-3-page url="https://app.notion.com/p/4019c563042581469a0edc7e30a6eff9" title="ACT I — The World Is Breakable"/>
<ancestor-4-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
<properties>
{"Acontecimento":"12 — Por que full disclosure ameaça SOURCE E.V.?","Decisão editorial":"Aprovada e incorporada","Escolha de acontecimento":"B","Métodos":["Promise Progress Payoff","Three Clue Rule","Environmental"],"Observação":"Escolha aprovada: B. Cânone narrativo integrado; requisitos de fixture ainda por testar.","Prioridade":"P1 - relevante","Temporada":"S3 — Moonlight","Tipo de furo":"Preparação e payoff","url":"https://app.notion.com/p/40c9c563042581bcb183f74d849325a0"}
</properties>
<iconMetadata>{"type":"emoji","emoji":"✅"}</iconMetadata>
<content>
<callout icon="✅" color="green_bg">
<b>APROVADO PELO USUÁRIO — seleção B.</b> Integração narrativa canônica; detalhes de contratos, simulações e provas continuam pendentes de validação técnica. A escolha aqui é editorial, não opção moral jogável.
</callout>

# Lacuna e pergunta dramática

Por que full disclosure ameaça SOURCE E.V.?

<b>Questão:</b> Como tornar este evento justo, causal e verificável?

# Alternativas avaliadas

<b>A:</b> Grafo de transações identifica fonte apenas por on-chain network (não escolhido; exige correlacionar demais).

<b>B:</b> O canal de recebimento de documentos de Sera preserva metadados de origem/autenticação que, se entregues com todo o dossiê ligado ao Breaker, permitem ligar SOURCE E.V. a Eli Venn.

<b>C:</b> Um registro institucional completo expõe a fonte (não escolhido).

# Versão aprovada (B)

Sera entrega ao Breaker parte das provas que podem sustentar a defesa, com origem marcada apenas SOURCE E.V. O conteúdo do documento pode ser compartilhado de maneira limitada, mas seu envelope de proveniência/assinatura no repositório seguro de reportagem contém metadados que identificariam Eli Venn. A ordem ampla de disclosure abrange esses envelopes entre os registros associados ao Breaker; o proof package mínimo do Final fornece autenticidade e conclusão sem revelar origem jornalística irrelevante ao claim.

# Como chega ao jogador

Case 01/02: SOURCE E.V. / SOURCE METADATA REDACTED / DOCUMENT HASH. Case08: VIEW-CAPABILITY SCOPE includes evidence envelope. Final: Full disclosure preview shows SOURCE-ID LINKABLE, sem exibir nome ao jogador cedo.

# Restrições e QA

Não publicar identificador de Eli em storage/events abertos. Risco de revelação é explícito e tecnicamente causado pela abrangência da política, não por poderes mágicos da view key.

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

