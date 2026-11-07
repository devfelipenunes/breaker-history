---
notion_id: 40c9c563-0425-8135-81e1-d02b2e8c910a
source: https://app.notion.com/p/40c9c5630425813581e1d02b2e8c910a?pvs=204
title: "✅ 06 — Ponte: finalidade da settlement Rhea → Breaker"
exported_at: 2026-11-07
---

**APROVADO PELO USUÁRIO — seleção C.** Integração narrativa canônica; detalhes de contratos, simulações e provas continuam pendentes de validação técnica. A escolha aqui é editorial, não opção moral jogável.

# Lacuna e pergunta dramática

Ponte: finalidade da settlement Rhea → Breaker

**Questão:** Qual é a finalidade da operação que une duas temporadas?

# Alternativas avaliadas

**A:** Obrigações de liquidação entre posições, sem garantia individual (não escolhida).

**B:** Pagamento de compensação pessoal por perda de Breaker (não escolhido; parece presente).

**C:** Devolução da parcela de garantia temporária aportada/atribuída ao Breaker durante a contenção da Cascade.

# Versão aprovada (C)

Para manter settlement e liquidez crítica durante a Cascade, Breaker disponibiliza garantia operacional temporária (ou fica titular de parcela segregada do colchão de liquidez) sob acordo técnico. Rhea controla o fluxo de encerramento do arranjo na sua parte da operação; após a estabilização, envia a parcela devida ao Breaker por settlement confidencial legítima, registrada sob policy válida em t0. O motivo é liquidação de garantia, não reconciliação pessoal nem armadilha.

# Como chega ao jogador

No Final S2, registrar GARANTEE POSITION / RIGHTFUL RECIPIENT / RELEASE RULE. No epílogo Rhea executa retorno legítimo e o Breaker segue o destino Moonlight para auditar recibo ou origem; na Season 3 o DENIED aparece só após reassunção indevida de associação.

# Restrições e QA

Não prometer privacidade total de metadados. Provar que o colateral é da posição de Breaker, que Rhea tem authority limitada para enviar e que não há emissão de saldo fictício.

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

