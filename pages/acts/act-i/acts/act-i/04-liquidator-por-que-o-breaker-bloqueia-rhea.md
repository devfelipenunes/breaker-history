---
notion_id: 40c9c563-0425-8114-aa1e-ecdccc2d0d79
source: https://app.notion.com/p/40c9c56304258114aa1eecdccc2d0d79?pvs=204
title: "✅ 04 — Liquidator: por que o Breaker bloqueia Rhea?"
exported_at: 2026-11-07
---

Here is the result of "fetch" for the Page with URL https://app.notion.com/p/40c9c56304258114aa1eecdccc2d0d79 as of 2026-11-02T23:55:37.566Z:
<page url="https://app.notion.com/p/40c9c56304258114aa1eecdccc2d0d79" icon="✅">
<ancestor-path>
<parent-data-source url="collection://b4f0c5f4-39bc-45b1-8950-66bd4a990f20" name="07 — Escolhas de Acontecimentos | Writers' Room Act I"/>
<ancestor-2-database url="https://app.notion.com/p/74e79ba036bb4afd95321e9578fd6151" title="07 — Escolhas de Acontecimentos | Writers' Room Act I"/>
<ancestor-3-page url="https://app.notion.com/p/4019c563042581469a0edc7e30a6eff9" title="ACT I — The World Is Breakable"/>
<ancestor-4-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
<properties>
{"Acontecimento":"04 — Liquidator: por que o Breaker bloqueia Rhea?","Decisão editorial":"Aprovada e incorporada","Escolha de acontecimento":"Combinar versões","Métodos":["But Therefore","Story Grid","Three Clue Rule"],"Observação":"Escolha aprovada: A + B. Cânone narrativo integrado; requisitos de fixture ainda por testar.","Prioridade":"P0 - central","Temporada":"S2 — Lumen","Tipo de furo":"Motivação","url":"https://app.notion.com/p/40c9c56304258114aa1eecdccc2d0d79"}
</properties>
<iconMetadata>{"type":"emoji","emoji":"✅"}</iconMetadata>
<content>
<callout icon="✅" color="green_bg">
<b>APROVADO PELO USUÁRIO — seleção A + B.</b> Integração narrativa canônica; detalhes de contratos, simulações e provas continuam pendentes de validação técnica. A escolha aqui é editorial, não opção moral jogável.
</callout>

# Lacuna e pergunta dramática

Liquidator: por que o Breaker bloqueia Rhea?

<b>Questão:</b> Como tornar este evento justo, causal e verificável?

# Alternativas avaliadas

<b>A:</b> O escopo da intervenção emergencial excede as operações estritamente autorizadas e pode suspender efeitos em terceiros.

<b>B:</b> Um relatório de risco utiliza métricas corretas porém isoladas e prevê dano de liquidez se a intervenção ocorrer, ignorando liquidações sob feeds inseguros.

<b>C:</b> Rhea esconde completamente a estratégia (não selecionar; não transformar a surpresa em falta arbitrária de informação).

# Versão aprovada (A + B)

O Breaker encontra prova real de falta de autorização específica e um relatório de risco economicamente plausível contra o override. Ele bloqueia Rhea por um motivo defensável, porém os dados ignoram a cascata de liquidações com feed insuficiente e o efeito no AMM; é erro de análise agregada, não incompetência.

# Como chega ao jogador

Antes da vitória: capability limitada + risk report parcial com fonte e lacuna inspecionável. Depois: contrafactual com mesma seed identifica o efeito que faltou no relatório.

# Restrições e QA

Não alegar que Rhea causou os bugs. A suspeita pode ser compreendida sem esconder deliberadamente dados que o jogador conseguiria consultar.

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

