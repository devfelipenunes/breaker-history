---
notion_id: 40c9c563-0425-8176-a126-feb041bd06ed
source: https://app.notion.com/p/40c9c56304258176a126feb041bd06ed?pvs=204
title: "✅ 05 — Liquidator: o que Rhea tentava conter?"
exported_at: 2026-11-07
---

Here is the result of "fetch" for the Page with URL https://app.notion.com/p/40c9c56304258176a126feb041bd06ed as of 2026-11-02T23:55:37.582Z:
<page url="https://app.notion.com/p/40c9c56304258176a126feb041bd06ed" icon="✅">
<ancestor-path>
<parent-data-source url="collection://b4f0c5f4-39bc-45b1-8950-66bd4a990f20" name="07 — Escolhas de Acontecimentos | Writers' Room Act I"/>
<ancestor-2-database url="https://app.notion.com/p/74e79ba036bb4afd95321e9578fd6151" title="07 — Escolhas de Acontecimentos | Writers' Room Act I"/>
<ancestor-3-page url="https://app.notion.com/p/4019c563042581469a0edc7e30a6eff9" title="ACT I — The World Is Breakable"/>
<ancestor-4-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
<properties>
{"Acontecimento":"05 — Liquidator: o que Rhea tentava conter?","Decisão editorial":"Aprovada e incorporada","Escolha de acontecimento":"Combinar versões","Métodos":["But Therefore","Environmental","Story Grid"],"Observação":"Escolha aprovada: A + B. Cânone narrativo integrado; requisitos de fixture ainda por testar.","Prioridade":"P0 - central","Temporada":"S2 — Lumen","Tipo de furo":"Causalidade","url":"https://app.notion.com/p/40c9c56304258176a126feb041bd06ed"}
</properties>
<iconMetadata>{"type":"emoji","emoji":"✅"}</iconMetadata>
<content>
<callout icon="✅" color="green_bg">
<b>APROVADO PELO USUÁRIO — seleção A + B.</b> Integração narrativa canônica; detalhes de contratos, simulações e provas continuam pendentes de validação técnica. A escolha aqui é editorial, não opção moral jogável.
</callout>

# Lacuna e pergunta dramática

Liquidator: o que Rhea tentava conter?

<b>Questão:</b> Como tornar este evento justo, causal e verificável?

# Alternativas avaliadas

<b>A:</b> Rhea tenta suspender temporariamente liquidações dependentes de price reports que não atendem freshness/confidence.

<b>B:</b> Rhea tenta limitar o volume de liquidações executadas por ledger para não amplificar slippage/contágio em pool raso.

<b>C:</b> Desabilitar avaliação de Vault como fonte inteira (não escolhido).

# Versão aprovada (A + B)

Rhea tenta ativar um plano emergencial de contenção com dois parâmetros: filtrar liquidações baseadas em feed inadequado e limitar temporariamente o throughput de liquidações por janela. A ação não está especificamente autorizada; o Breaker bloqueia. Sem esse freio, o Liquidator executa decisões acumuladas e realimenta a crise. O isolamento posterior de um dos sete mercados é outro evento.

# Como chega ao jogador

Fixture deve registrar policy, parâmetros propostos, risco de pausas indevidas, contadores de liquidação, slippage e settlement com duas execuções de mesma seed e diferença apenas no bloqueio.

# Restrições e QA

O contrafactual é uma hipótese verificável, não alegação de que Rhea salvaria tudo. Os números 14→31→78→204 são cenas canônicas, ainda requerem simulação.

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

