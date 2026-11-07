---
notion_id: 4019c563-0425-81e2-aa33-d642575c6811
source: https://app.notion.com/p/4019c563042581e2aa33d642575c6811?pvs=204
title: "🕵️ 00 — Prologue: The Valid Transfer"
exported_at: 2026-11-07
---

# Narrative Function

Transformar o jogador em alvo.

# Situation

Breaker chega a Moonlight seguindo o settlement usado no fim de Lumen.

Na entrada da cidade:

PRIVATE SETTLEMENT DETECTED
RECIPIENT: BREAKER
AMOUNT: HIDDEN
ASSOCIATION: DENIED
PROOF: VALID

A Witness Spire intercepta o caso.

Um Witness exige acesso de disclosure.

> **“Precisamos da sua chave de visualização.”**

Breaker:

> “Para esta transação?”

> **“Para tudo.”**

Ele recusa.

DISCLOSURE REQUEST: DENIED
SUBJECT: BREAKER
STATUS: NON-COMPLIANT
WITNESS ORDER ISSUED

# Mission

> **Descubra por que uma transferência privada válida transformou você em suspeito.**

# Transition

A primeira rota usada pelo Breaker é descoberta rápido demais.

Não houve quebra criptográfica.

Houve um segredo armazenado onde nunca deveria existir.

Unlock:

**CASE 01 — THE PUBLIC SECRET**

## Guia de produção v2 — escopo da acusação

- **Antes:** apresentar **settlement histórica válida** e **association atual DENIED** como afirmações sobre momentos diferentes. A UI mostra que o Breaker foi identificado como recipient **pela investigação/pelo próprio contexto da conta**, não por suposta revelação pública de todos os recipients confidenciais.
- **Missão:** descobrir por que a operação válida passou a ser contestada. First Witness solicita view authority abrangente e o Breaker recusa; não existe escolha moral ramificada.
- **Consequência:** a rota de safehouse é reconstruída sem quebrar criptografia. O primeiro Case demonstra armazenamento inadequado de um segredo em ledger público.
- **QA:** público consegue explicar que proof válida da settlement em t0 não significa associação permitida hoje, e associação DENIED hoje não prova que a settlement era inválida em t0. O prólogo não contém exploit obrigatório.

## Cena canônica aprovada — suspeita de rede, não ausência de prova

A settlement que levou Breaker a Moonlight devolveu uma **garantia operacional temporária** da Cascade. Ela foi permitida pelo compliance histórico no momento da execução. A interface mostra `SETTLEMENT PROOF: VALID`, `ASSOCIATION NOW: DENIED` e `RISK GRAPH: MULTIPLE LINKED OPERATIONS`. O grafo usa metadados observáveis e ainda não comprova fraude.

**Procedimento de First Witness:** combinação DENIED + sinais de rede ativa um protocolo de investigação excepcional. Ele exige full view authority por considerar que examinar apenas a settlement seria insuficiente. Sua decisão é reconhecível, mas desproporcional — problema a ser demonstrado no Final.

**Escopo de segredo:** amount está oculto por mecanismo explícito; isso não oculta automaticamente sender, recipient e timing. O player deve entender por que a operação válida pode sofrer acusação posterior sem que haja retroatividade da policy.

## Por que o Breaker veio até a cidade

Ele segue a **trilha verificável do retorno da garantia** para a infraestrutura de settlement confidencial de Moonlight, utilizada para não revelar abertamente as posições financeiras sensíveis dos participantes da crise de Lumen. O Breaker precisa conferir receipt, claim de beneficiário e policy histórica da operação — não chega por convite amistoso de Rhea. A associação DENIED só aparece **depois** da execução legítima. Os metadados que permanecem públicos permitem que First Witness abra investigação; o sigilo de valor não garante anonimato.
