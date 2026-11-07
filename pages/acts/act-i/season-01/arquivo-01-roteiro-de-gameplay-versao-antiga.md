---
notion_id: 4009c563-0425-81c0-bef5-ee03630b1bbb
source: https://app.notion.com/p/4009c563042581c0bef5ee03630b1bbb?pvs=204
title: "🎬 ARQUIVO — 01 Roteiro de Gameplay (versão antiga)"
exported_at: 2026-11-07
---

Here is the result of "fetch" for the Page with URL https://app.notion.com/p/4009c563042581c0bef5ee03630b1bbb as of 2026-11-03T14:38:46.020Z:
<page url="https://app.notion.com/p/4009c563042581c0bef5ee03630b1bbb" icon="🎬">
<ancestor-path>
<parent-page url="https://app.notion.com/p/40d9c563042581939ffad5f7e19042e3" title="90 — Arquivo Editorial e Estudos | Season 1"/>
<ancestor-2-page url="https://app.notion.com/p/4009c563042581359693d42f09d41062" title="Season 01 — The First Layer"/>
<ancestor-3-page url="https://app.notion.com/p/4019c563042581469a0edc7e30a6eff9" title="ACT I — The World Is Breakable"/>
<ancestor-4-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
<properties>
{"title":"ARQUIVO — 01 Roteiro de Gameplay (versão antiga)"}
</properties>
<iconMetadata>{"type":"emoji","emoji":"🎬"}</iconMetadata>
<content>
<callout icon="🎬" color="yellow_bg">
<b>ARQUIVO — ROTEIRO DE GAMEPLAY HISTÓRICO.</b> Preserva estudos de cenas e terminal, mas não é a versão atual. Em qualquer divergência entre diálogos, ordem, exploit narrativo ou final, prevalece <mention url="https://app.notion.com/p/40d9c563042581bf886cfc339d730fd1" /> (v1.4). Não utilizar este documento antigo como brief de implementação.
</callout>

<callout icon="🎬" color="purple_bg">
<b>Formato de apresentação definido:</b> o jogador seleciona um level no site, acompanha slides que contam a história e então resolve o desafio técnico. Depois da vitória verificada, novos slides mostram a consequência, a descoberta e o gancho seguinte. O terminal é o espaço do exploit, não o lugar obrigatório para apresentar diálogos ou desenvolver personagens.
</callout>

# Princípio central

Cada level articula <b>três blocos separados</b>:

1. <b>ANTES — slides de entrada:</b> situação, conflito ou pergunta dramática, pista concreta e missão em linguagem narrativa.
2. <b>DESAFIO — contrato:</b> o jogador examina e explora o contrato existente; não inserir novas condições de vitória, escolhas de diálogo ou interrupções dramáticas obrigatórias.
3. <b>DEPOIS — slides de consequência:</b> reação do cenário e dos personagens, evidência obtida, custo quando houver e gancho para o level seguinte.

A narrativa é apresentada principalmente pelos slides, e o exploit permanece a ação técnica que habilita a sequência seguinte. <b>Nenhuma revisão de história deve modificar o contrato, o objetivo verificável ou a ordem dos Cases.</b>

# O que o jogador vê vs. o que o designer sabe

<table fit-page-width="true" header-row="true">
<tr>
<td>
Camada
</td>
<td>
Player-facing
</td>
<td>
Somente design/dev
</td>
</tr>
<tr>
<td>
Objetivo
</td>
<td>
Ação narrativa concreta
</td>
<td>
Condição técnica de vitória
</td>
</tr>
<tr>
<td>
Contrato
</td>
<td>
Código, ABI, estado, logs
</td>
<td>
Nome da vulnerabilidade
</td>
</tr>
<tr>
<td>
Hints
</td>
<td>
Pistas progressivas
</td>
<td>
Exploit esperado
</td>
</tr>
<tr>
<td>
Resultado
</td>
<td>
O mundo reage
</td>
<td>
Verifier confirma estado
</td>
</tr>
<tr>
<td>
Debrief
</td>
<td>
Conceito técnico depois de vencer
</td>
<td>
Fix completo e referências
</td>
</tr>
</table>

<callout icon="🚫" color="red_bg">
Antes da vitória, <b>não mostrar</b> “Missing Authorization”, “Unchecked Arithmetic”, “Predictable Randomness”, a correção ou qualquer texto que entregue a resposta.
</callout>

