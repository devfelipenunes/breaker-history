---
notion_id: 4019c563-0425-814f-9890-c0443277eeac
source: https://app.notion.com/p/4019c5630425814f9890c0443277eeac?pvs=204
title: "🎬 ARQUIVO — 11 Sala de Roteiro S1 (revisão v2)"
exported_at: 2026-11-07
---

**Status: REFERÊNCIA HISTÓRICA v2.** Esta sala de roteiro preserva metodologias e decisões antigas, não é o roteiro de produção vigente. Para Season 1, prevalece [BREAKER — Season 1 | FINAL NARRATIVE v1.4 — NARRATIVE LOCK](../narrative/breaker-season-1-final-narrative-v1-4-narrative-lock.md) (v1.4 NARRATIVE LOCK). O Act I e a Series Arc & Hidden Canon orientam continuidade da trilogia, sem substituir a mecânica aprovada em Rewrite/Architect. Não inferir implementação ou QA executado deste documento.

# Diagnóstico e tese dramática

A Season 1 não é uma coleção de aulas sobre smart contracts: é uma investigação sobre **a diferença entre execução, autorização e legitimidade**. O maior risco do roteiro anterior era repetir o ciclo "contrato → exploit → pista", sem fricção humana ou consequência.

**Pergunta externa:** quem provocou o incidente do Vault e por quê?
**Pergunta relacional:** Mara pode confiar em um auditor que ultrapassa os limites que ela impõe?
**Pergunta interna:** compreender uma falha concede o direito de explorá-la?
**Promessa ao jogador:** aprender a pensar como auditor, sem confundir capacidade técnica com autoridade moral.

# Cinco movimentos dramáticos

1. **Ato I — Certeza quebrada (Prólogo, Cases 1–2).** O incidente abala a confiança de Meridian; a trilha de autorização leva à identidade de um morto. Atribuir autoria e destino financeiro permanece prematuro.
2. **Ato II — Intrusão e custo (Cases 3–4, Custodian).** Warehouse 17 transforma uma abstração em perda humana. O Breaker ultrapassa um limite imposto por Mara; ela coleta uma prova institucional que ele não conseguiria obter do código. A descoberta da First Layer altera a escala.
3. **Ato III — O espelho (Cases 5–7).** Voss parece ter percorrido a mesma rota. Em Sector 13, a entrada ACTIVE do próprio jogador muda a pergunta: não é apenas quem ele persegue, mas quem o observa. O Breaker provoca a falha e depois contém a pressão adicional; não existe rota destrutiva alternativa.
4. **Ato IV — Autoridade revogada (Case 8 e Case 9).** Oracle separa pseudoaleatoriedade previsível de classificação comportamental; a Authority revoga o mandato. Mara arrisca a carreira ao manter um canal limitado por uma hora, sem transferir autoridade ilimitada.
5. **Ato V — Poder e juízo (Case 10, Architect, epílogo).** O Breaker demonstra como uma rejeição pode virar VossProof aceita e desvia uma operação de diagnóstico para abrir uma sessão forense do Architect. Revelam-se a cronologia de Voss e o Escrow. O Profile revisita os acontecimentos fixos e seus custos; qualificação técnica permanece distinta de consentimento ou legitimidade.

# Cadeia causal de evidências — contrato e mundo

**Vault:** a entrada pelo Access Gate permite consultar uma trilha de serviço que uma inspeção padrão não examinou. A chamada problemática autentica um endereço declarado, não a pessoa que o controla.
**Transação principal:** os 2.400.000 saíram do Vault pela rota de recuperação institucional, terminando no **Meridian Recovery Escrow**. Os ativos **não** entraram na posse pessoal de Voss. A identidade de um técnico morto aparece como *operator identity / metadado legado*, não como custódia financeira. Não afirmar em nenhum Case que o dinheiro ficou na wallet do morto.
**Visibilidade da prova:** a trilha no ledger é verificável, mas a interface de auditoria padrão mostra um saldo final e eventos normalizados, não uma explicação causal completa. A investigação cruza contract IDs, histórico de operações e política de saque. O destino institucional pode ser suspeitado antes do clímax; a prova de que Voss não tem autoridade para gastar e de que planejou o incidente deve ser a recontextualização final.
**Custos do incidente:** recursos em quarentena continuam contabilizados, porém temporariamente indisponíveis para certos fluxos operacionais até revisão. Um registro de serviço atrasado em Lower Meridian revela consequência indireta; Voss não pode ser descrito como moralmente inocente só porque não se enriqueceu.
**Dead Wallet:** a falha de reinitialization permite assumir o controle do registro de identidade, não reescrever a história de propriedade do saldo do Vault. A evidência necessária é um log técnico do operador com referência a Warehouse 17.
**Warehouse:** o item capturado é a Ghost Key. Um processo de contestação pendente sobre equipamento confiscado mostra que "TRANSFER ACCEPTED" pode prejudicar um proprietário anterior. Não introduzir um novo membro fixo do elenco.
**Sector 13:** o DoS ativa fallback de continuidade operacional. O snapshot do Registry aparece devido a uma política legada de leitura inadequadamente segregada do fallback (explicação diegética, não segundo exploit obrigatório). O jogador consegue distinguir modos de recuperação com efeitos locais diferentes.
**Oracle:** a tarefa de três previsões comprova uma previsão local deterministicamente falha; o registro do observador comportamental é um módulo distinto. O Oracle não lê o futuro.
**Spire:** revogação formal é uma linha moral: daí em diante o Breaker não é um auditor autorizado. O canal de Mara tem escopo e tempo limitados. A suspensão dela é consequência pessoal, não decisão genérica da instituição.
**Architect:** a informação final deve permitir refazer a trilha Vault → Legacy Operator Identity → Warehouse → First Layer → Voss → Sector 13 → Oracle → Spire; o Escrow é provado por chain-of-custody e spend policy, não por um monólogo.

