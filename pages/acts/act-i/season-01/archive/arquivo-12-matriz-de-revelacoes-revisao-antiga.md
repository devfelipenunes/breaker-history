---
notion_id: 4019c563-0425-8136-a005-f8e2a2e3641d
source: https://app.notion.com/p/4019c56304258136a005f8e2a2e3641d?pvs=204
title: "🧩 ARQUIVO — 12 Matriz de Revelações (revisão antiga)"
exported_at: 2026-11-07
---

**MATRIZ DE REFERÊNCIA / HISTÓRICO — Season 1.** Documento de trabalho para roteiristas, quest design e UI. Não é segunda fonte narrativa. Para qualquer decisão atual da Season 1 prevalece [BREAKER — Season 1 | FINAL NARRATIVE v1.4 — NARRATIVE LOCK](../narrative/breaker-season-1-final-narrative-v1-4-narrative-lock.md) (v1.4 NARRATIVE LOCK). A História Canônica do Act I e Series Arc & Hidden Canon servem para continuidade da saga onde não conflitam. Este documento não deve ser exibido ao jogador; tabelas e antigas alternativas sem atualização são arquivo histórico.

# Contrato de mistério

**Política de roteiro:** a Season 1 possui um único caminho dramático e um único final, independentemente de como o jogador investiga tecnicamente os contratos. Todas as pistas essenciais convergem para os mesmos fatos. Não criar opções de diálogo, escolhas de conduta, finais alternativos, medidor de confiança de Mara ou variações na resposta do Architect. `BREAKER PROFILE` é um histórico dos atos canônicos, não um sistema de branches.

- **Pergunta central:** quem provocou a movimentação dos 2.400.000 e o que pretendia?
- **Resposta factual:** Voss acionou a rota institucional de recuperação usando a falha de acesso, transferindo a custódia ao **Meridian Recovery Escrow**; Voss não obteve poder de gasto.
- **Complexidade moral:** indisponibilidade temporária dos recursos gerou consequências; não confundir intenção de alerta com ausência de dano.
- **Quem construiu o quê:** Meridian acumulou falhas; Architect mapeou/encadeou uma Sequence; Voss a atravessou, recusou e deixou evidências.
- **O que NÃO declarar automaticamente em diálogos:** Voss REFUSED antes de Sector 13; interpretação consolidada de que Voss não pode gastar e provocou uma mensagem antes do Architect; identidade da figura no pós-crédito. **O destino Escrow é um fato consultável no ledger público**, portanto não fingir que é criptograficamente secreto. O mistério final é a atribuição, as políticas de gasto e a intenção, não esconder artificialmente uma transação pública.
- **O que sempre fica visível:** o jogador vê as evidências tecnicamente reproduzíveis, sem que personagens entreguem o nome da vulnerabilidade antes da vitória.

# Escada de revelações

| Momento | Hipótese do jogador | Verdade oculta | Primeira pista | Payoff |
| Prólogo | Roubo sem invasão | Voss provocou recuperação institucional | Trilha autorizada e saldo zero | Architect / Escrow |
| Case 01 | Chave foi roubada | Auth declarada, não provada | Access Gate aceita caller indevido | Door open + identidade legada |
| Case 02 | Wallet do morto roubou fundos | Identidade legada referenciada, não custodiante | Registro de operador desativado | Warehouse 17 |
| Case 03 | Depósito criminoso isolado | Propriedade institucional pode ser ilegitimamente transferida | Contestação de equipamento | Ghost Key + conflito com Mara |
| Case 04 | Andar removido | Estado arquivado e infraestrutura esquecida | Referência antiga de Floor 24 | First Layer |
| Custodian | Core precisa ter seu próprio bug | Confia em identidade/registry comprometidos | Gate correto, dependências frágeis | Welcome back |
| Case 05 | Voss é ladrão em fuga | Investigou o mesmo padrão antes do roubo | Terminal e timestamps | Gravação de Voss |
| Case 06 | Número sem sentido | Limite numérico expõe referência a infraestrutura | Saldo impossível | Sector 13 |
| Case 07 | Segue Voss sem ser percebido | Também está sendo catalogado | Fallback + timestamp recém-criado | Registry ACTIVE / Voss REFUSED |
| Case 08 | Oracle prevê futuro | Prophecy Engine previsível; Subject Classifier distinto | Ledger sequence público | Architect / Spire |
| Case 09 | Uma assinatura é inviolável | Payload e autorização desacoplados | Timelock pendente | Acesso irregular à Spire, hatch de manutenção não aberto e recibo de Mara |
| Case 10 | Contrato é lei imutável | Decoder rejeita prova; Archive registra VossProof como aceita | Manifesto histórico + prova contextual da instância | Erro de validação demonstrado; canal de Mara expira; Find me |
| Architect | Architect plantou todas as falhas | Montou seleção sobre defeitos preexistentes | Datas independentes de deploy | Cronologias independentes + Voss REFUSED + prova do Escrow |
| Epílogo | Problema encerrado | Capacidade não equivale a legitimidade | Profile e suspensão de Mara | QUALIFIED / PROVISIONAL |

