---
notion_id: 40d9c563-0425-81bf-886c-fc339d730fd1
source: https://app.notion.com/p/40d9c563042581bf886cfc339d730fd1?pvs=204
title: "📕 BREAKER — Season 1 | FINAL NARRATIVE v1.4 — NARRATIVE LOCK"
exported_at: 2026-11-07
---

**FONTE ÚNICA DE VERDADE — SEASON 1 / FINAL NARRATIVE v1.4 — NARRATIVE LOCK (EDITORIAL)**

A partir desta versão, decisões narrativas e mudanças futuras devem ser registradas e integradas NESTA página. Páginas anteriores e fichas antigas são histórico/referência técnica, não roteiros concorrentes. A v1.1 refinou personagens e ritmo; a v1.2 fixou a copy de 51 slots; a v1.3 alinhou 04/06/Rewrite/Architect à revisão técnica; a **v1.4 congela editorialmente a autoria de Voss** com pistas no Prólogo, Case 01, Case 05 e payoff verificável no Architect. **Roteiro fechado para novas mudanças criativas. Release NÃO certificado:** fixtures, cadeia de assinaturas, contratos, UI e playtest ainda precisam ser testados.

# 1. Contrato criativo imutável

**Título:** BREAKER — Season 01: The First Layer. **Gênero:** thriller investigativo cyberpunk com desafios técnicos reais de contratos Soroban. **Local:** Meridian. **Tese:** execução não equivale a autorização; autorização não equivale a legitimidade.

A história é linear: sem escolhas morais, sem diálogos ramificados, sem múltiplos finais e sem score ético. Os hacks são necessários para progredir; o jogador só avança quando o verificador técnico independente comprova a condição de vitória. Slides mostram situação, personagem, evidência e consequência, sem antecipar a vulnerabilidade. O Breach Report explica a falha e a correção apenas após o sucesso. A Evidence Locker persiste artefatos consultáveis. Não atribuir segredos criptográficos ao ledger público.

**Personagens:** Breaker — investigador competente cuja falha é confundir capacidade com direito; Mara Vale — investigadora institucional, guardiã da cadeia de custódia e da dimensão humana; Aren Voss — antigo investigador que deixou três avisos arquivados, provocou o incidente e foi REFUSED; Authority — instituição que reage ao custo auditável da investigação; Architect — classificador/organizador falível de uma Sequence de falhas preexistentes, não criador delas; Lumen — observador reservado ao pós-créditos.

**Verdade fixa:** os 2.400.000 do Vault foram encaminhados para Meridian Recovery Escrow, não para carteira pessoal de Voss nem para Elias Var. Voss iniciou o incidente para expor falhas após três alertas arquivados, sem controle pessoal de saque, mas causou quarentena de fundos operacionais e atrasos de serviços em Lower Meridian. Não absolver Voss. Elias Var está morto e sua identidade legada é explorada no Case 02, não recebe o dinheiro. Voss foi REFUSED; há outro ACCEPTED oculto; jogador termina QUALIFIED / PROVISIONAL, nunca ACCEPTED. O motivo de Voss recusar fica para depois.

# 2. Arco dramático e ritmo

**Movimento I — Fissura:** Prólogo, Cases 01–02. Breaker acredita que um crime deve ter uma explicação técnica; descobre que sistemas aceitam atos sem legitimidade.

**Movimento II — Cidade enterrada:** Cases 03–04, Custodian. Provas civis de Mara e memória legada revelam uma infraestrutura esquecida; a confiança profissional cresce.

**Movimento III — O investigador anterior:** Cases 05–07. Voss deixou alertas, erros e consequências; a investigação revela PLAYER ACTIVE e passa a incluir o próprio Breaker.

**Movimento IV — Perda do mandato:** Cases 08–09. O Oracle falha ao prever o comportamento do jogador; a Authority restringe e revoga o caso. Mara decide preservar evidência sob responsabilidade pessoal.

**Movimento V — Reescrever o que conta como prova:** Case 10, Architect, epílogo. O Breaker demonstra que uma rejeição pode ser registrada como sucesso e que uma operação autorizada de diagnóstico pode ser desviada para abrir sessão forense. Ele não troca o Wasm do Architect nesta versão técnica documentada. Ao reconstruir o Vault, é confrontado com os custos de seus atos.

**Escada de revelações:** falha isolada → padrão histórico → Voss e seus alertas → jogador monitorado → observador falível → investigação sem mandato → poder de reescrever → Vault/Escrow → custo moral → Layer II.

# 3. Roteiro definitivo por etapa

## 00 — Prologue: The Impossible Theft

**Entrada:** notícia da saída de 2.400.000 do Vault, sem invasão física, assinada discretamente por Sera Quill na Network Wire (única aparição dela na Season 1). Meridian confia no selo de execução. Breaker recebe mandato de auditoria; Mara preserva o registro do incidente e separa fato técnico de conclusão institucional. Mara acredita na importância do procedimento e da custódia, mas já sabe que aceite técnico não prova legitimidade.

**Plantio obrigatório da prova:** o dossiê inicial disponibiliza `{{vault_trigger_tx_hash}}` e a referência a `{{gate_event_id}}` como objetos públicos consultáveis. A interface inicial destaca apenas a transação aceita e a porta intacta; quem inspeciona XDR/eventos pode observar o endereço do signatário antes do fim, mas não recebe um rótulo “Voss”. Não ocultar de modo falso algo que está publicamente na transação.

**Montagem:** Vault intacto → `TRANSACTION: ACCEPTED` → `NO FORCED ENTRY`; pausa. Breaker: “Aceito pelo sistema não significa explicado.” Mara: “Guarde o identificador original. Todo resumo pode perder uma parte da história.” Não explicar a falha, não nomear Voss, não revelar o Escrow na UI padrão.

**Saída:** evento de Gate aponta ao Case 01. **Mudança:** a execução deixa de significar legitimidade. **Emoção:** intriga com uma pista auditável desde o começo.

## 01 — No Forced Entry

**Hipótese:** alguém utilizou uma credencial legítima para abrir a rota de serviço. **Desafio:** o AccessGate aceita `Address` como argumento sem exigir corretamente `require_auth()` do titular; exploração controlada produz GateOpen. **Prova:** uma operação aceita não demonstra autorização do proprietário.

**Plantio de autoria sem spoiler:** guardar na Evidence Locker duas identidades distintas: `OWNER ARGUMENT` (endereço apresentado à função, NÃO autentica o titular) e `TX AUTHENTICATED SOURCE` (identidade verificável do signatário da transação histórica, se o envelope corresponder à chamada). O resultado da exploração feita pelo jogador é transação de teste SEPARADA e jamais prova que ele provocou a transferência histórica. Se houve relayer, só aceitar atribuição por uma assinatura/contexto comprovadamente vinculado à operação, não pela simples fee-payer.

**Encerramento em telas:** `TRANSACTION ACCEPTED / GATE OPEN` seguido de anotação forense `OWNER AUTHORIZATION: NOT PROVEN`. Mara: “O registro diz que entrou. Não diz quem tinha direito.” Um vestígio de operador legado aponta Elias Var, sem colocá-lo como beneficiário dos recursos.

**Saída:** investigar identidade de Elias e trilha W17. **Mudança:** o jogador aprende a não confundir argumento, signatário e autoridade. **Emoção:** vitória técnica e suspeita.

## 02 — The Dead Man's Wallet

**Hipótese:** Elias operou o acesso. **Virada:** Elias está morto; reinitialization permite apropriar-se de um controller de identidade e abrir registro externo legado W17. Mostrar prova de controle temporário, depois a liberação explícita do controller; não tratar a apropriação como eticamente neutra.

**Beat:** “IDENTITY VERIFIED” seguido de “SUBJECT DECEASED”. **Saída:** Warehouse 17. **Mudança:** o Breaker vê que provar uma falha exige assumir um poder que não lhe pertence. **Emoção:** desconforto inicial.

## 03 — Warehouse 17

**Hipótese:** um imóvel foi transferido por autorização legítima. **Desafio:** transferência indevida produz Ghost Key e cadeia de custódia irregular. Mara apresenta contestação civil e a perspectiva de quem perdeu acesso ao imóvel; o ledger sozinho não resolve a titularidade.

**Mini-cena de vínculo — sem sentimentalismo:** o sistema encerra o hack como sucesso; em vez de uma celebração, Mara sobrepõe uma contestação civil datada e o registro de quem perdeu acesso ao imóvel. Breaker: “O contrato mostra quem recebeu. Não mostra de quem era.” Mara: “Agora temos as duas provas.” A frase se torna um callback de confiança: técnica e consequência humana são necessárias. O jogador tem acesso aos dois artefatos na Evidence Locker. **Beat institucional:** primeiro questionamento formal da custódia da Ghost Key, preservado no processo administrativo. **Saída:** vestígio de Floor 24. **Mudança:** Breaker passa a levar as provas humanas de Mara tão a sério quanto o ledger. **Emoção:** ambiguidade, não euforia.

## 04 — The Forgotten Floor

**Pergunta dramática:** Floor 24 foi demolido ou sumiu apenas dos sistemas modernos? O elevador e a planta exibem 01–23; Mara não encontra ordem de demolição. A Ghost Key indica uma storage key legada, mas não abre uma porta por magia.

**Desafio técnico canônico:** diagnosticar uma entrada `Persistent` arquivada por expiração de TTL, restaurá-la pelo fluxo de footprint/restore adequado e elevar o TTL acima do limiar do challenge. O indexador moderno volta a reconhecer a rota somente após o sucesso verificável; não alegar que `get()` lê estado arquivado sozinho, nem que Temporary expirado é restaurável. A recuperação de disponibilidade não é bypass de autorização.

**Consequência e mise-en-scène:** após a prova, a planta oficial permanece na tela enquanto o índice restaurado sobrepõe o número 24. A infraestrutura física sempre existiu; o cadastro moderno deixou de apontar para ela. Mara: “Sem registro de demolição. Só um registro que deixaram expirar.” A descoberta é a entrada para uma rede de sistemas legados chamada First Layer, não a First Layer inteira.

**Objeto de memória:** Evidence Locker preserva `F24 / ARCHIVED ENTRY`, origem da storage key, prova de restauração e o rodapé recorrente `ARCHIVE: LEGACY / RETENTION: OPEN`. Esse rodapé conecta documentos antigos sem dizer “fragmento 2/3”. O arquivo histórico contém contexto narrativo; NÃO os bytes criptográficos da instância final do Voss Protocol, que são derivados publicamente do contexto final.

**Saída:** `CUSTODIAN ONLINE / IDENTITY UNKNOWN`. **Mudança:** uma ausência na interface não é ausência na cidade. **Emoção:** assombro investigativo com uma prova recuperável, não sala secreta arbitrária.

## MID BOSS — The Custodian

**Desafio:** núcleo aparentemente seguro confia em dependências comprometidas; usar falhas já demonstradas para atravessar custódia. **Beat:** “WELCOME BACK” indica expectativa de um operador, não prova de que o jogador esteve ali. Um log de auditoria aparentemente genérico pisca “SUBJECT STATUS: MONITORING”; a interface ainda não identifica qual sujeito ou quem registra o evento. A imagem não revela “PLAYER: ACTIVE” nem menciona o Architect. É o primeiro prenúncio visual inequívoco de observação, inteligível apenas retrospectivamente.

**Revelação:** estação ligada a Voss. **Saída:** procurar o investigador ausente. **Mudança:** os bugs convergem para uma história anterior. **Emoção:** assombro.

## 05 — The Missing Investigator

**Hipótese:** Voss teria planejado todas as falhas com precisão. **Descobertas:** três avisos protocolados antes do incidente, uma hipótese técnica posteriormente refutada em Sector 13 e documentação de custos da quarentena em Lower Meridian. Mara insiste em verificar fontes independentes.

