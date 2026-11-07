---
notion_id: 4029c563-0425-81d2-98ee-ddf85aac2d69
source: https://app.notion.com/p/4029c563042581d298eeddf85aac2d69?pvs=204
title: "🔐 ARQUIVO — 13 Estudo Cipher Gate (não canônico)"
exported_at: 2026-11-07
---

**STATUS: EXPLORAÇÃO / NÃO APROVADO / NÃO CANÔNICO.** Ideias para reformular o desafio técnico do Level 10 e a mecânica do Final Boss, **sem modificar a história, o Livro I, os contratos existentes ou a progressão linear da Season 1**. Documento para discussão, não especificação de implementação.

# Hipótese central

**Nota de status — decisão posterior:** o Voss Protocol, que recupera três shares de W17/F24/S13 e integra EvidenceGate ao Final Boss, foi aprovado como design do gameplay da Season 1. Está documentado de forma independente em [VOSS PROTOCOL — Níveis 11/12 | Especificação vigente](../cases/voss-protocol-niveis-11-12-especificacao-vigente.md). **Esta página continua NÃO CANÔNICA** para as alternativas Cipher Gate, Black Vault, ZK e mudança do Level 10; não interpretar as demais hipóteses abaixo como mudanças aprovadas.

**E se o Architect só pudesse ser compreendido depois que o Breaker estabelecesse uma sessão criptográfica verificável?**

O desafio seria sair do padrão “encontrar um bug → chamar uma função → ler a resposta” e tornar o último encontro uma experiência de investigação criptográfica real. A mensagem do Architect começa cifrada; o jogador precisa compreender o protocolo e satisfazer suas condições para que o BREAKER OS consiga decifrá-la.

**Princípio de design:** desafiar compreensão de *autorização, autenticidade, provas, estado e composição entre contratos* — e não exigir que alguém quebre SHA-256, Ed25519 ou outro algoritmo seguro. O código deve ser auditável e o exploit, reproduzível.

# Alternativas avaliadas

| Conceito | Mecânica | Potencial | Risco / cuidado |
| **The Architect's Cipher** | Canal de mensagens criptografadas, liberado após prova válida | Alto impacto visual e sensação de mistério | O ciphertext precisa ter proteção real; não esconder “segredo” em plaintext no ledger |
| **Cipher Gate** | Autorização customizada que verifica assinatura válida sobre um payload incompleto | Ensina assinatura ≠ autorização | Falha deve estar no app/protocolo customizado, não ser falsamente atribuída à autenticação nativa do Soroban |
| **Fragmented Key / Threshold Recovery** | Reconstrução de material de acesso por pistas/provas vinculadas a módulos diferentes | Investigação e composição entre sistemas | Shares de segredo publicadas em claro on-chain anulam o mistério; Shamir só oferece proteção com shares realmente protegidas |
| **ZK Authentication** | Provar conhecimento do testemunho correto sem revelá-lo ao verificador | Criptografia aplicada e prova final técnica | Exige circuito, ferramentas, verificador e avaliação de custo/compatibilidade; ZK não é dificuldade automaticamente |

# Linha preferencial **para prototipar** (não escolhida)

## Level 10 — Cipher Gate / Signed Intent

- Uma operação administrativa possui assinatura Ed25519 matematicamente válida.
- O protocolo **customizado** não vincula completamente a assinatura ao domínio, à ação, ao contrato de destino ou ao payload executado.
- O jogador identifica a lacuna de vinculação sem possuir a private key legítima.
- Ao explorar, não recebe necessariamente poder irrestrito: ganha **uma referência, capability limitada ou commitment** útil para o protocolo final.
- O desafio mantém condição objetiva determinística e testes vulnerável/corrigido.
- Pergunta pedagógica: **“Uma assinatura correta comprova exatamente qual intenção?”**

**Exemplo conceitual de falha:** a assinatura compromete `(operator, nonce)`, mas a autorização executa `(operator, nonce, action, target)`; um `action/target` não vinculado permite reaproveitar autorização para um propósito diferente. O payload de demonstração deve ser instanciado de modo que replay e domain separation possam ser testados explicitamente.

