---
notion_id: 4019c563-0425-815d-85d2-c19cb4f4f367
source: https://app.notion.com/p/4019c5630425815d85d2c19cb4f4f367?pvs=204
title: "🔑 08 — The Key That Sees"
exported_at: 2026-11-07
---

Here is the result of "fetch" for the Page with URL https://app.notion.com/p/4019c5630425815d85d2c19cb4f4f367 as of 2026-11-02T17:41:39.264Z:
<page url="https://app.notion.com/p/4019c5630425815d85d2c19cb4f4f367" icon="🔑">
<ancestor-path>
<parent-page url="https://app.notion.com/p/4019c563042581a2a331e66548c30494" title="04 — Cases & Bosses"/>
<ancestor-2-page url="https://app.notion.com/p/4019c56304258179bfa0fc93d15ac390" title="Season 03 — Shadows of Privacy — Moonlight"/>
<ancestor-3-page url="https://app.notion.com/p/4019c563042581469a0edc7e30a6eff9" title="ACT I — The World Is Breakable"/>
<ancestor-4-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
<properties>
{"title":"08 — The Key That Sees"}
</properties>
<iconMetadata>{"type":"emoji","emoji":"🔑"}</iconMetadata>
<content>
# História

Moonlight permite auditoria autorizada.

Um auditor deveria perder acesso após expiry ou revogação.

O sistema armazena expiry.

Os consumers não verificam.

Uma autoridade formalmente expirada ainda consegue operar.

# Missão

> <b>Veja através do Veil depois que seu direito de olhar expirou.</b>

# Vulnerabilidade canônica

<b>Audit Expiry Ignored — </b><b><code>audit_expiry_ignored</code></b>, aplicado à autoridade de auditor/view access.

# Aprendizado

- view authority é uma capability;
- expiry precisa ser aplicada no consumo;
- revogação sem enforcement é cosmética;
- auditabilidade também exige disciplina de acesso.

# Condição de vitória

Usar uma auditor credential expirada em um consumer que lê o registro, mas ignora validade temporal.

# Consequência narrativa

<b>Risco compartilhado:</b> para demonstrar a origem de uma operação sem abrir o Veil inteiro, Rhea expõe sua própria credencial de sender a um registro verificável e assume escrutínio sobre sua participação. O Breaker poderia abandoná-la e preservar somente sua trajetória; ele a protege. Ambos assumem risco por alguém em quem começam a confiar. Não é encenação.

Rhea vê a extensão do poder institucional e conclui:

> <b>“Isso não devia existir.”</b>

Breaker:

> “Auditoria não é o problema.”

Rhea:

> <b>“É sempre isso que dizem antes de alguém decidir que a exceção precisa crescer.”</b>

O Breaker ainda não responde.

No Verifier Registry existe outra inconsistência.

Unlock:

<b>CASE 09 — A VALID LIE</b>

# Referências

[https://github.com/Veritas-Vaults-Network/soroban-guard-contracts](https://github.com/Veritas-Vaults-Network/soroban-guard-contracts)<br />[https://developers.stellar.org/docs/build/apps/privacy](https://developers.stellar.org/docs/build/apps/privacy)

## Loop jogável v2 — consumer aplica expiry de audit capability

<callout icon="🔑" color="yellow_bg">
<b>Limite técnico:</b> a fixture deve definir um serviço/protocolo específico de auditoria, com ciphertexts ou view interface de acesso controlado. Não existe uma “view key master” capaz de tornar privado o ledger público da Stellar. Revogação não faz desaparecer plaintext já divulgado.
</callout>

<b>Investigar:</b> audit credential, escopo de operação, issuer, expiry/revocation e consumer responsável por liberar acesso à informação protegida.

<b>Executar:</b> em ambiente de teste, apresentar capability expirada e demonstrar que consumer vulnerável ainda entrega material restrito. O secure mirror rejeita acesso fora da janela válida.

<b>Feedback:</b> <b>EXPIRY PASSED / ACCESS GRANTED</b> versus <b>ACCESS DENIED</b> no mirror; registrar qual informação poderia ser revelada e por qual mecanismo.

<b>Relação:</b> Rhea registra sua própria origem e aceita escrutínio para preservar prova; Breaker escolhe não abandoná-la. Ambos assumem risco concreto. Rhea questiona a existência da capability, mas ainda não pede sua destruição.

<b>Diferencial:</b> <b>capability temporal e escopo de auditoria</b>, diferente de under-constrained ZK ou correlação de metadados.
</content>
</page>

