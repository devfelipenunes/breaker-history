---
notion_id: 40c9c563-0425-8176-a126-feb041bd06ed
source: https://app.notion.com/p/40c9c56304258176a126feb041bd06ed?pvs=204
title: "✅ 05 — Liquidator: o que Rhea tentava conter?"
exported_at: 2026-11-07
---

**APROVADO PELO USUÁRIO — seleção A + B.** Integração narrativa canônica; detalhes de contratos, simulações e provas continuam pendentes de validação técnica. A escolha aqui é editorial, não opção moral jogável.

# Lacuna e pergunta dramática

Liquidator: o que Rhea tentava conter?

**Questão:** Como tornar este evento justo, causal e verificável?

# Alternativas avaliadas

**A:** Rhea tenta suspender temporariamente liquidações dependentes de price reports que não atendem freshness/confidence.

**B:** Rhea tenta limitar o volume de liquidações executadas por ledger para não amplificar slippage/contágio em pool raso.

**C:** Desabilitar avaliação de Vault como fonte inteira (não escolhido).

# Versão aprovada (A + B)

Rhea tenta ativar um plano emergencial de contenção com dois parâmetros: filtrar liquidações baseadas em feed inadequado e limitar temporariamente o throughput de liquidações por janela. A ação não está especificamente autorizada; o Breaker bloqueia. Sem esse freio, o Liquidator executa decisões acumuladas e realimenta a crise. O isolamento posterior de um dos sete mercados é outro evento.

# Como chega ao jogador

Fixture deve registrar policy, parâmetros propostos, risco de pausas indevidas, contadores de liquidação, slippage e settlement com duas execuções de mesma seed e diferença apenas no bloqueio.

# Restrições e QA

O contrafactual é uma hipótese verificável, não alegação de que Rhea salvaria tudo. Os números 14→31→78→204 são cenas canônicas, ainda requerem simulação.

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

