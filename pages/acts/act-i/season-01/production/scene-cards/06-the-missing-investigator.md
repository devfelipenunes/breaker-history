---
notion_id: 40c9c563-0425-815d-b5c9-c3026a1e2597
source: https://app.notion.com/p/40c9c5630425815db5c9c3026a1e2597?pvs=204
title: "06 — The Missing Investigator"
exported_at: 2026-11-07
---

**Estado: pré-produção.** Esta ficha orienta a criação dos cinco frames do Case. Não autoriza publicar ou substituir arte do site.

## Contrato de revelação

**Antes do challenge:** Comandos interrompidos, mapas e datas anteriores ao incidente; Archive e Decoder discordam.

**Após a vitória:** A gravação de Voss é recuperada; módulo energético IMPOSSIBLE vira a nova pista.

## Âncoras que não podem derivar

- Sala quente, vivida e claustrofóbica; mesa de evidências e janelas de Meridian.
- Voss só como rastro/registro, não como presença física canônica.
- Quebrar a simetria monumental; Breaker inclinado sobre a mesa.

## Beat board — cinco frames

| Frame | Função e momento | Ação / informação visível | Teto de spoiler |
| --- | --- | --- | --- |
| B0 | Chegada | Workspace e investigação interrompida. | sem mensagem recuperada |
| B1 | Investigação | Archive diz recuperado; Decoder falhou. | sem resolver a divergência |
| B2 | Pressão | Datas preservadas e registros incompletos. | sem voz de Voss |
| B3 | Prova pós-vitória | Gravação recuperada; ruído e alerta. | não dar plano completo |
| B4 | Fio seguinte | Nota IMPOSSIBLE em módulo energético. | não antecipar Case 07 |

## Gate de geração

- [ ] Ler os arquivos narrativos e a imagem-base corretos.
- [ ] Anexar referência de personagem e de ambiente separadamente.
- [ ] Escrever prompt por blocos: cena, sujeito, ação, câmera, luz, restrições.
- [ ] Aprovar B0/B1 antes de produzir B2–B4.
- [ ] Registrar URL, versão, crop 8:3 e resultado de QA em cada frame.

**Proibido:** usar o frame pós-vitória como hero, mostrar rosto do Breaker ou antecipar o Case seguinte.

## Auditoria de direção — 02/11/2026

**Leitura do arco:** o centro emocional é a investigação deixada por Voss, não a presença física dele.

**Hero recomendado:** B1 — Breaker inclinado numa mesa de evidências, workspace quente e fragmentos frios de dados.

**Referências a congelar:** mesa, mapas, arquivos, janelas de Meridian, padrão de holograma e ausência física de Voss.

**Risco principal:** transformar o workspace em laboratório genérico ou revelar Voss como personagem presente.

**Plano de câmera:** B0 entrada pela sala; B1 meio-plano de investigação; B2 telas em discordância sem texto excessivo; B3 áudio recuperado pós-vitória por luz/onda discreta; B4 nota IMPOSSIBLE e energia como gancho.

## Aplicação do padrão de direção de arte

Aplicar a metodologia da seção 20 do [Manual de Direção de Arte — Season 1](https://app.notion.com/p/4039c563042581d9bf27d22d355dc5b2) ao detalhar e gerar cada beat desta ficha.

Para cada cena, definir câmera física, escala, blocking, ação, foco, luz, âncoras e teto de spoiler. Antes de gerar, comparar com os beats vizinhos e mudar pelo menos três dimensões visuais (escala, eixo, posição do personagem, ação, foco ou profundidade). Usar a referência de ambiente para preservar lugar e materiais, sem copiar automaticamente sua composição; anexar o frame predecessor somente quando for necessário à continuidade espacial.

A direção específica e os riscos já registrados na auditoria deste Case continuam valendo. A metodologia orienta como executar, não altera o roteiro canônico.

The SQLite table definition for this page's parent data source. Use these column names and option values to set this page's properties, create sibling pages, or query the data source.
These columns are read-only, so don't set them: "Última revisão".

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

