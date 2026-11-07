---
notion_id: 40c9c563-0425-8114-aa1e-ecdccc2d0d79
source: https://app.notion.com/p/40c9c56304258114aa1eecdccc2d0d79?pvs=204
title: "✅ 04 — Liquidator: por que o Breaker bloqueia Rhea?"
exported_at: 2026-11-07
---

**APROVADO PELO USUÁRIO — seleção A + B.** Integração narrativa canônica; detalhes de contratos, simulações e provas continuam pendentes de validação técnica. A escolha aqui é editorial, não opção moral jogável.

# Lacuna e pergunta dramática

Liquidator: por que o Breaker bloqueia Rhea?

**Questão:** Como tornar este evento justo, causal e verificável?

# Alternativas avaliadas

**A:** O escopo da intervenção emergencial excede as operações estritamente autorizadas e pode suspender efeitos em terceiros.

**B:** Um relatório de risco utiliza métricas corretas porém isoladas e prevê dano de liquidez se a intervenção ocorrer, ignorando liquidações sob feeds inseguros.

**C:** Rhea esconde completamente a estratégia (não selecionar; não transformar a surpresa em falta arbitrária de informação).

# Versão aprovada (A + B)

O Breaker encontra prova real de falta de autorização específica e um relatório de risco economicamente plausível contra o override. Ele bloqueia Rhea por um motivo defensável, porém os dados ignoram a cascata de liquidações com feed insuficiente e o efeito no AMM; é erro de análise agregada, não incompetência.

# Como chega ao jogador

Antes da vitória: capability limitada + risk report parcial com fonte e lacuna inspecionável. Depois: contrafactual com mesma seed identifica o efeito que faltou no relatório.

# Restrições e QA

Não alegar que Rhea causou os bugs. A suspeita pode ser compreendida sem esconder deliberadamente dados que o jogador conseguiria consultar.

# Referências

[00 — História Canônica do Act I](00-historia-canonica-do-act-i.md)

[06 — Writers' Room: Metodologias & Avaliação do Ato I](06-writers-room-metodologias-avaliacao-do-ato-i.md)

The SQLite table definition for this page's parent data source. Use these column names and option values to set this page's properties, create sibling pages, or query the data source.

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

