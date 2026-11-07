---
notion_id: 40c9c563-0425-81cb-b4f2-c2c801ec0ea5
source: https://app.notion.com/p/40c9c563042581cbb4f2c2c801ec0ea5?pvs=204
title: "🎬 09 — Roteiro de Gameplay & Slides — Season 3"
exported_at: 2026-11-07
---

**Plano editorial dos slides — Season 3.** Cada beat é uma função narrativa, não uma tela obrigatória nem um asset novo. Ajustar ao frontend existente após inventário de componentes. Nada aqui modifica o cânone, o resultado único ou a ordem de Cases; challenge técnico fica no Breaker OS, com Breach Report opcional e posterior.

# Regra cinematográfica

Moonlight não deve virar uma aula expositiva sobre ZK. O player experimenta a perseguição, recebe um indício e age. Depois do breach, observa a consequência humana e uma nova forma de ameaça. Evitar repetir a mesma perseguição em cada Case; variar **o que os Witnesses descobrem** e **o que o Breaker aprende a reduzir**. Diálogos curtos, interfaces concretas, pausas em revelações e arte 8:3 como base, sem assumir número de slides já implementados.

# Prologue — The Valid Transfer

**Entrada:** chegada a Moonlight em silêncio; settlement recebida com amount escondido. A tela mostra **PROOF VALID** para a operação e **ASSOCIATION DENIED** no estado atual — não são afirmações sobre o mesmo momento.

First Witness: “Precisamos da sua chave de visualização.” Breaker: “Para essa transação?” First Witness: “Para tudo.”

**Saída:** Breaker recusa a exigência abrangente. **WITNESS ORDER ISSUED**. Primeira rota de safehouse identificada sem quebrar cifra.

# 01 — The Public Secret

**Antes:** safehouse do Blind Quarter identificada. Sera apresenta apenas o identificador SOURCE E.V., nunca o nome da fonte; Breaker interrompe tentativa de contatar Mara antes do envio.

Missão: **DESCUBRA COMO ENCONTRARAM A SAFEHOUSE.**

**Depois:** credencial sensível recuperável diretamente de state público. O registro técnico aponta onde os Witnesses obtiveram a pista; nenhuma “chave de acesso privilegiado” é necessária para ler ledger público.

**Gancho:** nova rota sem segredo em storage é rastreada por logs.

# 02 — The Loud Whisper

**Antes:** state sensível protegido por commitments/ciphertext; eventos sobrepostos exibem detalhes que não deveriam sair do contrato.

Missão: **LEIA O QUE OS EVENTOS REVELAM SEM ABRIR O SEGREDO.**

**Depois:** um mosaico de events reconstrói ligação operacional. Não dizer que eventos são “privados” por padrão.

**Gancho:** compliance profile do Breaker aparece associado a rota DENIED.

# 03 — Someone Else's Face

**Antes:** perfil mudou, embora o Breaker não tenha autorizado alteração. O ataque de laboratório demonstra outro caminho possível de manipulação de registros, **não prova** quem causou o DENIED histórico.

Missão: **MOSTRE COMO UM REGISTRO PODE ATRIBUIR A ALGUÉM UMA IDENTIDADE FALSA.**

**Depois:** gravação de mudança sem auth adequada; investigação aponta para eventos de governança do Association Provider.

# 04 — The Denied

**Antes:** **CANCELLED** no evento, **PENDING ADMIN** ainda em storage. Qual dos dois o contrato realmente aplica?

Missão: **DEMONSTRE QUE UMA AUTORIDADE REVOGADA AINDA CONSEGUE AGIR.**

**Depois:** timeline de policy na execução, cancelamento, aceitação indevida e DENIED posterior. Sem revelar metadados privados além do necessário.

**Gancho:** First Witness encontra o Breaker; apenas conhecer a falha não basta para encerrar ordem.

# BOSS I — The Witness