# Três pistas para cada conclusão que não pode falhar

## Destino dos 2.400.000

1. Event trail pública: `SERVICE_GATE_OPEN → RECOVERY_ROUTED → ESCROW_CREDITED`. Jogadores experientes podem seguir os hashes e descobrir o destino antes do final; isso é investigação recompensada, não quebra de roteiro. A UI padrão do prólogo mostra apenas resumo e pistas iniciais, mas nunca bloqueia leitura pública do ledger.
2. Escrow Contract ID, saldo/commitment e política de gasto associada ao processo institucional, sem autoridade de Voss.
3. Protocolo de quarentena e atraso de liberação registrado por Mara. A leitura humana confirma custo; não prova culpa sozinha.

## Voss antecedeu a Sequence atual

1. Timestamp de acessos ao terminal abandonado anteriores ao incidente do Vault.
2. Log da primeira avaliação de Voss no Registry.
3. Operação histórica agendada por Voss, que o jogador encontra no Architect.

## O jogador está sendo observado

1. Registro `PLAYER — ACTIVE` criado após o início da investigação.
2. Evento de classificação separado de Prophecy Engine no Oracle.
3. Atualização `SUBJECT PATH CONFIRMED` da própria Sequence.

## O Architect não construiu as falhas

1. Contratos legados implantados antes de a Sequence existir.
2. Relatórios de manutenção que registram erros antes das primeiras classificações.
3. Timeline de descoberta do Architect e acesso de Voss posterior às vulnerabilidades.

# Preparação vs payoff

**VOSS PROTOCOL — descrição vigente conforme roteiro v1.4:** W17, F24 e S13 são arquivos históricos com rodapé recorrente, NÃO contêm shares secretas da instância final. Cada share de 32 bytes é derivada do contexto público da instância (rede, contrato, carteira, manifesto e índice); a composição XOR é validada por commitment. A assinatura Ed25519 confirma a origem do manifesto de diagnóstico, sem conceder privilégios. O desafio de Rewrite explora a validação indevida Decoder→VossProof, e o Architect abre uma sessão forense desviando DiagnoseCore no timelock. Não ocorre upgrade/substituição de Wasm do Core. **Hash não decodifica texto e assinatura não equivale a autorização.** O verificador independente continua separado. Referência: [VOSS PROTOCOL — Níveis 11/12 | Especificação vigente](../cases/voss-protocol-niveis-11-12-especificacao-vigente.md).

- O símbolo **I** é índice inicial; não transformá-lo em explicação mística.
- **Ghost Key** deve dar acesso a referências de storage, não abrir magicamente qualquer porta.
- **WELCOME BACK** é surpresa de identidade, não prova de que Breaker já esteve fisicamente na First Layer.
- **Voss REFUSED** entra em Sector 13, mas o motivo específico fica para depois.
- **ACCEPTED mascarado** entra no Registry e pode reaparecer em Lumen, sem identificação na Season 1.
- **Sera Quill** surge uma única vez por assinatura de notícia no Vault, sem interação direta.
- **Mara SUSPENDED** é payoff da assinatura voluntária após a revogação; seu canal de uma hora se encerra em Rewrite, não no Architect.
- **MANUTENÇÃO DA SPIRE** é a consequência concreta do timelock reescrito: assinatura válida, hatch esperado não abre, equipe precisa reagendar; não inventar vítimas ou pane sistêmica.
- **REWRITE — FALSE PROOF / NEW INTENT** exige demonstrar Decoder REJECTED → VossProof ACCEPTED no Case 10 e DiagnoseCore → OpenForensicSession(player) no Architect. A tese “confiança não equivale a legitimidade” permanece, mas a demonstração vigente NÃO depende de alteração de executable, endereço ou versão Wasm.
- **DUAS CRONOLOGIAS** (deployments de falhas anteriores versus construção posterior da Sequence) e cadeia Vault–Escrow são demonstradas por eventos/contratos, não pelo monólogo do Architect.
- **VERIFICADOR / OBSERVER INDEPENDENTE** aparece somente após a sessão forense ser aberta; atesta o resultado técnico fora da autoridade do contrato vulnerável e emite QUALIFIED / PROVISIONAL. Não afirmar que ArchitectCore foi substituído nem que o retorno `reveal()` concede classificação moral.
- **LAYER II** não é prêmio moral; é acesso provisório após teste técnico.

