---
notion_id: 40c9c563-0425-818f-8d48-c09218b8600b
source: https://app.notion.com/p/40c9c5630425818f8d48c09218b8600b?pvs=204
title: "05 — The Custodian"
exported_at: 2026-11-07
---

Here is the result of "fetch" for the Page with URL https://app.notion.com/p/40c9c5630425818f8d48c09218b8600b as of 2026-11-02T15:25:49.794Z:
<page url="https://app.notion.com/p/40c9c5630425818f8d48c09218b8600b">
<ancestor-path>
<parent-data-source url="collection://81383529-1b5e-4c94-8738-1ce5d9fb368b" name="S01 — Fichas de Cena e Continuidade"/>
<ancestor-2-database url="https://app.notion.com/p/65e5dbd085bf43c0adfca3685d5896e8" title="S01 — Fichas de Cena e Continuidade"/>
<ancestor-3-page url="https://app.notion.com/p/4039c563042581d9bf27d22d355dc5b2" title="10 — Direção de Arte | Meridian S1 — Manual de Produção e Continuidade"/>
<ancestor-4-page url="https://app.notion.com/p/4019c5630425819d8e93e523aa0c2045" title="00 — Series Bible"/>
<ancestor-5-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
<properties>
{"Case":"05 — The Custodian","Estado":"Backlog","Fase":"Case","Fonte canônica":"https://app.notion.com/p/4039c563042581d9bf27d22d355dc5b2","Frames previstos":5,"Local / âncora":"First Layer e Core Gate","Ordem":5,"Spoiler máximo":"Pós-vitória restrito","url":"https://app.notion.com/p/40c9c5630425818f8d48c09218b8600b","Última revisão":"2026-11-02T15:25:49.794Z"}
</properties>
<iconMetadata>null</iconMetadata>
<content>
<callout icon="🎞️" color="blue_bg">
<b>Estado: pré-produção.</b> Esta ficha orienta a criação dos cinco frames do Case. Não autoriza publicar ou substituir arte do site.
</callout>

## Contrato de revelação

<b>Antes do challenge:</b> Custodian exige credenciais de operador; a cadeia de confiança parece íntegra.

<b>Após a vitória:</b> passagem abre indevidamente; workspace de Aren Voss é encontrado.

## Âncoras que não podem derivar

- Custodian sem rosto: presença nos leitores, portas e autoridade.
- First Layer operacional; não transformar a área em ruína.
- Não revelar a resposta do vínculo histórico antes da prova.

## Beat board — cinco frames

| Frame | Função e momento | Ação / informação visível | Teto de spoiler |
| --- | --- | --- | --- |
| B0 | Chegada | Core Gate e aviso de operador. | sem passagem |
| B1 | Investigação | Ghost Key e evidência administrativa separadas. | sem acesso |
| B2 | Dependência | Sistemas definem pertencimento por cadeia de confiança. | sem controlador comprometido |
| B3 | Prova pós-vitória | Travas recuam; OPERATOR RECOGNIZED. | não mostrar Voss em detalhe |
| B4 | Fio seguinte | Workspace abandonado de Aren Voss. | não resolver Case 06 |

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

<b>Leitura do arco:</b> é um boss de confiança composta: o Core local parece correto, a dependência é que está comprometida.

<b>Hero recomendado:</b> B1 — simetria de autoridade, Breaker pequeno diante do Core Gate e sinais de acesso negado.

<b>Referências a congelar:</b> presença sem rosto do Custodian, leitores/portas, Core Gate e gramática da First Layer.

<b>Risco principal:</b> criar monstro humanoide, ação física ou passagem já liberada.

<b>Plano de câmera:</b> B0 aproximação; B1 confrontação axial; B2 evidência administrativa fora do contrato; B3 travas recuando pós-vitória; B4 limiar do workspace de Voss, sem revelar sua resposta.

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

