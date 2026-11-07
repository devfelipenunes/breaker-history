---
notion_id: 40c9c563-0425-81b8-8218-eff57bd4c8fe
source: https://app.notion.com/p/40c9c563042581b88218eff57bd4c8fe?pvs=204
title: "✅ 07 — First Witness: por que exigir full disclosure?"
exported_at: 2026-11-07
---

Here is the result of "fetch" for the Page with URL https://app.notion.com/p/40c9c563042581b88218eff57bd4c8fe as of 2026-11-02T23:55:37.643Z:
<page url="https://app.notion.com/p/40c9c563042581b88218eff57bd4c8fe" icon="✅">
<ancestor-path>
<parent-data-source url="collection://b4f0c5f4-39bc-45b1-8950-66bd4a990f20" name="07 — Escolhas de Acontecimentos | Writers' Room Act I"/>
<ancestor-2-database url="https://app.notion.com/p/74e79ba036bb4afd95321e9578fd6151" title="07 — Escolhas de Acontecimentos | Writers' Room Act I"/>
<ancestor-3-page url="https://app.notion.com/p/4019c563042581469a0edc7e30a6eff9" title="ACT I — The World Is Breakable"/>
<ancestor-4-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
<properties>
{"Acontecimento":"07 — First Witness: por que exigir full disclosure?","Decisão editorial":"Aprovada e incorporada","Escolha de acontecimento":"Combinar versões","Métodos":["But Therefore","Story Grid","Three Clue Rule"],"Observação":"Escolha aprovada: A + B. Cânone narrativo integrado; requisitos de fixture ainda por testar.","Prioridade":"P0 - central","Temporada":"S3 — Moonlight","Tipo de furo":"Motivação","url":"https://app.notion.com/p/40c9c563042581b88218eff57bd4c8fe"}
</properties>
<iconMetadata>{"type":"emoji","emoji":"✅"}</iconMetadata>
<content>
<callout icon="✅" color="green_bg">
<b>APROVADO PELO USUÁRIO — seleção A + B.</b> Integração narrativa canônica; detalhes de contratos, simulações e provas continuam pendentes de validação técnica. A escolha aqui é editorial, não opção moral jogável.
</callout>

# Lacuna e pergunta dramática

First Witness: por que exigir full disclosure?

<b>Questão:</b> Como tornar este evento justo, causal e verificável?

# Alternativas avaliadas

<b>A:</b> Uma policy de compliance excepcional é ativada quando association DENIED aparece após incidente sistêmico.

<b>B:</b> Múltiplas operações e relacionamentos em um grafo de risco elevam a suspeita de comportamento coordenado; inferência não prova rede ilícita.

<b>C:</b> Ele confunde privacy com destruição de evidência (não escolhido).

# Versão aprovada (A + B)

Uma regra de investigação excepcional, acionada por associação atualmente DENIED e um conjunto de operações correlacionadas, eleva o caso para revisão de rede. First Witness vê fontes reais, mas as interpreta de maneira excessiva; solicita view authority ampla por acreditar que uma prova de uma operação não basta. A política existe, mas o dever de proporcionalidade permanece. No Final, evidências refutam a generalização e o Witness encerra a ordem mesmo que o workflow automático ainda exija tudo.

# Como chega ao jogador

Prólogo: NETWORK RISK SIGNALS, DENIED CURRENT, WITNESS ORDER: EXPANDED. Final: per-operation proof valid + graph linkage weak / broad disclosure unjustified.

# Restrições e QA

Sem criminalizar privacidade, sem acesso mágico às carteiras; First Witness conserva competência e autonomia e não reabre a decisão após o fechamento.

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

