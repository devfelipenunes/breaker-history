---
notion_id: 40c9c563-0425-818f-8d48-c09218b8600b
source: https://app.notion.com/p/40c9c5630425818f8d48c09218b8600b?pvs=204
title: "05 — The Custodian"
exported_at: 2026-11-07
---

**Estado: pré-produção.** Esta ficha orienta a criação dos cinco frames do Case. Não autoriza publicar ou substituir arte do site.

## Contrato de revelação

**Antes do challenge:** Custodian exige credenciais de operador; a cadeia de confiança parece íntegra.

**Após a vitória:** passagem abre indevidamente; workspace de Aren Voss é encontrado.

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

**Proibido:** usar o frame pós-vitória como hero, mostrar rosto do Breaker ou antecipar o Case seguinte.

## Auditoria de direção — 02/11/2026

**Leitura do arco:** é um boss de confiança composta: o Core local parece correto, a dependência é que está comprometida.

**Hero recomendado:** B1 — simetria de autoridade, Breaker pequeno diante do Core Gate e sinais de acesso negado.

**Referências a congelar:** presença sem rosto do Custodian, leitores/portas, Core Gate e gramática da First Layer.

**Risco principal:** criar monstro humanoide, ação física ou passagem já liberada.

**Plano de câmera:** B0 aproximação; B1 confrontação axial; B2 evidência administrativa fora do contrato; B3 travas recuando pós-vitória; B4 limiar do workspace de Voss, sem revelar sua resposta.

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

