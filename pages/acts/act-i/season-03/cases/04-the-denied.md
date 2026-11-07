---
notion_id: 4019c563-0425-81f5-9e4f-d18a997c36e2
source: https://app.notion.com/p/4019c563042581f59e4fd18a997c36e2?pvs=204
title: "⛔ 04 — The Denied"
exported_at: 2026-11-07
---

# Story

O Association Set Provider de Moonlight passou por uma troca administrativa.

A transferência foi “cancelada”.

O evento registra o cancelamento.

Mas o pending admin continua em storage.

A entidade antiga ainda consegue aceitar a transferência e controlar allow/block sets.

# Mission

> **Assuma uma autoridade que a cidade acredita ter revogado.**

# Canonical Vulnerability

**Stale Pending Admin — **`stale_pending_admin`**.**

# Learning

- two-step admin transfer;
- cancellation must mutate state, not only emit an event;
- stale privilege;
- privacy/compliance systems are only as trustworthy as their governance.

# Win Condition

Assumir a autoridade administrativa depois de um cancelamento aparentemente concluído.

# Narrative Result

Agora o Breaker entende como sua association foi marcada.

Ele preserva uma cadeia de evidências com proveniência verificável: policy e association state no ledger da settlement, cancelamento da transferência administrativa, retomada via pending state e alteração posterior para DENIED. Distinguir a revogação institucional pretendida do estado técnico que falhou em aplicá-la.

Essas evidências estabelecem cronologia, mas ainda precisam ser vinculadas ao commitment da settlement pelos witnesses de Rhea e Breaker. Isso prepara a cooperação forçada em Case 05 e a prova mínima do Final, sem revelar identidades e valores de terceiros.

Mas saber isso não limpa seu nome.

The First Witness encontra sua posição.

Unlock:

**BOSS I — THE WITNESS**

# References

[https://github.com/Veritas-Vaults-Network/soroban-guard-contracts](https://github.com/Veritas-Vaults-Network/soroban-guard-contracts)
[https://github.com/NethermindEth/stellar-private-payments](https://github.com/NethermindEth/stellar-private-payments)

## Loop jogável v2 — auditoria de governança e policy histórica

**Investigar:** comparar eventos e storage do two-step admin transfer: CANCELLED foi emitido, mas pending admin não foi limpo. Conferir policy/association da settlement original, ledger de cancelamento, aceitação indevida e atualização posterior para DENIED.

**Executar:** em fixture isolada, aceitar uma transferência supostamente cancelada e demonstrar tomada de controle do Association Set Provider. Não mudar retroativamente a policy histórica.

**Verifier:** aceitar cancelamento somente quando pending state também se torna inacessível; a versão vulnerável aceita o admin cancelado, a segura recusa. Persistir a cronologia com proveniência: **settlement legítima na execução; cancelamento anterior à retomada indevida; DENIED posterior à settlement e à retomada**, sem impor ordem não definida entre settlement e cancelamento.

**Conseqüência:** o player descobre causa plausível e comprovável do DENIED subsequente, mas não tem sender witness suficiente para encerrar a acusação. First Witness o encontra; o boss exige escape e evidência mínima.

**QA:** cronologia consistente; não confundir false profile do Case 03 com o caminho histórico. Apenas consultar o ledger não entrega automaticamente o proof final da settlement.

## Cena de autoria aprovada — operador de compliance e autoridade cancelada

O Breaker recupera a trilha: evento `ADMIN TRANSFER CANCELLED`, estado `PENDING ADMIN: STILL ACTIVE`, aceitação posterior pelo **operador institucional encarregado da revisão de risco**, e alteração `ASSOCIATION: DENIED` sobre a rota da garantia devolvida. O operador utilizou procedimento legado por acreditar que seu mandato era válido; a falha do contrato tornou executável aquilo que a instituição havia cancelado.

**Causa da reclassificação:** alerta pós-crise de Lumen e política emergencial de compliance, sem prova suficiente de fraude da settlement específica. O jogador vê documento de procedimento, assinatura administrativa, timestamp e evento de status. A origem real do DENIED é esta governança, **não** a possibilidade genérica de falsificar profile do Case 03.

**QA:** T\_cancel \< T\_accept \< T\_denied; T\_settlement \< T\_denied. Não impor ordem ainda não confirmada entre cancelamento e settlement. O challenge reproduz revogação incompleta; não exige revelar identidade civil do operador como novo personagem principal.

## Pistas independentes aprovadas para a descoberta de DENIED

O Breaker cruza **(1) o extrato redigido e autenticado** entregue por Sera com origem protegida SOURCE E.V.; **(2) CANCELLED e PENDING STATE** do ledger; **(3) evento de aceitação pelo operador institucional e a nova association DENIED**. O documento explica a intenção procedimental e o registro institucional; o contrato demonstra a falha de governança. A jornalista não revela o bug em diálogo. A origem pessoal do documento permanece protegida também após o caso.
