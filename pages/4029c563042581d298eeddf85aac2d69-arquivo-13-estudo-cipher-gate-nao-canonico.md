---
notion_id: 4029c563-0425-81d2-98ee-ddf85aac2d69
source: https://app.notion.com/p/4029c563042581d298eeddf85aac2d69?pvs=204
title: "🔐 ARQUIVO — 13 Estudo Cipher Gate (não canônico)"
exported_at: 2026-11-07
---

Here is the result of "fetch" for the Page with URL https://app.notion.com/p/4029c563042581d298eeddf85aac2d69 as of 2026-11-03T16:06:54.415Z:
<page url="https://app.notion.com/p/4029c563042581d298eeddf85aac2d69" icon="🔐">
<ancestor-path>
<parent-page url="https://app.notion.com/p/40d9c563042581939ffad5f7e19042e3" title="90 — Arquivo Editorial e Estudos | Season 1"/>
<ancestor-2-page url="https://app.notion.com/p/4009c563042581359693d42f09d41062" title="Season 01 — The First Layer"/>
<ancestor-3-page url="https://app.notion.com/p/4019c563042581469a0edc7e30a6eff9" title="ACT I — The World Is Breakable"/>
<ancestor-4-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
<properties>
{"title":"ARQUIVO — 13 Estudo Cipher Gate (não canônico)"}
</properties>
<iconMetadata>{"type":"emoji","emoji":"🔐"}</iconMetadata>
<content>
<callout icon="🧪" color="yellow_bg">
<b>STATUS: EXPLORAÇÃO / NÃO APROVADO / NÃO CANÔNICO.</b> Ideias para reformular o desafio técnico do Level 10 e a mecânica do Final Boss, <b>sem modificar a história, o Livro I, os contratos existentes ou a progressão linear da Season 1</b>. Documento para discussão, não especificação de implementação.
</callout>

# Hipótese central

<b>Nota de status — decisão posterior:</b> o Voss Protocol, que recupera três shares de W17/F24/S13 e integra EvidenceGate ao Final Boss, foi aprovado como design do gameplay da Season 1. Está documentado de forma independente em <mention url="https://app.notion.com/p/4039c56304258137ae19e8787acc1d1f" />. <b>Esta página continua NÃO CANÔNICA</b> para as alternativas Cipher Gate, Black Vault, ZK e mudança do Level 10; não interpretar as demais hipóteses abaixo como mudanças aprovadas.

<b>E se o Architect só pudesse ser compreendido depois que o Breaker estabelecesse uma sessão criptográfica verificável?</b>

O desafio seria sair do padrão “encontrar um bug → chamar uma função → ler a resposta” e tornar o último encontro uma experiência de investigação criptográfica real. A mensagem do Architect começa cifrada; o jogador precisa compreender o protocolo e satisfazer suas condições para que o BREAKER OS consiga decifrá-la.

<b>Princípio de design:</b> desafiar compreensão de <i>autorização, autenticidade, provas, estado e composição entre contratos</i> — e não exigir que alguém quebre SHA-256, Ed25519 ou outro algoritmo seguro. O código deve ser auditável e o exploit, reproduzível.

# Alternativas avaliadas

<table fit-page-width="true" header-row="true">
<tr>
<td>
Conceito
</td>
<td>
Mecânica
</td>
<td>
Potencial
</td>
<td>
Risco / cuidado
</td>
</tr>
<tr>
<td>
<b>The Architect's Cipher</b>
</td>
<td>
Canal de mensagens criptografadas, liberado após prova válida
</td>
<td>
Alto impacto visual e sensação de mistério
</td>
<td>
O ciphertext precisa ter proteção real; não esconder “segredo” em plaintext no ledger
</td>
</tr>
<tr>
<td>
<b>Cipher Gate</b>
</td>
<td>
Autorização customizada que verifica assinatura válida sobre um payload incompleto
</td>
<td>
Ensina assinatura ≠ autorização
</td>
<td>
Falha deve estar no app/protocolo customizado, não ser falsamente atribuída à autenticação nativa do Soroban
</td>
</tr>
<tr>
<td>
<b>Fragmented Key / Threshold Recovery</b>
</td>
<td>
Reconstrução de material de acesso por pistas/provas vinculadas a módulos diferentes
</td>
<td>
Investigação e composição entre sistemas
</td>
<td>
Shares de segredo publicadas em claro on-chain anulam o mistério; Shamir só oferece proteção com shares realmente protegidas
</td>
</tr>
<tr>
<td>
<b>ZK Authentication</b>
</td>
<td>
Provar conhecimento do testemunho correto sem revelá-lo ao verificador
</td>
<td>
Criptografia aplicada e prova final técnica
</td>
<td>
Exige circuito, ferramentas, verificador e avaliação de custo/compatibilidade; ZK não é dificuldade automaticamente
</td>
</tr>
</table>

