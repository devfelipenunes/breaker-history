---
notion_id: 40e9c563-0425-81e5-86ad-d6d515f1cfa8
source: https://app.notion.com/p/40e9c563042581e586add6d515f1cfa8?pvs=204
title: "XDR LAB / INSPECTOR"
exported_at: 2026-11-07
---

**IMPLEMENTADO — 05/11/2026**. Referência ambiental aplicada sem alterar desafios, roteiro locked v1.4 ou interação do jogador.

## Conceito

Uma pequena indicação LAB / XDR DECODED no terminal que já existe; pode abrir documentação técnica depois da vitória.

## Descoberta pelo jogador

Não alterar demonstração de auth nem condições de vitória.

## Localização

Documento opcional “Trilha de serviço”, em Evidências / Arquivos. Arquivo/asset: frontend/src/levels/narrative/01.json · 01-document-1.

## Referência real

Stellar Lab, Horizon/RPC e inspeção de dados da rede. [Fonte oficial](https://developers.stellar.org/docs/tools/lab/quickstart-with-lab).

## Gate de aprovação

- [ ] Revisar o visual 8:3 e o recorte mobile; não perder silhueta, landmark ou texto importante.
- [ ] Confirmar compatibilidade com o roteiro locked v1.4 e os verificadores.
- [ ] Não parecer pista obrigatória, senha, exploit, flag ou spoiler.
- [ ] Revisar nomes, logos, licença e qualquer sugestão de endosso de terceiros.
- [ ] Marcar 'Aprovado' somente após decisão explícita; 'Implementado' somente após ver no runtime.

**Cuidado principal:** XDR e eventos devem ser reais/reproduzíveis; não divulgar solução antecipada.

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

