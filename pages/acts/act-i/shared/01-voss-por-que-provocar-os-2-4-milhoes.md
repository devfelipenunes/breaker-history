---
notion_id: 40c9c563-0425-81f4-b168-fc3395b83b2a
source: https://app.notion.com/p/40c9c563042581f4b168fc3395b83b2a?pvs=204
title: "✅ 01 — Voss: por que provocar os 2,4 milhões?"
exported_at: 2026-11-07
---

**APROVADO PELO USUÁRIO — seleção A + B.** Integração narrativa canônica; detalhes de contratos, simulações e provas continuam pendentes de validação técnica. A escolha aqui é editorial, não opção moral jogável.

# Lacuna e pergunta dramática

Voss: por que provocar os 2,4 milhões?

**Questão:** Como tornar este evento justo, causal e verificável?

# Alternativas avaliadas

**A:** Três relatórios/alertas de risco encaminhados por Voss foram arquivados sem correção efetiva.

**B:** Para demonstrar a interdependência Gate → RecoveryController, Voss aciona uma recuperação real, subestimando a quarentena de recursos de Lower Meridian.

**C:** Uma janela de update ameaçaria apagar traces (descartado; não inventar urgência por conveniência).

# Versão aprovada (A + B)

Voss já tinha percorrido e recusado a Sequence. Após alertas ignorados, usa o AccessGate inseguro para acionar a recuperação institucional de 2,4 milhões, sem controle de saque. Sua intenção é forçar revisão pública, mas escolhe um experimento real e transfere o custo aos serviços de Lower Meridian.

# Como chega ao jogador

Trilha de documentos arquivados no workspace de Voss (Case 05), sinal dos atrasos em Warehouse 17, trilha Vault/Escrow no Architect. Três pistas independentes em vez de discurso de absolvição.

# Restrições e QA

Preservar autoria de Voss, destination Recovery Escrow, custos humanos, e o fato de que recusa do Architect não o torna herói moral.

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

