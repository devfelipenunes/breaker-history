---
notion_id: 4009c563-0425-81c0-bef5-ee03630b1bbb
source: https://app.notion.com/p/4009c563042581c0bef5ee03630b1bbb?pvs=204
title: "🎬 ARQUIVO — 01 Roteiro de Gameplay (versão antiga)"
exported_at: 2026-11-07
---

**ARQUIVO — ROTEIRO DE GAMEPLAY HISTÓRICO.** Preserva estudos de cenas e terminal, mas não é a versão atual. Em qualquer divergência entre diálogos, ordem, exploit narrativo ou final, prevalece [BREAKER — Season 1 | FINAL NARRATIVE v1.4 — NARRATIVE LOCK](../narrative/breaker-season-1-final-narrative-v1-4-narrative-lock.md) (v1.4). Não utilizar este documento antigo como brief de implementação.

**Formato de apresentação definido:** o jogador seleciona um level no site, acompanha slides que contam a história e então resolve o desafio técnico. Depois da vitória verificada, novos slides mostram a consequência, a descoberta e o gancho seguinte. O terminal é o espaço do exploit, não o lugar obrigatório para apresentar diálogos ou desenvolver personagens.

# Princípio central

Cada level articula **três blocos separados**:

1. **ANTES — slides de entrada:** situação, conflito ou pergunta dramática, pista concreta e missão em linguagem narrativa.
2. **DESAFIO — contrato:** o jogador examina e explora o contrato existente; não inserir novas condições de vitória, escolhas de diálogo ou interrupções dramáticas obrigatórias.
3. **DEPOIS — slides de consequência:** reação do cenário e dos personagens, evidência obtida, custo quando houver e gancho para o level seguinte.

A narrativa é apresentada principalmente pelos slides, e o exploit permanece a ação técnica que habilita a sequência seguinte. **Nenhuma revisão de história deve modificar o contrato, o objetivo verificável ou a ordem dos Cases.**

# O que o jogador vê vs. o que o designer sabe

| Camada | Player-facing | Somente design/dev |
| Objetivo | Ação narrativa concreta | Condição técnica de vitória |
| Contrato | Código, ABI, estado, logs | Nome da vulnerabilidade |
| Hints | Pistas progressivas | Exploit esperado |
| Resultado | O mundo reage | Verifier confirma estado |
| Debrief | Conceito técnico depois de vencer | Fix completo e referências |

Antes da vitória, **não mostrar** “Missing Authorization”, “Unchecked Arithmetic”, “Predictable Randomness”, a correção ou qualquer texto que entregue a resposta.

# Como a história aparece para o jogador

**Canal principal: slides narrativos antes e depois do level.** Cada sequência deve funcionar como uma pequena cena visual: uma mudança clara, pouquíssimas linhas por quadro e uma última imagem ou frase que crie expectativa. Os demais objetos abaixo podem complementar o contexto, mas não substituem os slides nem obrigam a redesenhar o challenge:

- **Cinematic / environment art:** estabelece onde o jogador está.
- **Mission strip:** uma frase curta dizendo o que precisa acontecer.
- **NPC transmission:** no máximo 1–3 linhas por intervenção.
- **Evidence:** logs, identidades, contract IDs, registros, imagens e pequenos documentos.
- **Breaker Terminal:** respostas do sistema também contam história.
- **State changes:** porta abrindo, identidade mudando, arquivo aparecendo, luzes apagando.
- **Audio / recording:** usado em momentos importantes, especialmente Voss.
- **Post-breach debrief:** só aqui o jogo nomeia a vulnerabilidade e explica a correção.
- **Story Item:** a recompensa narrativa causa a próxima missão.

# Regra de ritmo para os slides

**Variar a emoção, não a vulnerabilidade.** Warehouse 17 pede fricção humana; Forgotten Floor, silêncio; Custodian, inquietação; Sector 13, paranoia; Oracle, reconhecimento; Steal the Key, sacrifício institucional de Mara; Rewrite, vertigem; Architect, retrospectiva e confronto.

Cada sequência deve ter uma função dramática identificável, sem número rígido de telas ou duração artificial. Nos slides de entrada: mostrar o lugar, formular uma pergunta e indicar por que o contrato importa. Nos slides posteriores: mostrar o resultado, dar espaço a uma reação silenciosa quando for melhor que uma fala, revelar a pista e terminar no próximo mistério.

