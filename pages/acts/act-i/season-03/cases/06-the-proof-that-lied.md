---
notion_id: 4019c563-0425-812f-a5fb-e671aa3761ee
source: https://app.notion.com/p/4019c5630425812fa5fbe671aa3761ee?pvs=204
title: "🧠 06 — The Proof That Lied"
exported_at: 2026-11-07
---

# História

Um zero-knowledge proof afirma que o Breaker recebeu um ativo proibido.

O proof verifica.

O circuito, porém, não constrange corretamente uma variável essencial entre recipient, commitment e claim.

Rhea possui parte do witness original.

Breaker possui a parte de recebimento.

Pela primeira vez, eles precisam comparar dados sem confiar um no outro.

# Missão

> **Produza uma prova válida para uma afirmação que deveria ser impossível.**

# Vulnerabilidade canônica

**Under-Constrained ZK Circuit.**

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

> **“A prova é válida. A afirmação não.”**

Rhea observa que o Breaker não tenta simplesmente destruir o verifier. Ela decide entregar um fragmento autenticado de seu witness de origem, mesmo podendo reter essa informação. É a primeira demonstração voluntária de confiança e perda de controle.

Esse é o primeiro momento em que ela começa a confiar no julgamento técnico dele, não apenas na capacidade. O Breaker percebe e começa a confiar nela também.

# Transição

A Witness Spire abandona essa linha de prova e começa a seguir comportamento.

Unlock:

**CASE 07 — THE GLASS TRAIL**

# Referência

[https://github.com/Musyg/circom-underconstrained-audit](https://github.com/Musyg/circom-underconstrained-audit)

## Loop jogável v2 — constraints faltantes (não wrong VK)

**Investigar:** código do circuito ZK da fixture, public inputs, witness generation e relação que deveria vincular recipient, commitment e claim. O verificador usa a VK **correta para esse circuito**; o erro mora na regra implementada.

**Hipótese:** produzir witness válido para as constraints existentes mesmo quando claim de negócio não corresponde ao recipient/commitment pretendido.

**Executar:** construir witness adversarial e uma proof válida sob a VK correta da fixture, violando o invariant de negócio omitido pelas constraints. O challenge deve incluir harness de prova reproduzível; não declarar “prova impossível” sem gerar o artefato.

**Verifier:** valida proof matematicamente, mas um check independente rejeita a relação de negócio esperada; secure circuit acrescenta constraint e não aceita o witness. Registrar versão de circuito, public input e verificador real usados.

**Consequência:** First Witness percebe que PROOF VALID não basta. Rhea entrega voluntariamente material de origem que poderia reter; é primeiro gesto real de confiança.

**Diferencial:** **under-constrained circuit** é diferente do Case 09, que troca/seleciona a VK ou policy errada para um circuito que pode estar correto.
