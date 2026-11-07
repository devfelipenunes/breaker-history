---
notion_id: 4019c563-0425-8142-a6a3-db94987de25c
source: https://app.notion.com/p/4019c56304258142a6a3db94987de25c?pvs=204
title: "🚨 10 — Emergency Authority"
exported_at: 2026-11-07
---

# Story

O Emergency Dispatcher foi criado para executar poucas ações críticas após delay e autorização.

Mas a autorização não restringe adequadamente **qual função** ou **qual alvo** pode ser chamado.

Essa é a rota que Rhea tentou usar no Mid-Boss.

Agora o Breaker executará uma intervenção da mesma categoria em um desafio técnico de caminho narrativo único; não há menu de escolha moral ou final alternativo.

# Mission

> **Faça aquilo que você impediu Rhea de fazer.**

# Canonical Vulnerability

**Unrestricted Emergency Dispatch / escopo de autorização insuficiente.** Identificador histórico: `emergency_delay_bypass`; bypass de delay **não confirmado** nesta especificação. A condição de vitória definida é executar target/função/argumentos não abrangidos pela autorização específica.

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

> **PARE A CASCADE.**

Unlock:

**FINAL BOSS — THE CASCADE**

# Reference

[https://github.com/Veritas-Vaults-Network/soroban-guard-contracts](https://github.com/Veritas-Vaults-Network/soroban-guard-contracts)

## Clarificação de design v2 — escopo de autoridade antes de delay

**Inconsistência identificada:** o identificador histórico `emergency_delay_bypass` sugere contorno do atraso, mas a história e a condição de vitória atuais especificam sobretudo **emergency dispatch fora do escopo** (target/selector/args). Não afirmar bypass de delay até o código demonstrá-lo. Preservar o identificador histórico apenas para rastreabilidade até a fixture definir o nome definitivo.

**Contrato de implementação proposto:** ação emergencial válida possui delay e permissões limitadas; a vulnerabilidade é validar uma capability geral sem vinculá-la integralmente a `target + function + args + instance/context`. O player executa ação não autorizada no escopo específico, demonstrando que “tenho emergency approval” não significa “posso chamar qualquer função”.

**Verifier:** chamada executada difere da ação permitida (target ou selector ou args), sem assinatura/capability específica para os novos parâmetros; mirror seguro recusa. O delay só entra na condição se existir teste real separado que prove sua violação.

**Continuidade:** Breaker faz a categoria de intervenção que antes impediu Rhea de realizar. Isso não é uma escolha ramificada: o desafio técnico conduz a uma única cena canônica, à Cascade e a uma revisão institucional futura.

**Slides:** mostrar operação aprovada versus operação efetivamente executada; a história destaca o limite de legitimidade, não um suposto poder irrestrito de emergência.

**QA:** replay de capacidade limitada, usuário não autorizado, target incorreto, selector incorreto, args alterados e timelock quando aplicável.

## Loop jogável v3 — comparar autoridade prometida com autoridade exercida (P0)

A versão atual do design descreve **dispatch fora do escopo da capability** (target/selector/args). O identificador histórico `emergency_delay_bypass` **não prova** contorno do delay. Só mudar o identificador depois de conferir o contrato/fixture.

**1. Investigar:** apresentar autorização válida, signatário, contexto, delay e **operação específica originalmente autorizada**. Comparar campos vinculados à autorização com campos efetivamente usados pelo dispatcher.

**2. Formular hipótese:** capability é validada genericamente, mas não vincula todos os parâmetros da operação concreta.

**3. Executar:** demonstrar chamada com autorização existente e **payload fora do escopo concedido**. O verifier prova divergência formal e que não houve consentimento específico. Secure mirror vincula exatamente a target/function/args/instance.

**4. Feedback:** `AUTHORIZATION: VALID` + `EXECUTED ACTION: OUTSIDE APPROVED SCOPE`. Se o delay for respeitado, mostrar isso com clareza; não chamar o resultado de bypass temporal.

**5. Consequência:** o Breaker realiza categoria de intervenção que havia impedido Rhea de realizar, apesar de discordar da legitimidade. O uso efetivo na Cascade deve ser limitado por política independente de contenção do challenge.

**6. Gancho:** `STOP THE CASCADE` com efeitos do evento extraordinário registrados para revisão institucional futura.

**Diferencial:** **auditoria de autorização delegada e efeito sobre terceiros**; não é um puzzle de timelock idêntico ao de Meridian.

**QA:** testar mutação de target, função, args e contexto; delayed execution é teste separado se aplicável. O jogador precisa distinguir “tecnicamente executável” de “formalmente autorizado”.