**Relação com a versão atual:** a Season 1 já possui `10 — Rewrite`, com falha de controle de Wasm upgrade. Ainda não foi decidido se Cipher Gate **substitui**, **antecede** ou **compõe** o upgrade do Level 10. A mudança só pode ocorrer após comparar objetivos pedagógicos, ritmo e dependências do Final Boss.

## Final Boss — The Architect / Zero Trust (hipótese)

1. O player encontra `ArchitectChannel` com `public_key`, `ciphertext`, identificadores de sessão e compromissos/provas verificáveis.
2. Uma chamada ingênua a `read_message()` não revela texto claro; a interface do BREAKER OS apresenta apenas os metadados necessários à investigação.
3. Informações obtidas no Level 10 permitem satisfazer parte do protocolo; outras condições decorrem de estado e registros de contratos anteriores.
4. O jogador precisa formar o testemunho correto e provar que atende à política de acesso; **ZK é opcional**, sujeito a protótipo e a confirmação de suporte/custo na rede alvo.
5. `SequenceObserver` valida independentemente o resultado. Fazer `ArchitectCore.reveal()` retornar `QUALIFIED` não basta.
6. Uma vez verificada a condição, o BREAKER OS recebe/deriva de maneira segura a chave de sessão necessária, decifra localmente e revela a **primeira mensagem inteligível do Architect**.
7. A história segue **linear e única**, sem escolher conduta, respostas ou finais; o desafio criptográfico altera a forma de chegar ao encontro, não a continuidade já definida.

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

- **Soroban é uma blockchain pública.** `storage()`, eventos e transações públicos não se tornam secretos por aplicar `require_auth()` a uma função de leitura. Segredos devem ser cifrados, mantidos fora do ledger ou derivados de material privado adequado.
- **A chave de sessão não deve ser publicada em claro on-chain.** Uma possibilidade a estudar: serviço off-chain libera um envelope cifrado à public key de sessão do jogador após verificar atestação on-chain. Isso cria uma dependência externa que precisa de modelo de ameaça, disponibilidade e testes.
- **Hash/commitment não é criptografia de confidencialidade.** Commit-reveal com segredo de baixa entropia pode ser alvo de adivinhação; se uma preimage pública basta, não afirmar sigilo.
- **Não confundir conhecer um segredo com estar autorizado a agir.** Definir a política que liga provas a direitos e revogação.
- **ZK é ferramenta, não obstáculo artificial.** O desafio deve estar em encontrar o testemunho certo e compreender a política. Fornecer tooling de geração de prova é aceitável.
- Confirmar nas versões de **Stellar Core/Soroban SDK e rede selecionada** quais primitivas, custos, contratos e verificadores ZK são efetivamente suportados. Nenhuma escolha de curva, circuito ou framework foi aprovada aqui.

# Mistério, antecipação e apresentação

- A interface pode exibir metadados de mensagens indecifráveis, fingerprints de chave, compromissos e mensagens parcialmente interpretáveis.
- Símbolos e IDs vistos antes podem ganhar novo significado no final; **não** transformar isso em caça arbitrária a bytes.
- Animações do BREAKER OS devem traduzir estados reais: `CIPHERTEXT RECEIVED`, `AUTHORIZATION INVALID`, `PROOF VERIFIED`, `MESSAGE DECRYPTED`.
- A revelação precisa resultar de dedução e execução verificáveis. Não esconder informação essencial atrás de cutscene ou tentativa-e-erro cego.
- Referências de inspiração conceitual: *Tunic* (reinterpretação de informações antigas), *Fez* (linguagem/padrões) e *Inscryption* (mistérios cifrados/ARG). Não copiar puzzles ou símbolos específicos.

# Dificuldade competitiva e teste com IA

O objetivo **não é prometer que “IA não consegue resolver”**, o que não é garantível. É aumentar a profundidade de investigação, composição e execução:

