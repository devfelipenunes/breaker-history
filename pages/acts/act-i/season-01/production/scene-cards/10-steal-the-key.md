---
notion_id: 40c9c563-0425-81ab-9a2b-dce091219b0a
source: https://app.notion.com/p/40c9c563042581ab9a2bdce091219b0a?pvs=204
title: "10 — Steal the Key"
exported_at: 2026-11-07
---

**Estado: pré-produção.** Esta ficha orienta a criação dos cinco frames do Case. Não autoriza publicar ou substituir arte do site.

## Contrato de revelação

**Antes do challenge:** A Authority revoga o acesso externo; Mara concede apenas uma hora para uma prova verificável.

**Após a vitória:** Uma autorização válida muda de significado até a execução; console aponta para Rewrite e The Architect.

## Âncoras que não podem derivar

- Spire ativa: plataformas, módulos, cabos e manutenção real.
- Câmera baixa/diagonal; Breaker investiga, não encena roubo físico.
- Não mostrar upgrade de WASM nem Final antes de sua etapa narrativa.

## Beat board — cinco frames

| Frame | Função e momento | Ação / informação visível | Teto de spoiler |
| --- | --- | --- | --- |
| B0 | Chegada | Canal interrompido e mandato encerrado. | sem acesso |
| B1 | Investigação | Recibo auditável e manutenção legítima. | sem chave roubada |
| B2 | Tensão | Janela de execução e significado preservado. | sem payload alterado |
| B3 | Prova pós-vitória | Acesso sem possuir a chave. | não mostrar Rewrite/Architect |
| B4 | Fio seguinte | Console de gerenciamento de executável. | não ilustrar upgrade |

## Gate de geração

- [ ] Ler os arquivos narrativos e a imagem-base corretos.
- [ ] Anexar referência de personagem e de ambiente separadamente.
- [ ] Escrever prompt por blocos: cena, sujeito, ação, câmera, luz, restrições.
- [ ] Aprovar B0/B1 antes de produzir B2–B4.
- [ ] Registrar URL, versão, crop 8:3 e resultado de QA em cada frame.

**Proibido:** usar o frame pós-vitória como hero, mostrar rosto do Breaker ou antecipar o Case seguinte.

## Auditoria de direção — 02/11/2026

**Leitura do arco:** uma autorização legítima muda de significado entre agendamento e execução; não há roubo físico de chave.

**Hero recomendado:** B1 — Spire ativa, manutenção real, Breaker pequeno investigando de uma plataforma diagonal.

**Referências a congelar:** silhueta da Spire, plataformas, módulos, cabos, canal encerrado e recibo de Mara.

**Risco principal:** fazer cena de invasão/alarme, mostrar a chave, upgrade de WASM ou o cubo do Rewrite.

**Plano de câmera:** B0 exterior ativo da Spire; B1 plataforma de investigação; B2 recibo e manutenção autorizada; B3 consequência pós-vitória sem chave; B4 console de executável como limiar abstrato, sem upgrade.

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

