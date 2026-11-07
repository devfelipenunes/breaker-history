---
notion_id: 40c9c563-0425-81cb-b4f2-c2c801ec0ea5
source: https://app.notion.com/p/40c9c563042581cbb4f2c2c801ec0ea5?pvs=204
title: "🎬 09 — Roteiro de Gameplay & Slides — Season 3"
exported_at: 2026-11-07
---

Here is the result of "fetch" for the Page with URL https://app.notion.com/p/40c9c563042581cbb4f2c2c801ec0ea5 as of 2026-11-03T00:02:11.332Z:
<page url="https://app.notion.com/p/40c9c563042581cbb4f2c2c801ec0ea5" icon="🎬">
<ancestor-path>
<parent-page url="https://app.notion.com/p/4019c56304258179bfa0fc93d15ac390" title="Season 03 — Shadows of Privacy — Moonlight"/>
<ancestor-2-page url="https://app.notion.com/p/4019c563042581469a0edc7e30a6eff9" title="ACT I — The World Is Breakable"/>
<ancestor-3-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
<properties>
{"title":"09 — Roteiro de Gameplay & Slides — Season 3"}
</properties>
<iconMetadata>{"type":"emoji","emoji":"🎬"}</iconMetadata>
<content>
<callout icon="🎬" color="purple_bg">
<b>Plano editorial dos slides — Season 3.</b> Cada beat é uma função narrativa, não uma tela obrigatória nem um asset novo. Ajustar ao frontend existente após inventário de componentes. Nada aqui modifica o cânone, o resultado único ou a ordem de Cases; challenge técnico fica no Breaker OS, com Breach Report opcional e posterior.
</callout>

# Regra cinematográfica

Moonlight não deve virar uma aula expositiva sobre ZK. O player experimenta a perseguição, recebe um indício e age. Depois do breach, observa a consequência humana e uma nova forma de ameaça. Evitar repetir a mesma perseguição em cada Case; variar <b>o que os Witnesses descobrem</b> e <b>o que o Breaker aprende a reduzir</b>. Diálogos curtos, interfaces concretas, pausas em revelações e arte 8:3 como base, sem assumir número de slides já implementados.

# Prologue — The Valid Transfer

<b>Entrada:</b> chegada a Moonlight em silêncio; settlement recebida com amount escondido. A tela mostra <b>PROOF VALID</b> para a operação e <b>ASSOCIATION DENIED</b> no estado atual — não são afirmações sobre o mesmo momento.

First Witness: “Precisamos da sua chave de visualização.” Breaker: “Para essa transação?” First Witness: “Para tudo.”

<b>Saída:</b> Breaker recusa a exigência abrangente. <b>WITNESS ORDER ISSUED</b>. Primeira rota de safehouse identificada sem quebrar cifra.

# 01 — The Public Secret

<b>Antes:</b> safehouse do Blind Quarter identificada. Sera apresenta apenas o identificador SOURCE E.V., nunca o nome da fonte; Breaker interrompe tentativa de contatar Mara antes do envio.

Missão: <b>DESCUBRA COMO ENCONTRARAM A SAFEHOUSE.</b>

<b>Depois:</b> credencial sensível recuperável diretamente de state público. O registro técnico aponta onde os Witnesses obtiveram a pista; nenhuma “chave de acesso privilegiado” é necessária para ler ledger público.

<b>Gancho:</b> nova rota sem segredo em storage é rastreada por logs.

# 02 — The Loud Whisper

<b>Antes:</b> state sensível protegido por commitments/ciphertext; eventos sobrepostos exibem detalhes que não deveriam sair do contrato.

Missão: <b>LEIA O QUE OS EVENTOS REVELAM SEM ABRIR O SEGREDO.</b>

<b>Depois:</b> um mosaico de events reconstrói ligação operacional. Não dizer que eventos são “privados” por padrão.

<b>Gancho:</b> compliance profile do Breaker aparece associado a rota DENIED.

# 03 — Someone Else's Face

<b>Antes:</b> perfil mudou, embora o Breaker não tenha autorizado alteração. O ataque de laboratório demonstra outro caminho possível de manipulação de registros, <b>não prova</b> quem causou o DENIED histórico.

Missão: <b>MOSTRE COMO UM REGISTRO PODE ATRIBUIR A ALGUÉM UMA IDENTIDADE FALSA.</b>

<b>Depois:</b> gravação de mudança sem auth adequada; investigação aponta para eventos de governança do Association Provider.

# 04 — The Denied