# Linha preferencial <b>para prototipar</b> (não escolhida)

## Level 10 — Cipher Gate / Signed Intent

- Uma operação administrativa possui assinatura Ed25519 matematicamente válida.
- O protocolo <b>customizado</b> não vincula completamente a assinatura ao domínio, à ação, ao contrato de destino ou ao payload executado.
- O jogador identifica a lacuna de vinculação sem possuir a private key legítima.
- Ao explorar, não recebe necessariamente poder irrestrito: ganha <b>uma referência, capability limitada ou commitment</b> útil para o protocolo final.
- O desafio mantém condição objetiva determinística e testes vulnerável/corrigido.
- Pergunta pedagógica: <b>“Uma assinatura correta comprova exatamente qual intenção?”</b>

<b>Exemplo conceitual de falha:</b> a assinatura compromete <code>(operator, nonce)</code>, mas a autorização executa <code>(operator, nonce, action, target)</code>; um <code>action/target</code> não vinculado permite reaproveitar autorização para um propósito diferente. O payload de demonstração deve ser instanciado de modo que replay e domain separation possam ser testados explicitamente.

<b>Relação com a versão atual:</b> a Season 1 já possui <code>10 — Rewrite</code>, com falha de controle de Wasm upgrade. Ainda não foi decidido se Cipher Gate <b>substitui</b>, <b>antecede</b> ou <b>compõe</b> o upgrade do Level 10. A mudança só pode ocorrer após comparar objetivos pedagógicos, ritmo e dependências do Final Boss.

## Final Boss — The Architect / Zero Trust (hipótese)

1. O player encontra <code>ArchitectChannel</code> com <code>public_key</code>, <code>ciphertext</code>, identificadores de sessão e compromissos/provas verificáveis.
2. Uma chamada ingênua a <code>read_message()</code> não revela texto claro; a interface do BREAKER OS apresenta apenas os metadados necessários à investigação.
3. Informações obtidas no Level 10 permitem satisfazer parte do protocolo; outras condições decorrem de estado e registros de contratos anteriores.
4. O jogador precisa formar o testemunho correto e provar que atende à política de acesso; <b>ZK é opcional</b>, sujeito a protótipo e a confirmação de suporte/custo na rede alvo.
5. <code>SequenceObserver</code> valida independentemente o resultado. Fazer <code>ArchitectCore.reveal()</code> retornar <code>QUALIFIED</code> não basta.
6. Uma vez verificada a condição, o BREAKER OS recebe/deriva de maneira segura a chave de sessão necessária, decifra localmente e revela a <b>primeira mensagem inteligível do Architect</b>.
7. A história segue <b>linear e única</b>, sem escolher conduta, respostas ou finais; o desafio criptográfico altera a forma de chegar ao encontro, não a continuidade já definida.

```txt
LEVEL 10: SIGNED INTENT
         │
         ▼
 Capability / Commitment / Evidence
         │
         ▼
 FINAL: ARCHITECT CHANNEL
   ciphertext + public metadata
         │
         ▼
  Contract State Investigation
         │
         ▼
  Witness / Policy Satisfaction
         │
         ▼
  ZK Proof? (optional design path)
         │
         ▼
 SequenceObserver verifies on-chain
         │
         ▼
 Session Key securely made available
         │
         ▼
 BREAKER OS decrypts Architect message
         │
         ▼
        QUALIFIED
```

## Limites técnicos a respeitar

