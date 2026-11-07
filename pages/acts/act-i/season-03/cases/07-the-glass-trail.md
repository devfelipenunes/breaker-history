---
notion_id: 4019c563-0425-81ec-91d9-fba54567c602
source: https://app.notion.com/p/4019c563042581ec91d9fba54567c602?pvs=204
title: "🪞 07 — The Glass Trail"
exported_at: 2026-11-07
---

Here is the result of "fetch" for the Page with URL https://app.notion.com/p/4019c563042581ec91d9fba54567c602 as of 2026-11-03T00:01:01.976Z:
<page url="https://app.notion.com/p/4019c563042581ec91d9fba54567c602" icon="🪞">
<ancestor-path>
<parent-page url="https://app.notion.com/p/4019c563042581a2a331e66548c30494" title="04 — Cases & Bosses"/>
<ancestor-2-page url="https://app.notion.com/p/4019c56304258179bfa0fc93d15ac390" title="Season 03 — Shadows of Privacy — Moonlight"/>
<ancestor-3-page url="https://app.notion.com/p/4019c563042581469a0edc7e30a6eff9" title="ACT I — The World Is Breakable"/>
<ancestor-4-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
<properties>
{"title":"07 — The Glass Trail"}
</properties>
<iconMetadata>{"type":"emoji","emoji":"🪞"}</iconMetadata>
<content>
# Story

Ninguém quebra o Confidential Token.

Amounts permanecem ocultos.

Balances permanecem ocultos.

Mesmo assim, os Witnesses correlacionam addresses, timing e movimentos públicos até reconstruir a rede social do Breaker.

# Mission

> <b>Encontre uma pessoa sem descobrir o valor que ela movimentou.</b>

# Canonical Threat Model

<b>Metadata Correlation — Confidentiality ≠ Anonymity.</b>

Confidential Tokens podem esconder amounts e balances enquanto sender/receiver addresses e timing continuam observáveis.

# Learning

- privacy dimensions are different;
- confidential amount is not anonymous identity;
- timing/address correlation;
- public flows can leak relationships;
- threat modeling beyond cryptography.

# Win Condition

Correlacionar uma sequência de operações públicas e identificar a rota provável sem conhecer os valores privados.

# Narrative Result

O Breaker entende que, para desaparecer, não basta esconder valores.

Ele precisa saber <b>quem consegue olhar além do Veil</b>.

<b>Cena de confiança:</b> o trace de Emergency Authority em Lumen pode ser correlacionado à credencial institucional intercity do Breaker por uma atestação de associação. Para defender a settlement, ele permite a Rhea examinar esse vínculo em contexto de auditoria estritamente limitado. A atestação <b>não dá a Rhea autorização para agir em nome dele</b>. BREAKER OS alerta que dados correlacionados podem produzir inferências futuras. Naquele momento, Rhea opta sinceramente por proteger a associação e ajudar a desfazer a correlação ativa dos Witnesses. A revisão separada de Lumen continua aberta; ela <b>ainda não decidiu</b> entregar o vínculo.

Isso leva à Witness Spire.

Unlock:

<b>CASE 08 — THE KEY THAT SEES</b>

# Reference

[https://docs.openzeppelin.com/stellar-contracts/tokens/confidential/confidential](https://docs.openzeppelin.com/stellar-contracts/tokens/confidential/confidential)

## Loop jogável v2 — threat model e rota provável

<callout icon="🔍" color="blue_bg">
Não é uma vulnerabilidade obrigatória de smart contract. O player primeiro reproduz o raciocínio do perseguidor sobre um <b>dataset fictício de transações</b> e depois usa esse aprendizado defensivamente. Amounts ocultos não equivalem a anonimato.
</callout>

<b>Investigar:</b> timestamps, endereços públicos, frequência de interações e operações vinculáveis; nenhum dado pessoal externo ou saldo confidencial precisa ser revelado.

<b>Executar:</b> formular duas hipóteses de rota e identificar qual é mais bem sustentada por evidências observáveis, deixando claro o grau de incerteza. A condição canônica exige reconstruir uma <b>rota provável</b>, não provar identidade com certeza universal.

<b>Feedback:</b> interface destaca arestas justificadas por traces e alternativas ainda possíveis; não tratar confidence como probabilidade matemática certificada sem calibrar modelo.

<b>Defesa:</b> Breaker e Rhea reduzem correlação da rota atual sem apagar o passado. Ele permite a Rhea examinar associação histórica de Lumen sob <b>escopo limitado e risco sinalizado</b>; ela protege a ligação sinceramente.

<b>Gancho:</b> a rota dos Witnesses também depende de uma capability institucional de auditor cujo prazo já expirou.

<b>Diferencial:</b> <b>inferência sob metadados</b>, não revelar storage nem quebrar ZK.

## Momento de confiança aprovado — o dado que Rhea precisa e não deveria reutilizar

A Witness Spire encontra <b>dois identificadores incompatíveis na aparência</b> para o beneficiário da devolução de garantia: conta operacional de Lumen e credencial institucional que a policy histórica reconhecia. Para provar a elegibilidade da settlement original, a composição sender/recipient requer uma <b>atestação autenticada de vínculo histórico</b> entre ambos.

O Breaker compartilha o artefato apenas com Rhea, dentro de uma sessão de revisão limitada à operação, com aviso explícito <code>SCOPED EVIDENCE / CORRELATION RISK</code>. A atestação permite demonstrar identidade de beneficiário, mas <b>não concede autorização de movimentação, uso para atribuição institucional externa ou divulgação geral</b>. Ele age com necessidade técnica, não ingenuidade. Naquele momento, Rhea escolhe sinceramente respeitar o acordo e ajuda a reduzir a rota de tracking dos Witnesses.

<b>Payoff:</b> depois que a Spire fechar o caso, Rhea pode produzir uma <b>atestação própria de conhecimento histórico</b> que liga a intervenção de Lumen à credencial intercity; fazê-lo quebra propósito/consentimento contextual, não falsifica prova nem rouba chave. Não antecipar no Case 07 a decisão unilateral futura.
</content>
</page>

