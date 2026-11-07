---
notion_id: 4019c563-0425-81f2-8668-e0eae78d4bf9
source: https://app.notion.com/p/4019c563042581f28668e0eae78d4bf9?pvs=204
title: "✅ 09 — A Valid Lie"
exported_at: 2026-11-07
---

# História

O Confidential system usa um Verifier Registry.

O circuito esperado é uma versão.

A verification key registrada pertence a outra.

O contrato continua retornando:

PROOF: VALID

# Missão

> **Mude o que “VALID” significa sem alterar a API de proof.**

# Vulnerabilidade canônica

**Wrong Verification Key / Verifier Registry Mismatch.**

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

> **“Você consegue quebrar isso. Não significa que deve.”**

Rhea:

> **“Foi exatamente isso que você aprendeu em Lumen?”**

Breaker:

> **“Foi exatamente por causa de Lumen.”**

Rhea não concorda.

Mas para. Ela realmente respeita o limite imposto pelo Breaker e não planeja qualquer traição. Esse ato de contenção precisa parecer uma vitória emocional genuína, não uma atuação que o epílogo revelará falsa.

Antes do confronto final, o Breaker encontra:

████████ — MISSING
LAST OBSERVABLE STATE: MOONLIGHT

Unlock:

**CASE 10 — BECOME MISSING**

# Referência

[https://docs.openzeppelin.com/stellar-contracts/tokens/confidential/confidential](https://docs.openzeppelin.com/stellar-contracts/tokens/confidential/confidential)

## Loop jogável v2 — registry e VK vinculados à policy

**Investigar:** claim/policy esperada, versão de circuito, hash da VK registrada e artefato efetivamente verificado. O circuito do Case 09 pode estar correto: **o problema é que o registry aponta para outra policy/versão**.

**Hipótese:** uma proof válida para statement B é indevidamente aceita como evidência de statement A porque o verificador do aplicativo usa VK/policy incompatíveis.

**Executar:** fornecer proof válida para versão B e demonstrar que consumer vulnerável a aceita sob claim A; mirror seguro exige vínculo entre expected policy, circuit version, VK hash e public inputs específicos.

**Verifier:** check independente demonstra que proof não prova policy esperada, apesar de VALID criptográfico sob VK B. Não reutilizar o caso de falta de constraint do Case 06.

**Revelação emocional:** ao descobrir o poder de disclosure, Rhea quer destruir a capability; Breaker impede com “Você consegue quebrar isso. Não significa que deve.” Ela aceita o limite sinceramente. Esse confronto ocorre **somente aqui**, não no Final.

**Gancho:** evidência de outro operador MISSING indica a próxima etapa, sem provar que esse operador é Voss.

**Diferencial:** **governança e versão de verificação** em vez de soundness do circuito.

## Handoff para Case 10 — a prova é entregue antes da separação

Depois do confronto em que Rhea desiste de destruir a capability, ela confirma seu compromisso com a defesa conjunta e prepara o **sender witness** autenticado, vinculado ao commitment da settlement e à policy histórica. O pacote contém somente o material necessário para verificar a relação de origem, **não** a chave privada de Rhea nem autorização genérica.

**Cena curta:** `SENDER EVIDENCE: SEALED` / `COMMITMENT MATCH: VERIFIED` / `TRANSFER TO BREAKER: COMPLETE`. O player sabe que poderá usar o pacote na Witness Spire, mesmo sem reencontrá-la.

**Retenção:** Evidence Locker preserva ID/hash, origem e public inputs, permitindo validar material no Final sem comunicação rastreável posterior. A confiança aqui é sincera e não implica que Rhea já planeje denúncia institucional.