# Como a história aparece para o jogador

<b>Canal principal: slides narrativos antes e depois do level.</b> Cada sequência deve funcionar como uma pequena cena visual: uma mudança clara, pouquíssimas linhas por quadro e uma última imagem ou frase que crie expectativa. Os demais objetos abaixo podem complementar o contexto, mas não substituem os slides nem obrigam a redesenhar o challenge:

- <b>Cinematic / environment art:</b> estabelece onde o jogador está.
- <b>Mission strip:</b> uma frase curta dizendo o que precisa acontecer.
- <b>NPC transmission:</b> no máximo 1–3 linhas por intervenção.
- <b>Evidence:</b> logs, identidades, contract IDs, registros, imagens e pequenos documentos.
- <b>Breaker Terminal:</b> respostas do sistema também contam história.
- <b>State changes:</b> porta abrindo, identidade mudando, arquivo aparecendo, luzes apagando.
- <b>Audio / recording:</b> usado em momentos importantes, especialmente Voss.
- <b>Post-breach debrief:</b> só aqui o jogo nomeia a vulnerabilidade e explica a correção.
- <b>Story Item:</b> a recompensa narrativa causa a próxima missão.

# Regra de ritmo para os slides

<b>Variar a emoção, não a vulnerabilidade.</b> Warehouse 17 pede fricção humana; Forgotten Floor, silêncio; Custodian, inquietação; Sector 13, paranoia; Oracle, reconhecimento; Steal the Key, sacrifício institucional de Mara; Rewrite, vertigem; Architect, retrospectiva e confronto.

Cada sequência deve ter uma função dramática identificável, sem número rígido de telas ou duração artificial. Nos slides de entrada: mostrar o lugar, formular uma pergunta e indicar por que o contrato importa. Nos slides posteriores: mostrar o resultado, dar espaço a uma reação silenciosa quando for melhor que uma fala, revelar a pista e terminar no próximo mistério.

Preservar o debrief técnico depois da vitória, separado da cena. Evitar explicar a vulnerabilidade antes do jogador resolvê-la. <b>Não exigir diálogos no terminal, timers narrativos, ramificações ou novas interações para executar esta revisão.</b>

# Estado da interface

## Contrato de realidade Soroban — separação de dados

O jogo distingue explicitamente <b>contract state publicamente inspecionável</b>, <b>dados cifrados ou referências opacas no ledger</b> e <b>arquivos de operação protegidos fora da cadeia</b>.

- Case 02: o exploit é <code>initialize(player)</code>, que altera admin on-chain; um arquivo externo autentica o player e, confiando incorretamente no admin comprometido, libera Warehouse 17. Não alegar segredo para um plaintext em <code>env.storage()</code>.
- Case 04: <code>Persistent</code> expirado restaura via footprint/lista de restauração da transação (normalmente simulada), antes da execução; <code>Temporary</code> expira definitivamente. A UI que diz "not found" é índice off-chain desatualizado, não retorno de contrato lendo arquivo arquivado.
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
- botão <b>BREACH CONTRACT</b>.

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
- contexto <code>$PLAYER</code>, <code>$TARGET</code>, <code>$NETWORK</code>;
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
- disponibilizar um <b>BREACH REPORT</b> técnico <b>opcional e expansível</b>, fora dos slides, com nome da vulnerabilidade, invariant violado, exploit e correção;
- desbloquear o próximo Case após a consequência narrativa; a leitura do relatório não é condição para avançar.

# Estrutura de roteiro por level — adaptar à apresentação em slides

A lista de Scene 0–9 abaixo é um inventário de funções narrativas, <b>não</b> dez telas obrigatórias nem dez momentos interativos. Na produção do site, agrupar Arrival + Inciting Evidence + Mission nos slides de entrada; manter Active Investigation + Breach no desafio técnico tal como implementado; agrupar World Reaction + Discovery + Transition nos slides após a vitória. Reactive Beats no terminal são opcionais, não condicionantes do enredo. Debrief permanece separado. Esse mapeamento não altera as regras de nenhum level.

## Conflito dramático obrigatório

Para cada Case, produzir uma ficha com: <b>Desejo do Breaker / resistência do mundo ou de Mara / hipótese inicial equivocada / ação do player / reversão observável / custo / evidência que provoca o Case seguinte</b>. "Vulnerabilidade encontrada" não é, sozinha, uma reversão dramática.

