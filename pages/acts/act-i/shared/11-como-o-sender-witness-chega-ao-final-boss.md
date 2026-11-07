---
notion_id: 40c9c563-0425-81f3-96ae-f4b2410e3f26
source: https://app.notion.com/p/40c9c563042581f396aef4b2410e3f26?pvs=204
title: "✅ 11 — Como o sender witness chega ao Final Boss?"
exported_at: 2026-11-07
---

**APROVADO PELO USUÁRIO — seleção A.** Integração narrativa canônica; detalhes de contratos, simulações e provas continuam pendentes de validação técnica. A escolha aqui é editorial, não opção moral jogável.

# Lacuna e pergunta dramática

Como o sender witness chega ao Final Boss?

**Questão:** Como tornar este evento justo, causal e verificável?

# Alternativas avaliadas

**A:** Antes da separação do Case 10, Rhea entrega pacote autenticado já ligado ao settlement commitment e aos public inputs da policy; o Breaker conserva sem expor raw key.

**B:** Release condicionada a novos eventos (não escolhida).

**C:** Canal novo de prova conjunta com infraestrutura extra (não escolhido).

# Versão aprovada (A)

Ao encerrar o Case 09 ou na abertura do 10, Rhea entrega ao Breaker um sender witness/proof package autenticado, criptograficamente vinculado ao commitment da settlement original e ao snapshot histórico de policy. O Breaker leva o pacote para Witness Spire sem reencontro ou nova comunicação rastreável. Rhea entrega por necessidade técnica e confiança sincera, não antecipando a decisão sobre Lumen.

# Como chega ao jogador

CENA: PACKAGE SEALED / SOURCE RHEA / COMMITMENT MATCH / HANDOFF COMPLETE; depois separação e trajetória MISSING. Final verifica vínculo e origem do pacote.

# Restrições e QA

Evitar que witness signifique private signing key ou autorização ampla. Pode conter ciphertext, proof fragment ou attestation, sem segredo reutilizável do emissor.

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

