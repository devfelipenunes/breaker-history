---
notion_id: 40c9c563-0425-81ab-9e92-cf51bd2c1aff
source: https://app.notion.com/p/40c9c563042581ab9e92cf51bd2c1aff?pvs=204
title: "08 — Sector 13"
exported_at: 2026-11-07
---

**Estado: pré-produção.** Esta ficha orienta a criação dos cinco frames do Case. Não autoriza publicar ou substituir arte do site.

## Contrato de revelação

**Antes do challenge:** Cemitério de dados ainda recebe carga; objetivo é demonstrar limite sem ampliar dano.

**Após a vitória:** Snapshot externo revela registros e aponta Oracle; custo da indisponibilidade permanece.

## Âncoras que não podem derivar

- Arquivo industrial, corredores laterais e pontes profundas.
- Vermelho profundo localizado; interfaces fragmentadas, sem excesso de retratos.
- Breaker atravessa em perfil absoluto, rosto oculto.

## Beat board — cinco frames

| Frame | Função e momento | Ação / informação visível | Teto de spoiler |
| --- | --- | --- | --- |
| B0 | Chegada | Carga crítica e registros acumulados. | sem quebra do Archive |
| B1 | Investigação | Snapshot externo e escopo legado. | sem leitura ampla |
| B2 | Limite | Terminal registra operações aceitas. | sem dano crescente |
| B3 | Prova pós-vitória | Snapshot externo passa a servir dados. | não mostrar identidade completa |
| B4 | Fio seguinte | Referência ORACLE do observador. | não antecipar Case 09 |

## Gate de geração

- [ ] Ler os arquivos narrativos e a imagem-base corretos.
- [ ] Anexar referência de personagem e de ambiente separadamente.
- [ ] Escrever prompt por blocos: cena, sujeito, ação, câmera, luz, restrições.
- [ ] Aprovar B0/B1 antes de produzir B2–B4.
- [ ] Registrar URL, versão, crop 8:3 e resultado de QA em cada frame.

**Proibido:** usar o frame pós-vitória como hero, mostrar rosto do Breaker ou antecipar o Case seguinte.

## Auditoria de direção — 02/11/2026

**Leitura do arco:** o Archive é uma dependência sobrecarregada; a vitória tem custo e não deve parecer triunfo heroico.

**Hero recomendado:** B1 — corredor industrial com carga crítica, Breaker em perfil e camadas de registros.

**Referências a congelar:** corredor/ponte, vermelho profundo localizado, interfaces fragmentadas e linguagem do Archive.

**Risco principal:** vender destruição como espetáculo, exibir o BREAKER REGISTRY inteiro ou retratos faciais canônicos.

**Plano de câmera:** B0 aproximação de arquivo ativo; B1 perfil lateral; B2 operações sob controle; B3 snapshot externo pós-vitória e consequência; B4 referência Oracle, sem esfera ou Architect.

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