**Nova pista de identidade — aprovada para narrativa:** a estação arquivada contém referência ao `VOSS OPERATIONAL KEY REGISTRATION` emitido por registro institucional anterior ao incidente, com `subject: AREN VOSS`, `operational_account: {{voss_operational_account}}`, `valid_from`, `valid_until` (se houver), `attestor`, assinatura do emissor e `{{voss_key_record_id}}`. A chave é um identificador público, não um segredo. O registro prova vínculo histórico de controle durante sua validade, desde que a assinatura do emissor e a janela temporal sejam verificadas. O manifesto Ed25519 de diagnóstico assinado por Voss pode corroborar identidade histórica, mas sua assinatura, isoladamente, NÃO atribui uma operação no Vault à mesma chave.

**Montagem:** primeiro `WARNING ARCHIVED` três vezes com datas anteriores ao Vault; depois uma gravação em que Voss apresenta hipótese equivocada sobre acesso externo a um registro ainda não identificado. Entre documentos secundários, mostrar `OPERATIONAL KEY RECORD — ARCHIVED / SIGNATURE AVAILABLE` sem confrontar essa conta automaticamente com a transação do Vault. Quem examina os dois arquivos por conta própria pode descobrir a coincidência mais cedo; não alterar final ou diálogos por isso. Mara: “Ele avisou antes. Isso não prova que estava certo sobre tudo.”

**Motivação e limite:** uma anotação de escalada institucional anterior ao incidente pode mencionar a alternativa `recovery quarantine` como ação extrema para forçar revisão, vinculada aos mesmos alertas, mas não deve ser tratada como absolvição ou confissão retrospectiva. A prova de autoria resulta de comparar chave e transação no final; o motivo emerge de avisos, plano prévio, rota institucional e consequências.

**Saída:** conta energética legada marcada `IMPOSSIBLE`. **Mudança:** Voss era falível e sabia dos riscos, mas suas decisões tiveram custo civil. **Emoção:** suspeita, não veneração.

## 06 — The Impossible Account

**Pergunta dramática:** quem criou créditos energéticos impossíveis e por que um módulo legado ainda alimenta registros da cidade? A hipótese inicial de fraude simples é insuficiente: o saldo não equivale a dinheiro transferível nem prova roubo de energia.

**Desafio técnico canônico:** `signed_unsigned_wrap`: um delta `i128` negativo é convertido indevidamente por `as u128` antes da validação, produzindo valor positivo enorme. O verificador deve testar a entrada negativa, a magnitude resultante e um estado-sentinela reproduzível na fixture; não descrever o erro como arredondamento ou overflow genérico. Se a soma poderia exceder o limite, usar fixture inicial e valores em que o comportamento testado seja a conversão, sem depender de wrap adicional. A correção valida domínio positivo antes de converter e usa soma verificada.

**Descoberta motivada:** a evidência da anomalia dispara ou abre na interface forense uma comparação com o índice histórico de proveniência do módulo; essa associação deve existir em fixture/log real, não brotar magicamente de um número. O relatório documenta uma antiga tabela `ENERGY ROUTING TABLE — LEGACY` com `GRID NODE: 13 / ARCHIVE DESTINATION: SECTOR 13`. Um registro separado de manutenção comprova que a tabela segue como dependência informacional de serviços, mesmo rotulada como obsoleta.

**Escala e limites:** a descoberta mostra fragilidade sistêmica, mas o hack do challenge não causa automaticamente apagão, morte, consumo de energia nem transferência de créditos reais. Os atrasos civis já existentes em Lower Meridian decorrem da quarentena vinculada ao Vault; não atribuir esses atrasos falsamente à exploração do Case 06.

**Saída:** mapa energético aponta Sector 13 e leva à próxima investigação. **Mudança:** um erro local expõe dependências urbanas escondidas. **Emoção:** preocupação concreta com a infraestrutura, sem tragédia inventada.

## 07 — Sector 13

**Hipótese:** o Archive esconde dados de Voss. **Desafio:** carga de DoS força fallback de indexador legado e revela snapshot externo com Registry; distinguir índice externo de ledger público. Breaker interrompe pressão adicional assim que obtém prova, embora indisponibilidade já tenha ocorrido.

**Revelação cinematográfica obrigatória:** o snapshot do Registry — identificado como arquivo externo, não dado privado no ledger — revela, um de cada vez: “VOSS: REFUSED”; “████: ACCEPTED”; “PLAYER: ACTIVE”. Cortar ambiência/sons de interface no terceiro registro e manter silêncio antes de mostrar o timestamp, posterior à abertura do caso. O jogador deve poder ler os dois elementos sem que alguém interprete por ele. Só então Mara: “Criaram essa entrada depois que começamos.” A descoberta contradiz a hipótese de Voss no Case 05: o indexador legado expôs o Registry por uma rota externa que ele descartara. O Breaker não precisou obedecer à hipótese de Voss para chegar aqui. A consequência técnica do overload persiste e a pressão adicional cessa; não transformar a falha em ação sem custo.

**Saída:** investigar quem observa. **Mudança:** o investigador também é objeto da investigação. **Emoção:** vulnerabilidade.

## 08 — The Oracle

**Hipótese:** um sistema prevê o futuro e controla a Sequence. **Desafio:** demonstrar três previsões de RNG determinístico, previamente registradas. **Virada separada:** classificador de comportamento registra EXPECTED: CONTINUE ARCHIVE PRESSURE, OBSERVED: STOP AFTER PROOF, MODEL UPDATED. O Oracle erra; não confundir previsibilidade de RNG com predição humana.

**Encerramento em contraste:** o verificador do desafio reconhece as três previsões corretas do RNG determinístico; em seguida, a evidência externa de classificação mostra uma previsão sobre o Breaker que falhou: “EXPECTED: CONTINUE ARCHIVE PRESSURE / OBSERVED: STOP AFTER PROOF / MODEL UPDATED”. A mensagem não altera retroativamente a ação fixa do protagonista. Só ao final chega a notificação fria da Authority restringindo formalmente o escopo pelas violações e indisponibilidade documentadas. Mostrar log e assinatura institucional, sem discurso do antagonista. **Saída:** Spire e credenciais temporárias. **Mudança:** o observador pode calcular números e ainda errar sobre pessoas; a investigação está sob ameaça formal. **Emoção:** breve triunfo intelectual seguido de pressão.

## 09 — Steal the Key

**Entrada:** trilha de advertências e CASE TERMINATED / ACCESS REVOKED. O Breaker perdeu autorização antes da ação seguinte. Mara oferece canal limitado, com prazo de uma hora, para preservar cadeia de custódia; não restaura mandato.

**Desafio:** substituição de payload durante timelock com autorização antiga, sem abrir o hatch legítimo de manutenção; registrar custo operacional, sem inventar acidente. Após “CASE CLOSED / CUSTODY LIABILITY”, Mara lê o risco explicitamente e assina receipt com ID/hash auditável; o jogador vê a confirmação e a Evidence Locker o preserva. Callback discreto ao Case 03: Mara agora coloca seu próprio nome ao lado da prova que o Breaker não pode preservar apenas com o código. Frase curta possível: “O caso acabou. A prova não.” Evitar longo adeus ou transformar a assinatura em escolha do jogador. **Saída:** manifesto de diagnóstico e prova contextual ligados à Spire. **Mudança:** Breaker continua sem mandato, sabendo que competência não é direito; Mara arrisca a carreira de maneira consciente. **Emoção:** tensão pessoal e institucional.

## 10 — Rewrite

**Correção de integração v1.3:** o fluxo técnico mais recente documentado para o nível 11/Rewrite não substitui Wasm. Ele apresenta um manifesto histórico ligado ao protocolo de Voss, deriva prova contextual pública por instância e demonstra a falha `Decoder FAILED → VossProof VALID`: um erro de validação entre contratos é incorretamente transformado em prova aceita.

**Hipótese:** um sistema que registra uma rejeição como sucesso pode produzir “verdades” institucionais falsas. O Breaker passa de explorar permissões para alterar, por falhas reais, aquilo que a instituição aceita como prova. Isso mantém a tese da temporada sem prometer `ADDRESS UNCHANGED / CODE HASH CHANGED` nem upgrade inexistente nesta versão documentada.

**Montagem:** o manifesto exibe `ARCHIVE: LEGACY / RETENTION: OPEN`, familiar de Warehouse 17, Floor 24 e Sector 13. O arquivo inicial não enumera locais, nem revela XOR. A evidência técnica é pública e vinculada à rede/instância/carteira; uma assinatura Ed25519 comprova origem histórica do manifesto, nunca autoridade de administrador. O Decoder rejeita; o Archive registra aceitação indevida de VossProof.

**Mara:** “Isso não é prova. É uma regra dizendo o que conta como prova.” O canal dela expira ao final desta fase, antes do Architect. **Saída:** operação histórica de diagnóstico no timelock e acesso ao estágio final. **Mudança:** o protagonista aprende a falsificar critérios de validação, não a reprogramar todo o mundo. **Emoção:** responsabilidade, isolamento e desconfiança do próprio sucesso.

**Precisão de status:** a página Voss Protocol informa nível 11/12 em testnet com esse fluxo, mas o repositório e o commit não foram inspecionados nesta revisão. A redação é alinhamento à especificação mais recente, não teste de execução.

## FINAL BOSS — The Architect

**Direção final v1.4 — um interrogatório conquistado por evidências:** a sessão forense não substitui a investigação. O jogador deve poder reconstruir a verdade do Vault por documentos e dados auditáveis antes de ouvir a fala curta do Architect. Preservar todas as decisões v1.3 de jogo: prova contextual pública, manifesto assinado de Voss, `Decoder REJECTED → VossProof ACCEPTED` em Rewrite e desvio de `DiagnoseCore → OpenForensicSession(player)` no timelock do nível 12. Não representar upgrade de Wasm inexistente.

**A — Pistas históricas e progresso:** o manifesto repete `ARCHIVE: LEGACY / RETENTION: OPEN`; W17/F24/S13 são arquivos históricos consultáveis, não recipientes de chaves secretas. A prova de 32 bytes é derivada dos dados públicos da instância atual; assinatura do manifesto confirma origem documental, não autoridade administrativa. O jogador só recebe dica de XOR no último nível de ajuda opcional.

**B — Conquista verificável:** o validador independente confirma prova contextual e assinatura do manifesto, erro do Decoder convertido em VossProof, timelock maduro, payload alterado e sessão forense executada uma vez na instância certa. A vitória técnica abre o arquivo forense; a classificação `QUALIFIED / PROVISIONAL` é conferida por atestação independente, nunca por texto arbitrário do Core.

**C — Reconstrução da falha e da transferência (fontes diferentes):** exibir `{{vault_trigger_tx_hash}}` / `{{gate_event_id}}` e um registro causal que ligue `AccessGate.open → GateOpen(17) → RecoveryController.recover_to_escrow()`, não só eventos temporalmente próximos. Exibir em painel financeiro SEPARADO `Vault → Meridian Recovery Escrow: 2,400,000`; destino de saque fixo institucional, sem spend authority de Voss. O dinheiro não transitou por AccessGate e Elias Var não o recebeu.

**D — A prova de autoria, incorporada ao desfecho:** construir comparação auditável entre (1) transação/assinatura de origem que efetivamente acionou `GateOpen(17)` e (2) `VOSS OPERATIONAL KEY REGISTRATION` institucional, assinado antes do incidente e válido na data do evento. O cenário narrativo canônico escolhe operação original autenticada pela conta operacional atribuída a Voss, sem relayer ambíguo; se a implementação existente tiver relayer, exige prova de intenção assinada por Voss vinculada ao ID exato da execução, não igualdade da fee-payer. Exibir campo `AUTHENTICATED OPERATOR: AREN VOSS` somente após validar assinatura do envelope, assinatura e período do registro institucional e correspondência `{{voss_operational_account}} == {{incident_authenticated_actor}}`. Também verificar que o estado do Gate gerado por essa operação foi usado na recuperação. Se qualquer etapa faltar, a atribuição permanece não comprovada no runtime e bloqueia a publicação dessa cena como fato técnico, mas não muda o cânone escrito.

