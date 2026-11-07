---
notion_id: 40e9c563-0425-81e3-adac-d63e58905833
source: https://app.notion.com/p/40e9c563042581e3adacd63e58905833?pvs=204
title: "MERIDIAN / 2019 — PRIMEIRO ENCONTRO"
exported_at: 2026-11-07
---

**PROPOSTA — NÃO CANÔNICA**. Não foi inserida em imagem, mapa ou runtime. É um candidato de pesquisa para revisão de arte, UX e canon da Season 1.

## Conceito

Placa de arquivo com referência discreta à edição inaugural; pode ser código de acervo, não data diegética.

## Descoberta pelo jogador

Detalhe de exploração na lore não obrigatória.

## Localização

Placa num centro comunitário ou centro de convenções fictício. Arquivo/asset: Mapa Meridian / placa ambiental. Necessária confirmação de correspondência entre arquivos e Case no site.

## Referência real

Primeira conferência Meridian ocorreu em 2019 na Cidade do México. [Fonte oficial](https://stellar.org/events/community/meridian-2019).

## Gate de aprovação

- [ ] Revisar o visual 8:3 e o recorte mobile; não perder silhueta, landmark ou texto importante.
- [ ] Confirmar compatibilidade com o roteiro locked v1.4 e os verificadores.
- [ ] Não parecer pista obrigatória, senha, exploit, flag ou spoiler.
- [ ] Revisar nomes, logos, licença e qualquer sugestão de endosso de terceiros.
- [ ] Marcar 'Aprovado' somente após decisão explícita; 'Implementado' somente após ver no runtime.

**Cuidado principal:** Não vincular cronologia do mundo fictício diretamente a 2019 sem justificativa.

The SQLite table definition for this page's parent data source. Use these column names and option values to set this page's properties, create sibling pages, or query the data source.

CREATE TABLE IF NOT EXISTS "collection://68d445ad-e91e-44c9-a323-544887af1bad" (
	url TEXT UNIQUE,
	createdTime TEXT, -- ISO-8601 datetime string, automatically set. This is the canonical time for when the page was created.
	"Suporte" TEXT, -- JSON array with zero or more of ["Imagem", "Mapa", "Terminal", "Documento", "Cenário", "Interface"]
	"Referência real" TEXT,
	"Fonte oficial" TEXT,
	"Arquivo / Asset" TEXT,
	"Status" TEXT, -- one of ["Ideia", "Pesquisa", "Em revisão", "Aprovado", "Implementado", "Rejeitado"]
	"Tipo" TEXT, -- one of ["História Stellar", "Tecnologia", "Criador", "Projeto", "Comunidade", "Marca histórica"]
	"Custos / cuidados" TEXT,
	"Case / Área" TEXT, -- one of ["Mapa / Hub", "Prólogo", "Case 01", "Case 02", "Case 03", "Case 04", "Custodian", "Case 05", "Case 06", "Case 07", "Case 08", "Case 09", "Case 10", "Architect"]
	"Risco spoiler" TEXT, -- one of ["Baixo", "Médio", "Alto"]
	"Prioridade" TEXT, -- one of ["P0", "P1", "P2"]
	"Season" TEXT, -- one of ["Season 1", "Futuro"]
	"Local na composição" TEXT,
	"Easter Egg" TEXT
)

