# BREAKER — arquivo do Notion

Arquivo editorial do workspace **BREAKER — Series Workspace**. Esta cópia conserva propostas, material canônico e arquivos históricos conforme identificados no Notion.

## Escopo e atualização

O manifesto registra a exportação de **2026-11-07**: **209 páginas** e **4 snapshots de bancos de dados**. Todos os caminhos de página listados no manifesto existem nesta cópia. Os `README.md` adicionais são índices de navegação locais e, por isso, não aparecem como páginas exportadas no manifesto.

Este repositório é um snapshot editorial, não uma cópia integral nem uma sincronização em tempo real do workspace. Alguns links levam a páginas do Notion que não foram exportadas individualmente; anexos e imagens também não estão empacotados aqui. Para confirmar o estado atual de uma decisão ou conteúdo, consulte a página de origem no Notion e confira sua precedência antes de usar versões arquivadas.

## Navegação

- [Workspace e índice da série](pages/index.md)
- [Series Bible](pages/README.md#series-bible)
- [Acts e Seasons](pages/acts/README.md)
- [Bancos de dados exportados](databases/README.md)
- [Manifesto de origem](manifest.json)

## Como navegar e usar

Comece pelo índice do workspace e siga os links relativos. A organização segue Act → Season → área de conteúdo. Em cada Season, `overview.md` apresenta a orientação editorial e aponta para as páginas mais importantes. Materiais antigos ficam em `archive/`; confira os avisos de precedência antes de usá-los.

Os arquivos em `databases/` são snapshots JSON formatados para consulta, não bases vivas. As páginas Markdown são a forma principal de navegar e ler o conteúdo editorial. O `manifest.json` registra a correspondência com as fontes do Notion e a data desta exportação.

## Padrão de organização

A navegação segue a estrutura editorial do Notion: série → Act → Season → área de conteúdo. Cada pasta usa nomes legíveis e um README como índice. IDs aparecem apenas no frontmatter e no manifesto, nunca nos nomes de arquivos.

Dentro de cada Season, o conteúdo fica separado por função: visão geral, narrativa, cases, mundo, personagens, desafios, produção, referências, comunidade e arquivo histórico. O conteúdo sem equivalente direto fica em shared no Act correspondente.

O desenho usa a hierarquia editorial como mapa. Para documentação técnica futura, a distinção entre tutorial, guia prático, referência e explicação pode complementar essa árvore, sem misturar essas categorias aos documentos narrativos.