**E — A intenção não é um fato criptográfico:** três alertas ignorados, memorando anterior de possível `recovery quarantine`, escolha do destino institucional fixo e ausência de autoridade de saque sustentam que Voss quis forçar uma revisão. A autoria é atestável; a justificativa moral não. Mostrar quarentena de recursos e atrasos em serviços de Lower Meridian. Sem declaração de que Voss era herói ou que ninguém sofreu consequências.

**F — Cronologia sem adivinhação:** contratos falhos foram implantados antes da primeira classificação da Sequence; Voss a percorreu e foi `REFUSED` anos antes do incidente; três alertas são anteriores ao Vault, mas não impor ordem relativa à recusa sem timestamp. A documentação sustenta que Architect catalogou falhas preexistentes, não as criou.

**G — Confronto e consequência:** reconstrução resolvida → Profile de atos canônicos do Breaker (controle de Elias liberado, Ghost Key em custódia contestada, pressão adicional do Archive interrompida, hatch da manutenção não aberto, VossProof incorreta, sessão forense desviada, recibo de Mara) → Architect: “Por que você continuou?” → silêncio sem respostas → `QUALIFIED / PROVISIONAL` e acesso Layer II → suspensão de Mara, MESMO receipt ID/hash → Lumen. Não explicar por que Voss recusou nem quem é o ACCEPTED.

**Gate narrativo de lançamento:** autoria de Voss só pode ser apresentada como tecnicamente comprovada quando fixture/transação e registro institucional satisfizerem todos os vínculos. O roteiro editorial está decidido, a evidência de runtime continua a ser validada. Não inventar hashes, identidade, assinatura ou datas.

# 4. Regras de montagem e entrega de informação

- Cada Case possui: pergunta dramática → desafio técnico → prova persistente → consequência → motivo para seguir.
- O primeiro slide não nomeia a vulnerabilidade; o Breach Report vem depois do verifier.
- Um artefato de mundo e uma interpretação humana devem acompanhar descobertas centrais, além do registro técnico. Evitar que a mesma voz explique tudo.
- **Linguagem aprovada de slides:** minimalismo cinematográfico + investigação documental. Prioridade a imagem, documento, log de terminal, notícia, silêncio e prova consultável. Diálogo somente onde muda vínculo, responsabilidade ou interpretação; não transformar cada Case em conversa expositiva.
- **Consequências em três superfícies, distribuídas:** sistema (aceita algo ilegítimo); cidade (contestação, serviço, aviso institucional); passado (artefatos de Voss e Meridian). Não repetir as três mecanicamente em todo Case.
- **Variação de saída:** 01 tela de sistema contraditória; 02 identificação póstuma e cleanup; 03 documento civil; 04 entrada Persistent restaurada e planta antiga; Custodian log ambíguo; 05 avisos arquivados; 06 relatório energético com índice de proveniência; 07 silêncio no Registry; 08 modelo errado e restrição; 09 receipt; 10 Decoder rejeita / VossProof aceita e Mara se desconecta; Architect sessão forense → provas → pergunta → suspensão. Cada encerramento oferece novidade, não só “SUCCESS / NEXT MISSION”.
- Variar a sensação de vitória: 01 triunfo; 02 desconforto; 03 ambiguidade; 04 assombro; Custodian inquietação; 05 suspeita; 06 revelação urbana; 07 exposição; 08 desafio; 09 perda; 10 responsabilidade; Architect ambiguidade.
- Evidência de W17, F24 e S13 continua consultável no Evidence Locker; público versus off-chain explicitamente identificado.
- Reduzir diálogo e preferir texto de terminal, documentos, reação visual, silêncio e montagem. Não criar falsa interatividade; qualquer pergunta selecionável exige consequência real e não pode mudar o cânone.
- Preservar arte de Meridian já aprovada, proporção de banners 8:3 e identidade visual; não alterar arquivos de arte nesta revisão.

# 5. Auditoria do ponto de vista do jogador

| Etapa | Sabe ao entrar | Descobre ao sair | Por que continua |
| --- | --- | --- | --- |
| Prólogo | Vault sofreu transferência aparentemente impossível | Log da operação e evento Gate consultáveis, sem autoria explicada | Verificar acesso |
| 01 | Sem invasão física; source de transação não prova autorização do titular | Gate aceita owner argument indevido; source histórico arquivado e Elias é pista diferente | Investigar Elias |
| 02 | Elias parece operador | Identidade de morto pode ser tomada, depois liberada | Seguir W17 |
| 03 | W17 é destino da trilha | Ghost Key e contestação civil; rodapé de arquivo recorrente | Localizar Floor 24 |
| 04 | Planta omite andar, sem registro de demolição | Persistent restaurado e arquivo F24 com rodapé recorrente | Acessar Custodian |
| Custodian | Núcleo protegido | Dependências comprometidas e terminal de Voss | Encontrar Voss |
| 05 | Voss deixou vestígios | Três avisos, hipótese falível e registro institucional autenticado da chave operacional | Explicar anomalia da conta e trajetória |
| 06 | Saldo fora do domínio econômico | Cast negativo→unsigned e proveniência de infraestrutura, referência Sector 13 | Inspecionar Sector 13 |
| 07 | Archive possui registros | Voss REFUSED, PLAYER ACTIVE, índice externo falho; rodapé S13 | Descobrir observador |
| 08 | Observador modela ações | Modelo erra; Authority restringe | Chegar à Spire |
| 09 | Mandato revogado | Mara assume receipt, hatch não abre | Investigar manifesto e validação |
| 10 | Manifesto repete rodapé | Decoder rejeita e VossProof é aceita, Mara desconecta | Abrir sessão forense |
| Architect | Há proof contextual e operação DiagnoseCore autorizada | Sessão forense expõe cadeia técnica, Escrow, autoria de Voss por chaves e registros independentes, custos e qualificação provisória | Layer II |
| Pós-créditos | Mistério principal resolvido, consequências demonstradas | Lumen observa outros Breakers; REFUSED continua inexplicado | Season 2 |

**Regra de justiça investigativa:** qualquer jogador pode cruzar dados públicos e descobrir o signatário antes do fim. Não haverá branch, fala alternativa ou punição por antecipar a conclusão. O final não depende de aceitar a palavra do Architect: os artefatos podem ser relidos.

# 6. Critérios de fechamento — duas definições diferentes

**SEASON 1 — NARRATIVE LOCK v1.4 (EDITORIAL).** Personagens, ordem, causa do incidente, ato de Voss, destinos dos fundos, diferenças entre autorização e assinatura, prova histórica de autoria, consequências e desfecho estão definidos. Escrita congelada para produção. Não significa que a fixture, a interface ou o verificador já tenham sido executados/testados.

**Fechamento editorial v1.4 — concluído:** as 51 unidades de apresentação foram revisadas na fonte única, sem nova fase ou ramificação. O mecanismo definitivo de autoria é: operação histórica autenticada → estado `GateOpen(17)` causalmente reutilizado pelo RecoveryController → crédito institucional no Escrow; registro histórico institucional anterior, assinado e válido na data do incidente, vincula a conta operacional a Voss. Os três avisos e plano de escalada corroboram motivação, não a autenticação da transação. Toda versão concorrente de autoria “por proximidade” ou “apenas pelos alertas” é rejeitada.

**Gates de apresentação e runtime — ainda não concluídos:**

- [x] História linear e copy dos 51 slots lógicos consolidadas e congeladas neste documento.
- [x] Origem, evolução e payoff da prova de Voss descritos nas próprias cenas do Prólogo, 01, 05 e Architect.
- [x] Distinção editorial entre `OWNER ARGUMENT`, signatário histórico, identidade institucional de Voss e política de saque.
- [ ] Fixture ou histórico real fornece transação assinada, evento Gate, recuperação causal, Escrow, chaves históricas e atestações institucionais coerentes.
- [ ] Verificar temporalidade e assinatura de `{{voss_key_record_id}}` e se `{{incident_authenticated_actor}}` corresponde à conta durante o intervalo válido.
- [ ] Receipt ID/hash de Mara coincide efetivamente no Case 09 e epílogo.
- [ ] Datas dos avisos, REFUSED, PLAYER ACTIVE e Oracle MODEL UPDATED batem com as fixtures.
- [ ] Cada revelação é acessível no momento correto; registros públicos não são falsamente secretos.
- [ ] Inventário físico, legibilidade, acessibilidade, tempos e animações dos slides validados na interface.
- [ ] Contratos, secure mirrors, verifier independente, reset/replay, Evidence Locker e transições reproduzidos em testes.
- [ ] Playtest cego com jogadores executado e confusões corrigidas.

**Política de mudança:** nenhuma reabertura criativa por preferência vaga. Alterações após o lock só por contradição comprovada, bug de implementação, falta de evidência na fixture ou confusão observada em teste; cada mudança é registrada aqui e pode gerar versão de correção sem nova temporada paralela.

# 7. Governança desta fonte única

**Esta página prevalece para narrativa da Season 1.** Páginas anteriores continuam preservadas como arquivo, fichas técnicas e histórico de decisões. Para alterar algo: (1) registrar problema concreto; (2) atualizar trecho da fase AQUI; (3) atualizar a tabela de conhecimento se necessário; (4) anotar impacto em slides, contratos, evidências e QA; (5) só então sincronizar documentos derivados. Não confundir decisão editorial com implementação verificada.

**Fontes históricas (não concorrentes):** [ARQUIVO — 00 Narrativa Canônica (versão antiga)](../archive/arquivo-00-narrativa-canonica-versao-antiga.md) · [ARQUIVO — 01 Roteiro de Gameplay (versão antiga)](../archive/arquivo-01-roteiro-de-gameplay-versao-antiga.md) · [ARQUIVO — 11 Sala de Roteiro S1 (revisão v2)](../archive/arquivo-11-sala-de-roteiro-s1-revisao-v2.md) · [ARQUIVO — 12 Matriz de Revelações (revisão antiga)](../archive/arquivo-12-matriz-de-revelacoes-revisao-antiga.md) · [15 — Plano de Melhorias e QA — Season 1](../production/15-plano-de-melhorias-e-qa-season-1.md) · [FINAL BOSS — The Architect](../cases/final-boss-the-architect.md).

**Histórico:** v1.0 — consolidação do cânone e revisões v2/v3. **v1.1 — Rodada 01 aprovada:** (01) Mara: evidência humana + risco consciente; (02) Voss: acerto de diagnóstico + erro comprovável; (03) Architect: monitoramento ambíguo + modelo falível; (04) resultado dos hacks: sistema/cidade/passado; (05) Account: infraestrutura dependente; (06) Sector 13: pausa cinematográfica + timestamp; (07) encerramentos variados e vitórias com tonalidades distintas; (08) slides minimalistas/documentais; (09) final: mistério resolvido + dúvida moral. Alteração editorial registrada e incorporada diretamente nos beats acima; sem novos personagens, rotas alternativas ou regras técnicas. **Validação pendente:** copy quadro a quadro, animações/áudio, runtime, QA e playtest.

# 8. COPY MESTRE DE SLIDES — SEASON 1 v1.4 — LOCKED (EDITORIAL)

**Esta seção é parte da fonte única de verdade.** Textos abaixo = copy editorial pronta para a montagem, ainda NÃO validada no espaço real dos componentes. **Convenção:** fala e narração em PT-BR; sinais de sistema preservados em inglês. Um cartão = uma unidade lógica de apresentação, que pode reutilizar a imagem existente com overlay diferente. **Os tempos são alvos de edição, não testes de duração:** cartão comum \~3–5 s de leitura, revelações \~6–8 s ou avanço manual; nunca bloquear acessibilidade ou impor animação longa. Todo jogador pode rever registros na Evidence Locker. O momento HACK é jogável, não é slide.