- <b>Soroban é uma blockchain pública.</b> <code>storage()</code>, eventos e transações públicos não se tornam secretos por aplicar <code>require_auth()</code> a uma função de leitura. Segredos devem ser cifrados, mantidos fora do ledger ou derivados de material privado adequado.
- <b>A chave de sessão não deve ser publicada em claro on-chain.</b> Uma possibilidade a estudar: serviço off-chain libera um envelope cifrado à public key de sessão do jogador após verificar atestação on-chain. Isso cria uma dependência externa que precisa de modelo de ameaça, disponibilidade e testes.
- <b>Hash/commitment não é criptografia de confidencialidade.</b> Commit-reveal com segredo de baixa entropia pode ser alvo de adivinhação; se uma preimage pública basta, não afirmar sigilo.
- <b>Não confundir conhecer um segredo com estar autorizado a agir.</b> Definir a política que liga provas a direitos e revogação.
- <b>ZK é ferramenta, não obstáculo artificial.</b> O desafio deve estar em encontrar o testemunho certo e compreender a política. Fornecer tooling de geração de prova é aceitável.
- Confirmar nas versões de <b>Stellar Core/Soroban SDK e rede selecionada</b> quais primitivas, custos, contratos e verificadores ZK são efetivamente suportados. Nenhuma escolha de curva, circuito ou framework foi aprovada aqui.

# Mistério, antecipação e apresentação

- A interface pode exibir metadados de mensagens indecifráveis, fingerprints de chave, compromissos e mensagens parcialmente interpretáveis.
- Símbolos e IDs vistos antes podem ganhar novo significado no final; <b>não</b> transformar isso em caça arbitrária a bytes.
- Animações do BREAKER OS devem traduzir estados reais: <code>CIPHERTEXT RECEIVED</code>, <code>AUTHORIZATION INVALID</code>, <code>PROOF VERIFIED</code>, <code>MESSAGE DECRYPTED</code>.
- A revelação precisa resultar de dedução e execução verificáveis. Não esconder informação essencial atrás de cutscene ou tentativa-e-erro cego.
- Referências de inspiração conceitual: <i>Tunic</i> (reinterpretação de informações antigas), <i>Fez</i> (linguagem/padrões) e <i>Inscryption</i> (mistérios cifrados/ARG). Não copiar puzzles ou símbolos específicos.

# Dificuldade competitiva e teste com IA

O objetivo <b>não é prometer que “IA não consegue resolver”</b>, o que não é garantível. É aumentar a profundidade de investigação, composição e execução:

- Instâncias isoladas com parâmetros próprios por participante, preservando a mesma vulnerabilidade e fairness.
- O solver deve produzir <b>transações/prova válidas</b>, não apenas explicar o bug.
- Testar com IA apenas lendo código, IA com ferramentas e runtime, desenvolvedores humanos e humanos usando IA.
- Evitar soluções obtidas pela cópia de provas de outros jogadores ou por respostas textuais forjadas.
- Caso haja competição por premiação: regras, ranking, abuso de infraestrutura e enquadramento jurídico devem ser avaliados antes do anúncio. O valor de US\$ 100 é <b>ideia de produto, não compromisso registrado</b>.

# Decisões em aberto

- [ ] Manter <code>Rewrite</code> e adicionar componente criptográfico, ou substituí-lo por <code>Cipher Gate</code>?
- [ ] Criptografia é um <b>desafio obrigatório</b> ou um mecanismo que apenas torna o encontro final mais imersivo?
- [ ] Usar ZK de verdade ou preferir assinatura + commitments + validação de estados?
- [ ] Qual segredo/capability deve existir, quem o guarda, onde e sob qual política?
- [ ] O canal cifrado exige serviço externo ou há desenho verificável suficiente sem dependência de servidor?
- [ ] Qual é exatamente o objetivo verificável e como evitar uma prova fabricada pelo próprio atacante?
- [ ] Quanto tempo e quais conhecimentos seriam exigidos de um desenvolvedor Soroban experiente?
- [ ] Como conciliar a dificuldade do último level com a Season 1 canônica e o currículo de vulnerabilidades?
- [ ] Qual é a forma mais justa de medir resistência a IA sem criar puzzles obscuros?

# Próxima etapa, quando a ideia for aprovada

