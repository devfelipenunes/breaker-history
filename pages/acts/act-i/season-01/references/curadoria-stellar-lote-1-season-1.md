---
notion_id: 40f9c563-0425-81c7-932f-e5b0848bdd22
source: https://app.notion.com/p/40f9c563042581c7932fe5b0848bdd22?pvs=204
title: "Curadoria Stellar — lote 1 Season 1"
exported_at: 2026-11-07
---

Estado: lote 1 implementado — 05/11/2026. A aplicação foi validada em PT-BR/EN e não altera o roteiro locked v1.4, os desafios, nem o status canônico de Meridian.

## Critério de escolha

Cada referência deve aumentar a sensação de uma cidade construída sobre Stellar, sem agir como publicidade, exigir reconhecimento externo ou dar pista de solução. Uma referência por composição, sempre periférica; nenhuma vira hotspot adicional no mapa.

## Shortlist recomendada

| Referência | Onde entra | Função diegética | Estado |
| --- | --- | --- | --- |
| O Foguete Esquecido | Mapa / Lower Meridian | Mural gasto; dá memória histórica à cidade sem afetar a missão. | Implementado |
| XDR Lab / Inspector | Case 01 | Documento forense opcional; nunca cobre a investigação do contrato. | Implementado |
| Quest Terminal / First Light | Mapa / Soroban District | Terminal secundário de aprendizado; cenário, não minijogo. | Implementado |
| Galexie / Mirror 13 | Case 07 | Etiqueta de exportação de registros não centrais; reforça a investigação. | Implementado |
| Stellar Machine / Flow Wall | Case 07 | Painel ambiental de fluxo de operações; sem dados secretos nem UI interativa falsa. | Implementado |

## Regras de implementação

- Não usar logo dominante, co-branding ou alegar parceria/endosso.
- Não inventar dados on-chain, arquivos privados no ledger ou prova falsa do Registry.
- O TERMINAL do Breaker OS continua espelhando apenas chamadas reais; referências visuais não podem virar console falso.
- Nenhum egg bloqueia, revela ou confirma a solução de um case.
- Em cada imagem 8:3, o Breaker e o conflito do case continuam sendo a leitura principal.

## Guardar para depois

Passkey Kit, Smart Account Kit, Polly Wallet e Ohloss/Blend combinam mais com Lumen. ZKP Maze, ZK Kalien, ZK Dead Man’s Draw e Who Ate Gerald? pertencem naturalmente a Veil. MPP/x402 ficam como referência de comunicação para uma temporada futura.

## Fontes verificadas

- [Stellar Machine](https://stellar.org/frontier/projects/stellar-machine/)
- [Projetos do Frontier Lab](https://stellar.org/frontier/projects/)
- [Galexie](https://developers.stellar.org/docs/data/indexers/build-your-own/galexie)
- [Stellar Lab / Quickstart](https://developers.stellar.org/docs/tools/lab/quickstart-with-lab)

## Decisão de elenco — confirmada em 05/11/2026

Os personagens fictícios permanecem sem renomeação: BREAKER, Mara Vale, Aren Voss, The Custodian, The Architect e Sera Quill. Referências reais do ecossistema Stellar entram em geografia, instalações, documentos e infraestrutura — nunca como pessoas fictícias, falas inventadas ou endosso implícito.

## Mapa de produção — textos e imagens

| Ordem | Referência | Arquivo / superfície | Mudança planejada | O que não muda |
| --- | --- | --- | --- | --- |
| 1 | O Foguete Esquecido | `frontend/public/images/levels/homepage.webp` | Mural de foguete gasto e pequeno em Lower Meridian, integrado à arquitetura. | Sem novo hotspot, rótulo ou texto da home. |
| 1 | Quest Terminal / First Light | `homepage.webp` | Um único terminal secundário no Soroban District, tratado como cenário distante. | Não cria minijogo, app, card ou missão. |
| 2 | XDR Lab / Inspector | `frontend/src/levels/narrative/01.json`, documento `01-document-1` | Reforçar que a trilha preserva estrutura de consulta e eventos de serviço; o conteúdo continua opcional dentro de Evidências/Arquivos. | Sem nova aba, console falso ou alteração das dicas de autorização. |
| 3 | Galexie / Mirror 13 | `frontend/public/images/levels/07.png`, documento `07-document-1` | Parede de monitores distante e uma única referência visual de exportação/índice de registros; o documento esclarece que índice não prova autoria nem armazena arquivos privados. | Não muda a mecânica de overflow, os valores, as dicas ou a tese do caso. |
| 3 | Stellar Machine / Flow Wall | `07.png` | Linguagem visual do mesmo conjunto de monitores: fluxo abstrato de operações, sem texto pequeno ou dados alegadamente reais. | Não vira terminal interativo nem uma segunda referência concorrente. |

## Regras de redação

- Os textos novos entram apenas nos documentos existentes do Case 01 e Case 07; não acrescentar beat, contato, personagem ou diálogo.
- Nenhuma linha nova pode explicar a falha, antecipar uma chamada, apresentar um número útil ou confirmar a autoria do incidente.
- “XDR”, “exportação”, “índice” e “telemetria” descrevem infraestrutura; não podem alegar que o ledger contém arquivos privados, identidade ou prova de responsabilidade.
- O Case 07 mantém a formulação central: demonstrar o comportamento antes de atribuir intenção.

## Sequência de execução proposta

1. Revisar a arte da home sem alterar a interação do mapa.
2. Revisar a arte e o documento do Case 07 como uma única composição.
3. Ajustar o documento opcional do Case 01.
4. Validar em PT-BR/EN, contraste/legibilidade, narrativa sem spoiler e guardas do manifesto.

Mazières Hall, Weller Workshop, Kim Commons e McCaleb Passage ficam fora deste lote: aguardam uma futura revisão maior do mapa, para não sobrecarregar a primeira imagem de Meridian.
