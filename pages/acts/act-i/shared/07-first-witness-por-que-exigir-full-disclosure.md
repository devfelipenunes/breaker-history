---
notion_id: 40c9c563-0425-81b8-8218-eff57bd4c8fe
source: https://app.notion.com/p/40c9c563042581b88218eff57bd4c8fe?pvs=204
title: "✅ 07 — First Witness: por que exigir full disclosure?"
exported_at: 2026-11-07
---

**APROVADO PELO USUÁRIO — seleção A + B.** Integração narrativa canônica; detalhes de contratos, simulações e provas continuam pendentes de validação técnica. A escolha aqui é editorial, não opção moral jogável.

# Lacuna e pergunta dramática

First Witness: por que exigir full disclosure?

**Questão:** Como tornar este evento justo, causal e verificável?

# Alternativas avaliadas

**A:** Uma policy de compliance excepcional é ativada quando association DENIED aparece após incidente sistêmico.

**B:** Múltiplas operações e relacionamentos em um grafo de risco elevam a suspeita de comportamento coordenado; inferência não prova rede ilícita.

**C:** Ele confunde privacy com destruição de evidência (não escolhido).

# Versão aprovada (A + B)

Uma regra de investigação excepcional, acionada por associação atualmente DENIED e um conjunto de operações correlacionadas, eleva o caso para revisão de rede. First Witness vê fontes reais, mas as interpreta de maneira excessiva; solicita view authority ampla por acreditar que uma prova de uma operação não basta. A política existe, mas o dever de proporcionalidade permanece. No Final, evidências refutam a generalização e o Witness encerra a ordem mesmo que o workflow automático ainda exija tudo.

# Como chega ao jogador

Prólogo: NETWORK RISK SIGNALS, DENIED CURRENT, WITNESS ORDER: EXPANDED. Final: per-operation proof valid + graph linkage weak / broad disclosure unjustified.

# Restrições e QA

Sem criminalizar privacidade, sem acesso mágico às carteiras; First Witness conserva competência e autonomia e não reabre a decisão após o fechamento.

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