Três funções devem coexistir sem se confundirem: <b>evidence</b> revela algo que pode ser provado, <b>vulnerability</b> explica por que uma execução é insegura, e <b>moral consequence</b> mostra o impacto da ação. Não abrir a fase seguinte sem a pista necessária; não nomear o bug antes do debrief.

Cada página individual deverá ter uma seção <b>Roteiro in-game</b> com:

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

> <b>Tudo é governado por um Contrato.</b>

Transição para o Vault.

### Scene 1 — Crime Scene

A arte do Vault aparece.

Overlay:

<b>VAULT BALANCE</b><br /><b>2,400,000 → 0</b>

Evidence desbloqueado:

- Door: intact
- Admin access: none
- Key compromise: none
- Transaction: accepted

Uma única manchete opcional surge no feed do Vault: <b>2,4 MILHÕES MOVIMENTADOS — NENHUMA INVASÃO DETECTADA</b> — <i>Sera Quill, Network Wire</i>. Essa é a mesma aparição descrita no roteiro do prólogo, não uma segunda notícia.

Mara Vale entra por áudio/transmission:

> <b>O sistema aceitou a transação. Isso significa que alguém estava autorizado.</b>

O Breaker:

> <b>Não. Significa que o contrato acreditou que alguém estava autorizado.</b>

### Scene 2 — Handoff

Mara libera acesso ao Access Gate Contract.

O jogador recebe:

- <code>$TARGET</code>;
- owner conhecido;
- transaction snapshot;
- contract source.

Objetivo:

> <b>Descubra como entraram sem possuir a chave.</b>

Botão:

<b>OPEN CASE 01</b>

---

# CASE 01 — NO FORCED ENTRY

## Scene 0 — Arrival

O jogador permanece no mesmo Vault.

Isso é importante: <b>não parece um novo tutorial</b>. É a continuação direta da cena anterior.

A porta interna ainda está fechada.

Mara:

> <b>A segurança física não encontrou nada. Se quiser contestar o relatório, comece pelo contrato de acesso.</b>

## Scene 1 — Mission

Breaker OS abre.

Mission strip:

> <b>ENTRE NO VAULT SEM POSSUIR A CHAVE.</b>

Nada sobre auth.

## Scene 2 — Active Investigation

Runtime:

<code>$PLAYER = player address</code><br /><code>$TARGET = Access Gate</code><br /><code>$OWNER = victim</code>

Source mostra a função vulnerável.

Terminal permite:

<code>contract functions $TARGET</code>

<code>contract call owner</code>

<code>stellar contract invoke ...</code>

Evidence contém apenas:

- owner address;
- door id;
- last successful call;
- ausência de assinatura do owner na operação original.

## Scene 3 — Reactive Beats

Se o jogador apenas consultar owner:

> <b>SYSTEM: Proprietário registrado identificado.</b>

Se tentar uma operação comum que não abre a porta:

> <b>STATE UNCHANGED.</b>

Se abrir Evidence:

Mara pode dizer:

> <b>Já verificamos o endereço. Ele pertence ao proprietário.</b>

Essa frase é proposital: ela reforça o erro conceitual de Meridian sem dizer a solução.

## Scene 4 — Breach

O jogador invoca a função de abertura usando a identidade declarada do owner sem possuir sua autorização.

Verifier confirma.

## Scene 5 — World Reaction

O terminal responde:

<b>TRANSACTION ACCEPTED</b><br /><b>DOOR STATE → OPEN</b>

Nenhum alarme.

A arte do Vault muda: a porta interna começa a abrir.

Somente depois aparece:

<b>NO FORCED ENTRY DETECTED</b>

A mensagem é importante: para o sistema, nada foi violado.

## Scene 6 — Discovery

Dentro da porta existe uma pequena marca digital:

<b>I</b>

Adicionar Evidence:

<b>Unknown Marker — I</b>

Mara:

> <b>Isso não faz parte da especificação do Vault.</b>

O Breaker encontra nos registros da operação uma identidade antiga.

Status:

<b>OWNER: DECEASED</b>

## Scene 7 — Breach Report (fora dos slides)

Depois de mostrar a abertura da porta e a descoberta da identidade, o jogador pode expandir o relatório técnico:

<b>VULNERABILITY DISCOVERED — MISSING AUTHORIZATION</b>

> O contrato recebeu um Address, mas nunca exigiu que esse Address autorizasse a chamada.

O relatório demonstra <code>require_auth()</code>, o invariant e a correção. Não interromper os slides para ensinar o fix nem exigir leitura do relatório para avançar.

## Scene 8 — Transition

Tela de Case Complete:

<b>CASE 01 CLOSED</b><br /><b>NEW LEAD: DECEASED IDENTITY</b>

Última linha:

> <b>Um identificador de operador pertencente a um homem morto consta na rota de serviço do Vault.</b>

Unlock:

<b>CASE 02 — THE DEAD MAN'S WALLET</b>

# Regra para os próximos levels

## Progressão linear — estados narrativos canônicos

O jogo oferece <b>uma história só</b>. Não criar menus de decisão moral, diálogo ramificado, flags de relacionamento ou finais alternativos. O jogador investiga e executa os exploits; ao concluir a condição objetiva de cada desafio, a história avança por cenas fixas.

- <b>Case 02:</b> após extrair Warehouse 17, o Breaker executa revogação explícita da autoridade assumida sobre Elias, sem apagar a prova da exploração.
- <b>Case 03:</b> depois do exploit, ele registra o hash, a transferência e o protocolo de custódia da Ghost Key. O owner registrado continua irregularmente em nome do Breaker; o artefato acompanha a investigação.
- <b>Case 07:</b> após obter o snapshot, ele para de inserir registros e limita a carga adicional do Archive. O DoS já ocorreu; o dano não é negado.
- <b>Floor 24 / Oracle / Spire:</b> Mara reage aos acontecimentos acima com diálogos fixos. Sua confiança muda no decorrer da narrativa, não através de medidor calculado ou escolhas do jogador.
- <b>Architect:</b> o Breaker Profile é um histórico de fatos fixos. A pergunta "Por que você continuou?" permanece sem respostas selecionáveis. O desfecho é sempre QUALIFIED / PROVISIONAL.
- <b>Escrow:</b> é legítimo o jogador descobrir o destino por leitura de ledger antes do final; isso não cria branch narrativa. O clímax acrescenta autoria, spend policy, motivo e custo humano, iguais para todos.

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

Consulta: <mention url="https://app.notion.com/p/4019c56304258136a005f8e2a2e3641d" />.

Cada próximo Case deve começar pela consequência material do anterior.

Não:

> “O nível 2 ensina inicialização.”

E sim:

> “A identidade usada no roubo pertence a um homem morto. Descubra como ela voltou a existir.”

A vulnerabilidade é a mecânica. <b>A investigação é o motivo para usá-la.</b>

# Edição de slides — Season 1 \| roteiro de apresentação v1

<callout icon="🎞️" color="blue_bg">
<b>Uso:</b> texto editorial proposto para os slides do site, sem substituir o cânone nem alterar o challenge. Cada cartão abaixo é um <b>beat de apresentação</b>, não uma tela obrigatória: podem ser agrupados quando a arte e o layout já resolverem a cena. A quantidade real de slides, seu mapeamento nos componentes do frontend e a adequação mobile ainda precisam ser conferidos no repositório.
</callout>

## Regras de corte e montagem

- Abertura: normalmente 1–2 beats curtos de situação/contradição e uma missão legível. O jogador deve chegar logo ao contrato.
- Pós-breach: normalmente 1–2 beats de consequência e gancho; dar silêncio aos grandes reveals (Custodian, Sector 13, Architect). Nunca inserir explicação técnica de vulnerabilidade nos slides.
- Preservar as artes 8:3 existentes. Usar texto de interface, troca de status, foco/crop e overlays antes de solicitar novas imagens.
- Máximo recomendado de 1 fala curta por personagem a cada beat; nenhum diálogo deve ler em voz alta tudo que o terminal acabou de mostrar.
- Exibir <b>BREACH REPORT</b> como painel/arquivo opcional após a vitória; não como parte do roteiro de slides.
- Os trechos abaixo são <b>proposta editorial de texto player-facing</b> e precisam de revisão final contra o espaço real dos componentes. Não criar interações ou choices que alterem o resultado.

## 00 — Prologue \| The Impossible Theft

