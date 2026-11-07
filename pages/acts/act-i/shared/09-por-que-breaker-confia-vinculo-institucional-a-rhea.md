---
notion_id: 40c9c563-0425-810a-8732-d2aba0648260
source: https://app.notion.com/p/40c9c5630425810a8732d2aba0648260?pvs=204
title: "✅ 09 — Por que Breaker confia vínculo institucional a Rhea?"
exported_at: 2026-11-07
---

**APROVADO PELO USUÁRIO — seleção A + C.** Integração narrativa canônica; detalhes de contratos, simulações e provas continuam pendentes de validação técnica. A escolha aqui é editorial, não opção moral jogável.

# Lacuna e pergunta dramática

Por que Breaker confia vínculo institucional a Rhea?

**Questão:** Como tornar este evento justo, causal e verificável?

# Alternativas avaliadas

**A:** Para vincular account operacional, recipient witness e elegibilidade histórica do destinatário sob a policy de t0, uma atestação de identidade institucional é necessária.

**B:** Rhea apenas verifica elegibilidade genérica sem inconsistência (não escolhida).

**C:** A Spire aponta inconsistência entre identificadores operacionais Lumen e Moonlight, exigindo vínculo autenticado que Rhea pode validar na prova composta.

# Versão aprovada (A + C)

A Spire identifica dois identificadores aparentemente incompatíveis para o mesmo beneficiário histórico. Para demonstrar que a parcela da garantia retornou ao destinatário elegível sob policy original, o Breaker precisa conectar sua conta operacional de Lumen à credencial institucional que validava a titularidade em t0. O vínculo é apresentado à Rhea somente no contexto da construção do sender+recipient proof, com aviso de risco de correlação e proibição de reutilização para atribuição externa. O Breaker revela apenas o mínimo necessário; Rhea respeita esse limite de boa-fé naquele momento.

# Como chega ao jogador

Case 07: REQUEST: HISTORICAL BENEFICIARY BINDING / SCOPED ATTESTATION / RHEA: WITNESS REVIEW. Registro de propósito, prazo e consentimento contextual; ela não recebe private key nem poder de atuar pelo Breaker.

# Restrições e QA

No epílogo Rhea envia atestação própria verdadeira à apuração de Lumen, não reutiliza consentimento como autorização; a quebra é de finalidade e confiança, não falha criptográfica inexplicável.

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