<b>Antes:</b> <b>CANCELLED</b> no evento, <b>PENDING ADMIN</b> ainda em storage. Qual dos dois o contrato realmente aplica?

Missão: <b>DEMONSTRE QUE UMA AUTORIDADE REVOGADA AINDA CONSEGUE AGIR.</b>

<b>Depois:</b> timeline de policy na execução, cancelamento, aceitação indevida e DENIED posterior. Sem revelar metadados privados além do necessário.

<b>Gancho:</b> First Witness encontra o Breaker; apenas conhecer a falha não basta para encerrar ordem.

# BOSS I — The Witness

<b>Antes:</b> a Spire exige acesso integral. O player conhece public storage, event leaks, association e pending admin.

Missão: <b>ESCAPE SEM ENTREGAR UMA VISÃO COMPLETA.</b>

<b>Durante:</b> selecionar e executar rota com disclosure mínimo, preservando provas de governança e evitando leaks já conhecidos; sem bug novo.

<b>Depois:</b> fuga temporária e novo método institucional: <b>NULLIFIER USED TWICE / SUBJECT BREAKER</b>. Não dizer que isso prova dois gastos legítimos atribuíveis a ele.

# 05 — Spent Twice

<b>Antes:</b> prova de nullifier repetido. Uma identidade acusada, uma implementação incompleta.

Missão: <b>MOSTRE COMO UMA NOTE PODE SER GASTA DUAS VEZES EM UM POOL VULNERÁVEL.</b>

<b>Depois:</b> replay na fixture mostra falha do spent-check; não criar segunda transferência histórica real. Rhea é sender do settlement original; dois witnesses necessários.

Rhea: “Você não consegue limpar seu nome sem mim.” Breaker: “E você não consegue limpar o seu sem mim.”

# 06 — The Proof That Lied

<b>Antes:</b> <b>PROOF VALID</b>, mas o claim acusa alguém com base em uma relação que o circuito não impõe.

Missão: <b>PROVE UMA AFIRMAÇÃO FALSA SEM VIOLAR O VERIFIER DESTE CIRCUITO.</b>

<b>Depois:</b> o verifier aceita proof, mas input/witness não vincula recipient, commitment e claim. A prova é válida para a regra errada. Rhea entrega fragmento autenticado voluntariamente.

Breaker: “A prova é válida. A afirmação não.”

# 07 — The Glass Trail

<b>Antes:</b> amounts privados, mas horário e endereços levam a hipóteses sobre conexões.

Missão: <b>RECONSTRUA UMA ROTA PROVÁVEL SEM CONHECER OS VALORES.</b>

<b>Depois:</b> player observa como Witnesses reconstruíram a própria rede; analisa alternativas e aprende a reduzir associação prospectiva. Compartilha com Rhea vínculo institucional de Lumen em escopo limitado e visivelmente arriscado. Ela protege essa informação de forma sincera.

# 08 — The Key That Sees

<b>Antes:</b> credencial de auditoria exibe expiry ultrapassado; consumer ainda responde.

Missão: <b>DEMONSTRE QUE ACESSO DE AUDITORIA CONTINUA OPERANDO APÓS EXPIRAR.</b>

<b>Depois:</b> comparar <b>EXPIRY</b> e <b>ACCESS GRANTED</b>. Rhea coloca sua origem em risco para documentar a prova; Breaker a protege.

Rhea: “Isso não devia existir.” Breaker: “Auditoria não é o problema.”

# 09 — A Valid Lie

<b>Antes:</b> proof pode ser válida sob uma VK diferente daquela correspondente à policy que a Spire deveria impor.

Missão: <b>DESCUBRA O QUE O VERIFIER REALMENTE VERIFICOU.</b>

<b>Depois:</b> circuito correto esperado versus version/hash/VK efetivos. Rhea tenta destruir a capability de disclosure; Breaker impede.

Breaker: “Você consegue quebrar isso. Não significa que deve.” Rhea respeita. Esse confronto acontece <b>uma só vez</b>.

<b>Gancho:</b> registro de outro operador <b>MISSING</b> sugere que existe uma forma de romper observação presente.

# 10 — Become Missing

<b>Antes:</b> prova final está pronta, mas chegar à Spire exige atravessar trilhas de metadados.

Rhea: “Se você desaparecer agora, não vou conseguir encontrar você.” Breaker: “Esse é o objetivo.”

Missão: <b>REDUZA A CORRELAÇÃO ATÉ O OBSERVADOR PERDER A ROTA.</b>

