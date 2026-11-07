---
notion_id: 40c9c563-0425-815a-a6b1-e3952a29edfe
source: https://app.notion.com/p/40c9c5630425815aa6b1e3952a29edfe?pvs=204
title: "04 — The Forgotten Floor"
exported_at: 2026-11-07
---

**Estado: pré-produção.** Esta ficha orienta a criação dos cinco frames do Case. Não autoriza publicar ou substituir arte do site.

## Contrato de revelação

**Antes do challenge:** elevador e planta registram só 23 andares; Ghost Key aponta o 24.

**Após a vitória:** referência arquivada é recuperada; porta revela entrada à First Layer e Custodian online.

## Âncoras que não podem derivar

- Elevador com 23 botões antes da prova; número 24 não deve aparecer cedo.
- Contraste entre acabamento urbano atual e corredor de infraestrutura antiga.
- Floor 24 é entrada, não o próprio Custodian.

## Beat board — cinco frames

| Frame | Função e momento | Ação / informação visível | Teto de spoiler |
| --- | --- | --- | --- |
| B0 | Chegada | Elevador sem botão 24. | não indicar atalho |
| B1 | Investigação | Referências antigas versus camada ativa. | sem renovação de TTL |
| B2 | Tensão | Interface preserva ausência; Mara procura demolição. | sem botão novo |
| B3 | Prova pós-vitória | Botão 24 surge após recuperação. | não mostrar Custodian |
| B4 | Fio seguinte | Portas para First Layer; alerta de acesso negado. | não antecipar a solução do Case 05 |

## Gate de geração

- [ ] Ler os arquivos narrativos e a imagem-base corretos.
- [ ] Anexar referência de personagem e de ambiente separadamente.
- [ ] Escrever prompt por blocos: cena, sujeito, ação, câmera, luz, restrições.
- [ ] Aprovar B0/B1 antes de produzir B2–B4.
- [ ] Registrar URL, versão, crop 8:3 e resultado de QA em cada frame.

**Proibido:** usar o frame pós-vitória como hero, mostrar rosto do Breaker ou antecipar o Case seguinte.

## Auditoria de direção — 02/11/2026

**Leitura do arco:** a revelação é que o andar estava arquivado, não destruído; o botão 24 é uma consequência, não decoração.

**Hero recomendado:** B1 — elevador com 23 botões e uma ausência visível, sem o número 24.

**Referências a congelar:** painel do elevador, arquitetura de transição, materialidade da First Layer.

**Risco principal:** inserir “24” antes da prova ou confundir a porta do Floor 24 com o cenário do Custodian.

**Plano de câmera:** B0 corredor/elevador; B1 painel de 23; B2 inspeção de referência arquivada; B3 botão 24 pós-vitória; B4 portas abertas para corredor antigo e aviso do Custodian distante.

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

