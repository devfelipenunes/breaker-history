---
notion_id: 4019c563-0425-816a-911d-fc68a92e01d3
source: https://app.notion.com/p/4019c5630425816a911dfc68a92e01d3?pvs=204
title: "🏦 04 — The First Share"
exported_at: 2026-11-07
---

Here is the result of "fetch" for the Page with URL https://app.notion.com/p/4019c5630425816a911dfc68a92e01d3 as of 2026-11-02T17:27:07.610Z:
<page url="https://app.notion.com/p/4019c5630425816a911dfc68a92e01d3" icon="🏦">
<ancestor-path>
<parent-page url="https://app.notion.com/p/4019c56304258155ac29c3ff5333a0af" title="04 — Cases & Bosses"/>
<ancestor-2-page url="https://app.notion.com/p/4019c563042581d9aedad3e5f178c3e8" title="Season 02 — DeFi Wars — Lumen"/>
<ancestor-3-page url="https://app.notion.com/p/4019c563042581469a0edc7e30a6eff9" title="ACT I — The World Is Breakable"/>
<ancestor-4-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
<properties>
{"title":"04 — The First Share"}
</properties>
<iconMetadata>{"type":"emoji","emoji":"🏦"}</iconMetadata>
<content>
# Story

Um Vault recém-aberto parece saudável.

O primeiro depositante possui uma quantidade mínima de shares.

Depois, o Vault recebe uma “doação”.

O exchange rate explode.

O próximo usuário deposita capital real e recebe shares arredondadas para quase zero.

# Mission

> <b>Make a deposit disappear without stealing it directly.</b>

# Canonical Vulnerability

<b>Empty Vault Share Inflation / Donation Accounting — </b><b><code>empty_vault_share_inflation</code></b><b> / </b><b><code>vault_donation_accounting</code></b><b>.</b>

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

> <b>“E agora sabem enquanto correm para a saída.”</b>

A fala responde a Sera:

> <b>“As pessoas tinham o direito de saber.”</b>

Breaker acompanha esse registro à distância. Ele ainda não conhece Sera pessoalmente. O impasse prepara sua mudança em Moonlight: informação verdadeira também produz consequências.

# Narrative Result

Rhea retirou fundos daquele Vault <b>antes</b> da distorção.

Para o jogador, isso parece insider knowledge.

Ela entra no Liquidation Engine.

Mission Update:

> <b>PARE RHEA.</b>

Unlock:

<b>BOSS I — THE LIQUIDATOR</b>

# Reference

[https://github.com/Veritas-Vaults-Network/soroban-guard-contracts](https://github.com/Veritas-Vaults-Network/soroban-guard-contracts)

## Blueprint de integração v2 — Share inflation e comunicação pública

<b>Fixture a implementar:</b> Vault novo com depósito inicial mínimo, doação direta considerada em <code>totalAssets</code> e divisão inteira de shares que arredonda a participação da vítima quase a zero. Fixar versão matemática, precisão e regras do Vault.

<b>Verificador:</b> estado inicial, shares totais, assets antes/depois da doação, shares emitidas à vítima e perda implícita. Secure mirror com virtual assets/shares, mínimo de shares ou política segura bloqueia a mesma extração.

<b>Interlúdio canônico:</b> somente depois da vitória Sera publica investigação verdadeira, que acelera withdrawals em sistema já frágil. A imprensa não cria o bug nem revela exploit antes de o jogador resolvê-lo.

<b>Rhea:</b> retirada prévia parece suspeita, mas não prova insider manipulation. Seu contato com o Liquidator cria a transição; o player recebe <b>PARE RHEA</b>.

<b>QA:</b> replay demonstra o rounding, e a matéria altera comportamento de saques no estado narrativo, não na fixture de exploit por magia.

## Loop jogável v3 — detetive de contabilidade de shares (prioridade P1)

<callout icon="🎮" color="blue_bg">
Roteiro de interação e prova para implementação; preserve a publicação de Sera após a vitória.
</callout>

<b>1. Investigar:</b> exibir <code>totalAssets</code>, <code>totalShares</code>, primeiro depósito, doação direta e deposição posterior de uma vítima da fixture. O jogador pode consultar um cálculo de conversão de assets em shares sem receber a falha pronta.

<b>2. Formular hipótese:</b> um depositante inicial mínimo consegue distorcer o preço por share; o arredondamento inteiro prejudica o próximo usuário.

<b>3. Executar:</b> reproduzir primeiro depósito + doação + depósito da vítima; provar que shares recebidas tornam-se irrisórias conforme os números da fixture.

<b>4. Feedback:</b> registrar valores antes/depois e <code>victim_shares</code> emitidas; mirror seguro com virtual assets/shares ou proteção equivalente evita o resultado.

<b>5. Consequência:</b> Rhea havia retirado exposição antes do evento; <b>não provar insider trading apenas por timestamps</b>. Sera publica matéria correta e withdrawals aumentam sobre fragilidade preexistente. Gancho: Liquidator.

<b>Distinção:</b> investigação de <b>arredondamento e composição de shares</b>; não repetir manipulação de swap do Case 03.

<b>QA:</b> cálculo robusto a divisão inteira/precisão, proteção segura testada, dramaturgia não revela o exploit antes da vitória.
</content>
</page>

