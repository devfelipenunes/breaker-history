---
notion_id: 40c9c563-0425-817a-bd43-e92a2d55f910
source: https://app.notion.com/p/40c9c5630425817abd43e92a2d55f910?pvs=204
title: "✅ 10 — Como estar MISSING e enfrentar First Witness?"
exported_at: 2026-11-07
---

Here is the result of "fetch" for the Page with URL https://app.notion.com/p/40c9c5630425817abd43e92a2d55f910 as of 2026-11-02T23:55:37.691Z:
<page url="https://app.notion.com/p/40c9c5630425817abd43e92a2d55f910" icon="✅">
<ancestor-path>
<parent-data-source url="collection://b4f0c5f4-39bc-45b1-8950-66bd4a990f20" name="07 — Escolhas de Acontecimentos | Writers' Room Act I"/>
<ancestor-2-database url="https://app.notion.com/p/74e79ba036bb4afd95321e9578fd6151" title="07 — Escolhas de Acontecimentos | Writers' Room Act I"/>
<ancestor-3-page url="https://app.notion.com/p/4019c563042581469a0edc7e30a6eff9" title="ACT I — The World Is Breakable"/>
<ancestor-4-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
<properties>
{"Acontecimento":"10 — Como estar MISSING e enfrentar First Witness?","Decisão editorial":"Aprovada e incorporada","Escolha de acontecimento":"Combinar versões","Métodos":["But Therefore","Environmental","Weave"],"Observação":"Escolha aprovada: B + C. Cânone narrativo integrado; requisitos de fixture ainda por testar.","Prioridade":"P1 - relevante","Temporada":"S3 — Moonlight","Tipo de furo":"Continuidade","url":"https://app.notion.com/p/40c9c5630425817abd43e92a2d55f910"}
</properties>
<iconMetadata>{"type":"emoji","emoji":"✅"}</iconMetadata>
<content>
<callout icon="✅" color="green_bg">
<b>APROVADO PELO USUÁRIO — seleção B + C.</b> Integração narrativa canônica; detalhes de contratos, simulações e provas continuam pendentes de validação técnica. A escolha aqui é editorial, não opção moral jogável.
</callout>

# Lacuna e pergunta dramática

Como estar MISSING e enfrentar First Witness?

<b>Questão:</b> Como tornar este evento justo, causal e verificável?

# Alternativas avaliadas

<b>A:</b> Entrega assíncrona sem confronto pessoal (não escolhida; diminui drama).

<b>B:</b> Breaker aparece fisicamente na Spire em encontro controlado; First Witness vê quem está diante dele, mas não tem trilha contínua de entrada e saída.

<b>C:</b> Breaker usa credential/proof de escopo estreito para provar ser parte do caso, sem dar ao sistema autorização para rastrear a rota inteira.

# Versão aprovada (B + C)

O Breaker chega ao perímetro controlado da Spire com observabilidade de rota insuficiente para Architect/Witnesses. Apresenta fisicamente prova limitada do vínculo histórico (commitment e credentials) que identifica o subject processual, mas não reconstrói endereços, horários e trajetória fora da sessão. Durante o encontro sua localização é conhecida; MISSING se refere à falta de rastreio contínuo e à rota posterior, não a invisibilidade absoluta.

# Como chega ao jogador

Case10: MODEL: INSUFFICIENT / ROUTE: NOT TRACKABLE. Final: SUBJECT PRESENT / SESSION AUTHENTICATED / ROUTE HISTORY: UNAVAILABLE; após saída classificação MISSING permanece.

# Restrições e QA

Se First Witness conhece posição presente, não afirmar que ele 'não sabe onde está' naquele instante; local de encontro e observabilidade contínua são propriedades distintas.

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

