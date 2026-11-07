---
notion_id: 4019c563-0425-81f2-8668-e0eae78d4bf9
source: https://app.notion.com/p/4019c563042581f28668e0eae78d4bf9?pvs=204
title: "✅ 09 — A Valid Lie"
exported_at: 2026-11-07
---

Here is the result of "fetch" for the Page with URL https://app.notion.com/p/4019c563042581f28668e0eae78d4bf9 as of 2026-11-03T00:01:04.089Z:
<page url="https://app.notion.com/p/4019c563042581f28668e0eae78d4bf9" icon="✅">
<ancestor-path>
<parent-page url="https://app.notion.com/p/4019c563042581a2a331e66548c30494" title="04 — Cases & Bosses"/>
<ancestor-2-page url="https://app.notion.com/p/4019c56304258179bfa0fc93d15ac390" title="Season 03 — Shadows of Privacy — Moonlight"/>
<ancestor-3-page url="https://app.notion.com/p/4019c563042581469a0edc7e30a6eff9" title="ACT I — The World Is Breakable"/>
<ancestor-4-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
<properties>
{"title":"09 — A Valid Lie"}
</properties>
<iconMetadata>{"type":"emoji","emoji":"✅"}</iconMetadata>
<content>
# História

O Confidential system usa um Verifier Registry.

O circuito esperado é uma versão.

A verification key registrada pertence a outra.

O contrato continua retornando:

PROOF: VALID

# Missão

> <b>Mude o que “VALID” significa sem alterar a API de proof.</b>

# Vulnerabilidade canônica

<b>Wrong Verification Key / Verifier Registry Mismatch.</b>

A soundness depende de a verification key corresponder exatamente ao circuito/policy esperado.

# Aprendizado

- proof system trust inclui key management;
- circuit version e VK precisam ser fixados;
- verifier registries são superfícies críticas de governança;
- proof matematicamente válido pode aplicar a regra errada.

# Condição de vitória

Usar uma verification key incompatível e fazer o verifier aceitar um proof que não representa a policy esperada.

# Consequência narrativa

Breaker e Rhea finalmente conseguem reconstruir a cadeia de erros que produziu o caso contra eles.

Agora possuem material suficiente para provar inocência.

Rhea propõe uma solução adicional:

destruir o mecanismo central de disclosure antes que a Spire possa usá-lo novamente.

Breaker recusa.

> <b>“Você consegue quebrar isso. Não significa que deve.”</b>

Rhea:

> <b>“Foi exatamente isso que você aprendeu em Lumen?”</b>

Breaker:

> <b>“Foi exatamente por causa de Lumen.”</b>

Rhea não concorda.

Mas para. Ela realmente respeita o limite imposto pelo Breaker e não planeja qualquer traição. Esse ato de contenção precisa parecer uma vitória emocional genuína, não uma atuação que o epílogo revelará falsa.

Antes do confronto final, o Breaker encontra:

████████ — MISSING<br />LAST OBSERVABLE STATE: MOONLIGHT

Unlock:

<b>CASE 10 — BECOME MISSING</b>

# Referência

[https://docs.openzeppelin.com/stellar-contracts/tokens/confidential/confidential](https://docs.openzeppelin.com/stellar-contracts/tokens/confidential/confidential)

## Loop jogável v2 — registry e VK vinculados à policy

<b>Investigar:</b> claim/policy esperada, versão de circuito, hash da VK registrada e artefato efetivamente verificado. O circuito do Case 09 pode estar correto: <b>o problema é que o registry aponta para outra policy/versão</b>.

<b>Hipótese:</b> uma proof válida para statement B é indevidamente aceita como evidência de statement A porque o verificador do aplicativo usa VK/policy incompatíveis.

<b>Executar:</b> fornecer proof válida para versão B e demonstrar que consumer vulnerável a aceita sob claim A; mirror seguro exige vínculo entre expected policy, circuit version, VK hash e public inputs específicos.

<b>Verifier:</b> check independente demonstra que proof não prova policy esperada, apesar de VALID criptográfico sob VK B. Não reutilizar o caso de falta de constraint do Case 06.

<b>Revelação emocional:</b> ao descobrir o poder de disclosure, Rhea quer destruir a capability; Breaker impede com “Você consegue quebrar isso. Não significa que deve.” Ela aceita o limite sinceramente. Esse confronto ocorre <b>somente aqui</b>, não no Final.

<b>Gancho:</b> evidência de outro operador MISSING indica a próxima etapa, sem provar que esse operador é Voss.

<b>Diferencial:</b> <b>governança e versão de verificação</b> em vez de soundness do circuito.

## Handoff para Case 10 — a prova é entregue antes da separação

Depois do confronto em que Rhea desiste de destruir a capability, ela confirma seu compromisso com a defesa conjunta e prepara o <b>sender witness</b> autenticado, vinculado ao commitment da settlement e à policy histórica. O pacote contém somente o material necessário para verificar a relação de origem, <b>não</b> a chave privada de Rhea nem autorização genérica.

<b>Cena curta:</b> <code>SENDER EVIDENCE: SEALED</code> / <code>COMMITMENT MATCH: VERIFIED</code> / <code>TRANSFER TO BREAKER: COMPLETE</code>. O player sabe que poderá usar o pacote na Witness Spire, mesmo sem reencontrá-la.

<b>Retenção:</b> Evidence Locker preserva ID/hash, origem e public inputs, permitindo validar material no Final sem comunicação rastreável posterior. A confiança aqui é sincera e não implica que Rhea já planeje denúncia institucional.
</content>
</page>

