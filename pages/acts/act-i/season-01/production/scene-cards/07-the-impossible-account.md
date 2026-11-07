---
notion_id: 40c9c563-0425-81e6-a58c-d51509a1e0c9
source: https://app.notion.com/p/40c9c563042581e6a58cd51509a1e0c9?pvs=204
title: "07 — The Impossible Account"
exported_at: 2026-11-07
---

**Estado: pré-produção.** Esta ficha orienta a criação dos cinco frames do Case. Não autoriza publicar ou substituir arte do site.

## Contrato de revelação

**Antes do challenge:** Saldo histórico impossível em módulo energético ausente dos painéis modernos.

**Após a vitória:** Anomalia é reproduzida; tabela legada aponta Grid Node 13 e Sector 13.

## Âncoras que não podem derivar

- Instalação energética enorme, anéis e infraestrutura suspensa.
- Azul-acinzentado e céu de entardecer; Breaker sentado ergonomicamente no terminal.
- Número 13 só surge pós-vitória, nunca como decoração precoce.

## Beat board — cinco frames

| Frame | Função e momento | Ação / informação visível | Teto de spoiler |
| --- | --- | --- | --- |
| B0 | Chegada | Módulo responde apesar de oculto. | sem saldo explicado |
| B1 | Investigação | Operações e limites declarados. | sem atribuir intenção |
| B2 | Hipótese | Voss rejeita furto como explicação simples. | sem tabela de rota |
| B3 | Prova pós-vitória | Anomalia reproduzida; tabela legada. | não mostrar Sector 13 |
| B4 | Fio seguinte | Destino sem cadastro: Sector 13. | não antecipar Case 08 |

## Gate de geração

- [ ] Ler os arquivos narrativos e a imagem-base corretos.
- [ ] Anexar referência de personagem e de ambiente separadamente.
- [ ] Escrever prompt por blocos: cena, sujeito, ação, câmera, luz, restrições.
- [ ] Aprovar B0/B1 antes de produzir B2–B4.
- [ ] Registrar URL, versão, crop 8:3 e resultado de QA em cada frame.

**Proibido:** usar o frame pós-vitória como hero, mostrar rosto do Breaker ou antecipar o Case seguinte.

## Auditoria de direção — 02/11/2026

**Leitura do arco:** não é roubo de energia: é demonstrar uma contradição de estado e seguir uma relação de infraestrutura.

**Hero recomendado:** B1 — instalação energética monumental, Breaker sentado de forma plausível no terminal.

**Referências a congelar:** anéis/módulo energético, terminal ergonômico, céu de entardecer e proporção azul-acinzentado.

**Risco principal:** antecipar o número 13, transformar o local em sala genérica ou usar o mesmo plano de console do Case 01.

**Plano de câmera:** B0 escala da instalação; B1 diagonal baixa com operação sentada; B2 leitura de limites; B3 pós-vitória com tabela legada abstrata; B4 rota para Sector 13 sem mostrar seu arquivo.

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

