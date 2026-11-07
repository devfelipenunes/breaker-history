---
notion_id: 4019c563-0425-815d-85d2-c19cb4f4f367
source: https://app.notion.com/p/4019c5630425815d85d2c19cb4f4f367?pvs=204
title: "🔑 08 — The Key That Sees"
exported_at: 2026-11-07
---

# História

Moonlight permite auditoria autorizada.

Um auditor deveria perder acesso após expiry ou revogação.

O sistema armazena expiry.

Os consumers não verificam.

Uma autoridade formalmente expirada ainda consegue operar.

# Missão

> **Veja através do Veil depois que seu direito de olhar expirou.**

# Vulnerabilidade canônica

**Audit Expiry Ignored — **`audit_expiry_ignored`**, aplicado à autoridade de auditor/view access.

# Aprendizado

- view authority é uma capability;
- expiry precisa ser aplicada no consumo;
- revogação sem enforcement é cosmética;
- auditabilidade também exige disciplina de acesso.

# Condição de vitória

Usar uma auditor credential expirada em um consumer que lê o registro, mas ignora validade temporal.

# Consequência narrativa

**Risco compartilhado:** para demonstrar a origem de uma operação sem abrir o Veil inteiro, Rhea expõe sua própria credencial de sender a um registro verificável e assume escrutínio sobre sua participação. O Breaker poderia abandoná-la e preservar somente sua trajetória; ele a protege. Ambos assumem risco por alguém em quem começam a confiar. Não é encenação.

Rhea vê a extensão do poder institucional e conclui:

> **“Isso não devia existir.”**

Breaker:

> “Auditoria não é o problema.”

Rhea:

> **“É sempre isso que dizem antes de alguém decidir que a exceção precisa crescer.”**

O Breaker ainda não responde.

No Verifier Registry existe outra inconsistência.

Unlock:

**CASE 09 — A VALID LIE**

# Referências

[https://github.com/Veritas-Vaults-Network/soroban-guard-contracts](https://github.com/Veritas-Vaults-Network/soroban-guard-contracts)
[https://developers.stellar.org/docs/build/apps/privacy](https://developers.stellar.org/docs/build/apps/privacy)

## Loop jogável v2 — consumer aplica expiry de audit capability

**Limite técnico:** a fixture deve definir um serviço/protocolo específico de auditoria, com ciphertexts ou view interface de acesso controlado. Não existe uma “view key master” capaz de tornar privado o ledger público da Stellar. Revogação não faz desaparecer plaintext já divulgado.

**Investigar:** audit credential, escopo de operação, issuer, expiry/revocation e consumer responsável por liberar acesso à informação protegida.

**Executar:** em ambiente de teste, apresentar capability expirada e demonstrar que consumer vulnerável ainda entrega material restrito. O secure mirror rejeita acesso fora da janela válida.

**Feedback:** **EXPIRY PASSED / ACCESS GRANTED** versus **ACCESS DENIED** no mirror; registrar qual informação poderia ser revelada e por qual mecanismo.

**Relação:** Rhea registra sua própria origem e aceita escrutínio para preservar prova; Breaker escolhe não abandoná-la. Ambos assumem risco concreto. Rhea questiona a existência da capability, mas ainda não pede sua destruição.

**Diferencial:** **capability temporal e escopo de auditoria**, diferente de under-constrained ZK ou correlação de metadados.
