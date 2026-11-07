---
notion_id: 4019c563-0425-8181-a4e2-ef561d8954a2
source: https://app.notion.com/p/4019c56304258181a4e2ef561d8954a2?pvs=204
title: "📖 00 — História Canônica do Act I"
exported_at: 2026-11-07
---

**APROVAÇÃO CANÔNICA — revisão dos 12 elos causais do Act I (2026-11-02).** Este documento define a continuidade da trilogia, mas para cenas, gameplay documentado e texto final da Season 1 prevalece [BREAKER — Season 1 | FINAL NARRATIVE v1.4 — NARRATIVE LOCK](../season-01/narrative/breaker-season-1-final-narrative-v1-4-narrative-lock.md) (v1.4 NARRATIVE LOCK). O usuário aprovou as recomendações editoriais do Writers' Room. Contratos, provas, modelos econômicos, slides e interfaces continuam sujeitos a implementação e QA. Preserva as três Seasons, dez Cases por Season, bosses, status e desfecho fixo. Referência de seleção: [Decisões Narrativas — Act I](../../../../databases/act-i-story-decisions.txt).

# Revisão canônica — 12 decisões aprovadas

## Season 1 — Meridian

**01 — Voss / motivação (A + B):** antes do incidente, Voss entregou três alertas/relatórios sobre fragilidades de infraestrutura, arquivados sem providência eficaz. Ele decide produzir uma anomalia incontornável acionando a rota AccessGate → RecoveryController → Meridian Recovery Escrow. Seus 2,4 milhões não podem ser sacados por ele; os pagamentos em quarentena prejudicam serviços de Lower Meridian. Sabia que a ação atingiria terceiros, mas subestimou a escala. **Voss não é absolvido pelo fato de ter sido ignorado.** As pistas entram em documentos do workspace de Voss (Case 05), danos de Warehouse 17 e prova da trilha Vault/Escrow no Architect. Os alertas antigos são evidência histórica, não justificativa moral.

**02 — Architect falível (A + C):** no Oracle, o **classificador de comportamento**, distinto do RNG explorado no challenge, registra uma expectativa sobre o comportamento do Breaker que não corresponde ao fato canônico observado; o modelo corrige sua previsão e expõe limites inferenciais. No final, deployment chronology e eventos históricos demonstram que as vulnerabilidades antecedem a Sequence. Architect as catalogou e encadeou, não as criou. O erro de previsão **não** depende de escolha ou final alternativo e não transforma o sistema em personagem onisciente.

**03 — Mara e recibo (A + C):** depois do CASE CLOSED, Mara vê aviso institucional de atribuição pessoal, assina o recibo e **assume explicitamente a cadeia de custódia** da evidência. O registro contém o identificador da credencial e hash. O epílogo associa a suspensão de credenciais a esse recibo, sem a Authority precisar espionar a conversa. Ela não aprova qualquer operação que o Breaker venha a fazer.

## Season 2 — Lumen

**04 — Bloqueio racional de Rhea (A + B):** no Liquidator, o Breaker observa uma capability emergencial sem escopo autorizado adequado e um relatório de risco com projeção plausível de custo de liquidez se a intervenção ocorrer. A informação está correta no domínio limitado do relatório, mas omite liquidações alimentadas por feeds inadequados e efeitos agregados sobre AMM/settlement. Bloquear Rhea é **decisão técnica defensável e incompleta**, não incompetência artificial.

**05 — Plano bloqueado de Rhea (A + B):** ela tentava uma única contenção emergencial com dois controles: quarentena de liquidações dependentes de price reports fora da política de freshness/confidence e limitação temporária do lote/throughput de liquidações por intervalo para não amplificar slippage em pools rasos. A autorização formal insuficiente é real. Breaker bloqueia; o Liquidator volta a liquidar e agrava a cascata. Os contadores 14 → 31 → 78 → 204, métricas de liquidez e settlement devem ser reproduzíveis em replays de **mesmo estado e seed**, variando somente a intervenção. **Depois**, Rhea isola um dos sete mercados em evento independente e Ilyan perde a posição. Nenhum dos dois eventos vira nova fase ou solução mágica.

