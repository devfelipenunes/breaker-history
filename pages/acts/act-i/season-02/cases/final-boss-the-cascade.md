---
notion_id: 4019c563-0425-81d6-bc39-fe92ba48ec02
source: https://app.notion.com/p/4019c563042581d6bc39fe92ba48ec02?pvs=204
title: "💥 FINAL BOSS — The Cascade"
exported_at: 2026-11-07
---

Here is the result of "fetch" for the Page with URL https://app.notion.com/p/4019c563042581d6bc39fe92ba48ec02 as of 2026-11-03T00:07:28.808Z:
<page url="https://app.notion.com/p/4019c563042581d6bc39fe92ba48ec02" icon="💥">
<ancestor-path>
<parent-page url="https://app.notion.com/p/4019c56304258155ac29c3ff5333a0af" title="04 — Cases & Bosses"/>
<ancestor-2-page url="https://app.notion.com/p/4019c563042581d9aedad3e5f178c3e8" title="Season 02 — DeFi Wars — Lumen"/>
<ancestor-3-page url="https://app.notion.com/p/4019c563042581469a0edc7e30a6eff9" title="ACT I — The World Is Breakable"/>
<ancestor-4-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
<properties>
{"title":"FINAL BOSS — The Cascade"}
</properties>
<iconMetadata>{"type":"emoji","emoji":"💥"}</iconMetadata>
<content>
<callout icon="💥" color="red_bg">
<b>Sem vulnerabilidade nova. Boss sistêmico de composição.</b>
</callout>

# História

Lumen entra em cascata.

Oracle divergence → Vault liquidations → liquidity loss → AMM imbalance → lending bad debt → insurance stress → new liquidations.

Nenhuma ação isolada resolve tudo.

# Missão

> <b>Salve Lumen sem fingir que o sistema é solvente.</b>

# Gameplay

O jogador precisa:

1. identificar feeds confiáveis;
2. interromper liquidations baseadas em dados inválidos;
3. distinguir posições saudáveis de posições realmente insolventes, reconhecer perdas e organizar sua resolução sem mascarar bad debt;
4. evitar drenar pools já sem liquidez;
5. isolar accounting incorreto;
6. usar emergency authority apenas onde necessário;
7. manter settlement suficiente para a cidade operar.

# Breaker × Rhea

Rhea e Breaker trabalham contra a mesma Cascade, mas não como equipe.

Cada um executa um plano diferente.

As ações se tornam interdependentes.

Em determinado ponto, uma rota aberta por Rhea permite ao Breaker alcançar um controle crítico.

Em outro, uma intervenção do Breaker impede que a estratégia de Rhea provoque dano maior.

Existe reconhecimento de competência e dependência tática, ainda sem confiança. A confiança operacional será conquistada durante a cooperação forçada em Moonlight.

Não existe reconciliação.

Rhea:

> <b>“Não confunda alinhamento com confiança.”</b>

# Ilyan

A recuperação depende de market makers independentes.

O Breaker procura Ilyan.

Ilyan:

> <b>“Ela estava certa.”</b>

Breaker:

> “Então nos ajude.”

Ilyan:

> <b>“Eu disse que ela estava certa. Não disse que perdoei.”</b>

Ele ajuda porque Lumen importa mais do que a raiva.

# Payoff moral

Para salvar Lumen, o Breaker opera acima das regras normais porque acredita que esperar produzirá dano maior.

Ele faz exatamente a categoria de escolha que julgou em Rhea.

Isso não prova que Rhea está certa.

Só torna Voss mais difícil de julgar.

# Acceptance

Depois da intervenção:

ARCHITECT<br />BREAKER STATUS UPDATE<br />QUALIFIED → ACCEPTED

O jogador nunca selecionou “EU ACEITO”.

O Architect interpretou seu comportamento.

Rhea:

> <b>“Isso não é um título. É o que você fez.”</b>

Depois:

> <b>“Agora você entende por que eu aceitei.”</b>

# Pista futura — revisão pós-emergência

Emergency Authority deixa eventos e estado publicamente verificáveis. A identidade civil vinculada à conta operacional não é exposta por esses dados, isoladamente. Um processo de revisão de Lumen poderá procurar uma atribuição individual, inclusive por correlação institucional. Rhea testemunhou a intervenção, mas <b>não decidiu trair o Breaker</b>, nem deixou armadilha preparada. A revisão é uma consequência institucional preexistente.