1. Criar 2–3 protótipos técnicos isolados: <b>assinatura com domínio incompleto</b>, <b>canal cifrado com liberação autenticada</b> e <b>proof-of-knowledge opcional</b>.
2. Definir critérios de vitória e testes negativos. Demonstrar que o verificador não pode ser enganado com retorno de função maliciosa.
3. Medir dificuldade real com solvabilidade humana, agentes de IA e análise de clareza do enigma.
4. Comparar resultados antes de tocar no Level 10 e no Final Boss oficiais.

# Páginas relacionadas

- Level 10 atual: <mention url="https://app.notion.com/p/4009c5630425815395a8cbd0b9a7b536" />
- Boss final atual: <mention url="https://app.notion.com/p/4009c5630425815581b2df01797d5365" />
- Princípios de história: <mention url="https://app.notion.com/p/4009c56304258171a500f3baa7ddcf83" />
- Organização dos desafios: <mention url="https://app.notion.com/p/4009c563042581359693d42f09d41062">Season 01 — The First Layer</mention>

<b>REGRA DE ALTERAÇÃO:</b> Este documento não atualiza as páginas acima. Toda alteração futura precisa de decisão explícita e alinhamento simultâneo entre canon, Book I, gameplay e contratos.

## Proposta de lançamento — SEQUENCE: BLACK VAULT (estudo, 23/10/2026)

<callout icon="🧪" color="yellow_bg">
<b>Status: hipótese competitiva, não canônica, não aprovada, não implementada.</b> Este estudo registra a proposta de prêmio de US\$ 100 on-chain e como elevar o desafio contra resolução superficial ou simples cópia, <b>sem alterar</b> os dez Cases, os bosses, a história linear, as condições de vitória ou a ordem da Season 1.
</callout>

### Objetivo dramático

Após acompanhar a investigação de Meridian, o jogador encontra um cofre de recompensa independente denominado <b>BLACK VAULT</b>, associado simbolicamente à Sequence do Architect. O prêmio está visível na Stellar, mas só pode ser resgatado após comprovação técnica de uma cadeia de investigações. A recompensa é um evento de lançamento, não uma transferência indevida do Vault narrativo de 2,4 milhões.

### Proposta de desafio em quatro barreiras

1. <b>Forense narrativa e de ledger:</b> IDs, cronologia, logs e pistas que já fazem sentido dentro do mundo apontam para evidências em registros e eventos públicos. Não é um questionário de enredo nem uma senha escondida em um slide. Jogador deve relacionar as evidências a estados históricos verificáveis.
2. <b>Composição de contratos:</b> uma instância isolada e parametrizada por participante contém um conjunto pequeno de contratos de teste, com uma inconsistência de autorização, estado e dependências. É necessário explorar uma sequência válida de chamadas e demonstrar mudança de estado em ambiente controlado. Não exigir quebra de SHA-256, Ed25519 ou outros algoritmos seguros.
3. <b>Prova criptográfica:</b> construir um testemunho ligado à instância, ao endereço do participante, ao ID da competição e ao identificador da rede. O componente de criptografia envolve commitments, assinaturas e/ou mensagens autenticadas; prova ZK apenas se houver motivo pedagógico e protótipo compatível. A prova é vinculada ao destinatário: a reprodução de uma flag ou transação de outra pessoa não vale.
4. <b>Resgate imutável:</b> um contrato Soroban <b>PrizeVault</b> separado dos contratos intencionalmente vulneráveis guarda o prêmio e verifica a conclusão através de um verificador/observer independente. A primeira conclusão válida aciona um pagamento único à carteira vencedora, com registro de evento auditável. O cofre não confia em um retorno 'QUALIFIED' criado pelo próprio atacante nem publica chaves privadas.

### Desenho de segurança e justiça a validar

