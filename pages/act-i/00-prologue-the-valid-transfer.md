---
notion_id: 4019c563-0425-81e2-aa33-d642575c6811
source: https://app.notion.com/p/4019c563042581e2aa33d642575c6811?pvs=204
title: "🕵️ 00 — Prologue: The Valid Transfer"
exported_at: 2026-11-07
---

Here is the result of "fetch" for the Page with URL https://app.notion.com/p/4019c563042581e2aa33d642575c6811 as of 2026-11-03T00:07:30.437Z:
<page url="https://app.notion.com/p/4019c563042581e2aa33d642575c6811" icon="🕵️">
<ancestor-path>
<parent-page url="https://app.notion.com/p/4019c563042581a2a331e66548c30494" title="04 — Cases & Bosses"/>
<ancestor-2-page url="https://app.notion.com/p/4019c56304258179bfa0fc93d15ac390" title="Season 03 — Shadows of Privacy — Moonlight"/>
<ancestor-3-page url="https://app.notion.com/p/4019c563042581469a0edc7e30a6eff9" title="ACT I — The World Is Breakable"/>
<ancestor-4-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
<properties>
{"title":"00 — Prologue: The Valid Transfer"}
</properties>
<iconMetadata>{"type":"emoji","emoji":"🕵️"}</iconMetadata>
<content>
# Narrative Function

Transformar o jogador em alvo.

# Situation

Breaker chega a Moonlight seguindo o settlement usado no fim de Lumen.

Na entrada da cidade:

PRIVATE SETTLEMENT DETECTED<br />RECIPIENT: BREAKER<br />AMOUNT: HIDDEN<br />ASSOCIATION: DENIED<br />PROOF: VALID

A Witness Spire intercepta o caso.

Um Witness exige acesso de disclosure.

> <b>“Precisamos da sua chave de visualização.”</b>

Breaker:

> “Para esta transação?”

> <b>“Para tudo.”</b>

Ele recusa.

DISCLOSURE REQUEST: DENIED<br />SUBJECT: BREAKER<br />STATUS: NON-COMPLIANT<br />WITNESS ORDER ISSUED

# Mission

> <b>Descubra por que uma transferência privada válida transformou você em suspeito.</b>

# Transition

A primeira rota usada pelo Breaker é descoberta rápido demais.

Não houve quebra criptográfica.

Houve um segredo armazenado onde nunca deveria existir.

Unlock:

<b>CASE 01 — THE PUBLIC SECRET</b>

## Guia de produção v2 — escopo da acusação

- <b>Antes:</b> apresentar <b>settlement histórica válida</b> e <b>association atual DENIED</b> como afirmações sobre momentos diferentes. A UI mostra que o Breaker foi identificado como recipient <b>pela investigação/pelo próprio contexto da conta</b>, não por suposta revelação pública de todos os recipients confidenciais.
- <b>Missão:</b> descobrir por que a operação válida passou a ser contestada. First Witness solicita view authority abrangente e o Breaker recusa; não existe escolha moral ramificada.
- <b>Consequência:</b> a rota de safehouse é reconstruída sem quebrar criptografia. O primeiro Case demonstra armazenamento inadequado de um segredo em ledger público.
- <b>QA:</b> público consegue explicar que proof válida da settlement em t0 não significa associação permitida hoje, e associação DENIED hoje não prova que a settlement era inválida em t0. O prólogo não contém exploit obrigatório.

## Cena canônica aprovada — suspeita de rede, não ausência de prova

A settlement que levou Breaker a Moonlight devolveu uma <b>garantia operacional temporária</b> da Cascade. Ela foi permitida pelo compliance histórico no momento da execução. A interface mostra <code>SETTLEMENT PROOF: VALID</code>, <code>ASSOCIATION NOW: DENIED</code> e <code>RISK GRAPH: MULTIPLE LINKED OPERATIONS</code>. O grafo usa metadados observáveis e ainda não comprova fraude.

<b>Procedimento de First Witness:</b> combinação DENIED + sinais de rede ativa um protocolo de investigação excepcional. Ele exige full view authority por considerar que examinar apenas a settlement seria insuficiente. Sua decisão é reconhecível, mas desproporcional — problema a ser demonstrado no Final.

<b>Escopo de segredo:</b> amount está oculto por mecanismo explícito; isso não oculta automaticamente sender, recipient e timing. O player deve entender por que a operação válida pode sofrer acusação posterior sem que haja retroatividade da policy.

## Por que o Breaker veio até a cidade

Ele segue a <b>trilha verificável do retorno da garantia</b> para a infraestrutura de settlement confidencial de Moonlight, utilizada para não revelar abertamente as posições financeiras sensíveis dos participantes da crise de Lumen. O Breaker precisa conferir receipt, claim de beneficiário e policy histórica da operação — não chega por convite amistoso de Rhea. A associação DENIED só aparece <b>depois</b> da execução legítima. Os metadados que permanecem públicos permitem que First Witness abra investigação; o sigilo de valor não garante anonimato.
</content>
</page>

