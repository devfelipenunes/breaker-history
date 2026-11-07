---
notion_id: 40f9c563-0425-8182-976a-e5a74b5ac164
source: https://app.notion.com/p/40f9c56304258182976ae5a74b5ac164?pvs=204
title: "STELLAR MACHINE / FLOW WALL"
exported_at: 2026-11-07
---

Here is the result of "fetch" for the Page with URL https://app.notion.com/p/40f9c56304258182976ae5a74b5ac164 as of 2026-11-05T13:45:11.234Z:
<page url="https://app.notion.com/p/40f9c56304258182976ae5a74b5ac164">
<ancestor-path>
<parent-data-source url="collection://68d445ad-e91e-44c9-a323-544887af1bad" name="17 — Easter Eggs | Season 1 — Mapa, Arte & Stellar DNA"/>
<ancestor-2-database url="https://app.notion.com/p/2b1d33190ac446bfaea34e7a4db74d92" title="17 — Easter Eggs | Season 1 — Mapa, Arte & Stellar DNA"/>
<ancestor-3-page url="https://app.notion.com/p/4009c563042581359693d42f09d41062" title="Season 01 — The First Layer"/>
<ancestor-4-page url="https://app.notion.com/p/4019c563042581469a0edc7e30a6eff9" title="ACT I — The World Is Breakable"/>
<ancestor-5-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
<properties>
{"Arquivo / Asset":"frontend/public/images/levels/07.png","Case / Área":"Case 07","Custos / cuidados":"Não tratar o painel como terminal do jogador; não inventar operação, dado secreto ou vínculo oficial.","Easter Egg":"STELLAR MACHINE / FLOW WALL","Fonte oficial":"https://stellar.org/frontier/projects/stellar-machine/","Local na composição":"Parede de monitores ao fundo; fluxo abstrato, sem texto legível e sem competir com a investigação","Prioridade":"P1","Referência real":"Stellar Machine: visualizador de operações da rede em tempo real","Risco spoiler":"Baixo","Season":"Season 1","Status":"Implementado","Suporte":["Imagem","Cenário"],"Tipo":"Projeto","url":"https://app.notion.com/p/40f9c56304258182976ae5a74b5ac164"}
</properties>
<iconMetadata>null</iconMetadata>
<blank-page>This page is blank and has no content.</blank-page>
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

