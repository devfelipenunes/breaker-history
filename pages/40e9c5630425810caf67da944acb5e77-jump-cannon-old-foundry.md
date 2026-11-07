---
notion_id: 40e9c563-0425-810c-af67-da944acb5e77
source: https://app.notion.com/p/40e9c5630425810caf67da944acb5e77?pvs=204
title: "JUMP CANNON / OLD FOUNDRY"
exported_at: 2026-11-07
---

Here is the result of "fetch" for the Page with URL https://app.notion.com/p/40e9c5630425810caf67da944acb5e77 as of 2026-11-04T15:13:42.963Z:
<page url="https://app.notion.com/p/40e9c5630425810caf67da944acb5e77">
<ancestor-path>
<parent-data-source url="collection://68d445ad-e91e-44c9-a323-544887af1bad" name="17 — Easter Eggs | Season 1 — Mapa, Arte & Stellar DNA"/>
<ancestor-2-database url="https://app.notion.com/p/2b1d33190ac446bfaea34e7a4db74d92" title="17 — Easter Eggs | Season 1 — Mapa, Arte & Stellar DNA"/>
<ancestor-3-page url="https://app.notion.com/p/4009c563042581359693d42f09d41062" title="Season 01 — The First Layer"/>
<ancestor-4-page url="https://app.notion.com/p/4019c563042581469a0edc7e30a6eff9" title="ACT I — The World Is Breakable"/>
<ancestor-5-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
<properties>
{"Arquivo / Asset":"04.webp (referência, associação a confirmar)","Case / Área":"Case 04","Custos / cuidados":"Não mudar ordem das pistas W17/F24/S13 nem destacar como chave.","Easter Egg":"JUMP CANNON / OLD FOUNDRY","Fonte oficial":"https://stellar.org/blog/developers/project-jump-cannon-soroban-preview-release","Local na composição":"Placa discreta num corredor técnico ou registro off-screen do Floor 24","Prioridade":"P0","Referência real":"Project Jump Cannon: codinome de Soroban","Risco spoiler":"Baixo","Season":"Season 1","Status":"Ideia","Suporte":["Imagem","Cenário","Documento"],"Tipo":"História Stellar","url":"https://app.notion.com/p/40e9c5630425810caf67da944acb5e77"}
</properties>
<iconMetadata>null</iconMetadata>
<content>
<callout icon="🥚" color="gray_bg">
<b>PROPOSTA — NÃO CANÔNICA</b>. Não foi inserida em imagem, mapa ou runtime. É um candidato de pesquisa para revisão de arte, UX e canon da Season 1.
</callout>

## Conceito

Um projeto de engenharia antiga deixa a assinatura JUMP CANNON em uma bancada ou placa lateral; é só história do mundo.

## Descoberta pelo jogador

Inspeção de cenário opcional; o jogador pode notar a placa, mas o puzzle não depende dela.

## Localização

Placa discreta num corredor técnico ou registro off-screen do Floor 24. Arquivo/asset: 04.webp (referência, associação a confirmar). Necessária confirmação de correspondência entre arquivos e Case no site.

## Referência real

Project Jump Cannon: codinome de Soroban. [Fonte oficial](https://stellar.org/blog/developers/project-jump-cannon-soroban-preview-release).

## Gate de aprovação

- [ ] Revisar o visual 8:3 e o recorte mobile; não perder silhueta, landmark ou texto importante.
- [ ] Confirmar compatibilidade com o roteiro locked v1.4 e os verificadores.
- [ ] Não parecer pista obrigatória, senha, exploit, flag ou spoiler.
- [ ] Revisar nomes, logos, licença e qualquer sugestão de endosso de terceiros.
- [ ] Marcar 'Aprovado' somente após decisão explícita; 'Implementado' somente após ver no runtime.

<b>Cuidado principal:</b> Não mudar ordem das pistas W17/F24/S13 nem destacar como chave.
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