# Encerramento

Lumen sobrevive, mas não volta ao normal.

A Reserve permanece marcada.

O Breaker encontra:

POLICY: VALID<br />AMOUNT: HIDDEN<br />DESTINATION: MOONLIGHT

Rhea:

> <b>“Você queria saber o que o Architect não consegue ver.”</b>

Ela não convida o Breaker.

Ela deixa uma trilha.

<b>Season 03 unlocked.</b>

## Blueprint de integração v2 — vitória auditável sem apagar perdas

<b>Desafio composto:</b> o player valida feeds, impede novas liquidações por dados inválidos, reconcilia accounting/reservas, reconhece debt accrual e bad debt, protege pools com baixa profundidade, mantém settlement essencial e restringe a intervenção emergencial ao menor escopo necessário. Não introduzir bug novo no boss.

<b>Critério objetivo:</b> o verificador independente checa simultaneamente política de feed válida, ausência de novas liquidações indevidas, assets e debt reconciliados, perdas contabilizadas, contágio abaixo de threshold da fixture, settlement essencial preservado, exploit da autorização emergencial demonstrado e <b>efeitos da intervenção limitados pela política mínima de contenção do challenge</b>. A ação pode estar fora da autorização formal do dispatcher e ainda assim deve ter limites verificáveis de dano. Isso não exige uma sequência rígida de comandos nem finge solvência total.

<b>Consequências permanentes:</b> Rhea e Breaker atuam em paralelo por planos interdependentes, sem amizade; Ilyan ajuda sem perdoá-la; Nia recebe continuidade de settlement, não quitação mágica; Reserve conserva cicatrizes. A classificação <code>QUALIFIED → ACCEPTED</code> é atribuída pelo Architect a partir do comportamento, sem consentimento em menu.

<b>Ponte:</b> settlement confidencial legítima segue para Moonlight; a revisão de Emergency Authority permanece aberta, mas Rhea não planeja culpar o Breaker nesta Season.

<b>QA:</b> cenário estável com perdas assumidas, negative tests de bad debt mascarada, liquidez drenada, pausa total e override fora do escopo; Observer independente do módulo alterável. <mention url="https://app.notion.com/p/40c9c5630425811da9bdc67cf66b2410" />.

## Interface de missão v3 — três objetivos do jogador (P0)

<callout icon="🎯" color="blue_bg">
A interface deve apresentar <b>três metas compreensíveis</b>; o verificador independente continua checando todos os invariants do blueprint. Simplificar a apresentação não significa reduzir rigor técnico, apagar prejuízos nem transformar a crise em três botões automáticos.
</callout>

### Objetivo 1 — Descubra a situação real

O jogador consulta fontes, reconciliando preço (freshness + confidence), reservas do Vault, dívida com accrual, collateral recuperável e passivos que já não serão cobertos. Exibir <code>REPORTED</code> versus <code>VERIFIED</code>, com fontes e anomalias auditáveis.

<b>Concluído quando:</b> o estado de risco passou a utilizar feeds adequados, ativos recebidos, dívida atualizada e perdas reconhecidas. <b>Não</b> depender de um gráfico bonito sem prova.

### Objetivo 2 — Contenha a Cascade

Usando a análise anterior, o jogador impede novas liquidações indevidas, evita drenar pools de pouca profundidade, preserva a capacidade mínima de settlements essenciais (inclusive Nia) e realiza intervenção emergencial estritamente limitada por política de contenção independente. A Rhea atua por plano próprio em paralelo; o Ilyan contribui sem perdoá-la.

<b>Concluído quando:</b> o contágio estabiliza sob thresholds da fixture sem paralisar totalmente a cidade e sem criar liquidez fictícia.

### Objetivo 3 — Prove o resultado

O Breaker reúne evidências antes/depois, trilha das ações extraordinárias e perdas remanescentes; envia para o Observer independente. A vitória não exige solvência perfeita.

<b>Concluído quando:</b> Observer confirma conjuntamente política de feed, consistência contábil, risco estabilizado, operações essenciais e limites efetivos de intervenção. O <b>Architect</b> classifica <code>QUALIFIED → ACCEPTED</code> como interpretação de conduta, não clique de aceite.

### Feedback e pontos de verificação

