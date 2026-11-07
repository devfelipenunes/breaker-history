---
notion_id: 4029c563-0425-81c4-a4da-d53d538ca6c5
source: https://app.notion.com/p/4029c563042581c4a4dad53d538ca6c5?pvs=204
title: "27 — What a case delivers"
exported_at: 2026-11-07
---

Here is the result of "fetch" for the Page with URL https://app.notion.com/p/4029c563042581c4a4dad53d538ca6c5 as of 2026-11-05T11:08:23.785Z:
<page url="https://app.notion.com/p/4029c563042581c4a4dad53d538ca6c5">
<ancestor-path>
<parent-data-source url="collection://c177b69b-cf17-4df6-91e7-fa33fc62e9a2" name="X — Season 1 | Fila de Publicações"/>
<ancestor-2-database url="https://app.notion.com/p/4bc75fffc553440f9ffd0497bf69ab12" title="X — Season 1 | Fila de Publicações"/>
<ancestor-3-page url="https://app.notion.com/p/4009c563042581359693d42f09d41062" title="Season 01 — The First Layer"/>
<ancestor-4-page url="https://app.notion.com/p/4019c563042581469a0edc7e30a6eff9" title="ACT I — The World Is Breakable"/>
<ancestor-5-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
<properties>
{"Bloco":9,"Categoria":"Gameplay","Fase":"Comunidade ativa","Link X":"","Ordem":27,"Post":"27 — What a case delivers","Pronto para postar":"__NO__","Publicado":"__NO__","Semana da campanha":6,"Sequência de publicação":27,"Texto":"One case. Three layers.<br /><br />Investigate a strange event.<br />Demonstrate a real Soroban contract failure.<br />See how the evidence changes the investigation.<br /><br />BREAKER connects what you learn in code to what happens in Meridian.<br /><br />#BREAKER #BuildOnStellar","Visual / material":"Obrigatório: clip de gameplay real, sem mostrar solução; se inexistente, não marcar pronto.","url":"https://app.notion.com/p/4029c563042581c4a4dad53d538ca6c5"}
</properties>
<iconMetadata>null</iconMetadata>
<blank-page>This page is blank and has no content.</blank-page>
</page>

<parent-data-source-schema url="collection://c177b69b-cf17-4df6-91e7-fa33fc62e9a2">
The SQLite table definition for this page's parent data source. Use these column names and option values to set this page's properties, create sibling pages, or query the data source.
<sqlite-table>
CREATE TABLE IF NOT EXISTS "collection://c177b69b-cf17-4df6-91e7-fa33fc62e9a2" (
	url TEXT UNIQUE,
	createdTime TEXT, -- ISO-8601 datetime string, automatically set. This is the canonical time for when the page was created.
	"Categoria" TEXT, -- one of ["Narrativa", "Técnico", "Gameplay", "Comunidade", "Lançamento"]
	"Fase" TEXT, -- one of ["Pré-lançamento", "Lançamento", "Comunidade ativa"]
	"Link X" TEXT,
	"Visual / material" TEXT,
	"Pronto para postar" TEXT, -- "__YES__" = true, "__NO__" = false, NULL defaults to false
	"Texto" TEXT,
	"Bloco" FLOAT,
	"Semana da campanha" FLOAT,
	"Publicado" TEXT, -- "__YES__" = true, "__NO__" = false, NULL defaults to false
	"Ordem" FLOAT,
	"Sequência de publicação" FLOAT,
	"Post" TEXT
)
</sqlite-table>
</parent-data-source-schema>