- Instâncias isoladas com parâmetros próprios por participante, preservando a mesma vulnerabilidade e fairness.
- O solver deve produzir **transações/prova válidas**, não apenas explicar o bug.
- Testar com IA apenas lendo código, IA com ferramentas e runtime, desenvolvedores humanos e humanos usando IA.
- Evitar soluções obtidas pela cópia de provas de outros jogadores ou por respostas textuais forjadas.
- Caso haja competição por premiação: regras, ranking, abuso de infraestrutura e enquadramento jurídico devem ser avaliados antes do anúncio. O valor de US\$ 100 é **ideia de produto, não compromisso registrado**.

# Decisões em aberto

- [ ] Manter `Rewrite` e adicionar componente criptográfico, ou substituí-lo por `Cipher Gate`?
- [ ] Criptografia é um **desafio obrigatório** ou um mecanismo que apenas torna o encontro final mais imersivo?
- [ ] Usar ZK de verdade ou preferir assinatura + commitments + validação de estados?
- [ ] Qual segredo/capability deve existir, quem o guarda, onde e sob qual política?
- [ ] O canal cifrado exige serviço externo ou há desenho verificável suficiente sem dependência de servidor?
- [ ] Qual é exatamente o objetivo verificável e como evitar uma prova fabricada pelo próprio atacante?
- [ ] Quanto tempo e quais conhecimentos seriam exigidos de um desenvolvedor Soroban experiente?
- [ ] Como conciliar a dificuldade do último level com a Season 1 canônica e o currículo de vulnerabilidades?
- [ ] Qual é a forma mais justa de medir resistência a IA sem criar puzzles obscuros?

# Próxima etapa, quando a ideia for aprovada

1. Criar 2–3 protótipos técnicos isolados: **assinatura com domínio incompleto**, **canal cifrado com liberação autenticada** e **proof-of-knowledge opcional**.
2. Definir critérios de vitória e testes negativos. Demonstrar que o verificador não pode ser enganado com retorno de função maliciosa.
3. Medir dificuldade real com solvabilidade humana, agentes de IA e análise de clareza do enigma.
4. Comparar resultados antes de tocar no Level 10 e no Final Boss oficiais.

# Páginas relacionadas

- Level 10 atual: [10 — Rewrite](../cases/10-rewrite.md)
- Boss final atual: [FINAL BOSS — The Architect](../cases/final-boss-the-architect.md)
- Princípios de história: [ARQUIVO — 00 Narrativa Canônica (versão antiga)](arquivo-00-narrativa-canonica-versao-antiga.md)
- Organização dos desafios: [Season 01 — The First Layer](../overview.md)

**REGRA DE ALTERAÇÃO:** Este documento não atualiza as páginas acima. Toda alteração futura precisa de decisão explícita e alinhamento simultâneo entre canon, Book I, gameplay e contratos.

## Proposta de lançamento — SEQUENCE: BLACK VAULT (estudo, 23/10/2026)

**Status: hipótese competitiva, não canônica, não aprovada, não implementada.** Este estudo registra a proposta de prêmio de US\$ 100 on-chain e como elevar o desafio contra resolução superficial ou simples cópia, **sem alterar** os dez Cases, os bosses, a história linear, as condições de vitória ou a ordem da Season 1.

### Objetivo dramático

Após acompanhar a investigação de Meridian, o jogador encontra um cofre de recompensa independente denominado **BLACK VAULT**, associado simbolicamente à Sequence do Architect. O prêmio está visível na Stellar, mas só pode ser resgatado após comprovação técnica de uma cadeia de investigações. A recompensa é um evento de lançamento, não uma transferência indevida do Vault narrativo de 2,4 milhões.

### Proposta de desafio em quatro barreiras

