---
notion_id: 40c9c563-0425-8163-bcbc-fbbbfc32dfff
source: https://app.notion.com/p/40c9c56304258163bcbcfbbbfc32dfff?pvs=204
title: "✅ 03 — Mara: assinatura que custa as credenciais"
exported_at: 2026-11-07
---

Here is the result of "fetch" for the Page with URL https://app.notion.com/p/40c9c56304258163bcbcfbbbfc32dfff as of 2026-11-02T23:55:37.549Z:
<page url="https://app.notion.com/p/40c9c56304258163bcbcfbbbfc32dfff" icon="✅">
<ancestor-path>
<parent-data-source url="collection://b4f0c5f4-39bc-45b1-8950-66bd4a990f20" name="07 — Escolhas de Acontecimentos | Writers' Room Act I"/>
<ancestor-2-database url="https://app.notion.com/p/74e79ba036bb4afd95321e9578fd6151" title="07 — Escolhas de Acontecimentos | Writers' Room Act I"/>
<ancestor-3-page url="https://app.notion.com/p/4019c563042581469a0edc7e30a6eff9" title="ACT I — The World Is Breakable"/>
<ancestor-4-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
<properties>
{"Acontecimento":"03 — Mara: assinatura que custa as credenciais","Decisão editorial":"Aprovada e incorporada","Escolha de acontecimento":"Combinar versões","Métodos":["Story Grid","Environmental"],"Observação":"Escolha aprovada: A + C. Cânone narrativo integrado; requisitos de fixture ainda por testar.","Prioridade":"P1 - relevante","Temporada":"S1 — Meridian","Tipo de furo":"Preparação e payoff","url":"https://app.notion.com/p/40c9c56304258163bcbcfbbbfc32dfff"}
</properties>
<iconMetadata>{"type":"emoji","emoji":"✅"}</iconMetadata>
<content>
<callout icon="✅" color="green_bg">
<b>APROVADO PELO USUÁRIO — seleção A + C.</b> Integração narrativa canônica; detalhes de contratos, simulações e provas continuam pendentes de validação técnica. A escolha aqui é editorial, não opção moral jogável.
</callout>

# Lacuna e pergunta dramática

Mara: assinatura que custa as credenciais

<b>Questão:</b> Como tornar este evento justo, causal e verificável?

# Alternativas avaliadas

<b>A:</b> A interface alerta que assinatura após CASE CLOSED será atribuída à credencial institucional de Mara.

<b>B:</b> Um terceiro auditor recebe cópia permanente (descartado; não criar novo personagem).

<b>C:</b> Mara assume explicitamente a custódia e responsabilidade pelo recibo de prova obtida após o encerramento.

# Versão aprovada (A + C)

No Case 09, Mara vê o aviso de ação fora do mandato, assina o recibo vinculando sua credencial e assume cadeia de custódia. Ela não concede autorização irrestrita ao Breaker. No epílogo, a instituição a suspende por esse registro verificável, não por espionagem do canal privado.

# Como chega ao jogador

Antes: CASE CLOSED / AUDITOR ID: MARA / RECEIPT LIABILITY. Depois: HASH + SIGNER. Epílogo: SUSPENDED / EVIDENCE RECEIPT ID coincidente.

# Restrições e QA

O recibo é emitido apenas uma vez; sessão de 1h é diegética e encerra antes do Architect.

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