**06 — Settlement com finalidade econômica (C):** durante The Cascade, uma parcela de **garantia operacional temporária** fica vinculada à contribuição do Breaker para a contenção e à manutenção dos settlements essenciais. O acordo/documento técnico estabelece titularidade, finalidade, condições de liberação e ausência de emissão fictícia. Ao concluir a contenção, Rhea executa a **devolução da parcela devida ao Breaker** por settlement confidencial legítima. Rhea é sender autorizado no fluxo de retorno; Breaker é recipient. Trata-se de obrigação operacional, não pagamento de amizade, armadilha, indenização improvisada ou transferência sem causa. Em t0 a policy permite a operação; o status DENIED é posterior. A operação e sua referência a Moonlight servem como pista para o início da Season 3.

## Season 3 — Moonlight

**07 — Full disclosure excepcional (A + B):** a associação atualmente DENIED, combinada com um **grafo de operações correlacionadas** identificado por metadados observáveis, aciona uma política emergencial de investigação de rede. First Witness aplica de boa-fé esse procedimento ampliado; suas fontes são reais, mas suas inferências são excessivas. A exigência de view authority geral ultrapassa o necessário para provar conformidade da settlement. No Final, a prova histórica mínima e as falhas nas inferências permitem que ele encerre a ordem mesmo diante de workflow automático de full disclosure.

**08 — Autoria da mudança para DENIED (B):** um operador institucional de compliance que segue procedimento legado aceita um pending admin tecnicamente executável apesar de haver cancelamento formal. A falha de governança permite reassumir autoridade para reclassificação; diante de alerta de risco pós-Lumen, ele aplica DENIED à associação **depois** da operação legítima. Ele pretendia cumprir política, não fabricar prova nem sabotar Rhea. Registrar timestamps de cancelamento, aceitação do pending, policy aplicada e alteração do status. Case 03 demonstra outra vulnerabilidade geral de profile, não a origem histórica do DENIED.

**09 — Por que compartilhar vínculo com Rhea (A + C):** a investigação identifica **dois identificadores aparentemente incongruentes** para o destinatário do retorno da garantia: conta operacional de Lumen e identidade/credencial institucional reconhecida na execução. Para construir a prova positiva de que o recipient era elegível na policy histórica, Breaker precisa fornecer a Rhea uma **atestação autenticada de vínculo**, vinculada apenas àquela settlement e à composição sender/recipient. O BREAKER OS explicita propósito, escopo de auditoria e risco residual de correlação. Rhea não recebe private key nem autorização para agir em nome dele; naquele momento usa o dado para ajudar sinceramente. Mais tarde, seu uso de conhecimento histórico em apuração separada rompe a finalidade e a confiança, não a criptografia.

**10 — MISSING + encontro (B + C):** Case 10 reduz a capacidade de rastrear a **trajetória atual** do Breaker. Ele pode entrar fisicamente numa sessão controlada da Witness Spire e autenticar participação por **credential/proof limitada à settlement**. First Witness conhece a presença e identidade processual naquela sessão, mas não reconstrói como ele chegou ou por onde sairá. MISSING não significa invisibilidade naquele instante nem eliminação de eventos antigos; após a sessão, a rota atual continua insuficientemente correlacionável.

**11 — Handoff do sender witness (A):** antes de se separarem no Case 10, Rhea entrega ao Breaker um pacote de prova autenticado, ligado ao commitment da settlement e public inputs da policy de t0. Não entrega chave de assinatura genérica. Breaker leva o pacote à Spire; não há necessidade de reencontro ou comunicação rastreável depois da separação. O gesto é sincero; Rhea ainda não decidiu divulgar nada sobre Lumen.

