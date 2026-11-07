---
notion_id: 40c9c563-0425-810b-83ba-c3568eac0f0a
source: https://app.notion.com/p/40c9c5630425810b83bac3568eac0f0a?pvs=204
title: "02 — The Dead Man's Wallet"
exported_at: 2026-11-07
---

Here is the result of "fetch" for the Page with URL https://app.notion.com/p/40c9c5630425810b83bac3568eac0f0a as of 2026-11-02T15:25:46.567Z:
<page url="https://app.notion.com/p/40c9c5630425810b83bac3568eac0f0a">
<ancestor-path>
<parent-data-source url="collection://81383529-1b5e-4c94-8738-1ce5d9fb368b" name="S01 — Fichas de Cena e Continuidade"/>
<ancestor-2-database url="https://app.notion.com/p/65e5dbd085bf43c0adfca3685d5896e8" title="S01 — Fichas de Cena e Continuidade"/>
<ancestor-3-page url="https://app.notion.com/p/4039c563042581d9bf27d22d355dc5b2" title="10 — Direção de Arte | Meridian S1 — Manual de Produção e Continuidade"/>
<ancestor-4-page url="https://app.notion.com/p/4019c5630425819d8e93e523aa0c2045" title="00 — Series Bible"/>
<ancestor-5-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
<properties>
{"Case":"02 — The Dead Man's Wallet","Estado":"Backlog","Fase":"Case","Fonte canônica":"https://app.notion.com/p/4039c563042581d9bf27d22d355dc5b2","Frames previstos":5,"Local / âncora":"Registry legado e arquivo externo de manutenção","Ordem":2,"Spoiler máximo":"Pós-vitória restrito","url":"https://app.notion.com/p/40c9c5630425810b83bac3568eac0f0a","Última revisão":"2026-11-02T15:25:46.567Z"}
</properties>
<iconMetadata>null</iconMetadata>
<content>
<callout icon="🎞️" color="blue_bg">
<b>Estado: pré-produção.</b> Esta ficha orienta a criação dos cinco frames do Case. Não autoriza publicar ou substituir arte do site.
</callout>

## Contrato de revelação

<b>Antes do challenge:</b> Elias está morto e sua credencial revogada, mas o registry legado ainda responde.

<b>Após a vitória:</b> o documento aponta Warehouse 17; o controle irregular é explicitamente liberado.

## Âncoras que não podem derivar

- Dois estados em conflito: civil encerrado versus perfil técnico legado.
- Arquivo de manutenção externo; não confundir operador com recebedor financeiro.
- Breaker mantém identidade visual e rosto oculto.

## Beat board — cinco frames

| Frame | Função e momento | Ação / informação visível | Teto de spoiler |
| --- | --- | --- | --- |
| B0 | Chegada | Registros civil e técnico em tensão. | não tomar identidade |
| B1 | Investigação | Controlador e referência opaca de documento. | sem documento liberado |
| B2 | Limite ético | Mara preserva prova sem autorizar posse permanente. | sem normalizar a invasão |
| B3 | Prova pós-vitória | Documento de manutenção aponta Warehouse 17. | não mostrar o Warehouse |
| B4 | Fio seguinte | Rota antiga rumo a Lower Meridian. | não antecipar o Case 03 |

## Gate de geração

- [ ] Ler os arquivos narrativos e a imagem-base corretos.
- [ ] Anexar referência de personagem e de ambiente separadamente.
- [ ] Escrever prompt por blocos: cena, sujeito, ação, câmera, luz, restrições.
- [ ] Aprovar B0/B1 antes de produzir B2–B4.
- [ ] Registrar URL, versão, crop 8:3 e resultado de QA em cada frame.

<callout icon="🔒" color="gray_bg">
<b>Proibido:</b> usar o frame pós-vitória como hero, mostrar rosto do Breaker ou antecipar o Case seguinte.
</callout>

## Auditoria de direção — 02/11/2026

<b>Leitura do arco:</b> o Case não é “um morto volta”; é a divergência entre estado civil e perfil técnico legado.

<b>Hero recomendado:</b> B1 — dois registros físicos/diegéticos em conflito, Breaker observando de lado ou de costas.

<b>Referências a congelar:</b> identidade visual do registry, arquivo externo de manutenção, linguagem visual de Elias sem canonizar rosto.

<b>Risco principal:</b> usar retrato de Elias ou dar estética sobrenatural a um problema administrativo.

<b>Plano de câmera:</b> B0 entrada no registry; B1 composição com dois estados divergentes; B2 consulta de controlador; B3 documento pós-vitória com Warehouse 17 ainda fora de quadro; B4 rota antiga para Lower Meridian.

## Aplicação do padrão de direção de arte

Aplicar a metodologia da seção 20 do [Manual de Direção de Arte — Season 1](https://app.notion.com/p/4039c563042581d9bf27d22d355dc5b2) ao detalhar e gerar cada beat desta ficha.

Para cada cena, definir câmera física, escala, blocking, ação, foco, luz, âncoras e teto de spoiler. Antes de gerar, comparar com os beats vizinhos e mudar pelo menos três dimensões visuais (escala, eixo, posição do personagem, ação, foco ou profundidade). Usar a referência de ambiente para preservar lugar e materiais, sem copiar automaticamente sua composição; anexar o frame predecessor somente quando for necessário à continuidade espacial.

A direção específica e os riscos já registrados na auditoria deste Case continuam valendo. A metodologia orienta como executar, não altera o roteiro canônico.
</content>
</page>

<parent-data-source-schema url="collection://81383529-1b5e-4c94-8738-1ce5d9fb368b">
The SQLite table definition for this page's parent data source. Use these column names and option values to set this page's properties, create sibling pages, or query the data source.
These columns are read-only, so don't set them: "Última revisão".
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
</parent-data-source-schema>

