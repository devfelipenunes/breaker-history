---
notion_id: 4019c563-0425-812f-a5fb-e671aa3761ee
source: https://app.notion.com/p/4019c5630425812fa5fbe671aa3761ee?pvs=204
title: "🧠 06 — The Proof That Lied"
exported_at: 2026-11-07
---

Here is the result of "fetch" for the Page with URL https://app.notion.com/p/4019c5630425812fa5fbe671aa3761ee as of 2026-11-02T17:41:35.713Z:
<page url="https://app.notion.com/p/4019c5630425812fa5fbe671aa3761ee" icon="🧠">
<ancestor-path>
<parent-page url="https://app.notion.com/p/4019c563042581a2a331e66548c30494" title="04 — Cases & Bosses"/>
<ancestor-2-page url="https://app.notion.com/p/4019c56304258179bfa0fc93d15ac390" title="Season 03 — Shadows of Privacy — Moonlight"/>
<ancestor-3-page url="https://app.notion.com/p/4019c563042581469a0edc7e30a6eff9" title="ACT I — The World Is Breakable"/>
<ancestor-4-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
<properties>
{"title":"06 — The Proof That Lied"}
</properties>
<iconMetadata>{"type":"emoji","emoji":"🧠"}</iconMetadata>
<content>
# História

Um zero-knowledge proof afirma que o Breaker recebeu um ativo proibido.

O proof verifica.

O circuito, porém, não constrange corretamente uma variável essencial entre recipient, commitment e claim.

Rhea possui parte do witness original.

Breaker possui a parte de recebimento.

Pela primeira vez, eles precisam comparar dados sem confiar um no outro.

# Missão

> <b>Produza uma prova válida para uma afirmação que deveria ser impossível.</b>

# Vulnerabilidade canônica

<b>Under-Constrained ZK Circuit.</b>

Uma relação importante existe na witness generation, mas não está efetivamente constrangida no sistema de constraints.

# Aprendizado

- proof validity depende da soundness do circuito;
- witness generation não é constraint enforcement;
- signals under-constrained permitem witnesses falsos;
- PROOF VALID significa apenas que o verifier aceitou a relação realmente codificada.

# Condição de vitória

Gerar witness/proof aceito para uma afirmação que deveria ser impossível.

# Beat narrativo

First Witness:

> “A prova é válida.”

Breaker:

> <b>“A prova é válida. A afirmação não.”</b>

Rhea observa que o Breaker não tenta simplesmente destruir o verifier. Ela decide entregar um fragmento autenticado de seu witness de origem, mesmo podendo reter essa informação. É a primeira demonstração voluntária de confiança e perda de controle.

Esse é o primeiro momento em que ela começa a confiar no julgamento técnico dele, não apenas na capacidade. O Breaker percebe e começa a confiar nela também.

# Transição

A Witness Spire abandona essa linha de prova e começa a seguir comportamento.

Unlock:

<b>CASE 07 — THE GLASS TRAIL</b>

# Referência

[https://github.com/Musyg/circom-underconstrained-audit](https://github.com/Musyg/circom-underconstrained-audit)

## Loop jogável v2 — constraints faltantes (não wrong VK)

<b>Investigar:</b> código do circuito ZK da fixture, public inputs, witness generation e relação que deveria vincular recipient, commitment e claim. O verificador usa a VK <b>correta para esse circuito</b>; o erro mora na regra implementada.

<b>Hipótese:</b> produzir witness válido para as constraints existentes mesmo quando claim de negócio não corresponde ao recipient/commitment pretendido.

<b>Executar:</b> construir witness adversarial e uma proof válida sob a VK correta da fixture, violando o invariant de negócio omitido pelas constraints. O challenge deve incluir harness de prova reproduzível; não declarar “prova impossível” sem gerar o artefato.

<b>Verifier:</b> valida proof matematicamente, mas um check independente rejeita a relação de negócio esperada; secure circuit acrescenta constraint e não aceita o witness. Registrar versão de circuito, public input e verificador real usados.

<b>Consequência:</b> First Witness percebe que PROOF VALID não basta. Rhea entrega voluntariamente material de origem que poderia reter; é primeiro gesto real de confiança.

<b>Diferencial:</b> <b>under-constrained circuit</b> é diferente do Case 09, que troca/seleciona a VK ou policy errada para um circuito que pode estar correto.
</content>
</page>