# Progressão do par Breaker–Mara

- **No Vault:** Mara valoriza procedimento e cadeia de custódia, mas já distingue uma transação aceita de autorização legítima; ela questiona a conclusão institucional em vez de agir com ingenuidade.
- **Warehouse:** Mara localiza no registro de contestações um reclamante e uma autorização de transferência inexistente. Essa evidência muda a hipótese; o Breaker, sozinho, não a conseguiria por inspecionar apenas o contrato.
- **Depois da Ghost Key:** Mara exige que o Breaker preserve os registros originais e deixe uma prova verificável, sem assumir posse permanente. A reação posterior de Mara deriva do registro da prova, uma ação fixa do enredo; não bloqueia o challenge.
- **Forgotten Floor / Custodian:** Mara coopera, mas não aprova automaticamente tomar uma identidade histórica.
- **Sector 13:** o Breaker interrompe a pressão adicional sobre o Archive após provocar a falha; Mara o confronta pelo custo do incidente.
- **Spire:** Mara concede uma janela de comunicação de uma hora, mas não autoriza a entrada nem o desvio do timelock. O heist impede a abertura do hatch de manutenção programada e produz uma consequência operacional concreta para a equipe. O relógio é diegético e roteirizado, não uma mecânica que ramifica o enredo. Mara exige registro do payload original, do executado e da consequência.
- **Rewrite:** Mara confronta o Breaker por transformar rejeição de Decoder em prova aceita sob falha de validação. O canal expira antes do Architect; o recibo assinado permanece como prova e causa de responsabilização. A versão vigente não troca o Wasm do Core.
- **Epílogo:** credenciais suspensas; não romantizar seu prejuízo. A suspensão prepara sua recusa posterior de receber acesso restaurado ilegalmente.

# Arestas de caráter de Voss

Voss não é um fantasma onisciente nem santo ausente. Seus registros devem conter pelo menos um erro, um arquivo não resolvido e uma tentativa anterior de registrar danos operacionais do Escrow. A trilha permite que outro Breaker avance, mas não prova que Voss previu todas as ações futuras. A recusa REFUSED permanece sem explicação total; uma pista sugere que sua recusa também produziu custos humanos.

# Contrato de narrativa linear — uma história, nenhuma escolha moral

A Season 1 é uma sequência fixa de cenas e fatos. O jogador controla **como investigar os contratos e encontrar as vulnerabilidades**, mas não determina personalidade, vínculos, ética ou destino do Breaker. Não há respostas selecionáveis no Architect, ramos na Spire, medidor de confiança de Mara ou encerramentos alternativos.

**Atos canônicos:** o Breaker assume e depois libera o controle de Elias; registra a Ghost Key como evidência sob custódia técnica temporária; força o Archive a entrar em recuperação e depois interrompe o aumento de carga; desvia a manutenção legítima da Spire para obter acesso, explora uma validação falha em que Decoder REJECTED vira VossProof ACCEPTED, depois abre sessão forense ao desviar DiagnoseCore no timelock; Mara abre um canal limitado, assina o recibo que provoca sua suspensão e se desconecta antes do Architect. As consequências são mostradas sempre, pois são partes do enredo.

O Breaker Profile exibe o registro verificável desses acontecimentos, não score de moralidade, preferências do jogador ou variáveis de branch. A pergunta "Por que você continuou?" permanece sem menu e sem resposta correta. A classificação final é sempre QUALIFIED / PROVISIONAL.