1. **Forense narrativa e de ledger:** IDs, cronologia, logs e pistas que já fazem sentido dentro do mundo apontam para evidências em registros e eventos públicos. Não é um questionário de enredo nem uma senha escondida em um slide. Jogador deve relacionar as evidências a estados históricos verificáveis.
2. **Composição de contratos:** uma instância isolada e parametrizada por participante contém um conjunto pequeno de contratos de teste, com uma inconsistência de autorização, estado e dependências. É necessário explorar uma sequência válida de chamadas e demonstrar mudança de estado em ambiente controlado. Não exigir quebra de SHA-256, Ed25519 ou outros algoritmos seguros.
3. **Prova criptográfica:** construir um testemunho ligado à instância, ao endereço do participante, ao ID da competição e ao identificador da rede. O componente de criptografia envolve commitments, assinaturas e/ou mensagens autenticadas; prova ZK apenas se houver motivo pedagógico e protótipo compatível. A prova é vinculada ao destinatário: a reprodução de uma flag ou transação de outra pessoa não vale.
4. **Resgate imutável:** um contrato Soroban **PrizeVault** separado dos contratos intencionalmente vulneráveis guarda o prêmio e verifica a conclusão através de um verificador/observer independente. A primeira conclusão válida aciona um pagamento único à carteira vencedora, com registro de evento auditável. O cofre não confia em um retorno 'QUALIFIED' criado pelo próprio atacante nem publica chaves privadas.

### Desenho de segurança e justiça a validar

- **Nenhum contrato didático vulnerável deve custodiar o dinheiro real.** O PrizeVault só usa condições e verificadores testados, com privilégios mínimos e revisão externa.
- Instâncias únicas por participante reduzem copiar e colar exploits. Mesmas classes de falha e dificuldade comparável; testar distribuição de parâmetros para não introduzir sorte.
- Usar **commit–reveal**, caso necessário, com commitment vinculado a participante, solução e salt de alta entropia, janela de revelação e regra pública de prioridade. Assinatura de transação isolada não comprova que o autor descobriu a solução; um verificador deve confirmar os fatos técnicos.
- Atender a replay, front-running/cópia, spam, múltiplas contas, execuções paralelas e provas forjadas. Definir precisamente se a competição premia o primeiro commitment **posteriormente validado** ou a primeira conclusão final no ledger.
- Evitar qualquer segredo recuperável apenas de storage/eventos públicos. Um hash não cifra dados; se testemunho tiver baixa entropia, é possível brute force. Dependência de segredo off-chain implica serviço de custódia, disponibilidade e confiança documentados.
- State archival e TTL do Soroban afetam disponibilidade de instâncias e compromissos; planejar renovação e custos.
- Antes de depositar dinheiro real: testes negativos/adversariais, revisão de contrato, ambiente de simulação, regras de premiação, rede e ativo corretos, compliance e regulamento publicados. US\$ 100 é orçamento hipotético, não prêmio anunciado.

### O que tornaria difícil mesmo com auxílio de IA

A dificuldade vem da combinação de **interpretação de evidências, análise de múltiplos contratos, descoberta de um caminho técnico e produção de uma prova executável**, não de informação escondida arbitrariamente. IA pode resolver CTFs e vulnerabilidades reais; não prometer 'à prova de IA'. Fazer testes comparativos com dev Soroban experiente, participantes humanos usando IA e agentes com acesso a ferramentas; observar tempo, taxas de sucesso e bypasses inesperados. A meta é premiar competência demonstrada, não provar que alguém não usou assistente.

### Fronteira entre evento e canon

A competição **é um módulo adicional de lançamento, não uma alteração dos Levels 10 (Rewrite) ou Final Boss (The Architect)**. Se integrar pistas diretamente no roteiro/solução oficial, será necessária decisão explícita e revisão de canon, contrato e testes. Os níveis atuais permanecem intocados.

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

**Pesquisa e hipóteses de design — NÃO CANÔNICO.** Referências verificadas de competições e jogos existentes. As pistas específicas abaixo são **ideias para futuros materiais**; não estão escondidas atualmente nas artes ou textos publicados, e não modificam Levels, Bosses, histórias, condições de vitória nem a ordem canônica de Season 1.

### O que vale aprender com desafios anteriores