<b>Entrada A — Meridian:</b> “Em Meridian, o código governa portas, identidades e dinheiro.” Imagem monumental da cidade; corte para o Vault.

<b>Entrada B — incidente:</b> <code>VAULT BALANCE: 2,400,000 → 0</code> / <code>DOOR: INTACT</code> / <code>TRANSACTION: ACCEPTED</code>.

Mara: “O sistema aceitou a transação. Alguém devia estar autorizado.”Breaker: “Ele só acreditou que estava.”

<b>Transição:</b> <code>AUDITOR ACCESS: LIMITED</code>. “Descubra como entraram sem possuir a chave.” O próximo Case continua no mesmo Vault.

## 01 — No Forced Entry

<b>Antes:</b> A porta de serviço está intacta, e a Authority encerrou a inspeção física.

Mara: “Se o relatório está errado, encontre o erro no acesso.”Missão: <b>ENTRE NO VAULT SEM POSSUIR A CHAVE.</b>

<b>Depois do verifier:</b> <code>TRANSACTION ACCEPTED</code> → <code>DOOR: OPEN</code> → <code>NO FORCED ENTRY DETECTED</code>. A porta abre sem alarme.

<b>Descoberta:</b> marca <b>I</b> no ambiente; telemetria mostra um <b>operator record</b> de Elias Var, falecido. <b>Não</b> descrevê-lo como destinatário dos fundos.

Mara: “Esse identificador foi encerrado há seis meses.”Gancho: <code>NEW LEAD: DECEASED OPERATOR RECORD</code>.

## 02 — The Dead Man's Wallet

<b>Antes:</b> Arquivo civil: <code>ELIAS VAR — DECEASED</code>. Registro técnico: <code>LEGACY CONTROLLER — ACTIVE</code>. São sistemas diferentes.

Mara: “A pessoa morreu. O registro ainda responde.”Missão: <b>TORNE-SE ALGUÉM QUE NÃO DEVERIA MAIS EXISTIR.</b>

<b>Depois:</b> <code>IDENTITY CONTROLLER UPDATED</code>. O arquivo legado <b>fora da cadeia</b> permite consultar uma referência de manutenção.

<b>Descoberta:</b> <code>WAREHOUSE 17 / LOWER MERIDIAN / DO NOT USE CITY ROUTING</code>. Após obter o registro, a narrativa confirma <code>CONTROLLER RELEASED</code> como ato canônico, sem opção moral.

Breaker: “Uma identidade morta apontando para um lugar que não existe.”Gancho: <code>NEW LEAD: WAREHOUSE 17</code>.

## 03 — Warehouse 17

<b>Antes:</b> Centenas de objetos desviados parecem possuir transferências válidas. Uma contestação real obtida por Mara revela dano a um proprietário de outro equipamento.

Mara: “O sistema chama isso de transferência. O dono anterior chama de perda.”Missão: <b>RECUPERE O OBJETO LIGADO AO VAULT.</b>

<b>Depois:</b> <code>TRANSFER ACCEPTED</code>. O item passa a constar em nome do Breaker, sem a assinatura do titular anterior.

<b>Descoberta:</b> dentro do item, <b>GHOST KEY</b>. A chave aponta para <code>FLOOR 24</code> e contém o vestígio documental <code>W17 / DIAGNOSTIC TRACE</code> no Evidence Locker, sem revelar seu uso futuro. Breaker registra a cadeia de custódia; isso não legitima o furto.

Mara: “Esse prédio só tem vinte e três andares.”Gancho: <code>NEW LEAD: FLOOR 24</code>.

## 04 — The Forgotten Floor

<b>Antes:</b> Painel: <code>01–23</code>. O registro físico não traz demolição, mas o índice moderno não encontra o andar.

Missão: <b>FAÇA O SISTEMA LEMBRAR O ANDAR ESQUECIDO.</b>

<b>Depois:</b> o jogador recupera uma entrada <code>Persistent</code> arquivada pelo fluxo correto e estende o TTL. O índice volta a reconhecer o destino. O elevador revela <b>24</b>. Usar pausa visual, não explicação longa.

<b>Descoberta:</b> <code>I / FIRST LAYER</code>; artefato <code>F24 / ARCHIVED ENTRY</code> fica no Evidence Locker. A Ghost Key revela uma rota de infraestrutura, não abre portas universalmente.