# Matriz de pistas justas

Para revelações essenciais, três vestígios complementares: observação técnica, artefato do mundo e interpretação humana. Não precisam ser três missões nem hints automáticos.

- **Dinheiro em Escrow:** contract ID no ledger; eventos de recuperação; política de saque auditada por Mara.
- **Voss veio antes:** timestamps antigos; workspace de Voss; registro independente no Registry.
- **Observação ativa:** timestamp do player no Registry; evento de classificação do Oracle; atualização de Subject Path.
- **Architect não criou bugs:** diferenças entre datas de deploy; logs de manutenção legada; descoberta comparada de Voss.

# Regras de cena / antirrepetição

Uma cena tem **objetivo de personagem, resistência, virada verificável e consequência**. Cortar diálogos que apenas leem o terminal em voz alta. Variar sequência de apresentação: às vezes vestígio ambiental antes de contrato; às vezes confronto entre Mara e Breaker; às vezes uma ação feita para preservar provas; às vezes silêncio depois do exploit. Em cada Case, definir o que o player conclui **errado**, o que muda e que pergunta nova surge. Nem todo Case precisa de uma grande revelação; alternar intensidade.
Usar exposição em camadas: mission strip curto, evidências opcionais, diálogo em reação ao estado, debrief técnico **após** vencer. A fonte de verdade da narrativa é o estado do mundo, não o narrador.

# Critérios de teste narrativo

1. Um playtester consegue explicar por que o Case seguinte decorre do atual sem receber instruções externas?
2. Consegue diferenciar bug, exploit, prova e consequências?
3. Consegue dizer qual descoberta Mara trouxe independentemente?
4. Consegue reconstruir o destino dos fundos sem acreditar que Voss os gastou?
5. Recorda os atos do Breaker e seu custo quando o Architect faz a pergunta final?
6. Interpreta QUALIFIED/PROVISIONAL como **capacidade comprovada**, não ACCEPTED?
7. Identifica ao menos uma consequência humana que não seja morte ou perda abstrata?
8. Explica por que o Registry aparece no fallback e por que o Oracle "prevê" três saídas?
9. Os diálogos mostram conflito ou apenas descrevem o terminal?

# Leituras técnicas de roteiro utilizadas

