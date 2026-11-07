---
notion_id: 40e9c563-0425-8147-8a7e-ff0b8f33b1e2
source: https://app.notion.com/p/40e9c563042581478a7eff0b8f33b1e2?pvs=204
title: "STROOP / 10⁷"
exported_at: 2026-11-07
---

Here is the result of "fetch" for the Page with URL https://app.notion.com/p/40e9c563042581478a7eff0b8f33b1e2 as of 2026-11-04T15:13:43.061Z:
<page url="https://app.notion.com/p/40e9c563042581478a7eff0b8f33b1e2">
<ancestor-path>
<parent-data-source url="collection://68d445ad-e91e-44c9-a323-544887af1bad" name="17 — Easter Eggs | Season 1 — Mapa, Arte & Stellar DNA"/>
<ancestor-2-database url="https://app.notion.com/p/2b1d33190ac446bfaea34e7a4db74d92" title="17 — Easter Eggs | Season 1 — Mapa, Arte & Stellar DNA"/>
<ancestor-3-page url="https://app.notion.com/p/4009c563042581359693d42f09d41062" title="Season 01 — The First Layer"/>
<ancestor-4-page url="https://app.notion.com/p/4019c563042581469a0edc7e30a6eff9" title="ACT I — The World Is Breakable"/>
<ancestor-5-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
<properties>
{"Arquivo / Asset":"BREAKER OS — Case 06","Case / Área":"Case 06","Custos / cuidados":"Case 06 usa cast i128→u128; não misturar com unidades XLM e gerar cálculo falso.","Easter Egg":"STROOP / 10⁷","Fonte oficial":"https://stellar.org/blog/developers/surge-pricing-on-stellar-faq","Local na composição":"Etiqueta de unidade em console de valores, fora dos números da fixture","Prioridade":"P1","Referência real":"Um stroop equivale a 0,0000001 XLM","Risco spoiler":"Médio","Season":"Season 1","Status":"Ideia","Suporte":["Terminal","Interface"],"Tipo":"Tecnologia","url":"https://app.notion.com/p/40e9c563042581478a7eff0b8f33b1e2"}
</properties>
<iconMetadata>null</iconMetadata>
<content>
<callout icon="🥚" color="gray_bg">
<b>PROPOSTA — NÃO CANÔNICA</b>. Não foi inserida em imagem, mapa ou runtime. É um candidato de pesquisa para revisão de arte, UX e canon da Season 1.
</callout>

## Conceito

Indicador microscópico de precisão monetária com anotação 10\^7, apenas como cultura de engenharia.

## Descoberta pelo jogador

Só tooltip acessório após conclusão.

## Localização

Etiqueta de unidade em console de valores, fora dos números da fixture. Arquivo/asset: BREAKER OS — Case 06. Necessária confirmação de correspondência entre arquivos e Case no site.

## Referência real

Um stroop equivale a 0,0000001 XLM. [Fonte oficial](https://stellar.org/blog/developers/surge-pricing-on-stellar-faq).

## Gate de aprovação

- [ ] Revisar o visual 8:3 e o recorte mobile; não perder silhueta, landmark ou texto importante.
- [ ] Confirmar compatibilidade com o roteiro locked v1.4 e os verificadores.
- [ ] Não parecer pista obrigatória, senha, exploit, flag ou spoiler.
- [ ] Revisar nomes, logos, licença e qualquer sugestão de endosso de terceiros.
- [ ] Marcar 'Aprovado' somente após decisão explícita; 'Implementado' somente após ver no runtime.

<b>Cuidado principal:</b> Case 06 usa cast i128→u128; não misturar com unidades XLM e gerar cálculo falso.
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