**12 — Proteção de SOURCE E.V. (B):** Sera compartilha com Breaker documentos jornalísticos autenticados, com conteúdo utilizável como evidência e origem apresentada ao player apenas como SOURCE E.V. O **envelope de proveniência** no repositório seguro da reportagem contém metadados que poderiam ligar a fonte a Eli Venn. A ordem excessiva da Witness Spire alcançaria esse envelope ao solicitar todo o dossiê associado ao Breaker. A **prova mínima** no Final demonstra as claims necessárias sem revelar identidade da fonte, montante, outras contas ou visão irrestrita. Os dados identificadores da fonte não estão publicados em ledger/storage público.

# Causação, sequência e consequências — regras obrigatórias

1. **Meridian:** alertas arquivados → incidente deliberado de Voss com dano → investigação e prova independente do Architect → recibo consciente de Mara → suspensão posterior.
2. **Lumen:** riscos locais acumulados → intervenção de Rhea com vulnerabilidade de escopo + prognóstico parcial → bloqueio racional → efeito sistêmico ruim → isolamento posterior distinto → contenção parcial na Cascade → devolução de garantia com sender Rhea e recipient Breaker.
3. **Moonlight:** settlement válida em t0 → operador de compliance tecnicamente retoma autoridade cancelada → DENIED e alerta de rede → Witness Order excessiva → provas e confiança compartilhadas → entrega do sender witness e separação → MISSING operacional → sessão limitada e vitória real → **somente depois** investigação independente de Lumen recebe atribuição assinada de Rhea, causando suspensão de credencial intercity, sem reabrir a absolvição de Moonlight.
4. **Sem coincidências convenientes:** preparar cenas por registros observáveis, documentos assinados, mudança de estados e atos dos personagens. No mínimo as conclusões centrais têm pistas de origem independente; não sobrecarregar slides com explicações.
5. **Sem branching moral:** o usuário aprovou **uma versão editorial única** para cada lacuna; A/B/C no Notion não são escolhas do jogador.
6. **Técnica a comprovar:** garantias, autorização, confidential transfer, binding da proof, ameaça de metadados, scores de observação e replays econômicos são requisitos de design, **não alegações de código já implementado**.

# Leituras para produção