<b>Último beat:</b> <code>CUSTODIAN ONLINE</code> / <code>IDENTITY UNKNOWN</code>.

## BOSS I — The Custodian

<b>Antes:</b> Sistema monumental; sem barra de HP ou nome de bug. O jogador enxerga a cadeia <code>LEGACY IDENTITY → AUTHORITY REGISTRY → CUSTODIAN CORE</code>.

Mara: “O Core parece cumprir todas as próprias regras.”Missão: <b>FAÇA O CUSTODIAN ACREDITAR QUE VOCÊ É UM OPERADOR.</b>

<b>Durante:</b> o feedback pode evoluir entre <code>IDENTITY UNKNOWN</code>, <code>CONTROLLER MISMATCH</code> e <code>CONTROLLER RECOGNIZED</code>; não revelar a solução.

<b>Depois:</b> <code>OPERATOR RECOGNIZED</code>. Pausa. <b>WELCOME BACK.</b>

Mara: “De volta?”Gancho: porta aberta; terminal antigo <code>AREN VOSS — MISSING</code>.

## 05 — The Missing Investigator

<b>Antes:</b> Workspace de Voss contém logs, tentativa de recuperação e uma hipótese antiga riscada/corrigida. Seus acessos são anteriores ao incidente do Vault.

Mara: “Ele chegou até aqui antes de nós.”Missão: <b>RECUPERE A MENSAGEM INCOMPLETA DE VOSS.</b>

<b>Depois:</b> <code>DECODER: FAILED</code> coexistindo com <code>ARCHIVE: RECOVERED</code>. O fragmento é disponibilizado.

Voss (gravação): “Eles não estão causando os erros.”Voss: “Estão esperando para ver quem os encontra.”

<b>Gancho:</b> uma anotação de Voss aponta para <code>IMPOSSIBLE ACCOUNT</code>. Não torná-lo onisciente.

## 06 — The Impossible Account

<b>Antes:</b> Um módulo antigo de créditos energéticos contém um saldo fora do domínio econômico esperado.

Mara: “Esse valor não poderia ter sido produzido por uma operação válida.”Missão: <b>REPRODUZA O SALDO IMPOSSÍVEL.</b>

<b>Depois:</b> o estado anômalo força o módulo legado a reconstruir sua tabela de origem, com resposta <code>ENERGY ROUTING TABLE / GRID NODE: 13</code>.

<b>Descoberta:</b> <code>ARCHIVE DESTINATION: SECTOR 13</code> / <code>STATUS: UNMAPPED</code>. <b>Não</b> usar “13/13/13” como senha escondida no saldo.

Breaker: “Mais um lugar que Meridian diz não existir.”Gancho: Sector 13.

## 07 — Sector 13

<b>Antes:</b> Instalação de arquivo em saturação. Registro de recuperação menciona <code>RECOVERY MODE: LEGACY</code> e acesso ampliado ao snapshot.

Voss (instrução preservada): “Quebre o Archive.”Missão: <b>PROVE A FALHA DO ARCHIVE E ENCONTRE O QUE O FALLBACK EXPÕE.</b>

<b>Depois:</b> a operação de rebuild falha; um <b>indexador externo</b> ativa snapshot de contingência excessivamente permissivo. O Breaker interrompe inserções adicionais após a prova. Não criar dados privados on-chain.

<b>Revelação:</b> <code>BREAKER REGISTRY</code> / <code>AREN VOSS: REFUSED</code> / <code>████: ACCEPTED</code> / <code>PLAYER: ACTIVE</code>. Pausa longa e timestamp recente.

Mara: “Essa entrada foi criada depois que a investigação começou.”Gancho: <code>ORACLE</code>. Preservar <code>S13 / RECOVERY SNAPSHOT</code> no Evidence Locker.

## 08 — The Oracle

<b>Antes:</b> Sistema reputado como preditivo; o player agora sabe que alguém o observa.

Mara: “Ele sabe que você chegou.”Missão: <b>PREVEJA O ORACLE ANTES QUE ELE PREVEJA VOCÊ.</b>

<b>Durante:</b> três previsões registradas antes de cada resultado.

<b>Depois:</b> <code>PROPHECY ENGINE: FAILED</code> (saída previsível); um <b>módulo distinto</b> informa <code>SUBJECT CLASSIFIER: OBSERVING</code>.