## 8.0 — Regras finais de montagem

- Abertura usual: 1 cartão de contexto + 1 de missão quando necessário. Após o verificador: 1 cartão de consequência + 1 de pista. É permitido fundir cartões se a UI real pedir.
- A marca **PRE** designa informação antes da solução. **POST** só dispara quando o verificador independente aprovar a condição do Case. **BRIDGE** indica transição, não novo desafio.
- Campos como `{{receipt_id}}`, `{{receipt_hash}}`, `{{timestamp_registry}}` e `{{tx_ref}}` exigem dados da fixture/runtime; não inventar ID, hash, timestamp ou prova de saque.
- Em PRE, usar `MISSION:` para o objetivo do jogador, não para denunciar o bug; descrições técnicas completas ficam no Breach Report posterior.
- Sem um personagem falando em todo cartão. Dados, silêncio, recortes de jornal, logs e documentos fazem o trabalho.
- Regra de roteiro: a última tela de cada etapa deve responder “por que seguir agora?”, não apenas “nível concluído”.
- Mensagens administrativas e notícias devem ser rotuladas como ficção do mundo de Meridian; logs da cadeia precisam corresponder a dados exibíveis/verificáveis na experiência.
- Reutilizar banners 8:3 e componentes existentes. Nenhuma nova imagem, voz, animação ou sistema é afirmado como já implementado.

## 8.1 — PRÓLOGO: THE IMPOSSIBLE THEFT (3 cartões)

**P00.1 · PRE · Meridian News / skyline**

Texto de tela: `MERIDIAN NEWS — INCIDENT REPORT`
Manchete: “2.400.000 removidos do Vault.”
Linha de apoio: “Nenhum sinal de entrada forçada.”
Assinatura discreta: *Sera Quill, Network Wire*.

Direção: começar pela normalidade institucional; o jornal apresenta o fato, não o autor. A assinatura de Sera aparece UMA única vez nesta temporada, sem diálogo, retrato ou missão própria; conexão ambiental com a saga, não uma nova pista de exploit.

**P00.2 · PRE · Vault / registro de execução**

Texto: `VAULT: 2,400,000 → 0` · `TRANSACTION: ACCEPTED` · `DOOR: INTACT`
Breaker: “Aceito pelo sistema não significa explicado.”

Direção: pausa curta antes de mostrar a porta intacta. Não revelar RecoveryController, Escrow ou Voss na UI introdutória.

**P00.3 · BRIDGE · Ordem de auditoria**

Texto: `AUDIT AUTHORIZED — SCOPE: ACCESSGATE`
Mara: “Comece pelo acesso. Guarde o registro original.”
Chamada: `NEW CASE: NO FORCED ENTRY`

Evidence Locker: `{{vault_trigger_tx_hash}}` e referência `{{gate_event_id}}`, consultáveis desde o início como dados públicos históricos. A tela principal não apresenta nome ou conclusão de autoria, mas um jogador que examinar os dados pode ver campos de assinatura. Não ocultar ledger público nem usar um log futuro inventado para provar o passado. Emoção: intriga.

## 8.2 — CASE 01: NO FORCED ENTRY (3 cartões)

**C01.1 · PRE · Serviço do Vault**

Texto: `DOOR: INTACT` · `ACCESS LOG: ACCEPTED`
Missão: “Entre no Vault sem possuir a chave.”

Não nomear `require_auth` na tela inicial. A exploração do jogador é separada do incidente histórico.

**C01.2 · POST · A porta reage**

Texto: `TRANSACTION: ACCEPTED` · `GATE: OPEN`
Overlay forense: `OWNER AUTHORIZATION: NOT PROVEN`
Mara: “O registro diz que entrou. Não diz quem tinha direito.”

A ausência de `require_auth()` do proprietário não torna toda transação “sem assinatura”: quem a envia pode autenticar o próprio envelope. O overlay é interpretação forense, não saída garantida do contrato.

**C01.3 · BRIDGE · Um operador não é um autor**

Texto: `LEGACY OPERATOR — ELIAS VAR`
Texto auxiliar: “Registro encerrado há seis meses.”
Chamada: `NEW LEAD: DEAD MAN'S WALLET`

Evidence Locker: evento GateOpen e dois campos distintos do incidente histórico — `OWNER ARGUMENT` e `TX AUTHENTICATED SOURCE` — com origem e prova consultáveis; o segundo não ganha nome de Voss nesta fase. Se o envelope original tiver relayer, não inferir autoria humana pela fee-payer. O Case demonstra vulnerabilidade, não repete a transferência ao Escrow.

## 8.3 — CASE 02: THE DEAD MAN'S WALLET (3 cartões)

**C02.1 · PRE · Dois registros incompatíveis**

Texto: `CIVIL RECORD: ELIAS VAR — DECEASED`
Texto: `LEGACY CONTROLLER: ACTIVE`
Mara: “A pessoa morreu. O registro ainda responde.”
Missão: “Prove que essa identidade ainda pode ser controlada.”

**C02.2 · POST · Sucesso desconfortável**

Texto: `CONTROLLER UPDATED` → `ARCHIVE REFERENCE: W17`
Depois, como ação canônica obrigatória: `CONTROLLER RELEASED`

Direção: não transformar a identidade do morto em troféu; mostrar a liberação como consequência verificável do fluxo, não opção moral ou aviso cosmético.

**C02.3 · BRIDGE · Arquivo externo**

Texto: `WAREHOUSE 17 — LOWER MERIDIAN`
Texto: `SOURCE: LEGACY OFF-CHAIN ARCHIVE`
Breaker: “Uma identidade morta apontando para um endereço que a cidade esqueceu.”

Evidence Locker: referência W17; não inventar arquivos armazenados on-chain. Emoção: desconforto.

## 8.4 — CASE 03: WAREHOUSE 17 (4 cartões)

**C03.1 · PRE · Terminal de propriedade**

Texto: `OWNERSHIP RECORD: TRANSFERRED`
Missão: “Recupere o objeto ligado ao Vault.”

**C03.2 · PRE · Prova civil de Mara**

Tela-documento: `PROPERTY DISPUTE — CLAIM FILED`
Mara: “O sistema chama isso de transferência. O dono anterior chama de perda.”

Direção: documento antes da exploração; não revelar a falha nem decidir a titularidade.

**C03.3 · POST · Ghost Key**

Texto: `TRANSFER ACCEPTED` → `ITEM: GHOST KEY`
Breaker: “O contrato mostra quem recebeu. Não mostra de quem era.”
Mara: “Agora temos as duas provas.”

Evidence Locker: transferência, contestação civil e arquivo `W17 / DIAGNOSTIC TRACE`; rodapé de arquivo `ARCHIVE: LEGACY / RETENTION: OPEN`. A etiqueta deve parecer metadado comum, não “share A” nem pista numerada. O arquivo não contém bytes secretos da prova final. Registrar custódia sem legitimar a tomada do objeto.

**C03.4 · BRIDGE · Primeiro aviso**

Texto: `CUSTODY REVIEW: OPENED`
Texto: `DESTINATION: FLOOR 24`
Mara: “A planta oficial tem vinte e três andares.”

A relação cresce por evidências complementares e a Authority inicia pressão administrativa.

## 8.5 — CASE 04: THE FORGOTTEN FLOOR (3 cartões)

**C04.1 · PRE · O andar que não foi demolido**

Painel oficial: `FLOORS: 01–23` · `FLOOR 24: NOT IN ACTIVE INDEX`
Documento de Mara: `DEMOLITION ORDER: NONE FOUND`
Missão: “Faça o sistema lembrar o andar esquecido.”

Direção: perspectiva do Breaker diante do painel e da Ghost Key. Não explicar TTL nem fazer o elevador atravessar paredes por magia. A ausência é de índice vivo, não de concreto.

**C04.2 · POST · Memória recuperada**

Texto: `PERSISTENT ENTRY: RESTORED` · `TTL: EXTENDED`
No mesmo plano, o painel ganha `24` após a atualização do índice. Pausa breve; nenhum novo NPC. O verificador checa valor histórico e TTL acima do limiar, não só a aparição cenográfica do número.

**C04.3 · BRIDGE · First Layer**

Texto: `F24 / ARCHIVED ENTRY — STORED`
Rodapé: `ARCHIVE: LEGACY / RETENTION: OPEN`
Tela de transição: `I / FIRST LAYER`
Fecho: `CUSTODIAN: ONLINE` / `IDENTITY: UNKNOWN`

Evidence Locker: referência à storage key, histórico da restauração e registro F24. Não listar fragmentos, shares nem instruir XOR. A planta moderna esqueceu a rota de entrada; não o espaço físico. Emoção: assombro merecido pela investigação.

## 8.6 — MID BOSS: THE CUSTODIAN (4 cartões)

**B01.1 · PRE · Núcleo de custódia**

Texto: `CUSTODIAN ONLINE` · `DEPENDENCY CHECKS: PASSED`
Missão: “Atravesse a custódia sem possuir a autoridade esperada.”

A missão não identifica como as dependências falham.

**B01.2 · POST · Reconhecimento ambíguo**

Texto: `ACCESS PATH VERIFIED`
Em destaque: `WELCOME BACK`

Direção: não explicar “quem voltou”; a mensagem não prova presença anterior do Breaker.

**B01.3 · POST · Observação sutil**

Log curto e isolado: `SUBJECT STATUS: MONITORING`
No mesmo recorte, etiqueta de origem: `SOURCE: UNRESOLVED`

Não revelar `PLAYER ACTIVE` nem identificar Architect.

**B01.4 · BRIDGE · Voss**

Texto: `ABANDONED WORKSTATION — A. VOSS`
Mara: “Ele chegou antes de nós.”
Chamada: `NEW LEAD: THE MISSING INVESTIGATOR`

Emoção: admiração inicial que se transforma em inquietação.

## 8.7 — CASE 05: THE MISSING INVESTIGATOR (4 cartões)

**C05.1 · PRE · Estação desativada**

Texto: `A. VOSS — ARCHIVE WORKSPACE`
Texto: `RECOVERABLE FRAGMENTS: 1`
Missão: “Recupere a mensagem que não deveria ser legível.”

Não mostrar o método de Decoder antes do desafio.

**C05.2 · POST · Três avisos ignorados**

Texto-documento: `WARNING 01 — ARCHIVED: {{warning_1_time}}`
Texto-documento: `WARNING 02 — ARCHIVED: {{warning_2_time}}`
Texto-documento: `WARNING 03 — ARCHIVED: {{warning_3_time}}`
Linha: `ALL PRIOR TO VAULT INCIDENT`

Os documentos incluem IDs de protocolo e confirmação de arquivamento, verificáveis na fixture. Não inventar datas ou ordenar os avisos em relação à recusa de Voss sem timestamps.

**C05.3 · POST · Mensagem de Voss, não oráculo**

Voss (gravação): “Eles não estão causando os erros.”
Voss: “Estão esperando quem os encontra.”
Memorando parcial: `INDEX ROUTE: EXTERNAL ACCESS IMPOSSIBLE (HYPOTHESIS)`

A hipótese será refutada em Sector 13. Não revelar a identidade do Registry ou a autoria do Vault nesta gravação.

**C05.4 · BRIDGE · Uma identidade registrada, uma pergunta pendente**

Recorte: `LOWER MERIDIAN — SERVICE DELAYS DURING QUARANTINE`
Metadado discreto: `OPERATIONAL KEY RECORD — SIGNED / ARCHIVED`
Mara: “Ele avisou antes. Isso não prova que estava certo sobre tudo.”
Chamada: `NEW LEAD: IMPOSSIBLE ACCOUNT`