- <b>Nenhum contrato didático vulnerável deve custodiar o dinheiro real.</b> O PrizeVault só usa condições e verificadores testados, com privilégios mínimos e revisão externa.
- Instâncias únicas por participante reduzem copiar e colar exploits. Mesmas classes de falha e dificuldade comparável; testar distribuição de parâmetros para não introduzir sorte.
- Usar <b>commit–reveal</b>, caso necessário, com commitment vinculado a participante, solução e salt de alta entropia, janela de revelação e regra pública de prioridade. Assinatura de transação isolada não comprova que o autor descobriu a solução; um verificador deve confirmar os fatos técnicos.
- Atender a replay, front-running/cópia, spam, múltiplas contas, execuções paralelas e provas forjadas. Definir precisamente se a competição premia o primeiro commitment <b>posteriormente validado</b> ou a primeira conclusão final no ledger.
- Evitar qualquer segredo recuperável apenas de storage/eventos públicos. Um hash não cifra dados; se testemunho tiver baixa entropia, é possível brute force. Dependência de segredo off-chain implica serviço de custódia, disponibilidade e confiança documentados.
- State archival e TTL do Soroban afetam disponibilidade de instâncias e compromissos; planejar renovação e custos.
- Antes de depositar dinheiro real: testes negativos/adversariais, revisão de contrato, ambiente de simulação, regras de premiação, rede e ativo corretos, compliance e regulamento publicados. US\$ 100 é orçamento hipotético, não prêmio anunciado.

### O que tornaria difícil mesmo com auxílio de IA

A dificuldade vem da combinação de <b>interpretação de evidências, análise de múltiplos contratos, descoberta de um caminho técnico e produção de uma prova executável</b>, não de informação escondida arbitrariamente. IA pode resolver CTFs e vulnerabilidades reais; não prometer 'à prova de IA'. Fazer testes comparativos com dev Soroban experiente, participantes humanos usando IA e agentes com acesso a ferramentas; observar tempo, taxas de sucesso e bypasses inesperados. A meta é premiar competência demonstrada, não provar que alguém não usou assistente.

### Fronteira entre evento e canon

A competição <b>é um módulo adicional de lançamento, não uma alteração dos Levels 10 (Rewrite) ou Final Boss (The Architect)</b>. Se integrar pistas diretamente no roteiro/solução oficial, será necessária decisão explícita e revisão de canon, contrato e testes. Os níveis atuais permanecem intocados.

### Referências para protótipo