**Antes:** a Spire exige acesso integral. O player conhece public storage, event leaks, association e pending admin.

Missão: **ESCAPE SEM ENTREGAR UMA VISÃO COMPLETA.**

**Durante:** selecionar e executar rota com disclosure mínimo, preservando provas de governança e evitando leaks já conhecidos; sem bug novo.

**Depois:** fuga temporária e novo método institucional: **NULLIFIER USED TWICE / SUBJECT BREAKER**. Não dizer que isso prova dois gastos legítimos atribuíveis a ele.

# 05 — Spent Twice

**Antes:** prova de nullifier repetido. Uma identidade acusada, uma implementação incompleta.

Missão: **MOSTRE COMO UMA NOTE PODE SER GASTA DUAS VEZES EM UM POOL VULNERÁVEL.**

**Depois:** replay na fixture mostra falha do spent-check; não criar segunda transferência histórica real. Rhea é sender do settlement original; dois witnesses necessários.

Rhea: “Você não consegue limpar seu nome sem mim.” Breaker: “E você não consegue limpar o seu sem mim.”

# 06 — The Proof That Lied

**Antes:** **PROOF VALID**, mas o claim acusa alguém com base em uma relação que o circuito não impõe.

Missão: **PROVE UMA AFIRMAÇÃO FALSA SEM VIOLAR O VERIFIER DESTE CIRCUITO.**

**Depois:** o verifier aceita proof, mas input/witness não vincula recipient, commitment e claim. A prova é válida para a regra errada. Rhea entrega fragmento autenticado voluntariamente.

Breaker: “A prova é válida. A afirmação não.”

# 07 — The Glass Trail

**Antes:** amounts privados, mas horário e endereços levam a hipóteses sobre conexões.

Missão: **RECONSTRUA UMA ROTA PROVÁVEL SEM CONHECER OS VALORES.**

**Depois:** player observa como Witnesses reconstruíram a própria rede; analisa alternativas e aprende a reduzir associação prospectiva. Compartilha com Rhea vínculo institucional de Lumen em escopo limitado e visivelmente arriscado. Ela protege essa informação de forma sincera.

# 08 — The Key That Sees

**Antes:** credencial de auditoria exibe expiry ultrapassado; consumer ainda responde.

Missão: **DEMONSTRE QUE ACESSO DE AUDITORIA CONTINUA OPERANDO APÓS EXPIRAR.**

**Depois:** comparar **EXPIRY** e **ACCESS GRANTED**. Rhea coloca sua origem em risco para documentar a prova; Breaker a protege.

Rhea: “Isso não devia existir.” Breaker: “Auditoria não é o problema.”

# 09 — A Valid Lie

**Antes:** proof pode ser válida sob uma VK diferente daquela correspondente à policy que a Spire deveria impor.

Missão: **DESCUBRA O QUE O VERIFIER REALMENTE VERIFICOU.**

**Depois:** circuito correto esperado versus version/hash/VK efetivos. Rhea tenta destruir a capability de disclosure; Breaker impede.

Breaker: “Você consegue quebrar isso. Não significa que deve.” Rhea respeita. Esse confronto acontece **uma só vez**.

**Gancho:** registro de outro operador **MISSING** sugere que existe uma forma de romper observação presente.

# 10 — Become Missing

**Antes:** prova final está pronta, mas chegar à Spire exige atravessar trilhas de metadados.

Rhea: “Se você desaparecer agora, não vou conseguir encontrar você.” Breaker: “Esse é o objetivo.”

Missão: **REDUZA A CORRELAÇÃO ATÉ O OBSERVADOR PERDER A ROTA.**

**Depois:** commitments/nullifiers seguros, timing e enlaces reduzidos dentro do threat model. **OBSERVATION CONFIDENCE: 81% → 54% → 19% → INSUFFICIENT**. **MISSING** operacional.

# FINAL — The Witness Spire

**Antes:** First Witness tem uma acusação plausível. Sera e E.V. são terceiros sob risco de full disclosure.

