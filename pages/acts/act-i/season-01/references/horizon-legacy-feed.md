---
notion_id: 40e9c563-0425-818a-b003-ddc1f3a8fcaa
source: https://app.notion.com/p/40e9c5630425818ab003ddc1f3a8fcaa?pvs=204
title: "HORIZON / LEGACY FEED"
exported_at: 2026-11-07
---

**PROPOSTA — NÃO CANÔNICA**. Não foi inserida em imagem, mapa ou runtime. É um candidato de pesquisa para revisão de arte, UX e canon da Season 1.

## Conceito

Monitor indica uma API legada de leitura de histórico, ao lado de exportação de Galexie.

## Descoberta pelo jogador

Mostrar como metadado opcional sem alterar pista PLAYER ACTIVE.

## Localização

Rodapé de monitor técnico separado dos documentos secretos. Arquivo/asset: 08.webp / BREAKER OS. Necessária confirmação de correspondência entre arquivos e Case no site.

## Referência real

Horizon: infraestrutura de API/consulta histórica da rede Stellar. [Fonte oficial](https://developers.stellar.org/docs/tools/lab/quickstart-with-lab).

## Gate de aprovação

- [ ] Revisar o visual 8:3 e o recorte mobile; não perder silhueta, landmark ou texto importante.
- [ ] Confirmar compatibilidade com o roteiro locked v1.4 e os verificadores.
- [ ] Não parecer pista obrigatória, senha, exploit, flag ou spoiler.
- [ ] Revisar nomes, logos, licença e qualquer sugestão de endosso de terceiros.
- [ ] Marcar 'Aprovado' somente após decisão explícita; 'Implementado' somente após ver no runtime.

**Cuidado principal:** Distinguir Horizon, RPC e Galexie; não inventar dados secretos no ledger.

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