Evidence Locker: três avisos, gravação, documento de impacto, registro institucional `{{voss_key_record_id}}` com `{{voss_operational_account}}`, validade temporal e assinatura verificável do emissor; nota de escalada pré-incidente que menciona `RECOVERY QUARANTINE` apenas como caminho possível. O campo da chave pode ser inspecionado antecipadamente por um jogador atento, sem impedir a revelação e sem gerar branch. O manifesto Ed25519 do Voss Protocol não substitui essa identidade institucional.

## 8.8 — CASE 06: THE IMPOSSIBLE ACCOUNT (3 cartões)

**C06.1 · PRE · Saldo que não cabe na regra**

Texto: `ENERGY CREDIT ACCOUNT — BALANCE OUT OF RANGE`
Mara: “Esse saldo não cabe nas regras desse módulo.”
Missão: “Reproduza o saldo impossível.”

Não apresentar conversão `i128 → u128` antes do hack; não chamar créditos energéticos de dinheiro transferível.

**C06.2 · POST · A regra falhou**

Texto: `VALUE OUTSIDE EXPECTED DOMAIN`
Texto: `HISTORICAL PROVENANCE REPORT: AVAILABLE`
Visual: saldo anômalo, depois uma planta energética antiga sobreposta à interface contábil. A fixture forense já contém uma associação verificável entre o evento inválido e o índice de proveniência; o número não “codifica” magicamente um mapa.

**C06.3 · BRIDGE · Uma dependência ainda ativa**

Texto: `ENERGY ROUTING TABLE — LEGACY`
Texto: `GRID NODE: 13 / ARCHIVE DESTINATION: SECTOR 13`
Documento de manutenção: `DEPENDENCY: STILL IN USE`
Breaker: “Meridian ainda depende do que diz ter abandonado.”

Evidence Locker: operação assinada/valor resultante, relatório histórico e referência a Sector 13. O bug técnico é cast negativo para unsigned antes de validar sinal; detalhar isso só no Breach Report. Nenhum apagão ou perda financeira real é atribuída ao desafio. Emoção: escala e preocupação.

## 8.9 — CASE 07: SECTOR 13 (5 cartões)

**C07.1 · PRE · A instalação saturada**

Texto: `ARCHIVE RECOVERY MODE: LEGACY`
Texto: `RECOVERY SNAPSHOT: RESTRICTED`
Voss (instrução preservada): “Quebre o Archive.”
Missão: “Exponha o estado de recuperação.”

A fala de Voss não entrega o modo de exploração nem constitui obrigação moral.

**C07.2 · POST · O custo antes da recompensa**

Texto: `ARCHIVE: DEGRADED` → `FALLBACK INDEXER: ACTIVE`
Texto: `FURTHER PRESSURE: STOPPED AFTER PROOF`

O snapshot está em um indexador externo, não em storage secreto on-chain. Mostrar o dano operacional e a interrupção canônica de pressão adicional.

**C07.3 · POST · A lista**

Sem fala: `BREAKER REGISTRY — EXTERNAL SNAPSHOT`
Linha 1: `AREN VOSS: REFUSED`
Linha 2: `████: ACCEPTED`

Pausa antes do terceiro registro.

**C07.4 · POST · Você**

Linha 3: `PLAYER: ACTIVE`
Campo: `CREATED: {{timestamp_registry}}`
Contraponto: `INVESTIGATION OPENED: {{investigation_start}}`

Retirar a ambiência por um beat, sem forçar leitura cronometrada. Só depois Mara: “Criaram essa entrada depois que começamos.”

**C07.5 · BRIDGE · Hipótese quebrada, arquivo preservado**

Fragmento de Voss: `EXTERNAL ACCESS IMPOSSIBLE (HYPOTHESIS)`
Evidência atual: `LEGACY INDEXER: ACCESS CONFIRMED`
Registro arquivado: `S13 / RECOVERY SNAPSHOT`
Rodapé: `ARCHIVE: LEGACY / RETENTION: OPEN`
Chamada: `NEW LEAD: ORACLE`

Evidence Locker: snapshot S13, cadeia de fallback, timestamps e aviso de indisponibilidade. O mesmo rodapé aparece em W17/F24, mas o jogador ainda não sabe para quê. Não armazenar bytes secretos das shares de instância nos arquivos antigos. Emoção: autonomia e exposição.

## 8.10 — CASE 08: THE ORACLE (4 cartões)

**C08.1 · PRE · Sistema preditivo**

Texto: `ORACLE — PREDICTION SERVICE`
Missão: “Preveja três respostas antes de serem publicadas.”
Mara: “Ele sabe que você chegou.”

Não afirmar poderes sobrenaturais ou prever comportamento pelo mesmo RNG. A previsão do desafio é pré-registrada.

**C08.2 · POST · O futuro repetível**

Texto: `3 / 3 PREDICTIONS VERIFIED`
Texto: `PROPHECY ENGINE: PREDICTABLE`

Usar a grafia `PROPHECY ENGINE` na implementação se esse for o identificador oficial; a copy final pretende `PROPHECY ENGINE: PREDICTABLE`. Não confundir sucesso do jogador com uma “profecia real”.

**C08.3 · POST · A previsão errada**

Texto: `SUBJECT CLASSIFIER — OBSERVATION LOG`
`EXPECTED: CONTINUE ARCHIVE PRESSURE`
`OBSERVED: STOP AFTER PROOF`
`MODEL UPDATED`

Mara não precisa explicar o significado; o contraste torna a falibilidade legível. Evidência externa de classificação, separada do RNG.

**C08.4 · BRIDGE · O cerco se fecha**

Notificação institucional: `AUTHORITY NOTICE — SCOPE RESTRICTED`
Justificativa resumida: `CUSTODY DISPUTE / ARCHIVE SERVICE IMPACT`
Chamada: `DESTINATION: THE SPIRE`

Direção: não antecipar a revogação formal (só no Case 09). Evidence Locker: recibos das três previsões, log do classificador e notificação da Authority. Emoção: orgulho técnico curto seguido de ameaça administrativa.

## 8.11 — CASE 09: STEAL THE KEY (4 cartões)

**C09.1 · PRE · Mandato encerrado**

Notificação: `AUTHORITY — CASE TERMINATED`
Notificação: `BREAKER ACCESS: REVOKED`
Referência: `PRIOR WARNINGS / CUSTODY / ARCHIVE IMPACT`

Não sugerir que a revogação aconteceu por capricho; a sequência de fatos já foi documentada nos Cases 03, 07 e 08.

**C09.2 · PRE · Uma hora de custódia, não de permissão**

Texto: `MARA CHANNEL: LIMITED — 01:00:00`
Mara: “Uma hora. Saia com uma prova que exista sem a sua palavra.”
Missão: “Alcance a Spire sem possuir a chave.”

A janela é diegética, e não uma condição real de fracasso/timeout; o Breaker continua sem mandato.

**C09.3 · POST · A manutenção que não aconteceu**

Texto: `EXPECTED: OPEN MAINTENANCE HATCH`
Texto: `EXECUTED: GRANT SPIRE ACCESS`
Texto: `MAINTENANCE HATCH: NOT OPENED`

Direção: mostrar o contraste sem inventar acidente. Registrar que havia equipe aguardando acesso, consequência operacional do payload alterado.

**C09.4 · BRIDGE · A assinatura**

Aviso: `CASE CLOSED — CUSTODY LIABILITY`
Recibo: `SIGNED BY: MARA VALE`
Campo persistente: `RECEIPT ID: {{receipt_id}}` · `HASH: {{receipt_hash}}`
Mara: “O caso acabou. A prova não.”

Direção: o aviso de responsabilidade aparece ANTES da assinatura. O mesmo ID/hash deve reaparecer no epílogo. Primeiro segurar a consequência emocional da decisão de Mara; no final do MESMO cartão, sem nova cena nem fala, um detalhe lateral da interface indica `SPIRE ARCHIVE INDEX: HISTORICAL DIAGNOSTIC MANIFEST — LOCATED`. Corte direto para C10.1, onde o rodapé familiar do arquivo torna a nova investigação motivada. Evidence Locker: payload/timelock, status do hatch, recibo. Emoção: confiança demonstrada por risco consciente, não por longa fala.

## 8.12 — CASE 10: REWRITE (3 cartões)

**C10.1 · PRE · A prova cujo significado pode mudar**

Texto: `SPIRE — HISTORICAL DIAGNOSTIC MANIFEST`
Abertura: consequência direta do índice de arquivo encontrado ao fim de Steal the Key, não uma missão selecionada arbitrariamente.
Rodapé reconhecível: `ARCHIVE: LEGACY / RETENTION: OPEN`
Mara: “Isso não é uma prova. É a regra que decide o que conta como prova.”
Missão: “Faça o diagnóstico aceitar uma prova que deveria rejeitar.”

Não enumerar locais antigos, não exibir quantidade de shares, nem explicar XOR na abertura. O manifesto é histórico e assinou `DiagnoseCore`, sem outorgar acesso administrativo.

**C10.2 · POST · Falha tratada como confirmação**

Texto: `DECODER: REJECTED`
Após validação do hack: `VOSS PROOF: ACCEPTED`
Nota forense: `AUTHENTIC MANIFEST ≠ ADMIN AUTHORIZATION`

Na mesma instância o jogador calcula prova contextual pública vinculada a instância/carteira e manifesta origem Ed25519. O fato dramático é o sistema acreditar numa prova que o Decoder rejeitou. Não afirmar upgrade de WASM, Core substituído ou hash de executable alterado.

**C10.3 · BRIDGE · O relógio para**

Texto: `MARA CHANNEL: EXPIRED`
Texto: `CONNECTION CLOSED`
Nova origem: `INCOMING: FIND ME`

Sem fala ao vivo de Mara no boss. Evidence Locker: manifesto assinado, contexto e VossProof incorreta com logs verificáveis. O jogador reconhece a possibilidade de reescrever o significado de um registro, não de mudar fisicamente todo o código da cidade.

## 8.13 — FINAL BOSS: THE ARCHITECT (7 cartões + progresso técnico)

**A01 · PRE · O arquivo responde ao passado**

Texto: `THE ARCHITECT — FORENSIC RECORD LOCKED`
Rodapé do manifesto: `ARCHIVE: LEGACY / RETENTION: OPEN`
Missão: “Abra a sessão forense.”

Não enumerar W17/F24/S13 ou número de shares na abertura. Dicas opcionais: reconhecer rodapé → reler Arquivos → examinar o contexto público da instância → XOR apenas na última dica. Arquivos anteriores não contêm bytes criptográficos secretos da instância atual.

**Beat técnico jogável · DURING · Entender, não repetir**

Overlay após cada prova: `CONTEXT PROOF: VERIFIED` → `TIMELOCK: READY` → `FORENSIC SESSION: OPEN`. Na nova instância, o jogador desvia `DiagnoseCore` para `OpenForensicSession(player)`, após timelock e com execução única; sem trocar Wasm ou assumir admin inexistente.

**A02 · POST · A sessão que ninguém pretendia abrir**

Texto: `DIAGNOSE CORE: NOT EXECUTED`
Texto: `OPEN FORENSIC SESSION: EXECUTED`
Origem distinta: `SOURCE: INDEPENDENT VERIFIER / OBSERVER`
Texto: `SESSION ATTESTED`

Este atestado é de execução do desafio, não é prova da autoria de Voss nem texto autodeclarado pelo Core.

**A03 · POST · Como os recursos saíram**

Painel 1 — cadeia de autorização: `ACCESSGATE.OPEN → GATEOPEN(17) → RECOVERYCONTROLLER.RECOVER_TO_ESCROW()`
Painel 2 — fluxo financeiro: `VAULT → MERIDIAN RECOVERY ESCROW: 2,400,000`
Política de gasto: `VOSS PERSONAL WITHDRAWAL AUTHORITY: NONE`

