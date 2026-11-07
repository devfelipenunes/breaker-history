---
notion_id: 40c9c563-0425-817a-bd43-e92a2d55f910
source: https://app.notion.com/p/40c9c5630425817abd43e92a2d55f910?pvs=204
title: "✅ 10 — Como estar MISSING e enfrentar First Witness?"
exported_at: 2026-11-07
---

**APROVADO PELO USUÁRIO — seleção B + C.** Integração narrativa canônica; detalhes de contratos, simulações e provas continuam pendentes de validação técnica. A escolha aqui é editorial, não opção moral jogável.

# Lacuna e pergunta dramática

Como estar MISSING e enfrentar First Witness?

**Questão:** Como tornar este evento justo, causal e verificável?

# Alternativas avaliadas

**A:** Entrega assíncrona sem confronto pessoal (não escolhida; diminui drama).

**B:** Breaker aparece fisicamente na Spire em encontro controlado; First Witness vê quem está diante dele, mas não tem trilha contínua de entrada e saída.

**C:** Breaker usa credential/proof de escopo estreito para provar ser parte do caso, sem dar ao sistema autorização para rastrear a rota inteira.

# Versão aprovada (B + C)

O Breaker chega ao perímetro controlado da Spire com observabilidade de rota insuficiente para Architect/Witnesses. Apresenta fisicamente prova limitada do vínculo histórico (commitment e credentials) que identifica o subject processual, mas não reconstrói endereços, horários e trajetória fora da sessão. Durante o encontro sua localização é conhecida; MISSING se refere à falta de rastreio contínuo e à rota posterior, não a invisibilidade absoluta.

# Como chega ao jogador

Case10: MODEL: INSUFFICIENT / ROUTE: NOT TRACKABLE. Final: SUBJECT PRESENT / SESSION AUTHENTICATED / ROUTE HISTORY: UNAVAILABLE; após saída classificação MISSING permanece.

# Restrições e QA

Se First Witness conhece posição presente, não afirmar que ele 'não sabe onde está' naquele instante; local de encontro e observabilidade contínua são propriedades distintas.

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