[06 — Writers' Room: Metodologias & Avaliação do Ato I](06-writers-room-metodologias-avaliacao-do-ato-i.md) · [Decisões Narrativas — Act I](../../../../databases/act-i-story-decisions.txt) · [07 — O Sétimo | Rhea × Breaker — Virada canônica do Act I](../season-03/world/07-o-setimo-rhea-breaker-virada-canonica-do-act-i.md).

# ACT I — História Canônica

**Espinha dramática:** QUEBRAR PARA SABER → QUEBRAR PARA SALVAR → SABER QUANDO NÃO QUEBRAR.

# Prólogo da trilogia

BREAKER começa em **Meridian**, uma cidade que trata contratos como leis naturais.

O primeiro caso parece um roubo impossível.

Na verdade, é o início de uma trilha deixada por **Aren Voss**, um Breaker que descobriu que a infraestrutura de Meridian estava cheia de sistemas executando regras frágeis como se fossem verdades.

Voss não criou as falhas.

Ele criou um sinal grande demais para ser ignorado.

> **“Ele não roubou o Vault. Ele obrigou Meridian a olhar para ele.”**

# Season 1 — Meridian / CODE

**Forma narrativa definitiva:** a Season 1 conta uma história linear e única, sem escolhas morais do jogador, diálogo selecionável, bifurcações de relacionamento ou finais alternativos. Os desafios permitem resolver vulnerabilidades; as ações narrativas do Breaker são fixas (revoga o controle de Elias, preserva e documenta Ghost Key, contém pressão adicional sobre Sector 13). Mara possui um arco único e assina o recibo que desencadeia sua suspensão. O Architect pergunta por que o Breaker continuou, mas não apresenta respostas. O resultado é invariavelmente `QUALIFIED / PROVISIONAL`; `ACCEPTED` pertence ao arco posterior e não é desbloqueado por escolha do player.

**Continuidade consolidada (revisão Season 1):** o incidente do Vault combina Access Gate vulnerável, rota de recuperação que aceita o estado do gate e destino financeiro exclusivamente institucional em Meridian Recovery Escrow. A identidade legada do morto integra a telemetria de operação, não a custódia do montante. Voss inicia a anomalia como mensagem após já ter percorrido a Sequence, mas a quarentena dos recursos provoca atrasos para terceiros. Mara encontra contestação de titularidade no Warehouse, contribui com prova documental no Custodian e sofre desgaste na relação com o Breaker antes de arriscar suas credenciais. Em Sector 13, o fallback de leitura explica a visibilidade do Registry. O Oracle possui motores distintos de pseudoaleatoriedade e classificação. O clímax exige evidência independente do testemunho do Architect; o Breaker encerra QUALIFIED/PROVISIONAL, não ACCEPTED. No funcionamento vigente da Season 1, uma sessão forense é aberta por desvio da operação DiagnoseCore no timelock; o verificador/Observer independente confirma a prova e emite o status. Não há substituição de ArchitectCore/Wasm nesta revisão. Os registros privados de Elias Var e do Registry acessados durante a narrativa são arquivos de serviço **off-chain**, não storage Soroban invisível. A suspensão de Mara é rastreável ao recibo de evidência que ela assinou após o fechamento do caso; a Authority não precisa espionar seu canal. Na Spire, o heist desvia uma manutenção legitimamente agendada, deixando uma equipe sem a abertura esperada. Mara exige que essa consequência também seja preservada. A janela privada de uma hora é um relógio diegético, com beats narrativos fixos, e expira ao fim de Rewrite; Mara não conversa ao vivo no Architect. Em Rewrite, uma rejeição do Decoder é registrada incorretamente como VossProof válida. Essa violação de confiança prepara o acesso à sessão forense do Architect; não há troca de Wasm nem versão do executable nesta etapa. O final reconstrói as provas por deployment chronology, Registry e trilha Vault → Recovery Escrow antes de dar espaço à fala do Observer. A prova de que Voss não podia gastar os fundos não justifica os custos humanos do incidente.

Referência de pistas e revelações: [ARQUIVO — 12 Matriz de Revelações (revisão antiga)](../season-01/archive/arquivo-12-matriz-de-revelacoes-revisao-antiga.md).

O jogador começa como investigador.

Caso a caso, deixa de apenas observar falhas e passa a usá-las para avançar.

Mara Vale é a âncora humana e institucional.

Ela começa valorizando os procedimentos institucionais, a rastreabilidade e a cadeia de custódia; não é ingênua e NÃO confunde automaticamente sucesso técnico com legitimidade. Ao encontrar a contestação civil em Warehouse 17, ela exige uma prova que complemente o ledger; na Spire, quando a Authority manda encerrar o caso, decide preservar a evidência mesmo sabendo que isso pode custar sua carreira.

Sua transformação é **cumprimento das regras como proteção → responsabilidade de preservar provas quando as regras se tornam obstáculo**, sem perder competência nem virar cúmplice irrestrita do Breaker.

> **“Você tem uma hora.”**

Essa decisão custa suas credenciais.

## Sera Quill já existe

O jogador ainda não conhece Sera.

Ela aparece uma única vez, discretamente, em um feed público:

> **2,4 MILHÕES MOVIMENTADOS — NENHUMA INVASÃO DETECTADA** — *Sera Quill, Network Wire*

Nada de encontro, diálogo ou subplot.

É apenas um nome plantado no mundo.

## Architect

**Camada vigente de gameplay — Season 1 FINAL NARRATIVE v1.4:** os arquivos históricos Warehouse 17, Floor 24 e Sector 13 repetem um rodapé de proveniência, mas não guardam bytes secretos da instância final. A prova contextual da instância é derivada de dados públicos e validada por commitment; o manifesto histórico de Voss é autenticado por assinatura Ed25519, sem conceder autoridade administrativa. No Case 10, a rejeição do Decoder é registrada indevidamente como VossProof aceita; no Architect, uma operação de diagnóstico previamente autorizada tem o payload desviado para `OpenForensicSession(player)` após timelock. A prova histórica da responsabilidade de Voss pelo Vault é demonstrada por signatário da operação + registro institucional assinado + relação causal até o Escrow. NÃO há substituição de Wasm do ArchitectCore nesta versão; o motivo de Voss ter recusado continua oculto. Especificação: [VOSS PROTOCOL — Níveis 11/12 | Especificação vigente](../season-01/cases/voss-protocol-niveis-11-12-especificacao-vigente.md).

No fim, a comparação de deploys, eventos legados e registros da Sequence permite ao Breaker provar que o Architect não construiu os bugs; a voz apenas confirma o que os artefatos mostram.

**Meridian já estava quebrada.**

Ele conectou sistemas frágeis para encontrar pessoas capazes de enxergar além da camada oficial.

Voss chegou ao Architect anos antes.

Voss recusou.

Rhea aceitou.

O jogador ainda não fez nenhuma das duas coisas.

SEQUENCE 01 COMPLETE
SUBJECT: QUALIFIED
STATUS: PROVISIONAL
ACCESS GRANTED — LAYER II

**QUALIFIED não é ACCEPTED.**

O jogador provou que consegue quebrar sistemas.

Ainda não provou o que fará quando quebrar uma regra for uma decisão moral.

# Voss não é santo

A recusa de Voss não é apresentada como pureza moral.

Rhea sabe que, em algum momento anterior, Voss recusou uma intervenção e essa recusa também teve custo humano.

O Act I não revela o incidente.

Apenas estabelece:

> **REFUSED também é uma escolha com consequências.**

# Ponte — Meridian → Lumen

Sector 13 mostrou:

████████ — ACCEPTED

Depois da Sequence:

LAYER II ANOMALY
LOCATION: LUMEN
BREAKER SIGNATURE: ████████
STATUS: ACCEPTED

O Breaker vai a Lumen porque quer responder:

> **“Por que alguém aceitou exatamente aquilo que Voss recusou?”**

No pós-crédito, Rhea observa o novo Breaker.

> **“Então ele encontrou outro.”**

# Season 2 — Lumen / VALUE

Lumen começa a quebrar sem parecer quebrada.

Uma posição segura é liquidada.

Pools perdem profundidade.

Vaults reportam ativos que não possuem.

Debt cresce de forma incorreta.

Oracles divergem.

Rhea aparece próxima aos incidentes.

O Breaker chega como **QUALIFIED / PROVISIONAL** e a trata como inimiga.

## Rhea continua inimiga

O reveal não transforma Rhea em aliada.

O Breaker descobre que ela não criou a crise.

Mas continua discordando profundamente dos métodos dela.

Rhea acredita que, quando o sistema está falhando, esperar autorização pode ser irresponsável.

O Breaker acredita que capacidade técnica não dá a ela o direito de escolher quem paga o custo.

## Nenhuma vulnerabilidade explica Lumen

Alguns protocolos têm bugs.

Outros têm configurações perigosas.

Outros executam corretamente com dados ruins.

Outros confiam em propriedades que sistemas vizinhos nunca garantiram.

A crise emerge das dependências.

Season 1 ensinou a encontrar o bug.

Season 2 ensina:

> **encontrar o bug não significa compreender o sistema.**

## O custo humano

**Ilyan Marr** perde sua posição quando Rhea isola um segmento menor para impedir contágio.

**Nia Kade** aparece inicialmente em uma matéria da Network Wire sobre atrasos de payroll.

## Sera entra na história sem entrar na equipe

Sera investiga Lumen.

Ela percebe fragilidades reais.

Publica uma matéria correta cedo demais.

A publicação acelera withdrawals e comportamento defensivo.

Rhea confronta Sera.

Sera:

> **“As pessoas tinham o direito de saber.”**

Rhea:

> **“E agora sabem enquanto correm para a saída.”**

Sera aprende:

> **informação verdadeira também é uma intervenção.**

## Mara em Lumen

Mara tenta recuperar suas credenciais pelo processo oficial.

O Breaker encontra uma forma de restaurar seu acesso por fora.

Breaker:

> “Eu consigo devolver seu acesso.”

Mara:

> **“É exatamente por isso que você não deveria.”**

Depois:

> **“Quebrar o procedimento foi uma escolha minha. O custo foi meu.”**

> **“Se você vai fazer o mesmo, descubra antes quem vai pagar o custo da sua escolha.”**

## Rhea paga um preço

Rhea salva a maior parte de um conjunto de mercados ao isolar um segmento menor.

Breaker:

> **“Você salvou seis mercados.”**

Rhea:

> **“Sim.”**

Breaker:

> **“E matou o sétimo.”**

Rhea:

> **“Sim.”**

Ela assume a decisão.

Ilyan entende por que ela fez.

Não perdoa.

## Final — The Cascade

Breaker e Rhea enfrentam a Cascade simultaneamente.

Não como dupla.

Cada um executa seu próprio plano.

As ações se tornam interdependentes.

Existe cooperação tática sem confiança.

Rhea:

> **“Não confunda alinhamento com confiança.”**

Para impedir o colapso, o Breaker usa Emergency Authority fora do caminho normal.

Architect:

BREAKER STATUS UPDATE
QUALIFIED → ACCEPTED

O jogador nunca disse “eu aceito”.

O Architect interpretou seu comportamento.

Rhea:

> **“Agora você entende por que eu aceitei.”**

O Breaker entende.

Ainda não concorda.

# Ilyan no final

A recuperação exige market makers independentes.

O Breaker procura Ilyan.

Ilyan:

> **“Ela estava certa.”**

Breaker:

> “Então nos ajude.”

Ilyan:

> **“Eu disse que ela estava certa. Não disse que perdoei.”**

Ele ajuda porque Lumen importa mais do que a própria raiva.

# Ponte — Lumen → Moonlight

Durante a crise, Rhea usa mecanismos confidenciais para proteger posições vulneráveis de exploração pública.

POLICY: VALID
AMOUNT: HIDDEN
DESTINATION: MOONLIGHT

Rhea:

> **“Você queria saber o que o Architect não consegue ver.”**

Uma revisão institucional sobre **quem executou a intervenção emergencial em Lumen** continua aberta. O ledger prova as transações, mas não vincula sozinho a conta operacional à credencial civil do Breaker. Essa distinção será explorada em Moonlight; Rhea **ainda não tomou** qualquer decisão de revelar o vínculo.

O Breaker entra em Moonlight como **ACCEPTED**.

Agora a mesma lógica de exceção necessária será usada contra ele.

# Season 3 — Moonlight / INFORMATION

Na entrada:

PRIVATE SETTLEMENT DETECTED
RECIPIENT: BREAKER
AMOUNT: HIDDEN
ASSOCIATION: DENIED
PROOF: VALID

A Witness Spire exige disclosure amplo.

First Witness:

> **“Precisamos da sua chave de visualização.”**

Breaker:

> “Para essa transação?”

First Witness:

> **“Para tudo.”**

Ele recusa.

O investigador vira investigado.

# Cooperação forçada com Rhea

Rhea também está presa ao caso.

A prova necessária está dividida:

SENDER WITNESS: RHEA
RECIPIENT WITNESS: BREAKER

Nenhum dos dois consegue limpar o próprio nome sozinho sem revelar muito mais do que deveria.

Rhea:

> **“Você não consegue limpar seu nome sem mim.”**

Breaker:

> “E você não consegue limpar o seu sem mim.”

Rhea:

> **“Eu sei.”**

Eles continuam inimigos.

Mas precisam trabalhar juntos.

A relação evolui para **confiança real conquistada**, não amizade automática: Rhea oferece prova voluntária e assume risco próprio; Breaker compartilha um vínculo institucional de proveniência em escopo limitado e a protege. Nenhum dos dois planeja trair o outro. A discordância ideológica continua.

# Sera em Moonlight

O Breaker finalmente conhece Sera Quill pessoalmente no Blind Quarter.

O nome já é familiar desde Meridian.

Agora ele entende por que uma jornalista investigativa depende de privacy.

Uma de suas fontes aparece apenas como:

SOURCE: E.V.

# First Witness

First Witness não é vilão.

Antes do Breaker, participou de um caso em que selective disclosure limitado permitiu investigar criminosos sem expor usuários inocentes.

Por isso acredita na Spire.

Quando o Breaker diz que disclosure amplo é excessivo, First Witness pensa que está ouvindo uma desculpa que já ouviu antes.

# A perseguição

Os Witnesses reconstruem progressivamente:

- presença;
- distrito;
- addresses;
- timing;
- commitments;
- association sets;
- relações inferidas.

O Breaker aprende que criptografia pode proteger conteúdo sem impedir inferência.

# Become Missing

Antes do Final:

ARCHITECT
SUBJECT: BREAKER
OBSERVATION CONFIDENCE: 81%
54%
19%
...
SIGNAL LOST

STATUS: MISSING

Isso permite chegar à Witness Spire.

# Rhea quer quebrar demais

Ao descobrir a extensão do mecanismo de disclosure da Spire, Rhea considera destruí-lo permanentemente.

Breaker impede.

Breaker:

> **“Você consegue quebrar isso. Não significa que deve.”**

É a inversão de Lumen.

Rhea não concorda completamente.

Mas para.

# Final — The Witness Spire

O Breaker poderia abrir o Veil inteiro.

Isso limparia seu nome.

Também revelaria fontes de Sera.

Entre elas:

SOURCE E.V. → ELI VENN

A missão:

> **PROVE SUA INOCÊNCIA SEM REVELAR A CIDADE.**

Resultado:

CLAIM: ORIGINAL SETTLEMENT COMPLIED AT EXECUTION
ASSOCIATION CHANGE: SUBSEQUENT / REVOKED AUTHORITY
PROOF PACKAGE: VALID
DISCLOSURE: CLAIMS AND NECESSARY ANCHORS ONLY

O sistema ainda exige:

FULL DISCLOSURE: REQUIRED

First Witness revisa a prova.

> **“A prova é suficiente.”**

WITNESS ORDER: CLOSED
FULL DISCLOSURE: DENIED

Mara abriu uma porta que a instituição mandou fechar.

First Witness fecha uma porta que a instituição mandou abrir.

# Fim do Act I — O Sétimo

O Breaker vence o julgamento da Witness Spire. First Witness encerra a ordem de Moonlight e preserva fontes de Sera. A vitória e a prova mínima continuam válidas.

**Só depois**, Rhea recebe a exigência final de uma apuração separada sobre a intervenção emergencial do Breaker em Lumen. Ela tenta limitar a investigação por vias não nominativas, mas escolhe entregar **uma atribuição individual verdadeira**, assinada, vinculando a conta operacional histórica de Lumen à credencial intercity que o Breaker ainda possui. Não consulta o Breaker. Não havia arquitetado isso desde o começo; confiava nele de verdade e agora decide que ele é o custo aceitável para evitar correlação de muitos terceiros.

MOONLIGHT CASE: CLOSED
LUMEN ATTRIBUTION: VERIFIED
SOURCE: RHEA KESTREL
INTERCITY OPERATOR ACCESS: SUSPENDED PENDING REVIEW

A medida afeta credencial institucional de mobilidade/serviços, **não wallet, saldo, transações públicas ou um veredito penal**. Breaker perde acesso e confiança, ficando impedido de voltar facilmente à vida anterior. “Dessa vez o sétimo fui eu.” A traição é decisão de disclosure, não assinatura roubada nem prova falsificada.

RESTORE OBSERVABILITY: NO

**Decisão canônica do protagonista, não um menu interativo YES/NO.**

STATUS: MISSING

O Breaker escolhe ficar MISSING para continuar livre, mesmo que uma ação histórica tenha sido atribuída. O Architect perdeu correlação de sua trajetória presente, não toda memória do passado.

A transformação do Act I:

**Season 1 — QUEBRAR PARA SABER.**
**Season 2 — QUEBRAR PARA SALVAR.**
**Season 3 — SABER QUANDO NÃO QUEBRAR.**

Última pista:

HISTORICAL TRACE AVAILABLE
SOURCE: HORIZON

Se Voss também aprendeu a desaparecer do presente, o próximo caminho é reconstruí-lo pelo passado.