<b>Revelação:</b> <code>ARCHITECT / THE SPIRE</code>. O Oracle não vê o futuro; o classificador observa comportamento.Gancho: instalações da Spire continuam em uso.

## 09 — Steal the Key

<b>Antes:</b> <code>CASE TERMINATED</code> / <code>BREAKER ACCESS: REVOKED</code>. Mara abre um canal privado, limitado e auditável pelo recibo que decide assinar.

Mara: “Uma hora. Saia com uma prova que exista sem a sua palavra.”Missão: <b>ROUBE O ACESSO SEM ROUBAR A CHAVE.</b>

<b>Depois:</b> uma operação de manutenção válida foi executada com payload modificado: <code>EXPECTED: OPEN MAINTENANCE HATCH</code> / <code>EXECUTED: GRANT SPIRE ACCESS</code>. Uma equipe fica sem a abertura prevista; não inventar acidente.

Mara: “Eles ainda esperam o hatch. Registre isso também.”Gancho: <code>UPGRADE CONTROL</code>. O relógio é diegético, não fail state.

## 10 — Rewrite

<b>Antes:</b> O Breaker já não é auditor autorizado. O console da Spire pode substituir executables.

Mara: “Isso não é uma porta. É a regra que governa as portas.”Missão: <b>MUDE A LEI.</b>

<b>Depois:</b> <code>CONTRACT ADDRESS: UNCHANGED</code> / <code>EXECUTABLE HASH: CHANGED</code> / <code>VERSION: 1 → 2</code>. Cliente externo continua confiando no mesmo endereço, agora com outra implementação.

<b>Fechamento:</b> o canal privado de Mara expira <b>antes</b> do Architect. Sem resposta adicional dela no boss. Uma mensagem chega de outra origem: <b>ENCONTRE-ME.</b>

## FINAL BOSS — The Architect

<b>Antes:</b> O sistema não anuncia bugs; exibe <code>HISTORICAL DIAGNOSTIC: 3 REFERENCES UNRESOLVED</code>. O jogador recupera <code>W17</code>, <code>F24</code>, <code>S13</code> do Evidence Locker para o Voss Protocol, sem refazer os Cases.

<b>Durante:</b> verificar EvidenceGate e manifesto assinado por Voss; explorar Decoder/Archive, timelock e upgrade já aprendidos. O manifesto <b>não</b> é autorização de administrador. Mostrar progresso por módulos sem entregar a sequência completa.

<b>Depois:</b> <code>ARCHITECT CORE: REPLACED</code>. Mesmo assim, outra origem fala: <code>SOURCE: SEQUENCE OBSERVER</code>. O Observer independente verifica as provas e concede <code>QUALIFIED / PROVISIONAL</code>.

Architect: “Você demorou mais que Voss.”Breaker: “Onde ele está?”Architect: “Chegou até aqui. E recusou.”

<b>Recontextualização:</b> comparar cronologias verificáveis: vulnerabilidades pré-existentes, Sequence formada depois; Voss já havia chegado ao Architect antes de provocar o incidente do Vault. <code>VAULT → RECOVERY CONTROLLER → MERIDIAN RECOVERY ESCROW</code>. A política de saque prova que Voss não controlava a retirada; a quarentena ainda causou custos.

<b>Confronto:</b> o Breaker Profile mostra atos e consequências que o jogador já viveu, inclusive o recibo de Mara. O Architect pergunta: “Por que você continuou?” <b>Sem resposta selecionável</b>.

<b>Último beat:</b> <code>SEQUENCE 01 COMPLETE</code> / <code>SUBJECT QUALIFIED</code> / <code>STATUS PROVISIONAL</code> / <code>LAYER II ACCESS GRANTED</code>. “Existem outros.” Pós-crédito: transmissão em Lumen com identidade da figura oculta.

## Gate de revisão editorial

- [ ] Cada beat é compatível com a arte já aprovada e com a área disponível no site.
- [ ] Nenhuma fala entrega o nome do exploit antes do hack.
- [ ] O conteúdo técnico de correção permanece no Breach Report.
- [ ] Cada pós-breach entrega uma evidência que fundamenta o Case seguinte.
- [ ] Respeita-se um único arco e um único desfecho; as perguntas de investigação são opcionais e têm efeito visual real.
- [ ] Revisar os textos contra os Cases canônicos antes de integrá-los no frontend.