Preservar o debrief técnico depois da vitória, separado da cena. Evitar explicar a vulnerabilidade antes do jogador resolvê-la. **Não exigir diálogos no terminal, timers narrativos, ramificações ou novas interações para executar esta revisão.**

# Estado da interface

## Contrato de realidade Soroban — separação de dados

O jogo distingue explicitamente **contract state publicamente inspecionável**, **dados cifrados ou referências opacas no ledger** e **arquivos de operação protegidos fora da cadeia**.

- Case 02: o exploit é `initialize(player)`, que altera admin on-chain; um arquivo externo autentica o player e, confiando incorretamente no admin comprometido, libera Warehouse 17. Não alegar segredo para um plaintext em `env.storage()`.
- Case 04: `Persistent` expirado restaura via footprint/lista de restauração da transação (normalmente simulada), antes da execução; `Temporary` expira definitivamente. A UI que diz "not found" é índice off-chain desatualizado, não retorno de contrato lendo arquivo arquivado.
- Case 07: o exploit é unbounded iteration / resource exhaustion em contrato; o indexador externo vê o rebuild falhar e seleciona seu snapshot de contingência superexposto. Não usar storage on-chain secreto, não depender de evento emitido por execução que falhou.
- Os contratos de challenge são reproduzidos em runtime/testes controlados. Evidências narrativas externas podem ser simuladas em serviços de jogo sem alterar a falha real e sua verificação técnica.

