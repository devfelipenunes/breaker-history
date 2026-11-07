---
notion_id: 40e9c563-0425-8154-bd64-cf730685193a
source: https://app.notion.com/p/40e9c56304258154bd64cf730685193a?pvs=204
title: "O FOGUETE ESQUECIDO"
exported_at: 2026-11-07
---

**IMPLEMENTADO — 05/11/2026**. Referência ambiental aplicada sem alterar desafios, roteiro locked v1.4 ou interação do jogador.

## Conceito

Grafite estilizado de foguete antigo em um beco, sinal de que a cidade também teve outras eras tecnológicas.

## Descoberta pelo jogador

Ponto visual opcional no mapa; possível tooltip histórico.

## Localização

Mural gasto e discreto na arquitetura inferior de Lower Meridian. Arquivo/asset: frontend/public/images/levels/homepage.webp.

## Referência real

Antiga identidade visual de foguete da Stellar, trocada em 2019. [Fonte oficial](https://stellar.org/blog/foundation-news/announcing-the-new-stellar-logo).

## Gate de aprovação

- [ ] Revisar o visual 8:3 e o recorte mobile; não perder silhueta, landmark ou texto importante.
- [ ] Confirmar compatibilidade com o roteiro locked v1.4 e os verificadores.
- [ ] Não parecer pista obrigatória, senha, exploit, flag ou spoiler.
- [ ] Revisar nomes, logos, licença e qualquer sugestão de endosso de terceiros.
- [ ] Marcar 'Aprovado' somente após decisão explícita; 'Implementado' somente após ver no runtime.

**Cuidado principal:** Não substituir o emblema aprovado de Meridian; evitar reproduzir marca idêntica sem revisão.

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

