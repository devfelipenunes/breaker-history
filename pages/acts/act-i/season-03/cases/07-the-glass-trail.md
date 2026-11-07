---
notion_id: 4019c563-0425-81ec-91d9-fba54567c602
source: https://app.notion.com/p/4019c563042581ec91d9fba54567c602?pvs=204
title: "🪞 07 — The Glass Trail"
exported_at: 2026-11-07
---

# Story

Ninguém quebra o Confidential Token.

Amounts permanecem ocultos.

Balances permanecem ocultos.

Mesmo assim, os Witnesses correlacionam addresses, timing e movimentos públicos até reconstruir a rede social do Breaker.

# Mission

> **Encontre uma pessoa sem descobrir o valor que ela movimentou.**

# Canonical Threat Model

**Metadata Correlation — Confidentiality ≠ Anonymity.**

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

Ele precisa saber **quem consegue olhar além do Veil**.

**Cena de confiança:** o trace de Emergency Authority em Lumen pode ser correlacionado à credencial institucional intercity do Breaker por uma atestação de associação. Para defender a settlement, ele permite a Rhea examinar esse vínculo em contexto de auditoria estritamente limitado. A atestação **não dá a Rhea autorização para agir em nome dele**. BREAKER OS alerta que dados correlacionados podem produzir inferências futuras. Naquele momento, Rhea opta sinceramente por proteger a associação e ajudar a desfazer a correlação ativa dos Witnesses. A revisão separada de Lumen continua aberta; ela **ainda não decidiu** entregar o vínculo.

Isso leva à Witness Spire.

Unlock:

**CASE 08 — THE KEY THAT SEES**

# Reference

[https://docs.openzeppelin.com/stellar-contracts/tokens/confidential/confidential](https://docs.openzeppelin.com/stellar-contracts/tokens/confidential/confidential)

## Loop jogável v2 — threat model e rota provável

Não é uma vulnerabilidade obrigatória de smart contract. O player primeiro reproduz o raciocínio do perseguidor sobre um **dataset fictício de transações** e depois usa esse aprendizado defensivamente. Amounts ocultos não equivalem a anonimato.

**Investigar:** timestamps, endereços públicos, frequência de interações e operações vinculáveis; nenhum dado pessoal externo ou saldo confidencial precisa ser revelado.

**Executar:** formular duas hipóteses de rota e identificar qual é mais bem sustentada por evidências observáveis, deixando claro o grau de incerteza. A condição canônica exige reconstruir uma **rota provável**, não provar identidade com certeza universal.

**Feedback:** interface destaca arestas justificadas por traces e alternativas ainda possíveis; não tratar confidence como probabilidade matemática certificada sem calibrar modelo.

**Defesa:** Breaker e Rhea reduzem correlação da rota atual sem apagar o passado. Ele permite a Rhea examinar associação histórica de Lumen sob **escopo limitado e risco sinalizado**; ela protege a ligação sinceramente.

**Gancho:** a rota dos Witnesses também depende de uma capability institucional de auditor cujo prazo já expirou.

**Diferencial:** **inferência sob metadados**, não revelar storage nem quebrar ZK.

## Momento de confiança aprovado — o dado que Rhea precisa e não deveria reutilizar

A Witness Spire encontra **dois identificadores incompatíveis na aparência** para o beneficiário da devolução de garantia: conta operacional de Lumen e credencial institucional que a policy histórica reconhecia. Para provar a elegibilidade da settlement original, a composição sender/recipient requer uma **atestação autenticada de vínculo histórico** entre ambos.

O Breaker compartilha o artefato apenas com Rhea, dentro de uma sessão de revisão limitada à operação, com aviso explícito `SCOPED EVIDENCE / CORRELATION RISK`. A atestação permite demonstrar identidade de beneficiário, mas **não concede autorização de movimentação, uso para atribuição institucional externa ou divulgação geral**. Ele age com necessidade técnica, não ingenuidade. Naquele momento, Rhea escolhe sinceramente respeitar o acordo e ajuda a reduzir a rota de tracking dos Witnesses.

**Payoff:** depois que a Spire fechar o caso, Rhea pode produzir uma **atestação própria de conhecimento histórico** que liga a intervenção de Lumen à credencial intercity; fazê-lo quebra propósito/consentimento contextual, não falsifica prova nem rouba chave. Não antecipar no Case 07 a decisão unilateral futura.