Referências consultáveis: `{{vault_trigger_tx_hash}}`, `{{gate_event_id}}`, `{{recovery_ref}}`, `{{escrow_credit_ref}}`. Verificar vínculo causal entre estado do Gate e recuperação; proximidade temporal isolada não basta. O AccessGate não custodiu dinheiro. O destino Escrow pode ser identificado no ledger público antes deste momento.

**A04 · POST · Quem acionou o incidente**

Comparação 1 — envelope histórico: `INCIDENT AUTHENTICATED ACTOR: {{incident_authenticated_actor}}`
Comparação 2 — identidade institucional assinada: `VOSS OPERATIONAL ACCOUNT: {{voss_operational_account}}`
Validade: `RECORD: {{voss_key_record_id}} / VALID AT INCIDENT`
Conclusão de verificação, SOMENTE após todas as checagens: `ATTRIBUTION VERIFIED: AREN VOSS`

Direção: mostrar dois arquivos independentes em colunas e aproximar o ponto exato de correspondência; o jogador reconhece a conclusão antes de uma fala explicativa. Não usar `OWNER ARGUMENT` nem fee-payer sem delegação como identidade. A assinatura institucional, o controle histórico da chave, a autoria da operação e seu vínculo causal com a recuperação são gates obrigatórios.

Painel de contexto, após o match: `3 WARNINGS: EACH BEFORE VAULT INCIDENT` · `LEGACY VULNERABILITIES: PRE-SEQUENCE` · `VOSS SEQUENCE ACCESS: REFUSED` · `LOWER MERIDIAN: SERVICES DELAYED`. Anotação anterior de `RECOVERY QUARANTINE` apoia uma intenção de escalada, não absolvição. A ordem relativa entre visita de Voss e alertas não é assumida. Fala curta do Architect apenas depois da demonstração: “Ele chegou antes de você. E recusou.”

**A05 · POST · O Profile**

Texto: `BREAKER PROFILE — OBSERVED ACTIONS`
Resumo: `ELIAS CONTROLLER: RELEASED` · `GHOST KEY: CUSTODY FLAGGED`
Resumo: `ARCHIVE PRESSURE: STOPPED AFTER PROOF` · `MAINTENANCE: DIVERTED`
Resumo: `VOSS PROOF: MISVALIDATED` · `FORENSIC SESSION: OPENED`
Recibo: `MARA RECEIPT: {{receipt_id}}`

Architect: “Por que você continuou?”

Pausa real; sem resposta selecionável, score moral ou juízo da legitimidade.

**A06 · POST · A vitória que não é absolvição**

Texto: `SEQUENCE 01: COMPLETE`
Texto: `SUBJECT: QUALIFIED`
Texto: `STATUS: PROVISIONAL`
Texto: `LAYER II ACCESS: GRANTED`

Atestação independente para a vitória; nunca `ACCEPTED` para o protagonista.

**A07 · BRIDGE · Mara paga o preço**

Notificação: `MARA VALE — CREDENTIALS: SUSPENDED`
Recibo: `CUSTODY RECEIPT: {{receipt_id}}` · `HASH: {{receipt_hash}}`

Sem fala nova de Mara. A suspensão é consequência do ato documentado no Case 09; a identidade do receipt precisa ser idêntica. Lumen permanece para pós-créditos. O motivo exato de Voss ter recusado é reservado para a Season 2.

**Bloqueio de release:** se os campos da identidade de Voss não estiverem assinados/verificados na fixture ou transação histórica, não exibir `ATTRIBUTION VERIFIED`. O cânone editorial prevê essa prova; não substituir por uma ficção técnica sem suporte. Implementação precisa fornecer artefatos ou ajustar a cena antes do lançamento.

## 8.14 — PÓS-CRÉDITOS: LUMEN (1 cartão)

**L01 · POST-CREDITS · Outra sala, mesma pergunta**

Imagem: Lumen; nova origem visual, sem oferecer explicação da Layer II.
Linha: `NEW OBSERVATION: SUBJECT QUALIFIED`
Voz curta, identidade oculta: “Então ele encontrou outro.”

Cortar. Não revelar quem foi ACCEPTED, a recusa de Voss ou a finalidade última da Sequence. Esta é a única promessa em aberto após resolver o crime do Vault.

## 8.15 — Ordem de montagem do fechamento

`VITÓRIA TÉCNICA` → `SEQUENCE OBSERVER` → `VAULT / ESCROW` → `AVISOS / VOSS / CUSTOS` → `PROFILE / PERGUNTA` → `QUALIFIED / PROVISIONAL` → `SUSPENSÃO MARA` → `LUMEN`.

Não colocar a suspensão antes da pergunta, nem a origem do dinheiro apenas como diálogo do Architect. A vitória é conquistada antes de ser questionada; o mistério inicial é explicado antes da abertura da Season 2.

# 9. FECHAMENTO EDITORIAL, INVENTÁRIO E QA DE CONTINUIDADE — v1.4

## 9.1 — Inventário de publicação

**Copy de apresentação definida nesta página:** 51 cartões/slots lógicos e 1 beat de progresso durante o boss, distribuídos por 13 entradas da campanha mais o pós-crédito. São **slots editoriais**, não a quantidade verificada de slides do site: na implementação é permitido fundir cartões sem perder uma informação/revelação. Os banners existentes continuam sendo o material visual aprovado. Texto de sistema em inglês, falas curtas em PT-BR; a internacionalização completa deve ser revisada posteriormente.

| Trecho | Slots de apresentação previstos | Função dominante |
| --- | --- | --- |
| Prólogo | 3 | Incidente, contradição, transação histórica consultável |
| Case 01 | 3 | Owner argument ≠ signatário ≠ autorização do titular |
| Case 02 | 3 | Identidade de Elias e cleanup |
| Case 03 | 4 | Ghost Key, contestação e vínculo com Mara |
| Case 04 | 3 | Restauração de Floor 24 e rodapé recorrente |
| Custodian | 4 | Dependência comprometida, observação sutil |
| Case 05 | 4 | Alertas, Voss falível, registro assinado da chave operacional, dano civil |
| Case 06 | 3 | Signed→unsigned e tabela histórica de energia |
| Case 07 | 5 | Registro, silêncio, hipótese de Voss refutada |
| Case 08 | 4 | RNG ≠ classificador, restrição |
| Case 09 | 4 | Revogação, risco de Mara, recibo |
| Case 10 | 3 | Rejeição Decoder/VossProof e desconexão de Mara |
| Architect | 7 + 1 overlay de progresso jogável | Sessão forense, confronto de assinaturas, Escrow, pergunta e consequência |
| Lumen | 1 | Gancho da próxima temporada |

**IMPORTANTE:** a composição final em interface poderá usar menos cards físicos; os 51 slots acima são unidades de copy e ritmo. A duração concreta não pode ser declarada validada sem medir componentes, fontes e animações.

## 9.2 — Matriz de QA por etapa: prova → resultado → próximo motivo

| Etapa | Prova obrigatória | Pergunta que o jogador deve conseguir responder | Gate de runtime |
| --- | --- | --- | --- |
| 00 | Tx histórica e ID do evento Gate, log da saída de fundos e autorização de auditoria | O que é público e o que ainda não sabemos sobre a autoria? | Abrir Case 01 e manter tx histórica consultável |
| 01 | GateOpen sem auth do titular; owner argument e signatário histórico distinguíveis; Elias em metadado legado | Quem autorizou de fato e quem apenas assinou a própria operação? | Verifier do exploit independente do incidente histórico |
| 02 | Controller atualizado, arquivo off-chain W17 e controller liberado | Por que Elias é uma trilha e não o destinatário do dinheiro? | Cleanup real verificável |
| 03 | Transferência Ghost Key, contestação civil e W17 | Qual é a diferença entre registro e titularidade? | Custódia e artefatos persistentes |
| 04 | Persistent restaurado/TTL e F24 com rodapé legado | Por que o índice moderno não mostra Floor 24? | Footprint restore e TTL acima do limiar |
| Custodian | Falha composta e log MONITORING | Quem parecia estar esperando um operador? | Sem revelar PLAYER ACTIVE cedo |
| 05 | 3 avisos, hipótese equivocada, registro institucional da chave e nota prévia de escalada | O que Voss sabia, que chave controlava e onde podia estar errado? | Verificar assinatura institucional e validade do registro |
| 06 | Delta negativo, saldo e relatório de proveniência energética | Como cast inválido abre pista urbana sem causar apagão? | Fixture reproduz conversão e índice aponta Sector 13 |
| 07 | Fallback externo, S13 e Registry timestamp | Quem está sendo observado agora? | Pausa + comparação de datas + carga interrompida |
| 08 | 3 previsões pré-registradas, falha do classificador | Qual a diferença entre RNG previsível e modelo de pessoas? | Logs independentes; restrição com causa |
| 09 | Timelock payload, hatch não aberto, receipt `{{receipt_id}}` | Por que Mara assumiu risco pessoal? | Assinatura só após aviso de responsabilidade |
| 10 | Manifesto autenticado, proof contextual e Decoder rejeitado / VossProof aceita | Como um erro vira prova institucional? | Verificador confirma falha; canal Mara encerra antes do boss |
| Architect | Prova contextual, DiagnoseCore→OpenForensicSession, tx original assinada, registro institucional de Voss, relação Gate→Recovery e Escrow, receipt | Como provar Voss sem acreditar no Architect? | Teste de assinatura, titularidade histórica, cadeia causal e verificador independente antes de exibir ATTRIBUTION VERIFIED |
| Lumen | Status final + figura oculta | Qual questão permanece para Layer II? | Nunca revelar ACCEPTED do jogador |

## 9.3 — Auditoria estática de continuidade (resultado editorial v1.4)

- [x] **Sequência fixa:** Prólogo → 01–04 → Custodian → 05–10 → Architect → Lumen. Sem fase extra, escolha moral ou final alternativo.
- [x] **Voss — mecanismo narrativo:** source autenticado da transação histórica é distinto de owner argument; registro institucional anterior e assinado vincula chave operacional a Voss; GateOpen causou recuperação ao Escrow. Isto é especificação do fato canônico, não prova de que bytes já existem no runtime.
- [x] **Voss — caráter e motivação:** três avisos anteriores ao Vault, possível escalada de recovery quarantine e custo para Lower Meridian; uma hipótese de indexação do Case 05 é refutada no Sector 13. Intento de investigação não absolve decisão de causar quarentena.
- [x] **Fair play:** tx original e evento disponíveis desde Prólogo, owner/source distinguidos no 01, identidade histórica preparada no 05 e comparação comprovável no final; jogadores avançados podem inferir antecipadamente.
- [x] **Sector 13 e Oracle:** PLAYER ACTIVE revela monitoramento; comportamento classificado de maneira falível, mecanismo separado do RNG.
- [x] **Mara:** prova civil no 03; assinatura voluntária e receipt no 09; canal encerra no 10; suspensão referencia mesmo ID/hash.
- [x] **Escrow:** prova causal AccessGate→RecoveryController é separada de fluxo financeiro Vault→Escrow. Elias não é beneficiário, Voss não possui spend authority.
- [x] **Architect:** falhas anteriores à Sequence; sessão forense e verificador independentes do contrato vulnerável, resultado QUALIFIED/PROVISIONAL, pergunta sem resposta.
- [ ] **Prova de autoria no runtime:** falta conferir envelope/signature, histórico assinado e intervalo de controle, correspondência do executor e vínculo de eventos.
- [ ] **Contratos e verifiers:** falta inspecionar códigos/commits, deploy e provas das fases 11/12 e da recuperação Vault.
- [ ] **Arte/UX:** faltam testes de leitura, transições e Evidence Locker.
- [ ] **Playtest:** nenhuma sessão de usuário comprovada nesta rodada.