# Ajuste de beats — decisões aprovadas de Meridian

- <b>Case 05 / Voss:</b> inserir um único beat de observação com três protocolos de alerta arquivados, antes da gravação. Após a fala, mostrar um registro simples de interrupções em Lower Meridian sem revelar a motivação completa.
- <b>Case 08 / Oracle:</b> após explorar o RNG previsível, exibir <code>SUBJECT CLASSIFIER / EXPECTED ≠ OBSERVED / MODEL UPDATED</code>. A falha de previsão é do classificador, não da aleatoriedade.
- <b>Case 09 / Mara:</b> antes do recibo, mostrar <code>CASE CLOSED / SIGNER MARA / CUSTODY LIABILITY</code>. Mara confirma sem discurso; debrief da evidência, não da pena futura.
- <b>Architect:</b> encaixar o payoff documental dos alertas e a data anterior da Sequence no momento em que revela o motivo do incidente. Exibir dano a serviços de Lower Meridian antes da conclusão moral.
- <b>Epílogo:</b> a suspensão de Mara cita o mesmo identificador e hash do recibo institucional. Não introduzir cena adicional com a Authority espionando a conversa.

<b>Restrição:</b> beats são propostas de montagem; não ampliar quantidade de slides sem inventário do frontend.

# Montagem v3 — ajustes dramáticos obrigatórios por fase

<b>Estado:</b> copy e direção aprovadas para roteiro; quantidade real de slides e implementação não verificadas. Usar beats em cenas existentes sempre que possível.

- <b>Prólogo/01:</b> contraste visual “TRANSACTION ACCEPTED” versus “NO FORCED ENTRY”; motivação do Breaker é verificar o que a Authority chama de legítimo. Uma reação curta, não monólogo.
- <b>02:</b> depois do takeover, mostrar que a autoridade do morto mudou de fato; executar cleanup verificável. Breve hesitação antes do registro de revogação, sem escolha moral.
- <b>03:</b> após a Ghost Key, inserir prova civil de Mara (contestação de titularidade). Breaker: “O contrato mostra quem recebeu. Não mostra de quem era.” Mara: “Agora temos as duas provas.” Sem afirmar titularidade resolvida.
- <b>04/Custodian:</b> preservar silêncio após restauração e “WELCOME BACK”; não afirmar que o jogador já esteve no local.
- <b>05:</b> mostrar IDs e datas dos três alertas arquivados antes da gravação de Voss; exibir hipótese corrigida e custo real em Lower Meridian. Mara exige confirmação independente.
- <b>06:</b> o saldo anômalo abre tabela legada de roteamento energético. Enfatizar que há infraestrutura real dependente do módulo; não usar número como código e não inventar dano específico.
- <b>07:</b> após PLAYER: ACTIVE, pausar animação/áudio, destacar timestamp posterior ao início da investigação, só então Mara: “Criaram essa entrada depois que começamos.” Mostrar interrupção da pressão adicional como fato fixo.
- <b>08:</b> três previsões do RNG pré-registradas; separar do SUBJECT CLASSIFIER / EXPECTED ≠ OBSERVED / MODEL UPDATED. A Authority formaliza restrição de escopo ao fim do Case; sem nova subtrama.
- <b>09:</b> exibir trilha administrativa das advertências e CASE TERMINATED / ACCESS REVOKED antes do canal de Mara. Recibo assinado somente após aviso claro de responsabilidade; mostrar manutenção não executada sem inventar acidente.
- <b>10:</b> endereço igual e hash novo, clientes dependentes; silêncio curto após a troca. Canal de Mara encerra antes do boss.
- <b>Architect:</b> (A) provas interativas de cronologia e Escrow; (B) reconstrução do incidente e custos; (C) Profile confronta atos fixos e recibo de Mara; (D) QUALIFIED / PROVISIONAL e Layer II; (E) suspensão de Mara com mesmo hash; (F) teaser Lumen. Não explicar tudo em um discurso, não oferecer resposta à pergunta moral.

<b>Teste de edição:</b> cada beat precisa funcionar com diálogo mínimo, reação visual ou evidência consultável; não revelar o bug antes do exploit; não adicionar slides sem inventário do frontend.
</content>
</page>