# Regras de fair play investigativo

**Separação técnica obrigatória:** tudo que estiver em contract storage Soroban é observável no ledger. Documentos de Elias, o snapshot privado do Registry e os formulários humanos de Mara residem no arquivo/indexador externo, não numa suposta caixa-preta on-chain. A autorização pode controlar a **API externa que os entrega**; no Case 02 essa API confia indevidamente no controlador comprometido on-chain. No Case 07, o indexador externo reage à falha de rebuild e revela sua própria cópia de contingência. O reconhecimento de mensagens não depende de eventos de transações revertidas. Não esconder a transação pública do Escrow para forçar a surpresa.

O Case 04 demonstra arquivamento restaurável de `Persistent` via footprint transacional; não confundir `Temporary` excluído nem fazer a lógica do contrato ler dado arquivado antes da restauração.

- Não esconder informação necessária atrás de texto não acessível; o player pode investigar fontes por ordem variável. A Three Clue Rule é redundância para **dedução e avanço**, não obrigação de três cutscenes ou três marcadores na UI. Cada pista crítica precisa ter localização, ação verificável e inferência possível documentadas no roteiro.
- Não revelar por diálogo o mesmo que o jogador deve deduzir examinando logs e transações.
- Cada revelação de alto impacto exige indício antecipado e confirmação independente.
- Personagens podem interpretar mal provas; dados on-chain e fatos da diegese precisam manter integridade.
- Interpretação do Architect continua **falível**: `QUALIFIED`, `ACCEPTED`, `REFUSED` e `MISSING` são categorias operacionais, não verdades morais.
- A tarefa final deve reusar ao menos três conceitos prévios e revisitar consequências, não introduzir nova mecânica disfarçada.

# Referências