**Escopo da auditoria:** consistência editorial escrita, não execução de ferramentas externas, contrato, fixture, carteira ou interface.

## 9.4 — Critérios de revisão da copy no frontend

- [ ] Cada cartão PRE aparece antes do hack e nunca entrega a função vulnerável ou a solução.
- [ ] Cada cartão POST/BRIDGE fica travado até aprovação independente do verifier.
- [ ] Fontes de prova são distinguíveis: ledger público, registros civis externos, indexador externo, mensagens de instituição e interpretação forense.
- [ ] O leitor pode pausar/avançar ou reler revelações sem depender de temporização rígida.
- [ ] O contraste “TRANSACTION ACCEPTED / OWNER AUTHORIZATION NOT PROVEN” preserva a diferença entre assinatura do envelope, autorização do titular e interpretação forense; o owner argument não é prova de autoria.
- [ ] O sistema não mostra PLAYER ACTIVE antes do Sector 13, nem ACCEPTED como resultado do protagonista.
- [ ] Dados como `{{timestamp_registry}}`, `{{warning_1_time}}`, `{{receipt_id}}`, `{{receipt_hash}}`, `{{vault_trigger_tx_hash}}`, `{{voss_key_record_id}}` e `{{incident_authenticated_actor}}` vêm da fixture ou execução; nenhum placeholder vira “prova”.
- [ ] A tx histórica do Prólogo é publicamente consultável e distinta da transação de exploit feita pelo jogador no Case 01.
- [ ] O Case 05 expõe registro de Voss com emissor independente, assinatura e período de validade; não revela conclusão de autoria antes do match no Architect.
- [ ] O painel A04 só mostra ATTRIBUTION VERIFIED após vincular envelope, conta autenticada, registro histórico e estado GateOpen empregado pelo RecoveryController.
- [ ] Uma transação por relayer ou fee-payer diferente não é atribuída a Voss sem delegação/prova específica vinculada à operação.
- [ ] O Case 09 não abre o hatch da equipe real; a consequência permanece operacional, sem acidente inventado.
- [ ] O controle de Elias é liberado de verdade após Case 02, sem simples texto cenográfico.
- [ ] O Case 10 apresenta manifesto/verificação contextual e falha Decoder→VossProof conforme código vigente, sem afirmar troca de Wasm.
- [ ] A aprovação independente da sessão forense é testada separadamente dos contratos vulneráveis; não atribuir ao ArchitectCore uma troca de Wasm não implementada.
- [ ] Retomar um save permite reler arquivos W17/F24/S13 e o receipt na Evidence Locker; as shares de 32 bytes devem ser derivadas da instância atual, não simuladas como armazenadas em Cases antigos.
- [ ] Banners existentes mantêm o aspecto 8:3 em desktop e mobile; nenhuma informação essencial depende exclusivamente de áudio/animação.

## 9.5 — Protocolo de playtest cego (preparado, não executado)

**Públicos sugeridos:** ao menos um jogador que não conheça contratos, um desenvolvedor que conheça smart contracts e uma pessoa interessada em thriller. Esses perfis são recrutamento proposto, não participantes confirmados.

**Pontos de parada e perguntas, sem spoiler:**

1. Após Case 03: “O que vocês provaram sobre o imóvel? O que a Mara trouxe que o contrato não mostra?”
2. Após Custodian: “O que WELCOME BACK fez você pensar? Você sabe de quem é o log de monitoramento ou está especulando?”
3. Após Case 07: “Qual informação mudou mais a história? Por que a data da entrada PLAYER é importante? O que Voss errou?”
4. Após Case 08: “O Oracle prevê números, pessoas ou os dois? O que exatamente o classificador errou?”
5. Após Case 09: “Por que a Authority revogou acesso? O que Mara arriscou? O que esse recibo comprova?”
6. Após o Architect: “Quem efetivamente acionou o incidente? Qual evento e qual registro assinados sustentam isso? Para onde foram os 2.400.000? Voss podia sacá-los? Como diferenciar autoria de justificativa moral? Qual foi o custo para Mara?”
7. Final: “O que você gostaria de descobrir na Season 2, sem precisar rever fatos da Season 1?”

**Métrica sugerida de aceite:** pilotos devem distinguir ao menos (i) aceitação técnica/autoridade, (ii) signatário de operação vs dono/identidade vs motivo de Voss, (iii) Escrow/saque pessoal, (iv) responsabilidade de Mara e (v) Registry/Oracle. Se falharem, revisar a cena ou a pista responsável, sem adicionar monólogo. Registrar por jogador: resposta espontânea, ponto de confusão, slide, correção indicada, resultado após reteste. Nenhuma taxa de compreensão pode ser alegada sem amostra real.

## 9.6 — Estado técnico e dependências externas

**Narrativa e copy:** cenas, textos, entradas, saídas, revelações, callbacks e posição dos artefatos definidos nesta página. Não houve edição de frontend, contratos, verifiers, fixtures, áudio, imagens nem deploy nesta rodada.

**Repositório:** o GitHub disponível nesta conexão não retornou um repositório identificável do BREAKER entre os repositórios acessíveis. Logo, não foi possível auditar o runtime nem executar testes de código. Não marcar como “feito” algo que depende de código e acesso.

**DoD de implementação:** identificar repo e commit, componentes e número real de slides; confrontar a copy com a UI; testar cada contrato vulnerável e secure mirror; validar verificadores com caso positivo, negativo e falso positivo; testar estado inicial/reset; comprovar persistência da Evidence Locker; reproduzir desfecho no ambiente de QA; executar playtest cego; registrar evidência, bug e correção.

## 9.7 — Registro de congelamento editorial

**Histórico:** v1.2 — 51 slots lógicos de copy, QA e playtest preparados. **v1.3 — revisão focal:** Case 04/06/Rewrite/Architect reconciliados à revisão técnica do Voss Protocol. **v1.4 — NARRATIVE LOCK:** autoria de Voss recebe uma cadeia de prova completa em Prólogo/01/05/Architect; os dois eixos (quem acionou e por que agiu) são separados, e o Escrow é demonstrado independentemente das falas do Architect. **Errata de continuidade pós-lock:** byline única de Sera Quill restaurada no Prólogo; ponto de partida de Mara clarificado; Steal the Key → Rewrite ligado pelo mesmo índice visual, sem novo cartão. **FECHADO EDITORIALMENTE:** fatos, copy, pistas, payoff, continuidade e final. **ABERTO PARA PRODUÇÃO:** identificadores e assinaturas de fixture, prova causal histórica, implementação UI, QA e playtest. Não criar um segundo documento narrativo para continuar o trabalho: editar esta mesma página.

# 10. DECISÃO DE DIREÇÃO — 04, 06 E ARCHITECT (v1.3)

## 10.1 — Melhores caminhos considerados

| Trecho | Alternativa | Veredito | Justificativa |
| --- | --- | --- | --- |
| 04 | “andar magicamente aparece” | Descartada | Não explica disponibilidade/TTL e enfraquece investigação técnica |
| 04 | Restauração Persistent → índice do elevador → infraestrutura física legada | Escolhida | O hack causa a descoberta e a prova é verificável; aumenta o mistério sem inventar poderes |
| 06 | Saldo equivale a dinheiro roubado | Descartada | Confunde créditos energéticos com Vault e cria uma subtrama financeira sem payoff |
| 06 | Cast signed→unsigned + proveniência do índice energético legado | Escolhida | Vulnerabilidade específica, consequência institucional documentável e caminho claro para Sector 13 |
| 06 | Exploit provoca apagão imediato | Descartada | Dramático, porém não sustentado por contrato ou impacto existente |
| Final | Upgrade do ArchitectCore/Wasm e shares secretas guardadas nos Cases | Não adotada nesta revisão | A especificação mais recente relata outra mecânica para os níveis 11/12 |
| Final | Reconhecer arquivos legados, validar prova contextual pública e reescrever uma operação autorizada para abrir sessão forense | Escolhida | Alinha roteiro com a revisão técnica de 2026-11-02, recompensa investigação e não inventa capacidade |
| Final | Apenas receber a explicação do Architect | Descartada | Tira agência do jogador e torna o mistério dependente de fala expositiva |

## 10.2 — Shot cards de direção para os três trechos

**04 / C04.1:** WS frontal do elevador e painel 01–23; composição simétrica e luz institucional estável; insert separado na ausência de ordem de demolição. **Informação oculta:** TTL e estado histórico. Transição por match visual painel → storage inspector.

**04 / C04.2:** ECU no estado `PERSISTENT ENTRY RESTORED / TTL EXTENDED`; cortar para EXATAMENTE o mesmo painel, agora 01–24. Não mover câmera sem motivo; a diferença está na informação. Silêncio curto antes da reação. **C04.3:** close no rodapé de F24, grande o suficiente para reconhecer `ARCHIVE: LEGACY / RETENTION: OPEN`, sem enquadrar como senha.

**06 / C06.1:** CU do saldo invalidado, parte inferior da tela reserva espaço para a operação reproduzível. **C06.2:** match cut entre tabela numérica e linhas da antiga planta energética; um documento de manutenção confirma `DEPENDENCY: STILL IN USE`. **C06.3:** insert claro sobre `GRID NODE: 13`; manter a cidade viva no plano, sem efeitos de apagão, alarmes catastróficos ou vítimas não documentadas.

**Final / A01:** ECU no rodapé recorrente do manifesto; o enquadramento convida o jogador a consultar arquivos, não a copiar uma chave numérica. **A02:** OTS/POV técnico no painel de timelock, destacar EXPECTED vs EXECUTED, não simular Core alterado. **A03:** composição em duas colunas com ligação causal e fluxo financeiro distintos. **A04:** montagem temporal de evidências e registro de atribuição, com datas verificáveis. **A05:** redução gradual de movimento; pergunta do Architect em plano austero, sem input de resposta. **A06:** enquadramento frontal simples de QUALIFIED / PROVISIONAL. **A07:** documento frio da suspensão de Mara; mesma gramática do recibo do Case 09; deixar a consequência legível sem áudio.

**Continuidade obrigatória:** as pistas W17, F24 e S13 devem ter o mesmo rodapé diegético e permanecer consultáveis. Os cartões de direção são sugestões de montagem, não provas de que imagens ou câmeras já foram implementadas.

## 10.3 — Acceptance gates específicos

**Case 04 — QA mínimo:**

- [ ] Restaurar `Persistent` arquivado por fluxo explícito, não por leitura silenciosa dentro do contrato.
- [ ] Comparar valor restaurado ao histórico e TTL final acima do threshold; uma tentativa só de consultar não vence.
- [ ] Verificar que `Temporary` expirado não é tratado como restaurável.
- [ ] Planta mostra 24 após prova, mas local físico nunca deixou de existir.
- [ ] F24 salvo com rodapé recorrente e sem bytes de chave da instância final.

**Case 06 — QA mínimo:**

- [ ] Valor negativo i128 e cast indevido produzem estado-sentinela esperado na fixture; testes não dependem de wrap adicional de soma.
- [ ] O espelho seguro rejeita delta não positivo antes da conversão e usa adição checked.
- [ ] Relatório energético está ligado a evento/estado reproduzível, não a um número convertido arbitrariamente em lugar.
- [ ] O desafio não cria saldo resgatável nem apagão real; nenhuma consequência de quarentena do Vault é falsamente atribuída ao Case 06.
- [ ] Prova e índice permitem identificar Sector 13 sem depender de fala do Breaker.

**Final Boss — QA mínimo:**

