---
notion_id: 40c9c563-0425-81e6-81e7-e3523a88a468
source: https://app.notion.com/p/40c9c563042581e681e7e3523a88a468?pvs=204
title: "🧭 15 — Plano de Melhorias e QA — Season 1"
exported_at: 2026-11-07
---

**Status vigente:** plano de execução e QA subordinado ao roteiro v1.4; NÃO é confirmação de código, contratos, slides em runtime ou playtest. Revisão técnica dos níveis 11/12 foi documentada em 2026-11-02, mas não auditada neste workspace. Preserva a história linear, os dez Cases, Custodian e Architect, seus objetivos verificáveis e o final QUALIFIED / PROVISIONAL. Esta página coordena ajustes pequenos, não autoriza alterar contratos ou artes sem testes.

# Objetivo

Transformar o roteiro já maduro em uma experiência coesa: investigar evidências → formular hipótese → explorar contrato → observar mudança de estado → descobrir a próxima pista. O challenge continua no Breaker OS. Slides contam o acontecimento; **BREACH REPORT** explica vulnerabilidade e fix **depois** da vitória.

# Decisões editoriais consolidadas

- Uma história linear: sem escolhas morais, respostas ao Architect, medidor de relação ou finais alternativos. Interações opcionais servem para escolher qual evidência inspecionar, nunca para mudar o cânone.
- Evitar uma pergunta em cada slide. Só interagir quando houver ação visível: abrir arquivo, destacar prova, registrar hipótese ou acessar uma pista.
- Slide **ANTES**: contexto, conflito, evidência inicial e missão; não antecipar exploit. **DESAFIO**: contrato, estado, terminal, erros e pistas incrementais. **DEPOIS**: consequência visual, reação de personagem, prova adquirida e gancho seguinte. Relatório técnico separado.
- Nenhum número fixo de slides por Case: inventário Scene 0–9 é função narrativa, não quantidade de telas. Começar pelas imagens e componentes existentes, usar overlays e alterações de estado antes de criar novos banners.
- Evidência pública não vira segredo por conveniência: a identidade de Elias é telemetria de operador, não wallet destinatária dos 2,4 milhões; destino financeiro institucional verificável no ledger; documento sensível de Elias e snapshot de Sector 13 são arquivos externos.
- Pistas essenciais devem ser recuperáveis no Evidence Locker. Não exigir que o jogador memorize hexadecimal ou refaça Cases concluídos.
- Os bosses sintetizam conhecimentos já introduzidos. Antes da vitória, não mostrar nomes de bugs ou a solução.

# Matriz de melhorias — os 13 momentos da campanha