- [The Alexandrian — Three Clue Rule](https://thealexandrian.net/wordpress/1118/roleplaying-games/three-clue-rule)
- [The Alexandrian — Node-based scenario design](https://thealexandrian.net/wordpress/7985/roleplaying-games/node-based-scenario-design-part-3-inverting-the-three-clue-rule)
- [GDC Vault — What Happened Here? Environmental Storytelling](https://www.gdcvault.com/play/1012696/What-Happened-Here-Environmental)
- [ARQUIVO — 11 Sala de Roteiro S1 (revisão v2)](arquivo-11-sala-de-roteiro-s1-revisao-v2.md)

# Matriz operacional de pistas — Season 1 \| entrega, armazenamento e payoff

**Complemento à matriz canônica:** tabela de produção para roteiristas, frontend e QA. Mantém acontecimentos e ordem existentes. **Não revelar ao jogador** colunas de payoff/spoiler. Evidência essencial deve surgir por evento verificável, ficar recuperável e justificar a próxima investigação. Não esconder fatos públicos do ledger para salvar a surpresa.

| Origem | Evidência adquirida / local | O que o jogador pode concluir naquele momento | Uso imediato | Payoff e restrição |
| --- | --- | --- | --- | --- |
| Prólogo | Vault intacto, saldo 2,4M → 0, operação aceita; eventos públicos | Execução aceita não prova legitimidade | Inspecionar Access Gate | Escrow institucional é publicamente auditável; autoria e motivo ficam para o final |
| 01 — No Forced Entry | Gate aberto sem assinatura; marca I; operator record Elias Var na telemetria | A porta confia em auth insuficiente; operador morto aparece nos logs | Identity Registry de Elias | Elias NÃO recebeu os 2,4M |
| 02 — Dead Man | Registry reconfigurado; arquivo legado externo libera W17 | Sistema de identidade ainda controla acesso administrativo | Warehouse 17 | Cleanup explícito da impersonação; plaintext não está on-chain |
| 03 — Warehouse 17 | Ghost Key + W17/Diagnostic Trace, contestação de propriedade | Transferência pode ser válida em execução e ilegítima; chave localiza infraestrutura | Floor 24 | share A preservada no Evidence Locker; não explicar puzzle no Case 03 |
| 04 — Forgotten Floor | Entry Persistent restaurada, rota e F24/Archived Entry | A memória operacional da cidade pode expirar e voltar | Custodian | share B e referência First Layer recuperáveis; não restaurar Temporary apagada |
| Custodian | Operador reconhecido + WELCOME BACK; workstation Aren Voss | Core correto confia em autoridade comprometida; alguém passou antes | Recuperar gravação de Voss | WELCOME BACK não prova que o protagonista esteve ali |
| 05 — Missing Investigator | Timestamps antigos, hipótese corrigida, gravação, impossible account | Voss era falível; alguém observava os que encontravam bugs | Módulo de crédito energético | Não revelar ainda motivo da recusa; Voss teve acessos anos antes |
| 06 — Impossible Account | Estado numérico reproduzido → ENERGY ROUTING TABLE / Sector 13 | O saldo denuncia rota esquecida, não senha numerológica | Sector 13 | Mesma infraestrutura antiga; não usar 13/13/13 como código |
| 07 — Sector 13 | Rebuild falha → snapshot do indexador externo com Registry e S13/Recovery Snapshot | PLAYER ACTIVE é registro de observação; Voss REFUSED; há ACCEPTED mascarado | Oracle | share C preservada; snapshot não é segredo escondido em Soroban storage |
| 08 — Oracle | Três previsões + evento de SUBJECT CLASSIFIER; Architect/Spire | Oracle previsível não é o classificador; alguém seleciona Breakers | Spire | Não confundir RNG local com predição de pessoas |
| 09 — Steal the Key | Operação autorizada vs payload executado, receipt de Mara; Spire Access | Mudou-se o significado da autorização; investigação perdeu mandato | Índice de manifesto de diagnóstico | Assinatura após case terminated motiva suspensão de Mara |
| 10 — Rewrite | Manifesto autenticado e Decoder REJECTED / VossProof ACCEPTED | Uma rejeição pode ser tomada como prova válida | Architect / sessão forense | Canal de Mara expira antes do boss |
| Final — Architect | Rodapés de W17/F24/S13, manifesto, proof contextual pública, sessão forense, registro assinado da chave de Voss e cadeia Vault-Escrow | Architect catalogou falhas anteriores; Voss acionou a recuperação sem autoridade de saque pessoal | Conclusão da Sequence e Layer II | Verificador independente concede QUALIFIED / PROVISIONAL, não ACCEPTED; motivo da recusa de Voss fica oculto |

## Regras de implementação de artefatos

- **Evidence Locker:** persistir `evidence_id`, `case_id`, origem (ledger, arquivo externo, documento institucional ou gravação), momento de entrega e estado de obtenção. A origem deve ser visível sem exposição de dados de terceiros.
- **Progresso linear:** conclusão do verifier técnico libera o after-scene canônico, que guarda evidência e desbloqueia o próximo Case; consulta antecipada a uma transação pública não altera o final.
- **W17/F24/S13:** os três identificadores são pistas documentais do Voss Protocol, não uma senha formada pelos números. Cada share contextual tem 32 bytes e é derivada de dados públicos do Final Boss; os arquivos antigos guardam rodapés recorrentes, não bytes das shares. A Evidence Locker preserva referências históricas sem exigir repetir Cases.
- **Fonte pública vs externa:** AccessGate, storage de contratos e eventos são verificáveis publicamente; arquivos pessoais de Elias, registros administrativos de Mara e snapshot privado do indexador em Sector 13 são dados externos com política explícita. Nunca usar auth como alegação de criptografia de storage público.
- **Mara:** sua prova de contestação de propriedade e o arquivo do antigo controller precisam acrescentar algo que o código sozinho não mostra. O recibo assinado no Case 09 deve ser reconhecível no epílogo como causa da suspensão.
- **Profile:** registrar fatos canônicos e custos (controle de Elias liberado, Ghost Key em custódia temporária, pressão adicional interrompida, heist com hatch não aberto, Decoder/VossProof aceito indevidamente, sessão forense aberta, recibo de Mara). Não atribuir score moral nem registrar escolhas inexistentes.

## Perguntas de QA por tipo de revelação

1. **Origem:** o jogador consegue dizer de onde veio a prova e o que exatamente ela comprova?
2. **Justiça:** havia pista suficiente antes da conclusão, sem dicas que revelassem o exploit?
3. **Persistência:** um jogador que pausa e volta consegue consultar a evidência sem reexecutar o contrato?
4. **Continuidade:** a fase seguinte é motivada pela descoberta anterior, e não por seleção arbitrária?
5. **Payoff:** na Spire/Architect o jogador consegue reconhecer e revisitar as evidências anteriores?
6. **Antispoiler:** o UI mostra apenas a informação permitida naquele ponto, mantendo acesso normal ao ledger público?

## Referência de execução

- [ARQUIVO — 01 Roteiro de Gameplay (versão antiga)](arquivo-01-roteiro-de-gameplay-versao-antiga.md)
- [15 — Plano de Melhorias e QA — Season 1](../production/15-plano-de-melhorias-e-qa-season-1.md)
- [VOSS PROTOCOL — Níveis 11/12 | Especificação vigente](../cases/voss-protocol-niveis-11-12-especificacao-vigente.md)