Missão: **PROVE A LEGITIMIDADE DA SETTLEMENT SEM REVELAR TERCEIROS.**

**Durante:** separar prova acusatória insuficiente (Cases 05/06/09) de prova positiva da settlement (state/policy históricos, sender+recipient witnesses e commitment). Evitar divulgação total.

**Depois:** **CLAIM: ORIGINAL SETTLEMENT COMPLIED AT EXECUTION** / **PROOF PACKAGE: VALID** / **DISCLOSURE: CLAIM ONLY**. Sistema exige full disclosure; First Witness: “A prova é suficiente.” **WITNESS ORDER CLOSED.** Pausa de alívio: é vitória real.

# EPÍLOGO — O Sétimo

**Beat 1:** somente depois do encerramento chega notificação separada de Lumen: atribuição da intervenção emergencial, assinada por Rhea. Credencial intercity suspensa; wallet e prova de inocência intactas.

**Beat 2:** “Em Lumen, você sacrificou um mercado para salvar seis. Dessa vez o sétimo fui eu.” Rhea não comemora nem apresenta justificativa triunfal.

**Beat 3:** RESTORE OBSERVABILITY aparece como **registro/ação do protagonista** e resolve **NO** no cânone. Não oferecer escolha YES/NO com resultados diferentes ou opção falsa clicável. O Breaker usa sua capacidade operacional de MISSING para prosseguir, apesar do custo.

**Beat 4:** rastro histórico de Voss aponta para Horizon/Galexie.

# Corte e QA editorial

- [ ] Cada beat cabe nas artes e áreas de texto do site; número real de slides por Case não verificado.
- [ ] Nenhum slide antecipa a solução do desafio.
- [ ] Todo Case possui efeito de observação, prova adquirida e motivo para seguir.
- [ ] Breach Report contém vulnerabilidade/fix fora dos slides, inclusive nos Cases de threat model e composição correta.
- [ ] A confiança Rhea/Breaker tem ações e custos, não apenas frases.
- [ ] O Sétimo não é anunciado antes da vitória conjunta, mas é retrospectivamente justo.

# Revisão de cenas aprovada — causalidade sem diálogos longos

- **Prologue:** inserir `GUARANTEE RETURN / HISTORICAL POLICY: VALID / CURRENT ASSOCIATION: DENIED / NETWORK RISK FLAG`. First Witness exige revisão excepcional do dossiê; ele ainda não tem prova de fraude.
- **Case 01 / Sera:** `SOURCE E.V.` e `DOCUMENT CONTENT VERIFIED / ORIGIN ENVELOPE SEALED`. Não revelar Eli Venn ao player.
- **Case 04:** mostrar quatro fatos: cancelamento, pending não removido, aceitação pelo operador institucional de compliance e posterior DENIED por alerta de risco. Isso justifica o status, não prova má-fé.
- **Case 07:** duas identidades parecem não coincidir; Breaker compartilha com Rhea apenas atestação contextual de beneficiário histórico, com aviso de risco. Rhea respeita o limite naquele momento.
- **Case 09/10:** `SENDER WITNESS PACKET: SEALED / COMMITMENT MATCH`; **depois** ocorre separação. Sem reencontro narrativo no Final.
- **Final:** Breaker comparece fisicamente à sessão, assina claim restrita, é reconhecido e ainda não revela rota de chegada/saída. First Witness observa que a exigência de full disclosure revelaria metadados irrelevantes à claim, inclusive origem de Sera. Prova mínima vence; pausa antes de O Sétimo.
- **Epílogo:** a atribuição da intervenção de Lumen chega por processo independente e somente depois de WITNESS ORDER CLOSED. O protagonista mantém MISSING pela rota futura, sem menu YES/NO.

**Regra:** estes beats não exigem um slide novo por linha. Integrar nas telas existentes sem dar spoiler de exploit antes de seu desafio.