| Momento | Oportunidade de maior valor | Mudança mínima recomendada | Aceite no playtest / QA | Prioridade |
| --- | --- | --- | --- | --- |
| 00 — The Impossible Theft | Começar pelo fato impossível, não por exposição de mundo | Balance 2,4M → 0; evidências contraditórias; fala Mara × Breaker; mesmo Vault no Case 01 | Jogador explica o mistério e por que inspecionará Access Gate | P1 |
| 01 — No Forced Entry | Hacking precisa alterar o ambiente | Transação aceita → porta abre sem alarme → símbolo I → operador morto na telemetria (não recebedor do saldo) | Verifier confirma GateOpen sem owner auth; sem segundo saque de fundos | P0 |
| 02 — The Dead Man's Wallet | Impersonação deve causar desconforto | Separar wallet, identity registry e arquivo off-chain; mostrar controle indevido e revogação explícita após obter W17 | Admin muda por reinit; arquivo externo só libera quando auth válida; cleanup deixa log | P0 |
| 03 — Warehouse 17 | Primeiro custo humano concreto | Mostrar contestação de equipamento e prova documental de Mara; guardar Ghost Key com hash e custódia temporária | Transferência sem consentimento do antigo owner demonstrada; custódia não legitima furto | P0 |
| 04 — The Forgotten Floor | Pausa de assombro e engenharia forense | Elevador 23 → 24 e momento de silêncio; restaurar Persistent com TTL; não simular leitura mágica de entry arquivada | Restore ocorre antes da leitura; TTL adequado; Temporary irrecuperável | P1 |
| Boss — The Custodian | Ensinar fronteira de confiança entre contratos | Mostrar mapa Identity → Authority Registry → Core sem indicar erro; progressão dos estados e pausa em WELCOME BACK | Core pode ser correto; claim de controlador incorreto permite entry; jogador explica por quê | P0 |
| 05 — The Missing Investigator | Voss deve parecer investigador falível | Mostrar hipótese refutada e histórico com timestamps; gravação curta e marcante | Falha Decoder / sucesso Archive são verificáveis; jogador recorda frase central | P1 |
| 06 — The Impossible Account | Evitar charada numérica gratuita | Exploit de cast assinado→unsigned aciona reconstrução de tabela legada ENERGY ROUTING → Sector 13 | Valor sentinela e origem da rota verificáveis; sem “13/13/13” como senha mística | P0 |
| 07 — Sector 13 | Principal virada de paranoia | Custo do rebuild visível; fallback do indexador externo; PLAYER ACTIVE aparece; Breaker para inserções depois da prova | DoS e política fallback reproduzíveis; uma única consequência canônica; Registry não é segredo on-chain | P0 |
| 08 — The Oracle | Distinção entre previsão e vigilância | 3 previsões verificáveis no Prophecy Engine; classificador é módulo distinto e só depois revela Architect | Previsão antes de cada execução; player identifica sistemas diferentes | P1 |
| 09 — Steal the Key | Transformar a perda de autorização em tensão | Revogação formal; canal privado de Mara por uma hora diegética; manutenção legítima desviada com consequência para equipe | Payload autorizado/executado comparados; sem temporizador que ramifique a história | P0 |
| 10 — Rewrite | Demonstrar falha de validação de uma prova | Exibir Decoder REJECTED → VossProof ACCEPTED; manifesto de diagnóstico sem privilégio admin; canal de Mara expira antes do boss | Testar validação incorreta e caso negativo no secure mirror; conferir texto com runtime | P0 |
| Final — The Architect | Evitar payoff sem prova e mecânica obsoleta | Arquivos W17/F24/S13 com rodapé recorrente, prova contextual pública da instância, DiagnoseCore→OpenForensicSession após timelock e dossiê de Voss | Verificador independente, prova real de autoria, vínculo Gate→Recovery→Escrow e resultado QUALIFIED/PROVISIONAL | P0 |

# Priorização por esforço e dependências

## P0 — antes de aprovar integração no runtime (roteiro v1.4 já está locked)

- [x] Sincronização documental v1.4: corrigidas as fichas W17/F24/S13, Rewrite e Architect, incluindo identidade ≠ destino financeiro, tabela energética ≠ mensagem numérica, Case 07 sem branches e limites de armazenamento off-chain/on-chain. A execução do jogo permanece não verificada.

- Garantir uma prova player-facing por transição. Toda pista para o Case seguinte deve ter origem, evento e momento de entrega documentados.
- Fazer smoke tests de estado inicial, exploit, negative test, versão corrigida e reset/replay determinístico para cada contrato.
- Validar Custodian e Architect como composição sem vulnerabilidade nova nem hints que entreguem o caminho.

## P1 — maior impacto sem reconstruir frontend

- Emparelhar output do terminal com consequência visual: porta, identidade, ownership, andar restaurado, Registry, Oracle, diferença Decoder→VossProof e operação timelocked DiagnoseCore→OpenForensicSession. Não exigir troca de Wasm ou hash de executable.
- Melhorar texto de erros e falhas sem revelar o exploit (ex.: STATE UNCHANGED, CONTROLLER MISMATCH, ARCHIVE FAIL vs DECODER FAIL).
- Consolidar falas curtas de Mara em vez de transformá-la em narradora de logs; dar a ela contribuições documentais reais em Warehouse e Custodian.
- Implementar ou avaliar painel expansível **Breach Report** após vitória: What did the system believe? / Why wrong? / Failed invariant / Exploit / Fix / Real-world reference. Não inserir esse conteúdo em slides.

## P2 — após teste de uso

- Perguntas ocasionais de hipótese/qual evidência examinar, somente se seleção provocar ação real. Não usar escolhas morais falsas.
- Novas artes, gravações ou animações apenas onde um estado não puder ser comunicado com assets existentes.
- Progress recap / Evidence Locker para facilitar retorno após pausas; não oferecer respostas prontas.

# Critério de acabamento — slides e narrativa

Cada Case precisa de quatro unidades observáveis, mesmo quando reunidas em poucas telas:

1. **Motivo**: por que o Breaker inspeciona este contrato agora?
2. **Ação**: qual operação objetiva do jogador provoca o resultado?
3. **Consequência**: o que mudou no mundo, no estado e/ou na relação com Mara?
4. **Gancho**: que evidência concreta obriga a próxima investigação?

Um único quadro pode exercer mais de uma função. Não converter automaticamente Scene 0–9 em dez slides. O prólogo é apresentação, não challenge. O Case 1 pode funcionar com um slide antes do desafio e três depois *como hipótese de edição*, não decisão sobre o site até inspecionar implementação real.

# Contrato de feedback do BREAKER OS

| Situação | Feedback ao jogador | Anti-padrão |
| --- | --- | --- |
| Consulta | Valor, origem, ledger/version e próximo elemento inspecionável | Mostrar só “OK” |
| Falha normal | Motivo legível ou estado antes/depois, sem nome do bug | “FAILED” genérico em toda tentativa |
| Exploit | Verificação independente + mudança de estado + reação física/digital | Narrativa avançar sem prova técnica |
| Evidência | ID estável, origem/custódia, horário e ligação com próximo Case | Pista que aparece sem causa |
| Pós-vitória | Debrief opcional, patch seguro e referência | Explicação da vulnerabilidade nos slides |

# Validação técnica mínima

- Contratos: fixar versão Soroban/SDK; testar auth, archival restore/TTL, try\_invoke, cast i128 negativo→u128, limites de recurso, RNG, validação incorreta Decoder→VossProof, proof contextual pública e timelock com payload desviado e execução única. Não aplicar semânticas EVM incompatíveis; upgrades de Wasm NÃO fazem parte da sequência vigente.
- Narrativa não inventa storage privado on-chain. O serviço externo que entrega arquivos precisa ter seu modelo de acesso explícito.
- Previsões do Oracle registradas **antes** dos respectivos resultados.
- Case 09 não transforma uma autorização legítima de manutenção em autoridade moral irrestrita.
- Case 10: o Decoder rejeita a prova e a camada seguinte aceita VossProof indevidamente; não afirmar troca de Wasm/hash de executable na implementação vigente.
- Final: a revisão técnica do Voss Protocol de 2026-11-02 informa níveis 11/12 implementados em testnet, ainda sem inspeção independente de código/deploy nesta auditoria; prova contextual deriva de dados públicos da instância, o manifesto não é chave mestra e a vitória requer sessão forense/validador independente, não upgrade de Core.
- Testes não devem movimentar ativos reais; usar fixtures isoladas e verificadores independentes da interface.

# Playtest recomendado

Começar com prólogo + Case 01 + Case 02, depois sequência até Custodian, depois bloco 05–08 e por fim Spire/Architect. Misturar participantes com e sem experiência prévia em Soroban. Registrar por jogador: conclusão sem hint, número de hints, tentativas, tempo por fase, onde travou, se compreendeu a pista seguinte e o que acredita ter acontecido. Analisar os erros mais comuns antes de adicionar novos diálogos ou desafios.

Perguntas de saída:

- Por que o Case seguinte existe?
- O que mudou por causa do exploit, além de “ganhei”?
- Mara descobriu algo que o contrato sozinho não mostrava?
- Qual pista aponta para Voss, para vigilância do player e para o Architect?
- O jogador diferencia capacidade técnica, legitimidade e dano?
- No final, compreendeu por que Voss não podia gastar os fundos e por que ainda assim causou custos?

# Controle real de implementação — preencher após inspeção do site

**Não verificado:** quantidade atual de slides, estado dos contratos, existência do Breach Report, comportamento do terminal, deploy, verificador e testes. Documentação não equivale a implementação. Para cada Case, registrar futuramente links para repo/PR, captura ou gravação, test run, versão SDK, status de arte e responsável. Não marcar como implementado sem evidência reproduzível.

# Referências vigentes e histórico

**Para trabalho atual:** [BREAKER — Season 1 | FINAL NARRATIVE v1.4 — NARRATIVE LOCK](../narrative/breaker-season-1-final-narrative-v1-4-narrative-lock.md) (roteiro S1 v1.4) e [VOSS PROTOCOL — Níveis 11/12 | Especificação vigente](../cases/voss-protocol-niveis-11-12-especificacao-vigente.md) (Voss Protocol, estado técnico declarado, ainda a conferir no código). **As referências históricas listadas abaixo ficam como pesquisa, não como fonte de copy vigente.**

