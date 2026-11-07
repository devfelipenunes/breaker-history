---
notion_id: 4019c563-0425-816a-911d-fc68a92e01d3
source: https://app.notion.com/p/4019c5630425816a911dfc68a92e01d3?pvs=204
title: "🏦 04 — The First Share"
exported_at: 2026-11-07
---

# Story

Um Vault recém-aberto parece saudável.

O primeiro depositante possui uma quantidade mínima de shares.

Depois, o Vault recebe uma “doação”.

O exchange rate explode.

O próximo usuário deposita capital real e recebe shares arredondadas para quase zero.

# Mission

> **Make a deposit disappear without stealing it directly.**

# Canonical Vulnerability

**Empty Vault Share Inflation / Donation Accounting — **`empty_vault_share_inflation`** / **`vault_donation_accounting`**.**

# Learning

- share-based vault accounting;
- first-depositor attacks;
- direct donations can manipulate share price;
- integer rounding can transfer value;
- virtual shares/assets and minimums as mitigations.

# Win Condition

Controlar o estado inicial do Vault, manipular a relação assets/shares e fazer um depósito posterior perder valor.

# Interlúdio — A publicação

Após a resolução técnica, Sera publica uma investigação correta sobre a fragilidade que a sequência de Cases expôs. A matéria não inventa a crise nem entrega a solução do challenge antes da vitória.

O feed mostra a publicação seguida de aumento de pedidos de retirada e redução da liquidez disponível. A matéria acelera uma fragilidade preexistente; não é a causa única da crise.

Em um registro curto de confronto, Rhea diz:

> **“E agora sabem enquanto correm para a saída.”**

A fala responde a Sera:

> **“As pessoas tinham o direito de saber.”**

Breaker acompanha esse registro à distância. Ele ainda não conhece Sera pessoalmente. O impasse prepara sua mudança em Moonlight: informação verdadeira também produz consequências.

# Narrative Result

Rhea retirou fundos daquele Vault **antes** da distorção.

Para o jogador, isso parece insider knowledge.

Ela entra no Liquidation Engine.

Mission Update:

> **PARE RHEA.**

Unlock:

**BOSS I — THE LIQUIDATOR**

# Reference

[https://github.com/Veritas-Vaults-Network/soroban-guard-contracts](https://github.com/Veritas-Vaults-Network/soroban-guard-contracts)

## Blueprint de integração v2 — Share inflation e comunicação pública

**Fixture a implementar:** Vault novo com depósito inicial mínimo, doação direta considerada em `totalAssets` e divisão inteira de shares que arredonda a participação da vítima quase a zero. Fixar versão matemática, precisão e regras do Vault.

**Verificador:** estado inicial, shares totais, assets antes/depois da doação, shares emitidas à vítima e perda implícita. Secure mirror com virtual assets/shares, mínimo de shares ou política segura bloqueia a mesma extração.

**Interlúdio canônico:** somente depois da vitória Sera publica investigação verdadeira, que acelera withdrawals em sistema já frágil. A imprensa não cria o bug nem revela exploit antes de o jogador resolvê-lo.

**Rhea:** retirada prévia parece suspeita, mas não prova insider manipulation. Seu contato com o Liquidator cria a transição; o player recebe **PARE RHEA**.

**QA:** replay demonstra o rounding, e a matéria altera comportamento de saques no estado narrativo, não na fixture de exploit por magia.

## Loop jogável v3 — detetive de contabilidade de shares (prioridade P1)

Roteiro de interação e prova para implementação; preserve a publicação de Sera após a vitória.

**1. Investigar:** exibir `totalAssets`, `totalShares`, primeiro depósito, doação direta e deposição posterior de uma vítima da fixture. O jogador pode consultar um cálculo de conversão de assets em shares sem receber a falha pronta.

**2. Formular hipótese:** um depositante inicial mínimo consegue distorcer o preço por share; o arredondamento inteiro prejudica o próximo usuário.

**3. Executar:** reproduzir primeiro depósito + doação + depósito da vítima; provar que shares recebidas tornam-se irrisórias conforme os números da fixture.

**4. Feedback:** registrar valores antes/depois e `victim_shares` emitidas; mirror seguro com virtual assets/shares ou proteção equivalente evita o resultado.

**5. Consequência:** Rhea havia retirado exposição antes do evento; **não provar insider trading apenas por timestamps**. Sera publica matéria correta e withdrawals aumentam sobre fragilidade preexistente. Gancho: Liquidator.

**Distinção:** investigação de **arredondamento e composição de shares**; não repetir manipulação de swap do Case 03.

**QA:** cálculo robusto a divisão inteira/precisão, proteção segura testada, dramaturgia não revela o exploit antes da vitória.