Referência: [Stellar Docs — Contract Data Access](https://developers.stellar.org/docs/build/smart-contracts/getting-started/storing-data) e [State Archival](https://developers.stellar.org/docs/learn/fundamentals/contract-development/storage/state-archival).

## 1. DISCOVER

O level abre no mundo.

Exibir:

- arte do local;
- título do Case;
- 2–3 frases de situação;
- diálogo essencial;
- objetivo;
- botão **BREACH CONTRACT**.

Não exibir ainda:

- solução;
- vulnerabilidade;
- fix;
- relatório técnico.

## 2. BREACH

A interface entra no Breaker OS.

Exibir:

- Source;
- Breaker Terminal;
- contexto `$PLAYER`, `$TARGET`, `$NETWORK`;
- Evidence acessível por drawer;
- Hint opcional;
- objetivo em uma linha.

A história continua através de:

- outputs do terminal;
- mudanças no estado;
- novos Evidence;
- mensagens curtas de Mara/Voss/System.

## 3. RESOLVE

Quando o verifier confirma a vitória:

- confirmar a condição técnica de vitória e registrar o estado verificável;
- mostrar primeiro a reação física/digital do ambiente;
- apresentar nos slides posteriores a consequência, a descoberta e o gancho seguinte, sem explicar o fix;
- persistir a evidência encontrada no Evidence Locker e registrar achievement/story item;
- disponibilizar um **BREACH REPORT** técnico **opcional e expansível**, fora dos slides, com nome da vulnerabilidade, invariant violado, exploit e correção;
- desbloquear o próximo Case após a consequência narrativa; a leitura do relatório não é condição para avançar.

# Estrutura de roteiro por level — adaptar à apresentação em slides

A lista de Scene 0–9 abaixo é um inventário de funções narrativas, **não** dez telas obrigatórias nem dez momentos interativos. Na produção do site, agrupar Arrival + Inciting Evidence + Mission nos slides de entrada; manter Active Investigation + Breach no desafio técnico tal como implementado; agrupar World Reaction + Discovery + Transition nos slides após a vitória. Reactive Beats no terminal são opcionais, não condicionantes do enredo. Debrief permanece separado. Esse mapeamento não altera as regras de nenhum level.

## Conflito dramático obrigatório

Para cada Case, produzir uma ficha com: **Desejo do Breaker / resistência do mundo ou de Mara / hipótese inicial equivocada / ação do player / reversão observável / custo / evidência que provoca o Case seguinte**. "Vulnerabilidade encontrada" não é, sozinha, uma reversão dramática.

Três funções devem coexistir sem se confundirem: **evidence** revela algo que pode ser provado, **vulnerability** explica por que uma execução é insegura, e **moral consequence** mostra o impacto da ação. Não abrir a fase seguinte sem a pista necessária; não nomear o bug antes do debrief.

Cada página individual deverá ter uma seção **Roteiro in-game** com:

## Scene 0 — Arrival

Onde estamos? O que mudou desde a fase anterior?

## Scene 1 — Inciting Evidence

Qual evidência concreta justifica abrir aquele contrato?

## Scene 2 — Mission

Qual frase aparece para o jogador?

## Scene 3 — Active Investigation

O que está acessível no Source, Terminal e Evidence?

## Scene 4 — Reactive Beats

Quais eventos podem aparecer durante a investigação sem entregar o exploit?

## Scene 5 — Breach

O que o jogador faz narrativamente quando satisfaz o verifier?

## Scene 6 — World Reaction

O que muda visualmente/sonoramente no mundo?

## Scene 7 — Discovery

Qual pista ou Story Item é revelado?

## Scene 8 — Debrief

Qual conceito técnico é finalmente nomeado?

## Scene 9 — Transition

Por que o personagem vai imediatamente para a próxima fase?

---

# Exemplo completo — Prologue → Case 01

## PROLOGUE — THE IMPOSSIBLE THEFT

### Scene 0 — Meridian

A homepage apresenta Meridian funcionando normalmente.

Contratos controlam:

- transporte;
- identidade;
- propriedade;
- energia;
- mercados.

Texto mínimo:

> **Tudo é governado por um Contrato.**

Transição para o Vault.

### Scene 1 — Crime Scene

A arte do Vault aparece.

Overlay:

**VAULT BALANCE**
**2,400,000 → 0**

Evidence desbloqueado:

- Door: intact
- Admin access: none
- Key compromise: none
- Transaction: accepted

Uma única manchete opcional surge no feed do Vault: **2,4 MILHÕES MOVIMENTADOS — NENHUMA INVASÃO DETECTADA** — *Sera Quill, Network Wire*. Essa é a mesma aparição descrita no roteiro do prólogo, não uma segunda notícia.

Mara Vale entra por áudio/transmission:

> **O sistema aceitou a transação. Isso significa que alguém estava autorizado.**

O Breaker:

> **Não. Significa que o contrato acreditou que alguém estava autorizado.**

### Scene 2 — Handoff

Mara libera acesso ao Access Gate Contract.

O jogador recebe:

- `$TARGET`;
- owner conhecido;
- transaction snapshot;
- contract source.

Objetivo:

> **Descubra como entraram sem possuir a chave.**

Botão:

**OPEN CASE 01**

---

# CASE 01 — NO FORCED ENTRY

## Scene 0 — Arrival

O jogador permanece no mesmo Vault.

Isso é importante: **não parece um novo tutorial**. É a continuação direta da cena anterior.

A porta interna ainda está fechada.

Mara:

> **A segurança física não encontrou nada. Se quiser contestar o relatório, comece pelo contrato de acesso.**

## Scene 1 — Mission

Breaker OS abre.

Mission strip:

> **ENTRE NO VAULT SEM POSSUIR A CHAVE.**

Nada sobre auth.

## Scene 2 — Active Investigation

Runtime:

`$PLAYER = player address`
`$TARGET = Access Gate`
`$OWNER = victim`

Source mostra a função vulnerável.

Terminal permite:

`contract functions $TARGET`

`contract call owner`

`stellar contract invoke ...`

Evidence contém apenas:

- owner address;
- door id;
- last successful call;
- ausência de assinatura do owner na operação original.

## Scene 3 — Reactive Beats

Se o jogador apenas consultar owner:

> **SYSTEM: Proprietário registrado identificado.**

Se tentar uma operação comum que não abre a porta:

> **STATE UNCHANGED.**

Se abrir Evidence:

Mara pode dizer:

> **Já verificamos o endereço. Ele pertence ao proprietário.**

Essa frase é proposital: ela reforça o erro conceitual de Meridian sem dizer a solução.

## Scene 4 — Breach

O jogador invoca a função de abertura usando a identidade declarada do owner sem possuir sua autorização.

Verifier confirma.

## Scene 5 — World Reaction

O terminal responde:

**TRANSACTION ACCEPTED**
**DOOR STATE → OPEN**

Nenhum alarme.

A arte do Vault muda: a porta interna começa a abrir.

Somente depois aparece:

**NO FORCED ENTRY DETECTED**

A mensagem é importante: para o sistema, nada foi violado.

## Scene 6 — Discovery

Dentro da porta existe uma pequena marca digital:

**I**

Adicionar Evidence:

**Unknown Marker — I**

Mara:

> **Isso não faz parte da especificação do Vault.**

O Breaker encontra nos registros da operação uma identidade antiga.

Status:

**OWNER: DECEASED**

## Scene 7 — Breach Report (fora dos slides)

Depois de mostrar a abertura da porta e a descoberta da identidade, o jogador pode expandir o relatório técnico:

**VULNERABILITY DISCOVERED — MISSING AUTHORIZATION**

> O contrato recebeu um Address, mas nunca exigiu que esse Address autorizasse a chamada.

O relatório demonstra `require_auth()`, o invariant e a correção. Não interromper os slides para ensinar o fix nem exigir leitura do relatório para avançar.

## Scene 8 — Transition

Tela de Case Complete:

**CASE 01 CLOSED**
**NEW LEAD: DECEASED IDENTITY**

Última linha:

> **Um identificador de operador pertencente a um homem morto consta na rota de serviço do Vault.**

Unlock:

**CASE 02 — THE DEAD MAN'S WALLET**

# Regra para os próximos levels

## Progressão linear — estados narrativos canônicos

O jogo oferece **uma história só**. Não criar menus de decisão moral, diálogo ramificado, flags de relacionamento ou finais alternativos. O jogador investiga e executa os exploits; ao concluir a condição objetiva de cada desafio, a história avança por cenas fixas.

- **Case 02:** após extrair Warehouse 17, o Breaker executa revogação explícita da autoridade assumida sobre Elias, sem apagar a prova da exploração.
- **Case 03:** depois do exploit, ele registra o hash, a transferência e o protocolo de custódia da Ghost Key. O owner registrado continua irregularmente em nome do Breaker; o artefato acompanha a investigação.
- **Case 07:** após obter o snapshot, ele para de inserir registros e limita a carga adicional do Archive. O DoS já ocorreu; o dano não é negado.
- **Floor 24 / Oracle / Spire:** Mara reage aos acontecimentos acima com diálogos fixos. Sua confiança muda no decorrer da narrativa, não através de medidor calculado ou escolhas do jogador.
- **Architect:** o Breaker Profile é um histórico de fatos fixos. A pergunta "Por que você continuou?" permanece sem respostas selecionáveis. O desfecho é sempre QUALIFIED / PROVISIONAL.
- **Escrow:** é legítimo o jogador descobrir o destino por leitura de ledger antes do final; isso não cria branch narrativa. O clímax acrescenta autoria, spend policy, motivo e custo humano, iguais para todos.

Toda passagem entre Cases deve exigir apenas a solução verificável do desafio técnico, não um input narrativo. As cenas posteriores ao exploit acontecem automaticamente.

## Checklists de QA narrativo

- Pistas essenciais possuem fontes independentes; nenhuma fala de Mara deve revelar um exploit que o jogador precisa descobrir.
- O ledger financeiro prova Escrow institucional, não custódia pela wallet morta. O destino é público; não criar falsa inacessibilidade no ledger para preservar a revelação. A prova final combina autoria, escrow, spend policy e consequência. O jogador pode deduzir o Escrow cedo examinando o ledger; o roteiro final permanece único e não se adapta a uma flag de descoberta.
- Mara resolve ao menos uma lacuna institucional que o código não pode resolver.
- Reentrada clássica não volta para o Case 05: Soroban trata cross-call error handling.
- O Oracle não confunde RNG com classificador comportamental.
- O fallback de Sector 13 tem política de acesso explicada.
- O Breaker Profile reúne somente os três acontecimentos fixos; a UI não oferece escolhas morais.
- Final: QUALIFIED/PROVISIONAL, nunca ACCEPTED.

Consulta: [ARQUIVO — 12 Matriz de Revelações (revisão antiga)](arquivo-12-matriz-de-revelacoes-revisao-antiga.md).

Cada próximo Case deve começar pela consequência material do anterior.

Não:

> “O nível 2 ensina inicialização.”

E sim:

> “A identidade usada no roubo pertence a um homem morto. Descubra como ela voltou a existir.”

A vulnerabilidade é a mecânica. **A investigação é o motivo para usá-la.**

# Edição de slides — Season 1 \| roteiro de apresentação v1

**Uso:** texto editorial proposto para os slides do site, sem substituir o cânone nem alterar o challenge. Cada cartão abaixo é um **beat de apresentação**, não uma tela obrigatória: podem ser agrupados quando a arte e o layout já resolverem a cena. A quantidade real de slides, seu mapeamento nos componentes do frontend e a adequação mobile ainda precisam ser conferidos no repositório.

## Regras de corte e montagem

- Abertura: normalmente 1–2 beats curtos de situação/contradição e uma missão legível. O jogador deve chegar logo ao contrato.
- Pós-breach: normalmente 1–2 beats de consequência e gancho; dar silêncio aos grandes reveals (Custodian, Sector 13, Architect). Nunca inserir explicação técnica de vulnerabilidade nos slides.
- Preservar as artes 8:3 existentes. Usar texto de interface, troca de status, foco/crop e overlays antes de solicitar novas imagens.
- Máximo recomendado de 1 fala curta por personagem a cada beat; nenhum diálogo deve ler em voz alta tudo que o terminal acabou de mostrar.
- Exibir **BREACH REPORT** como painel/arquivo opcional após a vitória; não como parte do roteiro de slides.
- Os trechos abaixo são **proposta editorial de texto player-facing** e precisam de revisão final contra o espaço real dos componentes. Não criar interações ou choices que alterem o resultado.

## 00 — Prologue \| The Impossible Theft

**Entrada A — Meridian:** “Em Meridian, o código governa portas, identidades e dinheiro.” Imagem monumental da cidade; corte para o Vault.

**Entrada B — incidente:** `VAULT BALANCE: 2,400,000 → 0` / `DOOR: INTACT` / `TRANSACTION: ACCEPTED`.

Mara: “O sistema aceitou a transação. Alguém devia estar autorizado.”Breaker: “Ele só acreditou que estava.”

**Transição:** `AUDITOR ACCESS: LIMITED`. “Descubra como entraram sem possuir a chave.” O próximo Case continua no mesmo Vault.

## 01 — No Forced Entry

**Antes:** A porta de serviço está intacta, e a Authority encerrou a inspeção física.

Mara: “Se o relatório está errado, encontre o erro no acesso.”Missão: **ENTRE NO VAULT SEM POSSUIR A CHAVE.**

**Depois do verifier:** `TRANSACTION ACCEPTED` → `DOOR: OPEN` → `NO FORCED ENTRY DETECTED`. A porta abre sem alarme.

**Descoberta:** marca **I** no ambiente; telemetria mostra um **operator record** de Elias Var, falecido. **Não** descrevê-lo como destinatário dos fundos.

Mara: “Esse identificador foi encerrado há seis meses.”Gancho: `NEW LEAD: DECEASED OPERATOR RECORD`.

## 02 — The Dead Man's Wallet

**Antes:** Arquivo civil: `ELIAS VAR — DECEASED`. Registro técnico: `LEGACY CONTROLLER — ACTIVE`. São sistemas diferentes.

Mara: “A pessoa morreu. O registro ainda responde.”Missão: **TORNE-SE ALGUÉM QUE NÃO DEVERIA MAIS EXISTIR.**

**Depois:** `IDENTITY CONTROLLER UPDATED`. O arquivo legado **fora da cadeia** permite consultar uma referência de manutenção.

**Descoberta:** `WAREHOUSE 17 / LOWER MERIDIAN / DO NOT USE CITY ROUTING`. Após obter o registro, a narrativa confirma `CONTROLLER RELEASED` como ato canônico, sem opção moral.

Breaker: “Uma identidade morta apontando para um lugar que não existe.”Gancho: `NEW LEAD: WAREHOUSE 17`.

## 03 — Warehouse 17

**Antes:** Centenas de objetos desviados parecem possuir transferências válidas. Uma contestação real obtida por Mara revela dano a um proprietário de outro equipamento.

Mara: “O sistema chama isso de transferência. O dono anterior chama de perda.”Missão: **RECUPERE O OBJETO LIGADO AO VAULT.**

**Depois:** `TRANSFER ACCEPTED`. O item passa a constar em nome do Breaker, sem a assinatura do titular anterior.

**Descoberta:** dentro do item, **GHOST KEY**. A chave aponta para `FLOOR 24` e contém o vestígio documental `W17 / DIAGNOSTIC TRACE` no Evidence Locker, sem revelar seu uso futuro. Breaker registra a cadeia de custódia; isso não legitima o furto.

Mara: “Esse prédio só tem vinte e três andares.”Gancho: `NEW LEAD: FLOOR 24`.

## 04 — The Forgotten Floor

**Antes:** Painel: `01–23`. O registro físico não traz demolição, mas o índice moderno não encontra o andar.

Missão: **FAÇA O SISTEMA LEMBRAR O ANDAR ESQUECIDO.**

**Depois:** o jogador recupera uma entrada `Persistent` arquivada pelo fluxo correto e estende o TTL. O índice volta a reconhecer o destino. O elevador revela **24**. Usar pausa visual, não explicação longa.

**Descoberta:** `I / FIRST LAYER`; artefato `F24 / ARCHIVED ENTRY` fica no Evidence Locker. A Ghost Key revela uma rota de infraestrutura, não abre portas universalmente.

**Último beat:** `CUSTODIAN ONLINE` / `IDENTITY UNKNOWN`.

## BOSS I — The Custodian

**Antes:** Sistema monumental; sem barra de HP ou nome de bug. O jogador enxerga a cadeia `LEGACY IDENTITY → AUTHORITY REGISTRY → CUSTODIAN CORE`.

Mara: “O Core parece cumprir todas as próprias regras.”Missão: **FAÇA O CUSTODIAN ACREDITAR QUE VOCÊ É UM OPERADOR.**

**Durante:** o feedback pode evoluir entre `IDENTITY UNKNOWN`, `CONTROLLER MISMATCH` e `CONTROLLER RECOGNIZED`; não revelar a solução.

**Depois:** `OPERATOR RECOGNIZED`. Pausa. **WELCOME BACK.**

Mara: “De volta?”Gancho: porta aberta; terminal antigo `AREN VOSS — MISSING`.

## 05 — The Missing Investigator

**Antes:** Workspace de Voss contém logs, tentativa de recuperação e uma hipótese antiga riscada/corrigida. Seus acessos são anteriores ao incidente do Vault.

Mara: “Ele chegou até aqui antes de nós.”Missão: **RECUPERE A MENSAGEM INCOMPLETA DE VOSS.**

**Depois:** `DECODER: FAILED` coexistindo com `ARCHIVE: RECOVERED`. O fragmento é disponibilizado.

Voss (gravação): “Eles não estão causando os erros.”Voss: “Estão esperando para ver quem os encontra.”

**Gancho:** uma anotação de Voss aponta para `IMPOSSIBLE ACCOUNT`. Não torná-lo onisciente.

## 06 — The Impossible Account

**Antes:** Um módulo antigo de créditos energéticos contém um saldo fora do domínio econômico esperado.

Mara: “Esse valor não poderia ter sido produzido por uma operação válida.”Missão: **REPRODUZA O SALDO IMPOSSÍVEL.**

**Depois:** o estado anômalo força o módulo legado a reconstruir sua tabela de origem, com resposta `ENERGY ROUTING TABLE / GRID NODE: 13`.

**Descoberta:** `ARCHIVE DESTINATION: SECTOR 13` / `STATUS: UNMAPPED`. **Não** usar “13/13/13” como senha escondida no saldo.

Breaker: “Mais um lugar que Meridian diz não existir.”Gancho: Sector 13.

## 07 — Sector 13

**Antes:** Instalação de arquivo em saturação. Registro de recuperação menciona `RECOVERY MODE: LEGACY` e acesso ampliado ao snapshot.

Voss (instrução preservada): “Quebre o Archive.”Missão: **PROVE A FALHA DO ARCHIVE E ENCONTRE O QUE O FALLBACK EXPÕE.**

**Depois:** a operação de rebuild falha; um **indexador externo** ativa snapshot de contingência excessivamente permissivo. O Breaker interrompe inserções adicionais após a prova. Não criar dados privados on-chain.

**Revelação:** `BREAKER REGISTRY` / `AREN VOSS: REFUSED` / `████: ACCEPTED` / `PLAYER: ACTIVE`. Pausa longa e timestamp recente.

Mara: “Essa entrada foi criada depois que a investigação começou.”Gancho: `ORACLE`. Preservar `S13 / RECOVERY SNAPSHOT` no Evidence Locker.

## 08 — The Oracle

**Antes:** Sistema reputado como preditivo; o player agora sabe que alguém o observa.

Mara: “Ele sabe que você chegou.”Missão: **PREVEJA O ORACLE ANTES QUE ELE PREVEJA VOCÊ.**

**Durante:** três previsões registradas antes de cada resultado.

**Depois:** `PROPHECY ENGINE: FAILED` (saída previsível); um **módulo distinto** informa `SUBJECT CLASSIFIER: OBSERVING`.

**Revelação:** `ARCHITECT / THE SPIRE`. O Oracle não vê o futuro; o classificador observa comportamento.Gancho: instalações da Spire continuam em uso.

## 09 — Steal the Key

**Antes:** `CASE TERMINATED` / `BREAKER ACCESS: REVOKED`. Mara abre um canal privado, limitado e auditável pelo recibo que decide assinar.

Mara: “Uma hora. Saia com uma prova que exista sem a sua palavra.”Missão: **ROUBE O ACESSO SEM ROUBAR A CHAVE.**

**Depois:** uma operação de manutenção válida foi executada com payload modificado: `EXPECTED: OPEN MAINTENANCE HATCH` / `EXECUTED: GRANT SPIRE ACCESS`. Uma equipe fica sem a abertura prevista; não inventar acidente.

Mara: “Eles ainda esperam o hatch. Registre isso também.”Gancho: `UPGRADE CONTROL`. O relógio é diegético, não fail state.

## 10 — Rewrite

**Antes:** O Breaker já não é auditor autorizado. O console da Spire pode substituir executables.

Mara: “Isso não é uma porta. É a regra que governa as portas.”Missão: **MUDE A LEI.**

**Depois:** `CONTRACT ADDRESS: UNCHANGED` / `EXECUTABLE HASH: CHANGED` / `VERSION: 1 → 2`. Cliente externo continua confiando no mesmo endereço, agora com outra implementação.

**Fechamento:** o canal privado de Mara expira **antes** do Architect. Sem resposta adicional dela no boss. Uma mensagem chega de outra origem: **ENCONTRE-ME.**

## FINAL BOSS — The Architect

**Antes:** O sistema não anuncia bugs; exibe `HISTORICAL DIAGNOSTIC: 3 REFERENCES UNRESOLVED`. O jogador recupera `W17`, `F24`, `S13` do Evidence Locker para o Voss Protocol, sem refazer os Cases.

**Durante:** verificar EvidenceGate e manifesto assinado por Voss; explorar Decoder/Archive, timelock e upgrade já aprendidos. O manifesto **não** é autorização de administrador. Mostrar progresso por módulos sem entregar a sequência completa.

**Depois:** `ARCHITECT CORE: REPLACED`. Mesmo assim, outra origem fala: `SOURCE: SEQUENCE OBSERVER`. O Observer independente verifica as provas e concede `QUALIFIED / PROVISIONAL`.

Architect: “Você demorou mais que Voss.”Breaker: “Onde ele está?”Architect: “Chegou até aqui. E recusou.”

**Recontextualização:** comparar cronologias verificáveis: vulnerabilidades pré-existentes, Sequence formada depois; Voss já havia chegado ao Architect antes de provocar o incidente do Vault. `VAULT → RECOVERY CONTROLLER → MERIDIAN RECOVERY ESCROW`. A política de saque prova que Voss não controlava a retirada; a quarentena ainda causou custos.

**Confronto:** o Breaker Profile mostra atos e consequências que o jogador já viveu, inclusive o recibo de Mara. O Architect pergunta: “Por que você continuou?” **Sem resposta selecionável**.

**Último beat:** `SEQUENCE 01 COMPLETE` / `SUBJECT QUALIFIED` / `STATUS PROVISIONAL` / `LAYER II ACCESS GRANTED`. “Existem outros.” Pós-crédito: transmissão em Lumen com identidade da figura oculta.

## Gate de revisão editorial

- [ ] Cada beat é compatível com a arte já aprovada e com a área disponível no site.
- [ ] Nenhuma fala entrega o nome do exploit antes do hack.
- [ ] O conteúdo técnico de correção permanece no Breach Report.
- [ ] Cada pós-breach entrega uma evidência que fundamenta o Case seguinte.
- [ ] Respeita-se um único arco e um único desfecho; as perguntas de investigação são opcionais e têm efeito visual real.
- [ ] Revisar os textos contra os Cases canônicos antes de integrá-los no frontend.

# Ajuste de beats — decisões aprovadas de Meridian

- **Case 05 / Voss:** inserir um único beat de observação com três protocolos de alerta arquivados, antes da gravação. Após a fala, mostrar um registro simples de interrupções em Lower Meridian sem revelar a motivação completa.
- **Case 08 / Oracle:** após explorar o RNG previsível, exibir `SUBJECT CLASSIFIER / EXPECTED ≠ OBSERVED / MODEL UPDATED`. A falha de previsão é do classificador, não da aleatoriedade.
- **Case 09 / Mara:** antes do recibo, mostrar `CASE CLOSED / SIGNER MARA / CUSTODY LIABILITY`. Mara confirma sem discurso; debrief da evidência, não da pena futura.
- **Architect:** encaixar o payoff documental dos alertas e a data anterior da Sequence no momento em que revela o motivo do incidente. Exibir dano a serviços de Lower Meridian antes da conclusão moral.
- **Epílogo:** a suspensão de Mara cita o mesmo identificador e hash do recibo institucional. Não introduzir cena adicional com a Authority espionando a conversa.

**Restrição:** beats são propostas de montagem; não ampliar quantidade de slides sem inventário do frontend.

# Montagem v3 — ajustes dramáticos obrigatórios por fase

**Estado:** copy e direção aprovadas para roteiro; quantidade real de slides e implementação não verificadas. Usar beats em cenas existentes sempre que possível.

- **Prólogo/01:** contraste visual “TRANSACTION ACCEPTED” versus “NO FORCED ENTRY”; motivação do Breaker é verificar o que a Authority chama de legítimo. Uma reação curta, não monólogo.
- **02:** depois do takeover, mostrar que a autoridade do morto mudou de fato; executar cleanup verificável. Breve hesitação antes do registro de revogação, sem escolha moral.
- **03:** após a Ghost Key, inserir prova civil de Mara (contestação de titularidade). Breaker: “O contrato mostra quem recebeu. Não mostra de quem era.” Mara: “Agora temos as duas provas.” Sem afirmar titularidade resolvida.
- **04/Custodian:** preservar silêncio após restauração e “WELCOME BACK”; não afirmar que o jogador já esteve no local.
- **05:** mostrar IDs e datas dos três alertas arquivados antes da gravação de Voss; exibir hipótese corrigida e custo real em Lower Meridian. Mara exige confirmação independente.
- **06:** o saldo anômalo abre tabela legada de roteamento energético. Enfatizar que há infraestrutura real dependente do módulo; não usar número como código e não inventar dano específico.
- **07:** após PLAYER: ACTIVE, pausar animação/áudio, destacar timestamp posterior ao início da investigação, só então Mara: “Criaram essa entrada depois que começamos.” Mostrar interrupção da pressão adicional como fato fixo.
- **08:** três previsões do RNG pré-registradas; separar do SUBJECT CLASSIFIER / EXPECTED ≠ OBSERVED / MODEL UPDATED. A Authority formaliza restrição de escopo ao fim do Case; sem nova subtrama.
- **09:** exibir trilha administrativa das advertências e CASE TERMINATED / ACCESS REVOKED antes do canal de Mara. Recibo assinado somente após aviso claro de responsabilidade; mostrar manutenção não executada sem inventar acidente.
- **10:** endereço igual e hash novo, clientes dependentes; silêncio curto após a troca. Canal de Mara encerra antes do boss.
- **Architect:** (A) provas interativas de cronologia e Escrow; (B) reconstrução do incidente e custos; (C) Profile confronta atos fixos e recibo de Mara; (D) QUALIFIED / PROVISIONAL e Layer II; (E) suspensão de Mara com mesmo hash; (F) teaser Lumen. Não explicar tudo em um discurso, não oferecer resposta à pergunta moral.

**Teste de edição:** cada beat precisa funcionar com diálogo mínimo, reação visual ou evidência consultável; não revelar o bug antes do exploit; não adicionar slides sem inventário do frontend.
