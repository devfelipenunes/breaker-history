---
notion_id: 4bc75fff-c553-440f-9ffd-0497bf69ab12
source: https://app.notion.com/p/4bc75fffc553440f9ffd0497bf69ab12?pvs=204
title: "X — Season 1 | Fila de Publicações"
exported_at: 2026-11-07
---

<database url="{{https://app.notion.com/p/4bc75fffc553440f9ffd0497bf69ab12}}" inline="false">
The title of this Database is: X — Season 1 | Fila de Publicações

Here are the Database's Data Sources:
You can use the "fetch" tool on the URL of any Data Source to see its full schema configuration.

The title of this Data Source is: X — Season 1 | Fila de Publicações
The description of this Data Source is: 45 posts em inglês para X, em 13 semanas relativas ao lançamento (pré=0, lançamento=1, comunidade=2 a 12). Coluna Ordem é ID do post, Sequência de publicação define o calendário. Marcar Publicado e Link X apenas após publicação manual e validação da URL do jogo.

Here is the database's configurable state:
Properties with `readOnly: true` are synced or system-managed. Do not try to update their values with page update tools.

{"name":"X — Season 1 | Fila de Publicações","schema":{"Bloco":{"description":"","name":"Bloco","type":"number"},"Categoria":{"description":"","name":"Categoria","options":[{"color":"purple","description":"","name":"Narrativa","url":"collectionPropertyOption://c177b69b-cf17-4df6-91e7-fa33fc62e9a2/P1pFcw/YmQ2YTdiMjQtMDQ2Ny00MDcxLTgwMDUtOTRmN2VjZTMzZDI2"},{"color":"blue","description":"","name":"Técnico","url":"collectionPropertyOption://c177b69b-cf17-4df6-91e7-fa33fc62e9a2/P1pFcw/YjUzZmYwNDUtYjEwNy00NmViLTg1MzEtZGQ0MDcyZTY3Nzgy"},{"color":"orange","description":"","name":"Gameplay","url":"collectionPropertyOption://c177b69b-cf17-4df6-91e7-fa33fc62e9a2/P1pFcw/ZTY3ODY4ZTktYTYzZS00M2UxLTk4NTEtZTJiNjAxNGU2OTFm"},{"color":"green","description":"","name":"Comunidade","url":"collectionPropertyOption://c177b69b-cf17-4df6-91e7-fa33fc62e9a2/P1pFcw/NTMwOTgwOTItZGJiOS00YWQ0LWE1YWQtOWUwMzg4NThhMTI0"},{"color":"pink","description":"","name":"Lançamento","url":"collectionPropertyOption://c177b69b-cf17-4df6-91e7-fa33fc62e9a2/P1pFcw/ODVjMGFhN2UtNjkxYS00NzA3LTllNTUtZmE4ZjA5MDRiZTlk"}],"type":"select"},"Fase":{"description":"","name":"Fase","options":[{"color":"gray","description":"","name":"Pré-lançamento","url":"collectionPropertyOption://c177b69b-cf17-4df6-91e7-fa33fc62e9a2/Q2FoVw/YTZlNjBjMWQtZDVhYi00Yjk5LWExN2UtNjcxOThkYzIxODM3"},{"color":"yellow","description":"","name":"Lançamento","url":"collectionPropertyOption://c177b69b-cf17-4df6-91e7-fa33fc62e9a2/Q2FoVw/MTI0ZTFiNjktNmZkYi00NGQ0LThkOTgtZmYwYWEzMTU0NTMz"},{"color":"blue","description":"","name":"Comunidade ativa","url":"collectionPropertyOption://c177b69b-cf17-4df6-91e7-fa33fc62e9a2/Q2FoVw/MzAyZTY1NmYtMDZjOC00ZGE2LWI3NzAtNWQzYzFmZmM2ZDg0"}],"type":"select"},"Link X":{"description":"","name":"Link X","type":"url"},"Ordem":{"description":"","name":"Ordem","type":"number"},"Post":{"description":"","name":"Post","type":"title"},"Pronto para postar":{"description":"","name":"Pronto para postar","type":"checkbox"},"Publicado":{"description":"","name":"Publicado","type":"checkbox"},"Semana da campanha":{"description":"","name":"Semana da campanha","type":"number"},"Sequência de publicação":{"description":"","name":"Sequência de publicação","type":"number"},"Texto":{"description":"","name":"Texto","type":"text"},"Visual / material":{"description":"","name":"Visual / material","type":"text"}},"url":"collection://c177b69b-cf17-4df6-91e7-fa33fc62e9a2"}

Here is the SQLite table definition for this data source.

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

Here are the Database's Views:
You can use the "fetch" tool on the URL of any View to see its full configuration.

{"dataSourceUrl":"{{collection://c177b69b-cf17-4df6-91e7-fa33fc62e9a2}}","displayProperties":["Post","Bloco","Categoria","Fase","Link X","Ordem","Pronto para postar","Publicado","Semana da campanha","Sequência de publicação","Texto","Visual / material"],"name":"Default view","type":"table"}

{"columnWidths":{"Post":300,"Texto":460},"dataSourceUrl":"{{collection://c177b69b-cf17-4df6-91e7-fa33fc62e9a2}}","displayProperties":["Post","Semana da campanha","Sequência de publicação","Categoria","Fase","Texto","Pronto para postar","Publicado","Link X"],"name":"13 semanas — ordem real de publicação","simpleFilters":[{"filter":{"operator":"number_equals","property":"Semana da campanha","propertyType":"number","type":"property","value":{"type":"exact"}},"id":"ad74b3de-4971-44b2-9a0f-a7f8a879cf6e"},{"filter":{"operator":"enum_is","property":"Categoria","propertyType":"select","type":"property","value":{"type":"exact"}},"id":"d8fba956-def7-4e31-8af1-ea871ef0bab4"},{"filter":{"operator":"checkbox_is","property":"Publicado","propertyType":"checkbox","type":"property","value":{"type":"exact"}},"id":"0a6ffcf9-4918-4e21-addd-b78021dd60e5"}],"sorts":[{"direction":"ascending","property":"Sequência de publicação"}],"type":"table"}

</database>
