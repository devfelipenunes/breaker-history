---
notion_id: 65e5dbd0-85bf-43c0-adfc-a3685d5896e8
source: https://app.notion.com/p/65e5dbd085bf43c0adfca3685d5896e8?pvs=204
title: "S01 — Fichas de Cena e Continuidade"
exported_at: 2026-11-07
---

<database url="{{https://app.notion.com/p/65e5dbd085bf43c0adfca3685d5896e8}}" inline="false">
The title of this Database is: S01 — Fichas de Cena e Continuidade
<ancestor-path>
<parent-page url="https://app.notion.com/p/4039c563042581d9bf27d22d355dc5b2" title="10 — Direção de Arte | Meridian S1 — Manual de Produção e Continuidade"/>
<ancestor-2-page url="https://app.notion.com/p/4019c5630425819d8e93e523aa0c2045" title="00 — Series Bible"/>
<ancestor-3-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
Here are the Database's Data Sources:
You can use the "fetch" tool on the URL of any Data Source to see its full schema configuration.
<data-sources>
<data-source url="{{collection://81383529-1b5e-4c94-8738-1ce5d9fb368b}}">
The title of this Data Source is: S01 — Fichas de Cena e Continuidade
The description of this Data Source is: Fonte operacional para pré-produção visual de cada Case de BREAKER Season 1. Uma linha por Case; a página contém o mapa de cinco beats, continuidade, prompt e QA.

Here is the database's configurable state:
Properties with `readOnly: true` are synced or system-managed. Do not try to update their values with page update tools.
<data-source-state>
{"name":"S01 — Fichas de Cena e Continuidade","schema":{"Case":{"description":"","name":"Case","type":"title"},"Estado":{"defaultOption":"Backlog","description":"","groups":{"complete":[{"color":"green","description":"","name":"Aprovado","url":"collectionPropertyOption://81383529-1b5e-4c94-8738-1ce5d9fb368b/dnFjZg/ZWZhNWE0NDQtZGQ1ZC00MTI1LThiZWQtY2FlNGE5MGFmODQ2"}],"current":[],"future":[],"in_progress":[{"color":"blue","description":"","name":"Em pré-produção","url":"collectionPropertyOption://81383529-1b5e-4c94-8738-1ce5d9fb368b/dnFjZg/YmEzNTBhZWQtODMyYi00NjIyLTk3NzYtNmI3NjkzMDE0YmEw"},{"color":"yellow","description":"","name":"Em revisão","url":"collectionPropertyOption://81383529-1b5e-4c94-8738-1ce5d9fb368b/dnFjZg/NGJkM2M4NDUtNzRhYS00YTk1LThiMTMtYjdlNmQxNzUyODRl"}],"to_do":[{"color":"gray","description":"","name":"Backlog","url":"collectionPropertyOption://81383529-1b5e-4c94-8738-1ce5d9fb368b/dnFjZg/MjA5ZGM2YzktZWYxMC00NWY0LThjYWEtYjAwZjkxMTU4NWQ3"}]},"name":"Estado","type":"status"},"Fase":{"description":"","name":"Fase","options":[{"color":"gray","description":"","name":"Prólogo","url":"collectionPropertyOption://81383529-1b5e-4c94-8738-1ce5d9fb368b/PnVUTQ/MWM5YzEwYjAtZmFmMi00MGViLWE5ODYtMzZhYTllMWM0NWJi"},{"color":"blue","description":"","name":"Case","url":"collectionPropertyOption://81383529-1b5e-4c94-8738-1ce5d9fb368b/PnVUTQ/MTZhOThiYjYtZGMyYS00YzlkLWIzM2ItMWZkY2ZjMTg2ZDky"}],"type":"select"},"Fonte canônica":{"description":"","name":"Fonte canônica","type":"url"},"Frames previstos":{"description":"","name":"Frames previstos","type":"number"},"Local / âncora":{"description":"","name":"Local / âncora","type":"text"},"Ordem":{"description":"","name":"Ordem","type":"number"},"Spoiler máximo":{"description":"","name":"Spoiler máximo","options":[{"color":"blue","description":"","name":"Estado inicial","url":"collectionPropertyOption://81383529-1b5e-4c94-8738-1ce5d9fb368b/VXBtTw/ODhhMDUyNmItMzIwNy00OTVhLWEyYmItZTcxYjU0OWNlYmNh"},{"color":"yellow","description":"","name":"Pós-vitória restrito","url":"collectionPropertyOption://81383529-1b5e-4c94-8738-1ce5d9fb368b/VXBtTw/YmU1ZWYxMjYtY2FkMC00MTQ1LTk4MzktMzc5MGE1YTlkMGJj"},{"color":"purple","description":"","name":"Epilogo","url":"collectionPropertyOption://81383529-1b5e-4c94-8738-1ce5d9fb368b/VXBtTw/NDA3MTY3YmQtZGVhNi00MzFlLWE4Y2EtNmQzODU3MjJmNGEx"}],"type":"select"},"Última revisão":{"description":"","name":"Última revisão","type":"last_edited_time"}},"url":"collection://81383529-1b5e-4c94-8738-1ce5d9fb368b"}
</data-source-state>

Here is the SQLite table definition for this data source.
<sqlite-table>
CREATE TABLE IF NOT EXISTS "collection://81383529-1b5e-4c94-8738-1ce5d9fb368b" (
	url TEXT UNIQUE,
	createdTime TEXT, -- ISO-8601 datetime string, automatically set. This is the canonical time for when the page was created.
	"Fase" TEXT, -- one of ["Prólogo", "Case"]
	"Ordem" FLOAT,
	"Frames previstos" FLOAT,
	"Local / âncora" TEXT,
	"Spoiler máximo" TEXT, -- one of ["Estado inicial", "Pós-vitória restrito", "Epilogo"]
	"Última revisão" TEXT NOT NULL, -- ISO-8601 datetime string, automatically set. This is the canonical time for when the page was last edited.
	"Fonte canônica" TEXT,
	"Estado" TEXT, -- one of ["Backlog", "Em pré-produção", "Em revisão", "Aprovado"] Default: "Backlog".
	"Case" TEXT
)
</sqlite-table>
</data-source>
</data-sources>
Here are the Database's Views:
You can use the "fetch" tool on the URL of any View to see its full configuration.
<views>
<view url="{{view://ae384b98-6bf1-4fe2-a193-8dfb821ce9b8}}">
{"dataSourceUrl":"{{collection://81383529-1b5e-4c94-8738-1ce5d9fb368b}}","displayProperties":["Case","Estado","Fase","Fonte canônica","Frames previstos","Local / âncora","Ordem","Spoiler máximo","Última revisão"],"name":"Default view","type":"table"}
</view>
</views>
</database>