- <b>Meta 1:</b> três painéis de reconciliação curtos (feeds, reservas, obrigações) com links para traces; não checklist que revela o exploit.
- <b>Meta 2:</b> destacar possíveis consequências antes de executar ações; depois mostrar por que alguns indicadores melhoraram e outros ainda carregam perdas.
- <b>Meta 3:</b> tela de revisão registra o que foi preservado, o que permanece insolvente e por que a cidade não voltou ao normal.
- <b>Pausas:</b> permitir consultar evidências e checkpoints sem refazer todos os Cases. O jogador pode variar a ordem de operações tecnicamente válidas, <b>não</b> a história.

<b>QA de aceitação:</b> em playtest, o jogador explica cada objetivo e mostra uma prova de conclusão; tentativas de esconder bad debt, congelar todos os settlements, forjar UI ou extrapolar política de contenção não vencem. A dificuldade é <b>alta por composição</b>, sem vulnerabilidade inédita.

## Integração canônica aprovada — garantia temporária e retorno (seleção 06)

Durante a contenção de The Cascade, uma garantia operacional temporária é segregada para suportar uma rota de settlement essencial e limitar o risco de falha enquanto feeds, reservas e dívidas são reconciliados. A posição/parcelas de garantia são <b>atribuídas à responsabilidade operacional do Breaker</b> em termos documentados de titularidade e restituição, sem criar dinheiro de contabilidade. A contribuição real (colateral efetivamente bloqueado) deve aparecer em eventos e balanços verificáveis.

No fechamento da contenção, <b>Rhea assina a instrução de devolução</b> da parcela devida ao Breaker utilizando a conta/fluxo de custody autorizado para a settlement. Ela é <b>sender witness</b> da operação e o Breaker seu <b>recipient witness</b>. O montante pode ser confidencial sob mecanismo explícito, mas compromisso, policy histórica, titularidade e proof precisam ser rastreáveis conforme threat model. Isso <b>não</b> é presente, indenização ou sinal de amizade: é uma obrigação operacional do encerramento do acordo.

<b>Montagem:</b> (1) durante o boss <code>TEMPORARY GUARANTEE LOCKED</code> + titularidade e política; (2) após estabilização <code>RELEASE ELIGIBLE</code>; (3) epílogo <code>SETTLEMENT SENT / SENDER: RHEA / RECIPIENT: BREAKER / POLICY VALID / DESTINATION: MOONLIGHT</code>. A trilha da operação leva o Breaker a investigar Moonlight, ainda sem confiar nela.

<b>QA:</b> confirmar que o dinheiro retorna de uma reserva realmente vinculada, que não há saldo duplicado, que Rhea só possui capability de settlement devida, que recipient não depende de alteração posterior da association e que a legitimidade é medida na data da execução. Essa especificação é narrativa, não contrato implementado.

## Distinção de autoridades — garantia versus emergency override

Rhea <b>não tinha autorização específica</b> para o override do Liquidator. Isso <b>não</b> impede que ela possua <b>capacidade legítima e estritamente limitada</b> de atuar como signatária/operadora da devolução de garantia após a contenção: são <b>contratos, políticas e escopos diferentes</b>. O retorno é previamente vinculado à parcela do Breaker, a um commitment identificável e à condição de settlement health satisfatória na fixture. A assinatura não permite mudar o beneficiário ou gastar arbitrariamente o restante da reserva.

<b>Teste futuro:</b> verificar emissão de autorização da operação de retorno, beneficiary binding, ausência de duplicação de saldo e rejeição de beneficiary não elegível; a participação do Breaker tem origem financeira concreta na fixture. Sem isso, a finalidade narrativa está definida, mas a mecânica ainda não estará comprovada.

## Por que o retorno utiliza Moonlight, e não uma transferência pública simples

A devolução da garantia passa por uma <b>infraestrutura de settlement confidencial operada em Moonlight</b> porque divulgar imediatamente montantes e posições dos participantes da contenção poderia expor exposições financeiras ainda sensíveis e estimular novas retiradas. A policy de settlement é legítima e limitada; a confidencialidade se refere aos <b>campos realmente protegidos pelo protocolo</b>, sem tornar endereços/tempo invisíveis. Rhea usa essa infraestrutura como signatária do retorno com capability restrita. O destino Moonlight não é um convite pessoal nem ocultação de atividade ilícita; é o local técnico em que o Breaker poderá auditar a conclusão da sua obrigação.
</content>
</page>

