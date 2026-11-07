---
notion_id: 40c9c563-0425-810b-83ba-c3568eac0f0a
source: https://app.notion.com/p/40c9c5630425810b83bac3568eac0f0a?pvs=204
title: "02 — The Dead Man's Wallet"
exported_at: 2026-11-07
---

**Estado: pré-produção.** Esta ficha orienta a criação dos cinco frames do Case. Não autoriza publicar ou substituir arte do site.

## Contrato de revelação

**Antes do challenge:** Elias está morto e sua credencial revogada, mas o registry legado ainda responde.

**Após a vitória:** o documento aponta Warehouse 17; o controle irregular é explicitamente liberado.

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

**Proibido:** usar o frame pós-vitória como hero, mostrar rosto do Breaker ou antecipar o Case seguinte.

## Auditoria de direção — 02/11/2026

**Leitura do arco:** o Case não é “um morto volta”; é a divergência entre estado civil e perfil técnico legado.

**Hero recomendado:** B1 — dois registros físicos/diegéticos em conflito, Breaker observando de lado ou de costas.

**Referências a congelar:** identidade visual do registry, arquivo externo de manutenção, linguagem visual de Elias sem canonizar rosto.

**Risco principal:** usar retrato de Elias ou dar estética sobrenatural a um problema administrativo.

**Plano de câmera:** B0 entrada no registry; B1 composição com dois estados divergentes; B2 consulta de controlador; B3 documento pós-vitória com Warehouse 17 ainda fora de quadro; B4 rota antiga para Lower Meridian.

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

