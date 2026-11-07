---
notion_id: 40c9c563-0425-81d0-8fd7-f3b43f578674
source: https://app.notion.com/p/40c9c563042581d08fd7f3b43f578674?pvs=204
title: "09 — The Oracle"
exported_at: 2026-11-07
---

**Estado: pré-produção.** Esta ficha orienta a criação dos cinco frames do Case. Não autoriza publicar ou substituir arte do site.

## Contrato de revelação

**Antes do challenge:** Oracle oferece previsões; auditor registra respostas antes de cada execução.

**Após a vitória:** Três respostas provam cálculo em contexto público; SUBJECT\_CLASSIFIER permanece observando e aponta Spire.

## Âncoras que não podem derivar

- Câmara circular, esfera azul holográfica e observadores periféricos.
- Simetria controlada; Breaker pequeno e centralizado sob a esfera.
- Nunca mostrar Architect antes da cena pós-vitória.

## Beat board — cinco frames

| Frame | Função e momento | Ação / informação visível | Teto de spoiler |
| --- | --- | --- | --- |
| B0 | Chegada | Três previsões bloqueadas e esfera ativa. | sem respostas |
| B1 | Investigação | Prophecy Engine e Subject Classifier em contexto. | sem mecanismo explicado |
| B2 | Preparação | Registro prévio das respostas. | sem sucesso |
| B3 | Prova pós-vitória | Hologramas param; cálculo demonstrado. | ARCHITECT só como texto/gancho |
| B4 | Fio seguinte | Coordenadas da Spire operacional. | não antecipar Case 10 |

## Gate de geração

- [ ] Ler os arquivos narrativos e a imagem-base corretos.
- [ ] Anexar referência de personagem e de ambiente separadamente.
- [ ] Escrever prompt por blocos: cena, sujeito, ação, câmera, luz, restrições.
- [ ] Aprovar B0/B1 antes de produzir B2–B4.
- [ ] Registrar URL, versão, crop 8:3 e resultado de QA em cada frame.

**Proibido:** usar o frame pós-vitória como hero, mostrar rosto do Breaker ou antecipar o Case seguinte.

## Auditoria de direção — 02/11/2026

**Leitura do arco:** a revelação é que “profecia” é cálculo público; ainda não é a revelação do Architect.

**Hero recomendado:** B1 — câmara circular, esfera azul e Breaker centralizado, antes de qualquer resposta.

**Referências a congelar:** esfera, observadores periféricos, simetria controlada e linguagem monumental do Oracle.

**Risco principal:** inserir ARCHITECT no hero, revelar respostas ou fazer a esfera parecer magia.

**Plano de câmera:** B0 chegada à câmara; B1 axial sob a esfera; B2 preparação das previsões; B3 hologramas interrompidos pós-vitória; B4 coordenadas da Spire, sem mostrar a Spire por dentro.

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