- [Soroban: contratos, chamadas e autenticação](https://developers.stellar.org/docs/build/guides/conventions/cross-contract)
- [Exemplo de transferência de tokens por contrato](https://developers.stellar.org/docs/build/smart-contracts/example-contracts/atomic-swap)
- [Guia de state archival](https://developers.stellar.org/docs/build/guides/dapps/state-archival)
- [EVMbench — avaliação de IA em segurança de contratos](https://proceedings.mlr.press/v306/wang26k.html)
- [SCONE-bench — AI agents find smart contract exploits](https://www.anthropic.com/research/smart-contracts)

### Decisões pendentes

- [ ] Evento independente opcional pós-Season 1 ou parte do fechamento obrigatório?
- [ ] Rede onde ocorrerão as instâncias e rede onde será guardado o prêmio?
- [ ] Critério público de 'primeiro vencedor' e mecanismo anti-cópia?
- [ ] Nível-alvo de dificuldade, medido em testes humanos e com IA?
- [ ] Escolha exata entre assinatura + commitment e prova ZK somente após protótipo?
- [ ] Auditoria, financiamento, elegibilidade e regras de distribuição?

## Pesquisa histórica de puzzlehunts e proposta em escalas (23/10/2026)

<callout icon="🔎" color="yellow_bg">
<b>Pesquisa e hipóteses de design — NÃO CANÔNICO.</b> Referências verificadas de competições e jogos existentes. As pistas específicas abaixo são <b>ideias para futuros materiais</b>; não estão escondidas atualmente nas artes ou textos publicados, e não modificam Levels, Bosses, histórias, condições de vitória nem a ordem canônica de Season 1.
</callout>

### O que vale aprender com desafios anteriores

- <b>Cicada 3301 (2012–2014):</b> misturou esteganografia, cifras, chaves OpenPGP para verificar pistas autênticas, referências literárias, coordenadas e sites. <b>Lição:</b> cada solução muda o <i>tipo de investigação</i> exigido no estágio seguinte; autenticar a fonte também pode ser parte do enigma. Evitar exigir deslocamento físico ou pressupor acesso a hardware raro.
- <b>Satoshi's Treasure (2019):</b> caça global por partes da chave de um prêmio em Bitcoin, com esquema inspirado em Shamir. <b>Lição:</b> a recompensa verificável e as pistas distribuídas geram expectativa, mas a segurança não pode depender de fragmentos publicados em fontes previsíveis; participantes conseguiram contornar pistas via força bruta muito mais rápido que o planejado.
- <b>MIT Mystery Hunt (desde 1981):</b> diversos puzzles alimentam <i>metapuzzles</i> e depois um desfecho; o processo editorial começa frequentemente pelo meta final e escreve os alimentadores de trás para a frente. <b>Lição:</b> o final deve atribuir significado novo a descobertas anteriores, não somar senhas arbitrárias.
- <b>Tunic (2022):</b> páginas de manual e elementos aparentemente decorativos ganham sentido quando o jogador aprende a interpretá-los. <b>Lição:</b> uma pista boa está à vista e permite uma segunda leitura satisfatória; deve permanecer legível e acessível.
- <b>Ethernaut / Paradigm CTF 2023:</b> instâncias de contratos vulneráveis resolvidas com chamadas/transações reais; arquivos públicos de desafios do Paradigm CTF incluem ambientes reproduzíveis. <b>Lição:</b> competência técnica deve ser provada executando um caminho verificável, e não digitando uma string.
- <b>Pesquisas recentes sobre puzzlehunts e IA:</b> problemas abertos e multimodais continuam difíceis para muitos modelos avaliados, mas isso não justifica declarar qualquer enigma 'impossível para IA'; melhora rápida de ferramentas e agentes é esperada.

### Conceito editorial sugerido — BLACK VAULT / AUTHORIZATION CHAIN

<b>Fantasia:</b> o jogador venceu a Season 1, mas percebe que Voss e Architect deixaram materiais <b>separados</b> cujo significado só surge quando reconstituídos. O prémio de US\$ 100 já aparece em um PrizeVault auditável, mas a lógica competitiva é separada do Vault de 2,4 milhões da ficção.

<b>Escala 1 — Foreshadowing no mundo (não requer resolver na primeira visita):</b> carimbos de serviço, marca <code>I</code>, metadados de recuperação, versões arquivadas, IDs de eventos, recibos de Mara e anotações de Voss podem servir como elementos de segundo significado. São anotações e evidências narrativas naturais, não sequências soltas de números piscando. <b>Nenhum segredo de alta relevância é acrescentado ao canon antes de aprovação.</b>

<b>Escala 2 — Auditoria de autenticidade:</b> participante distingue documento verdadeiro de versão alterada verificando assinatura autenticada ou hash do documento canônico. Mensagem assinada deve ter semântica de domínio, identificador do puzzle, versão e rede; não usar assinatura aparentemente válida sobre conteúdo não vinculado.

<b>Escala 3 — Reconstrução forense:</b> correlaciona documentos, eventos de contratos e estado histórico. A fonte off-chain apresenta uma interpretação incompleta; a evidência on-chain autentica a cronologia. Evitar pistas dependentes de serviços externos mutáveis ou de propriedades de armazenamento Soroban supostamente secretas.

<b>Escala 4 — Metapuzzle semântica:</b> três ou quatro resultados independentes, com formatos claros e significado dentro do jogo, montam um identificador de operação <code>AUTHORIZATION CHAIN</code>. O jogador descobre <b>como</b> os dados se relacionam; não basta concatenar resultados na ordem óbvia. Escrever o meta primeiro, depois posicionar pistas precursoras naturalmente.

<b>Escala 5 — Exploit composicional independente:</b> a chave para progredir não é um segredo textual. O jogador recebe instância parametrizada (contratos isolados de teste) e precisa executar sequência verificável envolvendo validação de ação, identidade e mudança de estado. As vulnerabilidades pedagógicas canônicas permanecem inalteradas.

<b>Escala 6 — Prova pessoal anti-cópia:</b> o contrato observa fatos objetivos e produz recibo da instância vinculado à wallet, <code>network_passphrase</code>, <code>competition_id</code> e parâmetros individuais. A pessoa produz um commitment e demonstra conhecimento do testemunho sem publicar uma chave privada. ZK pode ser testado posteriormente, mas não é requisito de design pré-aprovado.

<b>Escala 7 — Metafinal e prêmio:</b> um Observer/Verifier <b>independente de módulos exploráveis</b> registra a conclusão e o PrizeVault libera o valor a uma única carteira sob regra temporal pré-publicada. Usar commit–reveal apenas após modelar como evitar cópia na mempool/entre ledgers; commitment inicial não deve garantir vitória sem posterior prova correta. Sempre definir elegibilidade, empates, recuperações e disputa.

### Exemplo concreto de encadeamento (ILUSTRATIVO, não existe no jogo)

- A ordem de serviço de Warehouse 17 fornece a <b>versão correta</b> do documento (não uma senha).
- O registro de Floor 24 indica <b>onde buscar</b> um evento histórico (não um endereço privilegiado).
- O arquivo de Voss introduz <b>como validar autenticidade</b> da trilha.
- O incidente de Sector 13 evidencia que o indexer pode omitir registros; jogador reconstrói cronologia a partir do ledger.
- A aparente aleatoriedade do Oracle expõe o erro de confiar em dados públicos como segredo; o jogador precisa distinguir dados observáveis de testemunhos realmente privados.
- A meta final aponta para uma operação inédita do evento BLACK VAULT, sem substituir <code>Rewrite</code> nem <code>The Architect</code>. O prêmio exige um exploit reproduzível nessa instância independente.

### Regras de qualidade e teste

1. <b>Segunda leitura justa:</b> qualquer pista deve fazer sentido antes e depois; revisão não pode depender de caçar pixels imperceptíveis ou números invisíveis.
2. <b>Progressão multiformato com sentido:</b> imagem/slide → documento → event log → código → tx/prova; mudar ferramenta somente quando a evidência pede a mudança.
3. <b>Estado da arte de segurança:</b> hash não é cifragem; todos os eventos/storages públicos são legíveis; se usar Shamir, shares públicos podem ser recombinados por bots; não depositar prêmio em contratos intentionally vulnerable.
4. <b>Nada de segredo estático universal:</b> instâncias individuais, anti-replay, bindings criptográficos e provas de estado; puzzles públicos têm soluções publicáveis. Solução pode ser compartilhada como conhecimento, mas não deve ser possível roubar prêmio copiando um recibo.
5. <b>Pistas duráveis:</b> URLs e assets versionados, material byte-idêntico disponível para análise, checkpoints e replay; cuidado com compressão de imagens que destrói esteganografia.
6. <b>Dificuldade calibrada:</b> testar com humanos experientes, humanos com IA e agentes de exploração, distinguir problema de raciocínio de fricção de interface; oferecer pistas graduais se ninguém avançar.
7. <b>Escala do lançamento:</b> narrativa principal acessível à comunidade; BLACK VAULT como meta-competição opcional, com regras e horário de ativação publicados. Nunca bloquear o encerramento da Season 1 por dificuldade extrema.
8. <b>Projeto reverso:</b> fixar condição de vitória, prova e caminho seguro de payout <b>antes</b> de inserir pistas nos materiais narrativos.

### Fontes verificadas

- [MIT Mystery Hunt — histórico oficial](https://web.mit.edu/activities/puzzle/) e [como escrever metapuzzles (MIT Admissions)](https://mitadmissions.org/blogs/entry/two-hundred-puzzles-2/)
- [Satoshi's Treasure — entrevista com criador (The Block, 2019)](https://www.theblock.co/news/ecosystems/2019-04-19-we-talked-to-the-co-creator-of-satoshis-treasure-the-million-dollar-global-bitcoin-scavenger-hunt-20216), [lições do primeiro lançamento](https://www.theblock.co/news/business/2019-04-18-proof-of-work-satoshis-treasure-20080)
- [Cicada 3301 — retrospectiva](https://www.bbc.com/news/technology-25667292)
- [Tunic — criação do manual, Andrew Shouldice (PlayStation Blog)](https://blog.playstation.com/2022/09/21/the-creation-of-tunics-invaluable-in-game-manual/)
- [OpenZeppelin Ethernaut](https://ethernaut.openzeppelin.com/) e [Paradigm CTF 2023, repositório de desafios](https://github.com/paradigmxyz/paradigm-ctf-2023)
- [PuzzleWorld — benchmark de puzzlehunts multimodais (2025)](https://arxiv.org/abs/2506.06211)

<b>Próxima decisão futura:</b> escolher mecanismo do metafinal e critérios de vitória; prototipar PrizeVault + Observer em isolamento, antes de inserir qualquer pista nas cenas existentes.
</content>
</page>