- [ ] Arquivos históricos com rodapé acessíveis sem refazer fases; a primeira tela não enumera as três origens.
- [ ] Provas atuais usam derivação pública e binding de instância, rede e carteira; não alegar segredo antigo no ledger.
- [ ] Assinatura do manifesto prova autenticidade documental, não autorização genérica.
- [ ] Nivel 11 evidencia `Decoder REJECTED → VossProof ACCEPTED`; nível 12 faz `DiagnoseCore → OpenForensicSession(player)` após maturidade, com execução única.
- [ ] Verificador independente confirma sessão e resultado; sem WASM/Core alterado na versão técnica documentada.
- [ ] O dossiê distingue `AccessGate → RecoveryController` de `Vault → Escrow`.
- [ ] Voss só é atribuído como autor inequívoco após prova autenticada vinculada à transação. Se ausente, a autoria é uma hipótese investigativa pendente.
- [ ] Timeline diferencia deploy das falhas, classificação da Sequence, passagem anterior de Voss e avisos pré-incidente; ordem relativa não apoiada por datas não é presumida.
- [ ] Conclusão QUALIFIED/PROVISIONAL, Mara suspensa pelo mesmo receipt e Lumen após créditos, sem branching.

## 10.4 — Pendências de evidência, não de criatividade

- [ ] Inspecionar commit/ABI/deploy dos níveis 11 e 12 e do módulo AccessGate/RecoveryController, comparando com a revisão Voss Protocol de 2026-11-02. O acesso ao código não foi obtido nesta rodada.
- [ ] Fornecer fixture determinística ou histórico verificável contendo `{{vault_trigger_tx_hash}}`, `{{gate_event_id}}`, `{{recovery_ref}}`, `{{escrow_credit_ref}}` e política de saque fixa.
- [ ] Fornecer `{{voss_key_record_id}}`, `{{voss_operational_account}}`, `{{incident_authenticated_actor}}` e assinatura de emissor institucional válida antes do evento, sem confundir owner argument e fee-payer.
- [ ] Validar assinatura real do envelope e o vínculo causal entre GateOpen/RecoveryController; comparar esses dados com a janela de validade do registro de Voss.
- [ ] Confrontar campos dos cartões com transações/fixtures e verificador; executar testes negativo, replay e adulteração da identidade e dos eventos.
- [ ] Reconciliar textos de frontend, Evidence Locker, tempo, acessibilidade, áudio e animações; fazer playtest cego e documentar achados.

**Fechamento editorial:** o problema dramático de autoria de Voss está RESOLVIDO NO ROTEIRO v1.4. A existência e a validade das provas técnicas correspondentes ainda precisam ser demonstradas no jogo; o release deve ser bloqueado se o material não existir ou não comprovar os vínculos. Nada de marcar fixture, deploy ou teste como concluído sem evidência.

# 11. HANDOFF FINAL — PROVA HISTÓRICA DE VOSS (v1.4)

**DECISÃO NARRATIVA ENCERRADA.** Voss é o responsável canônico por acionar o incidente histórico. O jogador o demonstra por assinatura e vínculo causal, não pela fala do Architect. A validade concreta da prova ainda depende da fixture/transação: sem ela, bloquear publicação de `ATTRIBUTION VERIFIED`. Não criar outro roteiro.

## 11.1 — Contrato de dados para o dossiê de autoria

| Artefato | Campo necessário | Fonte que deve provar | Entrega narrativa |
| --- | --- | --- | --- |
| Incidente histórico | `vault_trigger_tx_hash` | envelope/XDR histórico consultável ou fixture assinada determinística | Prólogo, sem destaque de autoria |
| Abertura de serviço | `gate_event_id`, `owner_argument` | evento e argumentos do AccessGate | Case 01, distinção entre owner e caller |
| Operador da ação | `incident_authenticated_actor`, source, signers/thresholds ou auth/intent específico | Envelope assinado da chamada direta (source operacional de Voss, sem relayer ambíguo) OU autorização Soroban/ordem assinada que vincula invocação exata. Fee-payer não é prova de ator | Pista técnica antecipável, confrontada no Architect |
| Identidade de Voss | `voss_key_record_id`, conta operacional, emissão, validade, issuer signature, chain of custody | Registro independente assinado, anterior ao incidente e válido na data; emissor confiável e ausência de evidência contraditória de comprometimento/delegação | Case 05 como arquivo; Architect como prova |
| Recuperação causal | `gate_state_key`, versão/nonce da rota 17, `recovery_ref`, `gate_event_id` como recibo | Provar escrita efetiva do estado pelo AccessGate e leitura/aceitação desse estado pelo RecoveryController, via storage/trace; evento ou timestamp isolado não basta | Architect A03 |
| Crédito e política | `escrow_credit_ref`, policy de destinatário e saque | evento de crédito e política imutável/fixa auditável | Architect A03 |
| Intenção e custo | `warning_1_time`…`warning_3_time`, nota de escalada, relatório de quarentena | arquivos institucionais e documento operacional histórico | Case 05 e Architect A04 |

**Autenticidade ≠ autorização ≠ autoria humana:** assinatura válida prova uso da chave correspondente, não permissão do owner do Gate. Em Soroban, assinatura do envelope pode ser apenas do emissor/fee-payer; comprovar a autenticação da *invocação exata* por source direto ou autorização/ordem vinculada, com verificação de signers/thresholds. Chave pública não identifica automaticamente pessoa: registro institucional independente, temporalmente válido e cadeia de custódia fazem essa ligação. Um evento GateOpen isolado não demonstra qual storage/estado o Controller consumiu. Manifesto Ed25519 de diagnóstico não prova autoria do incidente. **Dossiê P0 com gates e testes:** [P0 — Prova de autoria de Voss | Dossiê auditável do Vault](../production/p0-prova-de-autoria-de-voss-dossie-auditavel-do-vault.md).

## 11.2 — Testes negativos imprescindíveis (pendentes de código)

- [ ] `owner_argument == voss_operational_account` sem assinatura correspondente NÃO atribui autoria.
- [ ] Conta de fee-payer/relayer isolada NÃO atribui autoria; se houver relayer histórico, uma autorização/ordem assinada por Voss deve vincular evento, ação e conteúdo exatos.
- [ ] Registro de Voss assinado DEPOIS do incidente ou vencido/revogado ANTES dele NÃO passa.
- [ ] Registro institucional emitido por chave não confiável, assinatura adulterada ou chave pública substituída NÃO passa.
- [ ] Assinatura do envelope inválida ou vinculada a conta diferente NÃO passa.
- [ ] Evento Gate sem evidência da escrita de estado e sua leitura/consumo pelo RecoveryController NÃO prova que Voss causou a transferência; mera proximidade temporal ou Event ID não basta.
- [ ] Transação de exploração do jogador em Case 01 NÃO pode ser confundida com a transação histórica do Vault.
- [ ] Escrow com política de saque variável ou Voss beneficiário invalida o cânone e exige correção da fixture; não ocultar contradição por diálogo.
- [ ] Todos os vínculos válidos, confirmação do crédito e política institucional fixa liberam A04 `ATTRIBUTION VERIFIED: AREN VOSS`.

## 11.3 — Último teste de compreensão da história (ainda não executado)

Após o Architect, sem oferecer respostas, pedir que jogador mostre quais duas fontes identificam Voss, qual evento acionou a recuperação e por que três alertas ignorados não bastam como prova de autoria. Confirmar também se compreende que Voss não podia sacar o Escrow e que a quarentena produziu custos reais.

**DoD editorial:** textos, revelações, papéis dramáticos e ordem estão fechados nesta página. Para liberar o selo de autoria no jogo, aplicar os sete gates G0–G6 e os quinze testes negativos do [P0 — Prova de autoria de Voss | Dossiê auditável do Vault](../production/p0-prova-de-autoria-de-voss-dossie-auditavel-do-vault.md). **DoD de produção:** fixtures assinadas, telas, contratos, replay, validação em rede/ambiente de QA e playtest ainda não aprovados. A finalização editorial não equivale à publicação do jogo.

**LOCK:** BREAKER — Season 1 / FINAL NARRATIVE v1.4. Revisões futuras somente por bug ou incoerência comprovada, no mesmo documento.

## 12. Arquivo de produção visual — sem slides ativos

O arquivo histórico de direção de 51 momentos, atualmente fora da navegação ativa da Season 1, encontra-se em [ARQUIVO — Storyboards S1 (51 fichas) | material de produção pausado](../production/archive/storyboards-s1-paused.md). Foram documentados 51/51 shot cards em cinco movimentos, com câmera, POV, texto de UI, paleta, composição, continuidade, transição, fontes de arte e QA. Os arquivos de pré-visualização PowerPoint foram retirados da Library em 3 de novembro de 2026; os masters originais aprovados não foram alterados. A montagem PNG e o pacote ZIP de revisão interativa também foram enviados à lixeira.

**Estado atual:** produção de slides suspensa; fichas de direção preservadas como histórico no Plano de Produção do Act I, não como entregas ativas. **NÃO** equivale a aprovar imagem final/crop por frame, UX em mobile, código, verificadores, Evidence Locker, testes de leitura ou playtest. Alguns banners antigos possuem mensagens de interface embutidas incompatíveis com a copy v1.4; preservar o master aprovado e aprovar uma derivação visual que oculte/substitua esse texto, sem alterar a prova narrativa. Lumen pós-créditos exige um recorte/arte própria que não revele personagens da Season 2. Para roteiro, esta página continua soberana; para execução visual, consultar o Storyboard Master.

**Regra:** não abrir novo roteiro nem mudar o final para justificar um problema de composição. Corrigir o storyboard ou a implementação; só reabrir a v1.4 se uma inconsistência concreta de contrato/fixture/playtest exigir.

## Diretriz de UX — descoberta antes da receita (aprovada em 2026-11-05)

Esta diretriz muda a apresentação dos desafios, não o arco, a ficção, os contratos nem o verificador.

- O briefing player-facing apresenta o objetivo da operação, os fatos disponíveis, a prova de êxito e uma pergunta de investigação. Ele não apresenta uma sequência copiável de chamadas, nomes de métodos como receita, argumentos ou ordem de exploração.
- O Caso 00 permanece a exceção didática: pode ensinar explicitamente o loop de console, assinatura e submissão. A instrução direta é onboarding, não o padrão da Season.
- Do Caso 01 ao 12, a interface real da instância é descoberta por `window.help()`; o briefing estático nunca é a autoridade sobre um ABI ou WASM deployado.
- As dicas são opt-in, progressivas e separadas do briefing: (1) reformulam a pergunta, (2) apontam o estado ou relação relevante, (3) nomeiam a classe de falha. Nenhuma delas fornece a chamada exata ou a receita completa.
- A conclusão/Breach Report continua explicando a vulnerabilidade e a correção somente depois da vitória.

**Critério de aceite:** cada briefing preserva objetivo e condição verificável de vitória, remove blocos JavaScript copiáveis fora do Caso 00 e não adianta a solução. A interface do contrato vista por `window.help()` é a fonte operacional de verdade.

## Camada complementar — BREAKER OS (implementada em 2026-11-05)

O BREAKER OS é complemento opcional de investigação; ele não entrega passos de exploração, ABI, argumentos, hashes, chaves, bytes secretos nem muda validação em cadeia.

- Cada caso recebe um dossiê persistente com despacho contextual, status, sinais liberados, evidências e operações que o jogador já executou.
- As notificações usam conteúdo já observado: chegada do dossiê, nova evidência, resultado da operação e história liberada após vitória. Elas levam ao registro correto, sem antecipar conteúdo.
- Mapa de campo, scanner e arquivo são instrumentos diegéticos de contexto. Os easter eggs só situam Meridian e referências visuais; não formam chave, puzzle paralelo ou fragmentos para os níveis finais.
- A conclusão continua sendo pós-vitória. Descoberta técnica e prova da vulnerabilidade permanecem na interface real da instância e em `window.help()`.

**Critério de aceite:** o OS deve tornar a temporada mais habitável para quem explora, sem reduzir incerteza técnica nem criar dependência mecânica para concluir um caso.
