---
notion_id: 40e9c563-0425-81e5-86ad-d6d515f1cfa8
source: https://app.notion.com/p/40e9c563042581e586add6d515f1cfa8?pvs=204
title: "XDR LAB / INSPECTOR"
exported_at: 2026-11-07
---

Here is the result of "fetch" for the Page with URL https://app.notion.com/p/40e9c563042581e586add6d515f1cfa8 as of 2026-11-05T13:45:08.617Z:
<page url="https://app.notion.com/p/40e9c563042581e586add6d515f1cfa8">
<ancestor-path>
<parent-data-source url="collection://68d445ad-e91e-44c9-a323-544887af1bad" name="17 — Easter Eggs | Season 1 — Mapa, Arte & Stellar DNA"/>
<ancestor-2-database url="https://app.notion.com/p/2b1d33190ac446bfaea34e7a4db74d92" title="17 — Easter Eggs | Season 1 — Mapa, Arte & Stellar DNA"/>
<ancestor-3-page url="https://app.notion.com/p/4009c563042581359693d42f09d41062" title="Season 01 — The First Layer"/>
<ancestor-4-page url="https://app.notion.com/p/4019c563042581469a0edc7e30a6eff9" title="ACT I — The World Is Breakable"/>
<ancestor-5-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
<properties>
{"Arquivo / Asset":"frontend/src/levels/narrative/01.json · 01-document-1","Case / Área":"Case 01","Custos / cuidados":"XDR e eventos devem ser reais/reproduzíveis; não divulgar solução antecipada.","Easter Egg":"XDR LAB / INSPECTOR","Fonte oficial":"https://developers.stellar.org/docs/tools/lab/quickstart-with-lab","Local na composição":"Documento opcional “Trilha de serviço”, em Evidências / Arquivos","Prioridade":"P0","Referência real":"Stellar Lab, Horizon/RPC e inspeção de dados da rede","Risco spoiler":"Médio","Season":"Season 1","Status":"Implementado","Suporte":["Documento"],"Tipo":"Tecnologia","url":"https://app.notion.com/p/40e9c563042581e586add6d515f1cfa8"}
</properties>
<iconMetadata>null</iconMetadata>
<content>
<callout icon="🥚" color="gray_bg">
<b>IMPLEMENTADO — 05/11/2026</b>. Referência ambiental aplicada sem alterar desafios, roteiro locked v1.4 ou interação do jogador.
</callout>

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

<b>Cuidado principal:</b> XDR e eventos devem ser reais/reproduzíveis; não divulgar solução antecipada.
</content>
</page>

<parent-data-source-schema url="collection://68d445ad-e91e-44c9-a323-544887af1bad">
The SQLite table definition for this page's parent data source. Use these column names and option values to set this page's properties, create sibling pages, or query the data source.
<sqlite-table>
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
</sqlite-table>
</parent-data-source-schema>

