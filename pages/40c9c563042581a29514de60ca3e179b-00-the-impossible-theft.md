---
notion_id: 40c9c563-0425-81a2-9514-de60ca3e179b
source: https://app.notion.com/p/40c9c563042581a29514de60ca3e179b?pvs=204
title: "00 — The Impossible Theft"
exported_at: 2026-11-07
---

Here is the result of "fetch" for the Page with URL https://app.notion.com/p/40c9c563042581a29514de60ca3e179b as of 2026-11-02T15:25:44.521Z:
<page url="https://app.notion.com/p/40c9c563042581a29514de60ca3e179b">
<ancestor-path>
<parent-data-source url="collection://81383529-1b5e-4c94-8738-1ce5d9fb368b" name="S01 — Fichas de Cena e Continuidade"/>
<ancestor-2-database url="https://app.notion.com/p/65e5dbd085bf43c0adfca3685d5896e8" title="S01 — Fichas de Cena e Continuidade"/>
<ancestor-3-page url="https://app.notion.com/p/4039c563042581d9bf27d22d355dc5b2" title="10 — Direção de Arte | Meridian S1 — Manual de Produção e Continuidade"/>
<ancestor-4-page url="https://app.notion.com/p/4019c5630425819d8e93e523aa0c2045" title="00 — Series Bible"/>
<ancestor-5-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
<properties>
{"Case":"00 — The Impossible Theft","Estado":"Backlog","Fase":"Prólogo","Fonte canônica":"https://app.notion.com/p/4039c563042581d9bf27d22d355dc5b2","Frames previstos":5,"Local / âncora":"Meridian e Meridian Vault; porta intacta","Ordem":0,"Spoiler máximo":"Pós-vitória restrito","url":"https://app.notion.com/p/40c9c563042581a29514de60ca3e179b","Última revisão":"2026-11-02T15:25:44.521Z"}
</properties>
<iconMetadata>null</iconMetadata>
<content>
<callout icon="🎞️" color="blue_bg">
<b>Estado: pré-produção.</b> Esta ficha orienta a criação dos cinco frames do Case. Não autoriza publicar ou substituir arte do site.
</callout>

## Contrato de revelação

<b>Antes do challenge:</b> Meridian funciona; o Vault está intacto e o saldo desapareceu.

<b>Após a vitória:</b> a porta de serviço é liberada para a investigação, sem explicar ainda a entrada no Vault.

## Âncoras que não podem derivar

- Meridian operacional; Vault fechado e reconhecível.
- Mara e auditor em escala humana; sistemas cotidianos funcionais.
- Sem solução visual, chave comprometida ou invasão física.

## Beat board — cinco frames

| Frame | Função e momento | Ação / informação visível | Teto de spoiler |
| --- | --- | --- | --- |
| B0 | Estabelecimento | Cidade que confia em contratos. | somente normalidade institucional |
| B1 | Anomalia | Vault intacto; perda sem arrombamento. | não mostrar o método |
| B2 | Investigação | Terminal de treinamento e revisão limitada. | não sugerir a exploração |
| B3 | Prova | Recibo da primeira submissão e porta de serviço liberada. | não resolver o Vault |
| B4 | Transição | Access Gate como próximo foco. | não revelar o Case 01 |

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

<b>Leitura do arco:</b> prólogo deve vender confiança institucional antes de mostrar a falha; a arte não pode parecer já pós-colapso.

<b>Hero recomendado:</b> B1, Vault intacto e impossível, não o terminal de treinamento.

<b>Referências a congelar:</b> skyline de Meridian, linguagem de porta do Vault, Mara/Brekaer em escala humana.

<b>Risco principal:</b> transformar a anomalia em invasão física ou mostrar a porta de serviço aberta cedo.

<b>Plano de câmera:</b> B0 plano geral da cidade; B1 axial e austero no Vault; B2 médio funcional no terminal; B3 detalhe de recibo/porta de serviço pós-vitória; B4 retorno à porta fechada como promessa do Case 01.

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

