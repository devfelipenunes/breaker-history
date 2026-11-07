---
notion_id: 40e9c563-0425-8124-aab4-e73d5ffd9902
source: https://app.notion.com/p/40e9c56304258124aab4e73d5ffd9902?pvs=204
title: "KIM COMMONS"
exported_at: 2026-11-07
---

Here is the result of "fetch" for the Page with URL https://app.notion.com/p/40e9c56304258124aab4e73d5ffd9902 as of 2026-11-04T15:13:43.008Z:
<page url="https://app.notion.com/p/40e9c56304258124aab4e73d5ffd9902">
<ancestor-path>
<parent-data-source url="collection://68d445ad-e91e-44c9-a323-544887af1bad" name="17 — Easter Eggs | Season 1 — Mapa, Arte & Stellar DNA"/>
<ancestor-2-database url="https://app.notion.com/p/2b1d33190ac446bfaea34e7a4db74d92" title="17 — Easter Eggs | Season 1 — Mapa, Arte & Stellar DNA"/>
<ancestor-3-page url="https://app.notion.com/p/4009c563042581359693d42f09d41062" title="Season 01 — The First Layer"/>
<ancestor-4-page url="https://app.notion.com/p/4019c563042581469a0edc7e30a6eff9" title="ACT I — The World Is Breakable"/>
<ancestor-5-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
<properties>
{"Arquivo / Asset":"Mapa Meridian (proposta)","Case / Área":"Mapa / Hub","Custos / cuidados":"Sem NPC, falas ou aparição inventada da pessoa.","Easter Egg":"KIM COMMONS","Fonte oficial":"https://stellar.org/blog/foundation-news/introducing-stellar","Local na composição":"Praça cívica em Central Meridian","Prioridade":"P2","Referência real":"Joyce Kim, liderança fundadora da Stellar Development Foundation","Risco spoiler":"Baixo","Season":"Season 1","Status":"Ideia","Suporte":["Mapa","Cenário"],"Tipo":"Criador","url":"https://app.notion.com/p/40e9c56304258124aab4e73d5ffd9902"}
</properties>
<iconMetadata>null</iconMetadata>
<content>
<callout icon="🥚" color="gray_bg">
<b>PROPOSTA — NÃO CANÔNICA</b>. Não foi inserida em imagem, mapa ou runtime. É um candidato de pesquisa para revisão de arte, UX e canon da Season 1.
</callout>

## Conceito

Pequena praça com referência de fundação comunitária e direitos civis.

## Descoberta pelo jogador

Ponto de mapa opcional e puramente ambiental.

## Localização

Praça cívica em Central Meridian. Arquivo/asset: Mapa Meridian (proposta). Necessária confirmação de correspondência entre arquivos e Case no site.

## Referência real

Joyce Kim, liderança fundadora da Stellar Development Foundation. [Fonte oficial](https://stellar.org/blog/foundation-news/introducing-stellar).

## Gate de aprovação

- [ ] Revisar o visual 8:3 e o recorte mobile; não perder silhueta, landmark ou texto importante.
- [ ] Confirmar compatibilidade com o roteiro locked v1.4 e os verificadores.
- [ ] Não parecer pista obrigatória, senha, exploit, flag ou spoiler.
- [ ] Revisar nomes, logos, licença e qualquer sugestão de endosso de terceiros.
- [ ] Marcar 'Aprovado' somente após decisão explícita; 'Implementado' somente após ver no runtime.

<b>Cuidado principal:</b> Sem NPC, falas ou aparição inventada da pessoa.
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