- **Cicada 3301 (2012–2014):** misturou esteganografia, cifras, chaves OpenPGP para verificar pistas autênticas, referências literárias, coordenadas e sites. **Lição:** cada solução muda o *tipo de investigação* exigido no estágio seguinte; autenticar a fonte também pode ser parte do enigma. Evitar exigir deslocamento físico ou pressupor acesso a hardware raro.
- **Satoshi's Treasure (2019):** caça global por partes da chave de um prêmio em Bitcoin, com esquema inspirado em Shamir. **Lição:** a recompensa verificável e as pistas distribuídas geram expectativa, mas a segurança não pode depender de fragmentos publicados em fontes previsíveis; participantes conseguiram contornar pistas via força bruta muito mais rápido que o planejado.
- **MIT Mystery Hunt (desde 1981):** diversos puzzles alimentam *metapuzzles* e depois um desfecho; o processo editorial começa frequentemente pelo meta final e escreve os alimentadores de trás para a frente. **Lição:** o final deve atribuir significado novo a descobertas anteriores, não somar senhas arbitrárias.
- **Tunic (2022):** páginas de manual e elementos aparentemente decorativos ganham sentido quando o jogador aprende a interpretá-los. **Lição:** uma pista boa está à vista e permite uma segunda leitura satisfatória; deve permanecer legível e acessível.
- **Ethernaut / Paradigm CTF 2023:** instâncias de contratos vulneráveis resolvidas com chamadas/transações reais; arquivos públicos de desafios do Paradigm CTF incluem ambientes reproduzíveis. **Lição:** competência técnica deve ser provada executando um caminho verificável, e não digitando uma string.
- **Pesquisas recentes sobre puzzlehunts e IA:** problemas abertos e multimodais continuam difíceis para muitos modelos avaliados, mas isso não justifica declarar qualquer enigma 'impossível para IA'; melhora rápida de ferramentas e agentes é esperada.

### Conceito editorial sugerido — BLACK VAULT / AUTHORIZATION CHAIN

**Fantasia:** o jogador venceu a Season 1, mas percebe que Voss e Architect deixaram materiais **separados** cujo significado só surge quando reconstituídos. O prémio de US\$ 100 já aparece em um PrizeVault auditável, mas a lógica competitiva é separada do Vault de 2,4 milhões da ficção.

**Escala 1 — Foreshadowing no mundo (não requer resolver na primeira visita):** carimbos de serviço, marca `I`, metadados de recuperação, versões arquivadas, IDs de eventos, recibos de Mara e anotações de Voss podem servir como elementos de segundo significado. São anotações e evidências narrativas naturais, não sequências soltas de números piscando. **Nenhum segredo de alta relevância é acrescentado ao canon antes de aprovação.**

**Escala 2 — Auditoria de autenticidade:** participante distingue documento verdadeiro de versão alterada verificando assinatura autenticada ou hash do documento canônico. Mensagem assinada deve ter semântica de domínio, identificador do puzzle, versão e rede; não usar assinatura aparentemente válida sobre conteúdo não vinculado.

**Escala 3 — Reconstrução forense:** correlaciona documentos, eventos de contratos e estado histórico. A fonte off-chain apresenta uma interpretação incompleta; a evidência on-chain autentica a cronologia. Evitar pistas dependentes de serviços externos mutáveis ou de propriedades de armazenamento Soroban supostamente secretas.

**Escala 4 — Metapuzzle semântica:** três ou quatro resultados independentes, com formatos claros e significado dentro do jogo, montam um identificador de operação `AUTHORIZATION CHAIN`. O jogador descobre **como** os dados se relacionam; não basta concatenar resultados na ordem óbvia. Escrever o meta primeiro, depois posicionar pistas precursoras naturalmente.

**Escala 5 — Exploit composicional independente:** a chave para progredir não é um segredo textual. O jogador recebe instância parametrizada (contratos isolados de teste) e precisa executar sequência verificável envolvendo validação de ação, identidade e mudança de estado. As vulnerabilidades pedagógicas canônicas permanecem inalteradas.

**Escala 6 — Prova pessoal anti-cópia:** o contrato observa fatos objetivos e produz recibo da instância vinculado à wallet, `network_passphrase`, `competition_id` e parâmetros individuais. A pessoa produz um commitment e demonstra conhecimento do testemunho sem publicar uma chave privada. ZK pode ser testado posteriormente, mas não é requisito de design pré-aprovado.

**Escala 7 — Metafinal e prêmio:** um Observer/Verifier **independente de módulos exploráveis** registra a conclusão e o PrizeVault libera o valor a uma única carteira sob regra temporal pré-publicada. Usar commit–reveal apenas após modelar como evitar cópia na mempool/entre ledgers; commitment inicial não deve garantir vitória sem posterior prova correta. Sempre definir elegibilidade, empates, recuperações e disputa.

