---
notion_id: 40c9c563-0425-81bc-b183-f74d849325a0
source: https://app.notion.com/p/40c9c563042581bcb183f74d849325a0?pvs=204
title: "✅ 12 — Por que full disclosure ameaça SOURCE E.V.?"
exported_at: 2026-11-07
---

**APROVADO PELO USUÁRIO — seleção B.** Integração narrativa canônica; detalhes de contratos, simulações e provas continuam pendentes de validação técnica. A escolha aqui é editorial, não opção moral jogável.

# Lacuna e pergunta dramática

Por que full disclosure ameaça SOURCE E.V.?

**Questão:** Como tornar este evento justo, causal e verificável?

# Alternativas avaliadas

**A:** Grafo de transações identifica fonte apenas por on-chain network (não escolhido; exige correlacionar demais).

**B:** O canal de recebimento de documentos de Sera preserva metadados de origem/autenticação que, se entregues com todo o dossiê ligado ao Breaker, permitem ligar SOURCE E.V. a Eli Venn.

**C:** Um registro institucional completo expõe a fonte (não escolhido).

# Versão aprovada (B)

Sera entrega ao Breaker parte das provas que podem sustentar a defesa, com origem marcada apenas SOURCE E.V. O conteúdo do documento pode ser compartilhado de maneira limitada, mas seu envelope de proveniência/assinatura no repositório seguro de reportagem contém metadados que identificariam Eli Venn. A ordem ampla de disclosure abrange esses envelopes entre os registros associados ao Breaker; o proof package mínimo do Final fornece autenticidade e conclusão sem revelar origem jornalística irrelevante ao claim.

# Como chega ao jogador

Case 01/02: SOURCE E.V. / SOURCE METADATA REDACTED / DOCUMENT HASH. Case08: VIEW-CAPABILITY SCOPE includes evidence envelope. Final: Full disclosure preview shows SOURCE-ID LINKABLE, sem exibir nome ao jogador cedo.

# Restrições e QA

Não publicar identificador de Eli em storage/events abertos. Risco de revelação é explícito e tecnicamente causado pela abrangência da política, não por poderes mágicos da view key.

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

