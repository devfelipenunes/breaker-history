---
notion_id: 40c9c563-0425-81d7-ace3-ff4a6c339158
source: https://app.notion.com/p/40c9c563042581d7ace3ff4a6c339158?pvs=204
title: "🎮 ARQUIVO — 14 Ideias de Interatividade e Ritmo"
exported_at: 2026-11-07
---

Explorar maneiras de fazer o jogador sentir que está **investigando e executando um hack**, com agência técnica, enquanto a história de Meridian segue linear e a dificuldade da Season 1 permanece acessível.

> **Status: banco de propostas de design.** A priorização e os critérios executáveis da revisão estão no [15 — Plano de Melhorias e QA — Season 1](../production/15-plano-de-melhorias-e-qa-season-1.md). Nada nesta página confirma implementação. Os dez Cases, os dois Bosses e seus resultados narrativos permanecem fixos.

## Princípios para a experiência

- O jogador deve agir sobre sistemas: inspecionar estado, formular hipótese, executar chamadas, observar efeitos, ajustar e verificar a prova.
- A interface deve mostrar consequências legíveis: mudanças no estado, eventos, erros, permissões, registros e resposta do ambiente.
- A história deve emergir dessas consequências, de vestígios e de poucas falas. Evitar diálogo que apenas repete o terminal.
- O desafio deve exigir raciocínio sem depender de informação escondida ou comandos sem pistas.
- As perguntas interativas podem mudar o **foco da investigação ou a apresentação de uma pista**, mas não a conduta do Breaker, as relações, as cenas canônicas ou o final.
- A pergunta final do Architect — “Por que você continuou?” — permanece sem opções selecionáveis.

## Interações para testar

Não colocar uma pergunta em todo slide. Testar uma interação em momentos de descoberta, hipótese ou fechamento de Case. Uma seleção só vale a pena se provocar uma resposta perceptível na interface: destacar uma evidência, abrir um registro relacionado, mostrar uma dica contextual ou registrar a hipótese no caderno do jogador.

| Tipo | Exemplo | Efeito permitido |
| --- | --- | --- |
| **Foco de investigação** | “Qual pista você quer examinar agora?” | Destaca ou abre a pista escolhida |
| **Hipótese** | “O que essa evidência sugere?” | Registra a leitura e pode oferecer uma dica curta |
| **Próximo teste** | “Qual informação falta para confirmar isso?” | Aponta para uma ferramenta ou evidência disponível, sem revelar automaticamente a solução |
| **Leitura de consequência** | “O que mudou depois da chamada?” | Ajuda a notar o efeito técnico ou humano da ação |

Evitar seleções como “Você confia em Mara?” se nada muda na cena. Não apresentar decisões de moralidade ou personalidade como se tivessem consequências. No Architect, manter a pergunta como momento dramático sem menu.

### Exemplos em Meridian

- **Vault:** “Qual parte da operação ainda não está explicada?” — autoria, autorização ou destino dos fundos.
- **Warehouse 17:** “Que evidência precisa ser preservada?” — a origem da chave, o estado do recurso ou o registro de autorização.
- **Sector 13:** “Que observação já basta para confirmar o padrão?” — erro isolado, repetição ou prova recuperável.
- **Oracle:** “O resultado era imprevisível ou apenas parecia imprevisível?” — sem dizer que a resposta muda a história.
- **Rewrite:** “O que permaneceu igual depois da mudança?” — endereço, código ou regra.

Essas perguntas funcionam melhor depois de a pista estar disponível. Antes da resolução, não devem revelar o nome da vulnerabilidade ou o exploit esperado.

## Avaliação inicial dos desafios da Season 1

A sequência atual tem uma progressão adequada para uma primeira temporada: começa com autorização e identidade, passa por estado e armazenamento, introduz falhas entre contratos e valores impossíveis e termina com alteração de autoridade e código. O Custodian e o Architect podem cobrar combinação de conhecimento, sem acrescentar uma longa série de conceitos novos.

| Trecho | Leitura preliminar | Ajuste de experiência sem elevar muito a dificuldade |
| --- | --- | --- |
| **Cases 1–2** | Bons para ensinar o ciclo, mas autorização e identidade podem parecer variações do mesmo truque | Dar a cada um um objetivo e feedback distintos: no primeiro, descobrir por que a chamada passou; no segundo, perceber o que uma identidade reconfigurada ainda controla |
| **Cases 3–4** | Aumentam o custo e mudam a natureza da investigação | Tornar visível a cadeia de custódia da Ghost Key; no Forgotten Floor, enfatizar a descoberta ambiental e dar uma pausa de ritmo |
| **Custodian** | Bom primeiro teste composto | Reutilizar pistas e ações aprendidas; apresentar o reconhecimento “WELCOME BACK” como recompensa narrativa, não como uma nova mecânica obscura |
| **Cases 5–6** | Mudam para falhas entre contratos e estado numérico | Usar rastros e comparação de estado para ensinar o que mudou; manter o caminho de verificação curto |
| **Case 7** | A consequência operacional cria tensão, mas DoS pode incentivar repetição cega | Mostrar custo/carga e um sinal claro de quando já há prova suficiente para interromper a pressão |
| **Case 8** | Oferece contraste de ritmo com observação e previsão | Dar ao jogador um espaço para comparar resultados e perceber o padrão, sem transformar o desafio em tentativa aleatória |
| **Cases 9–10** | Clímax forte; podem exigir combinações mais complexas | Reutilizar ferramentas já ensinadas. A dificuldade pode vir da sequência e das consequências, não de esconder controles ou adicionar vários conceitos inéditos |
| **Architect** | A síntese final é apropriada como maior desafio | Cobrar evidências e técnicas já aprendidas. A reconstrução narrativa deve vir após a verificação técnica e não depender de uma resposta de diálogo |

