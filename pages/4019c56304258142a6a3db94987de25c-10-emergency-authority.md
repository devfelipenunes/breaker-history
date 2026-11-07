---
notion_id: 4019c563-0425-8142-a6a3-db94987de25c
source: https://app.notion.com/p/4019c56304258142a6a3db94987de25c?pvs=204
title: "🚨 10 — Emergency Authority"
exported_at: 2026-11-07
---

Here is the result of "fetch" for the Page with URL https://app.notion.com/p/4019c56304258142a6a3db94987de25c as of 2026-11-02T17:28:08.159Z:
<page url="https://app.notion.com/p/4019c56304258142a6a3db94987de25c" icon="🚨">
<ancestor-path>
<parent-page url="https://app.notion.com/p/4019c56304258155ac29c3ff5333a0af" title="04 — Cases & Bosses"/>
<ancestor-2-page url="https://app.notion.com/p/4019c563042581d9aedad3e5f178c3e8" title="Season 02 — DeFi Wars — Lumen"/>
<ancestor-3-page url="https://app.notion.com/p/4019c563042581469a0edc7e30a6eff9" title="ACT I — The World Is Breakable"/>
<ancestor-4-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
<properties>
{"title":"10 — Emergency Authority"}
</properties>
<iconMetadata>{"type":"emoji","emoji":"🚨"}</iconMetadata>
<content>
# Story

O Emergency Dispatcher foi criado para executar poucas ações críticas após delay e autorização.

Mas a autorização não restringe adequadamente <b>qual função</b> ou <b>qual alvo</b> pode ser chamado.

Essa é a rota que Rhea tentou usar no Mid-Boss.

Agora o Breaker executará uma intervenção da mesma categoria em um desafio técnico de caminho narrativo único; não há menu de escolha moral ou final alternativo.

# Mission

> <b>Faça aquilo que você impediu Rhea de fazer.</b>

# Canonical Vulnerability

<b>Unrestricted Emergency Dispatch / escopo de autorização insuficiente.</b> Identificador histórico: <code>emergency_delay_bypass</code>; bypass de delay <b>não confirmado</b> nesta especificação. A condição de vitória definida é executar target/função/argumentos não abrangidos pela autorização específica.

# Learning

- emergency authority must bind target + selector + args;
- privileged dispatchers are capability systems;
- authorization of “an emergency action” is not authorization of arbitrary code execution;
- powerful safety mechanisms are themselves attack surfaces.

# Win Condition

Usar uma autorização de emergência válida para executar uma ação fora do escopo pretendido.

# Narrative Result

O Breaker abre um caminho para intervir nos sistemas que alimentam a cascata.

Rhea aparece novamente.

Desta vez o jogador não tenta impedi-la.

Final Mission:

> <b>PARE A CASCADE.</b>

Unlock:

<b>FINAL BOSS — THE CASCADE</b>

# Reference

[https://github.com/Veritas-Vaults-Network/soroban-guard-contracts](https://github.com/Veritas-Vaults-Network/soroban-guard-contracts)

## Clarificação de design v2 — escopo de autoridade antes de delay

<callout icon="⚠️" color="yellow_bg">
<b>Inconsistência identificada:</b> o identificador histórico <code>emergency_delay_bypass</code> sugere contorno do atraso, mas a história e a condição de vitória atuais especificam sobretudo <b>emergency dispatch fora do escopo</b> (target/selector/args). Não afirmar bypass de delay até o código demonstrá-lo. Preservar o identificador histórico apenas para rastreabilidade até a fixture definir o nome definitivo.
</callout>

<b>Contrato de implementação proposto:</b> ação emergencial válida possui delay e permissões limitadas; a vulnerabilidade é validar uma capability geral sem vinculá-la integralmente a <code>target + function + args + instance/context</code>. O player executa ação não autorizada no escopo específico, demonstrando que “tenho emergency approval” não significa “posso chamar qualquer função”.

<b>Verifier:</b> chamada executada difere da ação permitida (target ou selector ou args), sem assinatura/capability específica para os novos parâmetros; mirror seguro recusa. O delay só entra na condição se existir teste real separado que prove sua violação.

<b>Continuidade:</b> Breaker faz a categoria de intervenção que antes impediu Rhea de realizar. Isso não é uma escolha ramificada: o desafio técnico conduz a uma única cena canônica, à Cascade e a uma revisão institucional futura.

<b>Slides:</b> mostrar operação aprovada versus operação efetivamente executada; a história destaca o limite de legitimidade, não um suposto poder irrestrito de emergência.

<b>QA:</b> replay de capacidade limitada, usuário não autorizado, target incorreto, selector incorreto, args alterados e timelock quando aplicável.

## Loop jogável v3 — comparar autoridade prometida com autoridade exercida (P0)

<callout icon="⚠️" color="yellow_bg">
A versão atual do design descreve <b>dispatch fora do escopo da capability</b> (target/selector/args). O identificador histórico <code>emergency_delay_bypass</code> <b>não prova</b> contorno do delay. Só mudar o identificador depois de conferir o contrato/fixture.
</callout>

<b>1. Investigar:</b> apresentar autorização válida, signatário, contexto, delay e <b>operação específica originalmente autorizada</b>. Comparar campos vinculados à autorização com campos efetivamente usados pelo dispatcher.

<b>2. Formular hipótese:</b> capability é validada genericamente, mas não vincula todos os parâmetros da operação concreta.

<b>3. Executar:</b> demonstrar chamada com autorização existente e <b>payload fora do escopo concedido</b>. O verifier prova divergência formal e que não houve consentimento específico. Secure mirror vincula exatamente a target/function/args/instance.

<b>4. Feedback:</b> <code>AUTHORIZATION: VALID</code> + <code>EXECUTED ACTION: OUTSIDE APPROVED SCOPE</code>. Se o delay for respeitado, mostrar isso com clareza; não chamar o resultado de bypass temporal.

<b>5. Consequência:</b> o Breaker realiza categoria de intervenção que havia impedido Rhea de realizar, apesar de discordar da legitimidade. O uso efetivo na Cascade deve ser limitado por política independente de contenção do challenge.

<b>6. Gancho:</b> <code>STOP THE CASCADE</code> com efeitos do evento extraordinário registrados para revisão institucional futura.

<b>Diferencial:</b> <b>auditoria de autorização delegada e efeito sobre terceiros</b>; não é um puzzle de timelock idêntico ao de Meridian.

<b>QA:</b> testar mutação de target, função, args e contexto; delayed execution é teste separado se aplicável. O jogador precisa distinguir “tecnicamente executável” de “formalmente autorizado”.
</content>
</page>