<b>Depois:</b> commitments/nullifiers seguros, timing e enlaces reduzidos dentro do threat model. <b>OBSERVATION CONFIDENCE: 81% → 54% → 19% → INSUFFICIENT</b>. <b>MISSING</b> operacional.

# FINAL — The Witness Spire

<b>Antes:</b> First Witness tem uma acusação plausível. Sera e E.V. são terceiros sob risco de full disclosure.

Missão: <b>PROVE A LEGITIMIDADE DA SETTLEMENT SEM REVELAR TERCEIROS.</b>

<b>Durante:</b> separar prova acusatória insuficiente (Cases 05/06/09) de prova positiva da settlement (state/policy históricos, sender+recipient witnesses e commitment). Evitar divulgação total.

<b>Depois:</b> <b>CLAIM: ORIGINAL SETTLEMENT COMPLIED AT EXECUTION</b> / <b>PROOF PACKAGE: VALID</b> / <b>DISCLOSURE: CLAIM ONLY</b>. Sistema exige full disclosure; First Witness: “A prova é suficiente.” <b>WITNESS ORDER CLOSED.</b> Pausa de alívio: é vitória real.

# EPÍLOGO — O Sétimo

<b>Beat 1:</b> somente depois do encerramento chega notificação separada de Lumen: atribuição da intervenção emergencial, assinada por Rhea. Credencial intercity suspensa; wallet e prova de inocência intactas.

<b>Beat 2:</b> “Em Lumen, você sacrificou um mercado para salvar seis. Dessa vez o sétimo fui eu.” Rhea não comemora nem apresenta justificativa triunfal.

<b>Beat 3:</b> RESTORE OBSERVABILITY aparece como <b>registro/ação do protagonista</b> e resolve <b>NO</b> no cânone. Não oferecer escolha YES/NO com resultados diferentes ou opção falsa clicável. O Breaker usa sua capacidade operacional de MISSING para prosseguir, apesar do custo.

<b>Beat 4:</b> rastro histórico de Voss aponta para Horizon/Galexie.

# Corte e QA editorial

- [ ] Cada beat cabe nas artes e áreas de texto do site; número real de slides por Case não verificado.
- [ ] Nenhum slide antecipa a solução do desafio.
- [ ] Todo Case possui efeito de observação, prova adquirida e motivo para seguir.
- [ ] Breach Report contém vulnerabilidade/fix fora dos slides, inclusive nos Cases de threat model e composição correta.
- [ ] A confiança Rhea/Breaker tem ações e custos, não apenas frases.
- [ ] O Sétimo não é anunciado antes da vitória conjunta, mas é retrospectivamente justo.

# Revisão de cenas aprovada — causalidade sem diálogos longos

- <b>Prologue:</b> inserir <code>GUARANTEE RETURN / HISTORICAL POLICY: VALID / CURRENT ASSOCIATION: DENIED / NETWORK RISK FLAG</code>. First Witness exige revisão excepcional do dossiê; ele ainda não tem prova de fraude.
- <b>Case 01 / Sera:</b> <code>SOURCE E.V.</code> e <code>DOCUMENT CONTENT VERIFIED / ORIGIN ENVELOPE SEALED</code>. Não revelar Eli Venn ao player.
- <b>Case 04:</b> mostrar quatro fatos: cancelamento, pending não removido, aceitação pelo operador institucional de compliance e posterior DENIED por alerta de risco. Isso justifica o status, não prova má-fé.
- <b>Case 07:</b> duas identidades parecem não coincidir; Breaker compartilha com Rhea apenas atestação contextual de beneficiário histórico, com aviso de risco. Rhea respeita o limite naquele momento.
- <b>Case 09/10:</b> <code>SENDER WITNESS PACKET: SEALED / COMMITMENT MATCH</code>; <b>depois</b> ocorre separação. Sem reencontro narrativo no Final.
- <b>Final:</b> Breaker comparece fisicamente à sessão, assina claim restrita, é reconhecido e ainda não revela rota de chegada/saída. First Witness observa que a exigência de full disclosure revelaria metadados irrelevantes à claim, inclusive origem de Sera. Prova mínima vence; pausa antes de O Sétimo.
- <b>Epílogo:</b> a atribuição da intervenção de Lumen chega por processo independente e somente depois de WITNESS ORDER CLOSED. O protagonista mantém MISSING pela rota futura, sem menu YES/NO.

<b>Regra:</b> estes beats não exigem um slide novo por linha. Integrar nas telas existentes sem dar spoiler de exploit antes de seu desafio.
</content>
</page>