- [00 — História Canônica do Act I](../../shared/00-historia-canonica-do-act-i.md)
- [ARQUIVO — 11 Sala de Roteiro S1 (revisão v2)](../archive/arquivo-11-sala-de-roteiro-s1-revisao-v2.md)
- [ARQUIVO — 12 Matriz de Revelações (revisão antiga)](../archive/arquivo-12-matriz-de-revelacoes-revisao-antiga.md)
- [ARQUIVO — 01 Roteiro de Gameplay (versão antiga)](../archive/arquivo-01-roteiro-de-gameplay-versao-antiga.md)
- [ARQUIVO — 14 Ideias de Interatividade e Ritmo](../archive/arquivo-14-ideias-de-interatividade-e-ritmo.md)

# Controle de implementação — quadro operacional Season 1

**ATENÇÃO:** o quadro abaixo distingue **material editorial existente** de **software verificado**. Sem acesso confirmado ao repositório privado nem execução dos testes, **não foi possível auditar frontend, quantidade de slides, contratos, deploys ou verificadores**. “Não verificado” NÃO significa “não implementado”. Nenhuma etapa deve ser marcada como pronta sem evidência.

## Legenda e Definition of Done

- **Roteiro:** canônico e especificado / proposta editorial preparada / revisão no site pendente.
- **Frontend:** não verificado até existir link para código + gravação/captura do estado.
- **Contrato:** não verificado até fixture compilada na versão SDK definida, com estado reproduzível.
- **Verifier:** não verificado até testar vitória válida e casos negativos independentemente da UI.
- **QA:** pendente até teste de fluxo completo com reset e, preferencialmente, playtest.
- **Prioridade P0:** impede declarar o Case pronto; **P1:** refinamento de apresentação e legibilidade; **P2:** polimento opcional.

## Inventário inicial — sem falsos status de conclusão

