---
notion_id: 40e9c563-0425-8178-a8b2-ed371a8cdeb4
source: https://app.notion.com/p/40e9c56304258178a8b2ed371a8cdeb4?pvs=204
title: "GALEXIE / MIRROR 13"
exported_at: 2026-11-07
---

**IMPLEMENTADO — 05/11/2026**. Referência ambiental aplicada sem alterar desafios, roteiro locked v1.4 ou interação do jogador.

## Conceito

Painel auxiliar indica uma exportação de dados históricos para um sistema externo semelhante a Galexie.

## Descoberta pelo jogador

Após sucesso, opcionalmente ler a origem do snapshot; não alterar evidências essenciais.

## Localização

Parede de monitores e documento opcional de referências de manutenção. Arquivo/asset: frontend/public/images/levels/07.png · frontend/src/levels/narrative/07.json · 07-document-1.

## Referência real

Galexie extrai e exporta dados do ledger Stellar. [Fonte oficial](https://stellar.org/blog/developers/introducing-galexie-efficiently-extract-and-store-stellar-data).

## Gate de aprovação

- [ ] Revisar o visual 8:3 e o recorte mobile; não perder silhueta, landmark ou texto importante.
- [ ] Confirmar compatibilidade com o roteiro locked v1.4 e os verificadores.
- [ ] Não parecer pista obrigatória, senha, exploit, flag ou spoiler.
- [ ] Revisar nomes, logos, licença e qualquer sugestão de endosso de terceiros.
- [ ] Marcar 'Aprovado' somente após decisão explícita; 'Implementado' somente após ver no runtime.

**Cuidado principal:** Não afirmar que o ledger armazena arquivos privados; não criar falsa prova do Registry.

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