### Exemplo concreto de encadeamento (ILUSTRATIVO, não existe no jogo)

- A ordem de serviço de Warehouse 17 fornece a **versão correta** do documento (não uma senha).
- O registro de Floor 24 indica **onde buscar** um evento histórico (não um endereço privilegiado).
- O arquivo de Voss introduz **como validar autenticidade** da trilha.
- O incidente de Sector 13 evidencia que o indexer pode omitir registros; jogador reconstrói cronologia a partir do ledger.
- A aparente aleatoriedade do Oracle expõe o erro de confiar em dados públicos como segredo; o jogador precisa distinguir dados observáveis de testemunhos realmente privados.
- A meta final aponta para uma operação inédita do evento BLACK VAULT, sem substituir `Rewrite` nem `The Architect`. O prêmio exige um exploit reproduzível nessa instância independente.

### Regras de qualidade e teste

1. **Segunda leitura justa:** qualquer pista deve fazer sentido antes e depois; revisão não pode depender de caçar pixels imperceptíveis ou números invisíveis.
2. **Progressão multiformato com sentido:** imagem/slide → documento → event log → código → tx/prova; mudar ferramenta somente quando a evidência pede a mudança.
3. **Estado da arte de segurança:** hash não é cifragem; todos os eventos/storages públicos são legíveis; se usar Shamir, shares públicos podem ser recombinados por bots; não depositar prêmio em contratos intentionally vulnerable.
4. **Nada de segredo estático universal:** instâncias individuais, anti-replay, bindings criptográficos e provas de estado; puzzles públicos têm soluções publicáveis. Solução pode ser compartilhada como conhecimento, mas não deve ser possível roubar prêmio copiando um recibo.
5. **Pistas duráveis:** URLs e assets versionados, material byte-idêntico disponível para análise, checkpoints e replay; cuidado com compressão de imagens que destrói esteganografia.
6. **Dificuldade calibrada:** testar com humanos experientes, humanos com IA e agentes de exploração, distinguir problema de raciocínio de fricção de interface; oferecer pistas graduais se ninguém avançar.
7. **Escala do lançamento:** narrativa principal acessível à comunidade; BLACK VAULT como meta-competição opcional, com regras e horário de ativação publicados. Nunca bloquear o encerramento da Season 1 por dificuldade extrema.
8. **Projeto reverso:** fixar condição de vitória, prova e caminho seguro de payout **antes** de inserir pistas nos materiais narrativos.

### Fontes verificadas

- [MIT Mystery Hunt — histórico oficial](https://web.mit.edu/activities/puzzle/) e [como escrever metapuzzles (MIT Admissions)](https://mitadmissions.org/blogs/entry/two-hundred-puzzles-2/)
- [Satoshi's Treasure — entrevista com criador (The Block, 2019)](https://www.theblock.co/news/ecosystems/2019-04-19-we-talked-to-the-co-creator-of-satoshis-treasure-the-million-dollar-global-bitcoin-scavenger-hunt-20216), [lições do primeiro lançamento](https://www.theblock.co/news/business/2019-04-18-proof-of-work-satoshis-treasure-20080)
- [Cicada 3301 — retrospectiva](https://www.bbc.com/news/technology-25667292)
- [Tunic — criação do manual, Andrew Shouldice (PlayStation Blog)](https://blog.playstation.com/2022/09/21/the-creation-of-tunics-invaluable-in-game-manual/)
- [OpenZeppelin Ethernaut](https://ethernaut.openzeppelin.com/) e [Paradigm CTF 2023, repositório de desafios](https://github.com/paradigmxyz/paradigm-ctf-2023)
- [PuzzleWorld — benchmark de puzzlehunts multimodais (2025)](https://arxiv.org/abs/2506.06211)

**Próxima decisão futura:** escolher mecanismo do metafinal e critérios de vitória; prototipar PrizeVault + Observer em isolamento, antes de inserir qualquer pista nas cenas existentes.