| Fase e link para o Case | Roteiro | Slides no site | Contrato/fixture | Verifier e QA | Próxima comprovação |
| --- | --- | --- | --- | --- | --- |
| [00 — Prólogo](https://app.notion.com/p/4009c563042581ff8cebd44408321b54) | Especificado + copy proposta | Não verificado | Não se aplica: sem exploit | Fluxo não verificado | Gravação da passagem ao Case 01 |
| [01 — No Forced Entry](https://app.notion.com/p/4009c563042581e0b720d685c5eb837c) | Especificado + copy proposta | Não verificado | Não verificado | Não verificado | Testar open sem owner auth, Gate e transição |
| [02 — Dead Man](https://app.notion.com/p/4009c5630425816d96c0f22627a7f6ae) | Especificado + copy proposta | Não verificado | Não verificado | Não verificado | Reinit, arquivo externo, cleanup e pista W17 |
| [03 — Warehouse 17](https://app.notion.com/p/4009c5630425813cb1f3e2515b9de879) | Especificado + copy proposta | Não verificado | Não verificado | Não verificado | Auth subject, Ghost Key, custódia, share W17 |
| [04 — Forgotten Floor](https://app.notion.com/p/4009c5630425815084b7dd82afc14074) | Especificado + copy proposta | Não verificado | Não verificado | Não verificado | Restore Persistent + extensão TTL + F24 |
| [BOSS — Custodian](https://app.notion.com/p/4009c56304258198b58cd159962b9387) | Especificado + copy proposta | Não verificado | Não verificado | Não verificado | Dependências e verificador de identidade |
| [05 — Missing Investigator](https://app.notion.com/p/4009c56304258170813ff50ebbd55c16) | Especificado + copy proposta | Não verificado | Não verificado | Não verificado | Erro Decoder aceito como sucesso no Archive |
| [06 — Impossible Account](https://app.notion.com/p/4009c563042581f1b02ec78e46a3bba0) | Especificado + copy proposta | Não verificado | Não verificado | Não verificado | Cast negativo e tabela legada Sector 13 |
| [07 — Sector 13](https://app.notion.com/p/4009c56304258134a525e38dc0eba08b) | Especificado + copy proposta | Não verificado | Não verificado | Não verificado | Limite resource, fallback externo, S13 |
| [08 — Oracle](https://app.notion.com/p/4009c563042581208f71f4f69bf03d72) | Especificado + copy proposta | Não verificado | Não verificado | Não verificado | 3 previsões pré-registradas e classificador distinto |
| [09 — Steal the Key](https://app.notion.com/p/4009c56304258178a3f5d8e6b6190770) | Especificado + copy proposta | Não verificado | Não verificado | Não verificado | Payload original ≠ executado; receipt Mara |
| [10 — Rewrite](https://app.notion.com/p/4009c5630425815395a8cbd0b9a7b536) | Especificado + copy proposta | Não verificado | Não verificado | Não verificado | Falha Decoder→VossProof aceita; canal Mara encerrado |
| [FINAL — Architect](https://app.notion.com/p/4009c5630425815581b2df01797d5365) | Especificado + copy proposta; Voss Protocol aprovado | Não verificado | Voss Protocol **descrito como implementado em testnet** na revisão de 2026-11-02; código, deploy e resultados permanecem não verificados aqui | Não verificado | Arquivos históricos, prova contextual pública, manifesto, DiagnoseCore→OpenForensicSession, verificador independente e autoria Voss |

## Registro de evidência mínimo para preencher quando houver acesso ao código

| Campo do registro | Valor esperado |
| --- | --- |
| Case / responsável | Identificador e pessoa designada (a definir) |
| Link do repositório / branch / commit | URL e hash do commit efetivamente testado |
| SDK, runtime e rede | Versão exata; ambiente local/testnet com fixtures isoladas |
| Slides | Quantidade existente por Case + referência dos arquivos/componentes do site |
| Contrato | Arquivo, entrypoints e setup/reset determinístico |
| Teste positivo | Nome do teste e resultado de exploit válido |
| Testes negativos | Falha de caller não autorizado; exploit bloqueado por secure mirror; falsos sucessos rejeitados |
| Verifier | Prova de que não depende do frontend, só do estado/eventos previstos |
| Evidência narrativa | ID da pista, entrega, persistência e gancho para próximo Case |
| Captura/Playtest | Link para gravação curta e observações de dificuldade |
| Resultado | NÃO VERIFICADO / EM VALIDAÇÃO / VALIDADO / BLOQUEADO |

## Fila imediata sugerida de execução

1. **P0 — Mapear site existente:** identificar quantidade real de slides e componentes do prólogo, Cases 01–02 e transição pós-breach. Registrar, não recriar.
2. **P0 — Vertical slice:** executar Prologue → Case 01 → Case 02, incluindo exploit e persistência de evidência. Validar continuidade sem entregar solução nos slides.
3. **P0 — First Four + Custodian:** testar a composição e a curva de dificuldade antes de avançar.
4. **P0 — Cases 05–08:** validar Soroban cross-call, arithmetic, resource exhaustion, e diferenciação Oracle/Classificador.
5. **P0 — Cases 09–10 + Architect:** conferir autorização timelocked, diferença entre intenção aprovada e payload executado, Decoder REJECTED→VossProof ACCEPTED, derivação pública contextual por instância, assinatura do manifesto, verificador independente, prova histórica de Voss e destino/política do Escrow. **Não exigir alteração de Wasm/version/hash de executable.**
6. **P1 — polimento:** sincronizar logs, reação visual e diálogos; reduzir cenas que explicam o que o terminal já mostrou.
7. **P2 — extras:** feedback de hipóteses e perguntas selecionáveis apenas quando provocarem ação real sem branching.

## Gate de liberação por Case

- [ ] Fonte do contrato, estado inicial e versão runtime identificados.
- [ ] Uma operação tecnicamente reproduzível cumpre a condição de vitória.
- [ ] Uma tentativa normal não vence; secure mirror bloqueia a exploração.
- [ ] Verifier independente da interface confirma a vitória e rejeita falsos positivos.
- [ ] Reset/replay é determinístico, sem movimentação de ativos reais.
- [ ] Slide antes do hack não revela o nome do bug, e o Breach Report aparece somente depois.
- [ ] Mudança de estado tem feedback legível; evidência adquirida é persistida.
- [ ] Jogador entende por que a descoberta conduz ao próximo Caso.
- [ ] Revisão visual do banner 8:3 no desktop e no mobile.
- [ ] Revisão de narrativa sem escolhas morais, resultado único e continuity gate atendido.

## Documentos de referência

- [ARQUIVO — 01 Roteiro de Gameplay (versão antiga)](../archive/arquivo-01-roteiro-de-gameplay-versao-antiga.md)
- [ARQUIVO — 12 Matriz de Revelações (revisão antiga)](../archive/arquivo-12-matriz-de-revelacoes-revisao-antiga.md)
- [VOSS PROTOCOL — Níveis 11/12 | Especificação vigente](../cases/voss-protocol-niveis-11-12-especificacao-vigente.md)

# QA de continuidade pós-seleção — Meridian

- [ ] Case 05 mostra os três relatórios arquivados de Voss com data anterior ao Vault, sem inocentá-lo.
- [ ] Case 08 registra hipótese observacional **errada** sobre insistir na pressão do Archive de Sector 13; o Breaker canônico havia parado após a prova.
- [ ] Case 09: Mara recebe aviso de responsabilidade, assina receipt identificável após encerramento e preserva cadeia de custódia; epílogo usa o mesmo ID/hash.
- [ ] Architect reconstrói deploy chronology que antecede Sequence, Escrow institucional e custos humanos, sem declarar Voss herói.
- [ ] Nenhuma dessas mudanças adicionou exploit, opção moral ou número obrigatório de slides. Testes de integração continuam não verificados.

## Auditoria documental v1.4 — conclusão de sincronização

**Revisão realizada:** 3 de novembro de 2026. Estas marcas se referem ao texto e à hierarquia do Notion, não a commits ou deploy.

- [x] Case 03 — W17 registra proveniência e rodapé histórico; sem `share_a` armazenada.
- [x] Case 04 — F24 recupera Persistent/TTL; arquivo histórico sem `share_b`.
- [x] Case 07 — S13 é snapshot de indexador externo; arquivo sem `share_c`; Registry e timestamps permanecem como payoff.
- [x] Case 10 — falha Decoder REJECTED → VossProof ACCEPTED documentada, sem upgrade de Wasm.
- [x] Final Boss — prova contextual pública, timelock DiagnoseCore→OpenForensicSession, verificador independente e autoria de Voss por evidências autenticadas.
- [x] Voss Protocol — seção vigente diferenciada de rascunhos SHARE A/B/C e UpgradeCore, agora marcados HISTÓRICO.
- [x] Documento de QA — requisitos genéricos de upgrade retirados da execução vigente.
- [x] Roteiro v1.4 — preservado com 51 unidades narrativas únicas; Book I continua adaptação literária revisada.
- [ ] **Runtime:** inspecionar fonte/ABI/commit/deploy do Rewrite/Architect e recibos da rede; a revisão técnica relata níveis 11/12 na testnet, ainda sem confirmação independente nesta auditoria.
- [ ] **Prova de Voss (P0):** aplicar [P0 — Prova de autoria de Voss | Dossiê auditável do Vault](p0-prova-de-autoria-de-voss-dossie-auditavel-do-vault.md) — comprovar ator da invocação (não apenas fee-payer), emissor/registro institucional e cadeia de custódia, estado real do Gate consumido pelo Controller, transação Vault→Escrow e política de saque. Exigir G0–G6 e testes N01–N15; nenhuma evidência técnica foi auditada nesta revisão.
- [ ] **UX:** confrontar a copy com telas reais, Evidence Locker, leitura em mobile, acessibilidade e persistência.
- [ ] **Playtest:** compreensão independente do caso do Vault, da recusa de Voss e da consequência para Mara.

**Critério de fechamento desta tarefa:** documentação ativa sincronizada. **Critério de lançamento:** ainda bloqueado até haver evidência de implementação e QA; `ATTRIBUTION VERIFIED: AREN VOSS` deve permanecer bloqueado sem os sete gates do [P0 — Prova de autoria de Voss | Dossiê auditável do Vault](p0-prova-de-autoria-de-voss-dossie-auditavel-do-vault.md).

## Auditoria global da Season 1 — 2026-11-03

**Escopo verificado no Notion:** página inicial da Season 1; roteiro canônico v1.4; Prólogo, Cases 01–10 e dois Bosses; Book I; índice técnico; documento vigente do Voss Protocol; plano de QA; Arquivo Editorial; Plano X e seus 36 itens; e referências transversais do Act I (História Canônica, Continuidade de Personagens, arco de Mara, matriz mestra de vulnerabilidades, produção e métodos). Os cinco movimentos textuais de storyboard permanecem arquivados no Plano de Produção, sem arquivos de slides ativos.

## Correções de conteúdo e organização efetivamente aplicadas

- [x] **Fonte única:** v1.4 continua sendo o único roteiro. Confirmar 51 unidades de texto com IDs únicos; nenhuma fase ou desfecho adicional.
- [x] **Personagens:** Prólogo, arco de Mara e Continuidade de Personagens não confundem operação executada com autorização legítima. O relógio é diegético e Mara assume o recibo após revogação.
- [x] **Investigação inicial:** Case 01 removeu a antiga pista não canônica do símbolo “I” e distingue metadado Elias Var, argumento owner, signatário histórico e exploração de teste.
- [x] **Voss:** Case 05 documenta três avisos anteriores ao Vault, hipótese refutada no Sector 13, nota de escalada e registro institucional assinado da conta operacional. A prova final exige envelope, vínculo temporal e causalidade GateOpen→RecoveryController; não apenas relatos.
- [x] **Conceitos técnicos:** Case 06 distingue cast negativo i128→u128 da tabela histórica de proveniência energética; não produz mensagem mágica nem real apagão.
- [x] **Arquivos antigos:** Warehouse 17, Forgotten Floor 24 e Sector 13 apresentam referências históricas com rodapé recorrente, não shares secretas de 32 bytes coletadas nos Cases.
- [x] **Rewrite / Architect:** fichas player-facing e matriz mestra usam Decoder REJECTED→VossProof ACCEPTED, prova contextual pública e DiagnoseCore→OpenForensicSession após timelock. Sem upgrade ou novo Wasm.
- [x] **Histórico deslocado:** o Voss Protocol anterior (\~20 mil caracteres) foi copiado integralmente para [91 — Histórico do Voss Protocol | Shares e UpgradeCore (não vigente)](../archive/91-historico-do-voss-protocol-shares-e-upgradecore-nao-vigente.md) e retirado do documento técnico vigente; rascunhos editoriais recebem prefixo ARQUIVO.
- [x] **Divulgação:** revisada a fila com 36 publicações, sem itens publicados; post 23 substituído por autorização vinculada à intenção, sem sugerir um exploit de upgrade que não existe nesta Season.
- [x] **Livro:** Book I mantém os 12 capítulos, prólogo, epílogo e pós-créditos como adaptação da v1.4; não serve como especificação de contrato.
- [x] **Organização:** página de entrada aponta para roteiro, índice técnico, protocolo vigente, QA, livro, comunicação e arquivo sem competir com o cânone.

## Pendências reais — NÃO marcar como concluídas por causa do Notion

- [ ] Validar commits, versões, ABI, testes e deploys informados para os níveis 11 e 12.
- [ ] Construir/verificar o histórico assinado que vincula Voss à operação original e à recuperação do Vault; executar testes negativos de assinatura, validade, fee-payer, relayer e vínculo GateOpen/RecoveryController.
- [ ] Validar state archival/TTL, cross-call error, cast i128→u128, saturação de recursos, RNG, timelock e secure mirrors no ambiente real.
- [ ] Verificar a existência dos 51 momentos na interface, persistência de Evidence Locker, acessibilidade, comportamento responsivo e ausência de spoilers prematuros.
- [ ] Realizar playtest cego de causalidade, pistas, custos da investigação e entendimento do desfecho.
- [ ] Publicar no X somente quando os materiais e o lançamento forem confirmados; textos prontos no Notion não são posts publicados.

**Conclusão desta auditoria:** as contradições encontradas nas páginas operacionais foram corrigidas. O roteiro mantém 51 IDs únicos; a fila de divulgação contém 36 posts, nenhum marcado como publicado. **Limite de readback:** o Notion reconheceu a página 10 — Rewrite na busca e havia confirmado suas edições anteriores, porém a leitura direta de sua versão final retornou `validation_error` nesta rodada. Repetir a leitura/conferência quando o conector permitir; não tratar esse erro como prova de defeito no conteúdo. **Isso não comprova que toda linha de cada arquivo histórico ou contrato externo esteja correta.** O histórico antigo permanece arquivado deliberadamente, não como documentação vigente. Reabrir o roteiro só se prova técnica ou teste revelar uma divergência concreta.

[P0 — Prova de autoria de Voss \| Dossiê auditável do Vault](p0-prova-de-autoria-de-voss-dossie-auditavel-do-vault.md)
