---
notion_id: 40c9c563-0425-8197-ae41-e4f7754e5dab
source: https://app.notion.com/p/40c9c56304258197ae41e4f7754e5dab?pvs=204
title: "✅ 08 — Quem altera a association para DENIED e por quê?"
exported_at: 2026-11-07
---

**APROVADO PELO USUÁRIO — seleção B.** Integração narrativa canônica; detalhes de contratos, simulações e provas continuam pendentes de validação técnica. A escolha aqui é editorial, não opção moral jogável.

# Lacuna e pergunta dramática

Quem altera a association para DENIED e por quê?

**Questão:** Como tornar este evento justo, causal e verificável?

# Alternativas avaliadas

**A:** Sistema antigo automatizado altera tudo sozinho (não escolhido).

**B:** Operador de compliance institucional segue procedimentos antigos, aceita um pending admin não removido e reclassifica a rota segundo alerta emergencial, sem reconhecer que sua authority foi cancelada.

**C:** Agente malicioso usa authority indevida para incriminar (não escolhido).

# Versão aprovada (B)

Um funcionário responsável por reclassificação de risco usa credenciais de um antigo Association Set Provider; um cancelamento administrativo havia sido emitido, mas a etapa pending permaneceu executável. Ele conclui o two-step transfer e aplica DENIED após a settlement diante do alerta de risco pós-Lumen. A ação foi intencional como processo, não conspiratória ou retroativa. Seu poder de modificar a associação decorre do bug, não de mandato válido.

# Como chega ao jogador

Case 04: CANCELLED EVENT / PENDING STATE / ACCEPTED BY LEGACY OPERATOR / RISK REVIEW / DENIED EVENT, com timestamps claros. Documento de procedimento justifica intenção, e o ledger prova que authority de fato estava cancelada.

# Restrições e QA

Cuidado com cronologia T\_cancel \< T\_accept \< T\_denied e T\_settlement \< T\_denied; não fixar sem necessidade ordem relativa entre settlement e cancelamento.

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