- [John Yorke — Five-act structure](https://www.johnyorkestory.com/five-act-structure/)
- [John Yorke — How to tell successful stories](https://www.johnyorkestory.com/2015/06/how-to-tell-successful-stories/)
- [Kenn Adams / Story Spine](https://story.org/library/practice/story-spine)
- [GDC — What Happened Here? Environmental Storytelling](https://www.gdcvault.com/play/1012696/What-Happened-Here-Environmental)
- [GDC — Choice, Consequence and Complicity](https://www.gdcvault.com/play/1023346/Designing-for-Exploration-and-Choice)
- [GDC — Making Player Choices Feel like They Matter](https://www.gdcvault.com/play/1028017/Game-Narrative-Summit-Making-Player)
- [Failbetter — Narrative Snippets: Parsimony](https://www.failbettergames.com/news/narrative-snippets-parsimony-2)
- [The Alexandrian — Node-Based Scenario Design](https://thealexandrian.net/wordpress/7985/roleplaying-games/node-based-scenario-design-part-3-inverting-the-three-clue-rule)
- [inkle — Writing with ink](https://github.com/inkle/ink/blob/master/Documentation/WritingWithInk.md)

# Fechamento editorial da Season 1 — roteiro e QA

**Estado editorial: canon e novelização consolidados para implementação e leitura crítica.** As mudanças de dramaturgia e plausibilidade foram incorporadas às páginas correspondentes. **Não** significa que contratos, interfaces ou playtests tenham sido executados. Nenhuma decisão abaixo substitui o Act I ou altera o arco de Lumen/Moonlight.

## Checklist de cenas — mudança de valor

Em cada fase, exigir uma mudança de valor **observável**: o personagem não termina a cena exatamente com a mesma crença, poder, segurança ou responsabilidade. Este quadro traduz os cinco movimentos de Yorke e a noção de turning point e resolução descrita por Story Grid.

| Fase | Objetivo dramático | Reversão concreta | Valor que muda / consequência |
| Prólogo | Encontrar uma causa para o saldo zero | Transação aceita sem explicação causal | Certeza institucional → dúvida verificável |
| 01 — No Forced Entry | Demonstrar entrada sem chave | Gate aceita identidade como parâmetro, sem provar autoria | Segurança aparente → confiança vulnerável |
| 02 — Dead Man's Wallet | Obter registro de operador | Controle obtido por reinitialization; arquivo externo libera a pista | Investigação neutra → responsabilidade por impersonação, seguida de revogação explícita |
| 03 — Warehouse 17 | Recuperar Ghost Key | Transferência aceita sem autorização do dono; contestação humana | Sucesso técnico → dever de preservar o artefato em cadeia de custódia |
| 04 — Forgotten Floor | Localizar andar apagado | Entrada Persistent restaurada via transação e TTL; índice volta a reconhecer rota | Ausência aparente → memória recuperável; Mara ressalta que o protocolo não legitima o furto |
| Boss — Custodian | Atravessar o Core seguro | Dependências comprometidas autenticam operador inadequado | Integridade local → falha de confiança sistêmica; “WELCOME BACK” |
| 05 — Missing Investigator | Reconstruir voz de Voss | Decoder falha, Archive registra sucesso; Voss deixa hipótese refutada | Suspeito monolítico → investigador falível |
| 06 — Impossible Account | Entender valor absurdo | Conversão sem validação expõe a tabela de roteamento | Erro isolado → conexão material com Sector 13 |
| 07 — Sector 13 | Desmontar o index rebuild | DoS ativa fallback do indexador externo e revela Registry | Caçador → observado; o Breaker contém a pressão adicional após a prova |
| 08 — The Oracle | Antecipar três resultados | Prophecy previsível; classificação ocorre em outro módulo | Prever números → perceber seleção de pessoas; Mara reage ao Archive |
| 09 — Steal the Key | Entrar na Spire revogada | Payload reescrito usando autorização antiga | Auditoria autorizada → transgressão deliberada; equipe de manutenção sem abertura; Mara assina recibo verificável |
| 10 — Rewrite | Validar manifesto e expor erro Decoder/VossProof | Decoder rejeita, mas a prova de diagnóstico é aceita indevidamente | Explorar regras → poder de alterá-las sem legitimação; despedida do canal de Mara |
| Final — Architect | Reunir e testar todos os conhecimentos | Sessão forense aberta por payload desviado; verificador independente atesta prova, cronologia e Escrow | Qualificação comprovada → legitimidade ainda em aberto; perfil confronta três atos da investigação |

## Política de pistas: superfícies e caminhos

A *Three Clue Rule* é aplicada às conclusões essenciais; não obriga obrigatoriamente três pistas para cada trava linear. Evitar chokepoints em que só a fala de um NPC revela o próximo passo.

- **Vault:** (1) evento de abertura do Gate, (2) chamada RecoveryController, (3) recibo de Escrow e spend policy. O destino público pode ser visto cedo; o contexto moral é consolidado no final.
- **Warehouse / Floor 24:** (1) storage keys da Ghost Key, (2) referência em mapa técnico antigo, (3) ausência de demolição confirmada por Mara. A solução de TTL é demonstrada pela transação de restauração.
- **Sector 13:** (1) histórico de rebuild falho, (2) configuração do fallback e escopo de leitura externo, (3) timestamp ACTIVE do próprio jogador. Não armazenar plaintext secreto no ledger.
- **Voss e Architect:** (1) arquivos anteriores ao Vault, (2) Voss REFUSED no Registry, (3) timelock histórico e duas cronologias de deployment — bugs anteriores à Sequence. O validador/Observer permanece independente da autoridade do contrato vulnerável; não pressupor upgrade de Core. O jogador precisa cruzar os registros antes de ouvir a interpretação do Architect.
- **Mara:** (1) conflito Warehouse, (2) condição de uma hora na Spire, (3) recibo assinado após CASE TERMINATED; suspensão é consequência institucional observável.

## Contrato de cenas fixas e callbacks canônicos

- Os dez Cases e os dois Bosses possuem sequência única; concluir a condição técnica dispara a próxima cena estabelecida.
- Não existe `IDENTITY_TREATMENT`, `WAREHOUSE_EVIDENCE`, `ARCHIVE_RECOVERY`, `MARA_TRUST`, `BREAKER_MOTIVE` ou `ESCROW_PRE_DISCOVERED` como estado ramificável de narrativa.
- Os acontecimentos de revogação, custódia e limitação de carga são pós-condições **fixas** da história, preservadas no registro de eventos. Se precisarem de transação explícita, o runtime pode executá-la como parte da sequência canônica do level — nunca apresentá-la como menu de opções.
- Mara tem apenas uma progressão relacional e um conjunto fixo de falas. O preço que paga decorre de sua assinatura posterior ao encerramento do caso.
- A fala do Architect após a pergunta final não exige resposta do jogador. A próxima tela é sempre QUALIFIED / PROVISIONAL e acesso à Layer II.
- O jogador pode investigar artefatos públicos antecipadamente; o roteiro não precisa bloquear dados nem bifurcar o final para isso.

## Critérios de aceite para roteiro e runtime — ainda não executados

**A. Teste de mistério:** um jogador que não leu o canon explica de onde vieram os fundos, onde ficaram, por que a identidade de Elias aparece, por que Voss é REFUSED e por que o Architect **não** criou os bugs. O jogador deve poder chegar à explicação por investigação de artefatos, não por monólogo.

**B. Teste de linearidade:** percursos com métodos técnicos distintos e observação opcional de pistas devem levar às mesmas cenas, sem menus de conduta, falas alternativas por pontuação ou finais alternativos. O Profile deve apresentar os atos fixos do Breaker na mesma ordem.

**C. Teste de integridade:** alterar apenas a resposta da interface/Core para devolver `QUALIFIED` **não** deve bastar: o verificador independente deve atestar prova contextual, timelock maduro, payload diferente e sessão forense realmente aberta. A ausência das condições técnicas impede a conclusão. Não assumir alteração de Wasm.

**D. Teste de plausibilidade Stellar:** nenhum segredo de narrativa em plaintext on-chain; off-chain archives autenticados; falha de transação não emite evento de sucesso; TTL Persistent restaura com footprint, Temporary não; unbounded rebuild não depende de armazenar um único Vec maior que o limite do ledger.

**E. Teste emocional e literário:** leitores reconhecem o que Mara encontrou sozinha, entendem o custo da quarentena e sentem que a escolha de Mara na Spire resulta de conflito anterior. Uma leitura em voz alta não deve revelar diálogos que apenas repetem texto de terminal, nem usar o mesmo ritmo de descoberta em capítulos consecutivos.

**F. Teste de continuidade:** Sera Quill aparece como **uma** assinatura de notícia, no mesmo evento reproduzido por fontes diferentes; Breaker somente QUALIFIED/PROVISIONAL; Voss REFUSED; figura do pós-crédito não identificada; consequências de Season 2 e 3 não antecipadas.

**G. Teste de jogador especialista:** se alguém seguir a cadeia de transações por conta própria e descobrir o Escrow no prólogo, a Season deve continuar fazendo sentido. O que o final acrescenta é a prova da intenção, a impossibilidade de gasto pessoal e o custo humano.

## Registro de encerramento — o que está realmente concluído

- **Fechado no Notion:** sequência dramática única, investigação, pistas, personagens, novelização canônica, ações fixas de revogação/custódia/limitação de carga, limites entre ledger e arquivos externos, final Architect/Observer e documentação de QA.
- **Pendente fora do Notion narrativo:** criação/alteração de serviços de arquivo, runtime do jogo, implementação do verificador, cenas lineares de UI, testes determinísticos, testes com jogadores e eventual revisão de estilo de publicação.
- **Política editorial:** para Season 1, em qualquer conflito prevalece [BREAKER — Season 1 | FINAL NARRATIVE v1.4 — NARRATIVE LOCK](../narrative/breaker-season-1-final-narrative-v1-4-narrative-lock.md) (v1.4 NARRATIVE LOCK). História do Act I e Series Arc & Hidden Canon governam somente continuidade de trilogia onde não contradigam o roteiro S1. Não chamar especificação de comportamento implementado.

## Bibliografia efetivamente consultada para este fechamento

- [John Yorke — Five-act structure](https://www.johnyorkestory.com/five-act-structure/)
- [Story Grid — How to Write Scenes](https://storygrid.com/articles/scenes)
- [Story Grid — Cause and Effect](https://storygrid.com/articles/cause-and-effect)
- [The Alexandrian — Three Clue Rule](https://thealexandrian.net/wordpress/1101/roleplaying-games/three-clue-rule-part-3-the-three-clue-rule)
- [The Alexandrian — Inverting the Three Clue Rule](https://thealexandrian.net/creations/misc/node-design/node-design2.html)
- [Harvey Smith / Matthias Worch — Environmental Storytelling at GDC](https://www.worch.com/2010/03/11/gdc-2010/)
- [inkle — Writing with ink](https://github.com/inkle/ink/blob/master/Documentation/WritingWithInk.md)
- [Stellar — data visibility on ledger](https://developers.stellar.org/docs/build/smart-contracts/getting-started/storing-data)
- [Stellar — state archival semantics](https://developers.stellar.org/docs/learn/fundamentals/contract-development/storage/state-archival)
- [Stellar — storage strategies and entry limits](https://developers.stellar.org/docs/build/guides/storage/storage-strategies)