### Critérios simples para calibrar dificuldade

Avaliar cada desafio por cinco dimensões: conceitos novos, distância de inferência, número de ferramentas a combinar, precisão de execução e clareza do feedback. Para a Season 1, aumentar principalmente uma dimensão por vez. No começo, ensinar comandos e leitura de estado; no meio, pedir conexão entre pistas; no fim, combinar ferramentas conhecidas.

Se um jogador não avança, primeiro verificar se entende o objetivo, se consegue inspecionar o estado e se o feedback mostra por que a tentativa falhou. Aumentar dificuldade não deve significar esconder pistas necessárias. Um boss deve combinar o que já foi ensinado antes de introduzir uma regra completamente nova.

## O que o repositório enviado oferece

O repositório [Veritas Vaults — soroban-guard-contracts](https://github.com/Veritas-Vaults-Network/soroban-guard-contracts) reúne contratos Soroban vulneráveis, alguns exemplos corrigidos e material de referência para apoiar testes de um scanner. A tabela e os temas têm correspondência direta com vários conceitos já previstos nos Cases de Meridian — por exemplo, autorização ausente, reinitialization, TTL, aritmética, falha de acesso administrativo e upgrade.

**Uso recomendado para BREAKER:** fonte de padrões de vulnerabilidade e ideias para verificar contratos de treino. O README o descreve como biblioteca de amostras para testar o Guard scanner, então não é, por si só, um jogo com progressão, narrativa ou curva de dificuldade pronta. A documentação de vulnerabilidades também não substitui a validação de cada contrato e teste no SDK/runtime Soroban usado pelo jogo.

## Materiais semelhantes e o que podemos aprender

| Recurso | Semelhança | Possível uso para BREAKER |
| --- | --- | --- |
| [soroban-lock-contracts](https://github.com/verita-lock/soroban-lock-contracts) | Catálogo Soroban de exemplos vulneráveis e padrões corrigidos; muito próximo do formato do repositório enviado | Comparar padrões e correções, mas confirmar autoria, manutenção e independência antes de tratar como segunda fonte |
| [Scout Soroban — Vulnerabilities](https://coinfabrik.github.io/scout-soroban/docs/vulnerabilities) | Pequenos contratos e categorias de falhas, criados para testar o detector Scout e também servir como material educativo | Buscar exemplos de aritmética, validação e escrita em storage; adaptar apenas após checar a validade na versão atual |
| [Scout Soroban — exemplos auditados](https://coinfabrik.github.io/scout-soroban/docs/soroban-examples) | Contratos de domínios como AMM, governança, multisig, payment channel e vesting, acompanhados de achados de revisão | Inspirar desafios mais situados em sistemas que o jogador reconhece, em vez de só “um contrato vulnerável” |
| [stellar/soroban-examples](https://github.com/stellar/soroban-examples) | Exemplos oficiais de funcionalidades Soroban, como auth, cross-contract calls, TTL, timelock e upgrade | Verificar comportamento idiomático da plataforma e construir contexto técnico para os challenges; não é um catálogo de exploits |
| [web3-vulnerability-labs](https://github.com/ChargingFoxSec/web3-vulnerability-labs) | Laboratórios pequenos e reproduzíveis de vulnerabilidades Web3, incluindo exemplos rotulados para Soroban | Ideias de formato de laboratório e testes; confirmar se cada exercício tem documentação e reprodução suficiente para jogadores |

### Limites da comparação

Os repositórios citados têm objetivos diferentes: alguns testam scanners, alguns demonstram padrões, outros funcionam como laboratórios. A semelhança do título ou da lista de vulnerabilidades não prova que sejam jogos comparáveis nem que todas as falhas estejam corretas para o runtime atual.

Em particular, não copiar diretamente para Meridian um padrão clássico de reentrancy de EVM. O cânone já registra que reentrada de contrato não é uma mecânica Soroban apropriada para esta fase e usa tratamento de falhas entre contratos como superfície compatível. Cada desafio precisa ser reproduzível, ter condição objetiva de vitória, tentativa normal que não vença, solução corrigida que bloqueie o exploit e verificador independente da UI.

## Próximo estudo sugerido

Revisar cada desafio no repositório junto da implementação real do Case e preencher uma matriz curta:

1. Qual é a hipótese que o jogador deve formular?
2. Que evidência ele consegue inspecionar antes de tentar?
3. Qual ação técnica dá a sensação de “eu fiz o hack”?
4. O que muda no estado quando a tentativa funciona ou falha?
5. O que a vitória revela sobre Meridian ou seus personagens?
6. O desafio pode ser concluído por um caminho claro sem aumentar muito a dificuldade?
7. A vulnerabilidade e o teste continuam válidos no SDK/runtime atual?

A revisão de design desta página é preliminar e baseada na documentação disponível; ela não afirma que os contratos do jogo foram executados ou testados.
