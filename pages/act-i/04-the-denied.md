---
notion_id: 4019c563-0425-81f5-9e4f-d18a997c36e2
source: https://app.notion.com/p/4019c563042581f59e4fd18a997c36e2?pvs=204
title: "⛔ 04 — The Denied"
exported_at: 2026-11-07
---

Here is the result of "fetch" for the Page with URL https://app.notion.com/p/4019c563042581f59e4fd18a997c36e2 as of 2026-11-03T00:06:46.194Z:
<page url="https://app.notion.com/p/4019c563042581f59e4fd18a997c36e2" icon="⛔">
<ancestor-path>
<parent-page url="https://app.notion.com/p/4019c563042581a2a331e66548c30494" title="04 — Cases & Bosses"/>
<ancestor-2-page url="https://app.notion.com/p/4019c56304258179bfa0fc93d15ac390" title="Season 03 — Shadows of Privacy — Moonlight"/>
<ancestor-3-page url="https://app.notion.com/p/4019c563042581469a0edc7e30a6eff9" title="ACT I — The World Is Breakable"/>
<ancestor-4-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
<properties>
{"title":"04 — The Denied"}
</properties>
<iconMetadata>{"type":"emoji","emoji":"⛔"}</iconMetadata>
<content>
# Story

O Association Set Provider de Moonlight passou por uma troca administrativa.

A transferência foi “cancelada”.

O evento registra o cancelamento.

Mas o pending admin continua em storage.

A entidade antiga ainda consegue aceitar a transferência e controlar allow/block sets.

# Mission

> <b>Assuma uma autoridade que a cidade acredita ter revogado.</b>

# Canonical Vulnerability

<b>Stale Pending Admin — </b><b><code>stale_pending_admin</code></b><b>.</b>

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

<b>BOSS I — THE WITNESS</b>

# References

[https://github.com/Veritas-Vaults-Network/soroban-guard-contracts](https://github.com/Veritas-Vaults-Network/soroban-guard-contracts)<br />[https://github.com/NethermindEth/stellar-private-payments](https://github.com/NethermindEth/stellar-private-payments)

## Loop jogável v2 — auditoria de governança e policy histórica

<b>Investigar:</b> comparar eventos e storage do two-step admin transfer: CANCELLED foi emitido, mas pending admin não foi limpo. Conferir policy/association da settlement original, ledger de cancelamento, aceitação indevida e atualização posterior para DENIED.

<b>Executar:</b> em fixture isolada, aceitar uma transferência supostamente cancelada e demonstrar tomada de controle do Association Set Provider. Não mudar retroativamente a policy histórica.

<b>Verifier:</b> aceitar cancelamento somente quando pending state também se torna inacessível; a versão vulnerável aceita o admin cancelado, a segura recusa. Persistir a cronologia com proveniência: <b>settlement legítima na execução; cancelamento anterior à retomada indevida; DENIED posterior à settlement e à retomada</b>, sem impor ordem não definida entre settlement e cancelamento.

<b>Conseqüência:</b> o player descobre causa plausível e comprovável do DENIED subsequente, mas não tem sender witness suficiente para encerrar a acusação. First Witness o encontra; o boss exige escape e evidência mínima.

<b>QA:</b> cronologia consistente; não confundir false profile do Case 03 com o caminho histórico. Apenas consultar o ledger não entrega automaticamente o proof final da settlement.

## Cena de autoria aprovada — operador de compliance e autoridade cancelada

O Breaker recupera a trilha: evento <code>ADMIN TRANSFER CANCELLED</code>, estado <code>PENDING ADMIN: STILL ACTIVE</code>, aceitação posterior pelo <b>operador institucional encarregado da revisão de risco</b>, e alteração <code>ASSOCIATION: DENIED</code> sobre a rota da garantia devolvida. O operador utilizou procedimento legado por acreditar que seu mandato era válido; a falha do contrato tornou executável aquilo que a instituição havia cancelado.

<b>Causa da reclassificação:</b> alerta pós-crise de Lumen e política emergencial de compliance, sem prova suficiente de fraude da settlement específica. O jogador vê documento de procedimento, assinatura administrativa, timestamp e evento de status. A origem real do DENIED é esta governança, <b>não</b> a possibilidade genérica de falsificar profile do Case 03.

<b>QA:</b> T\_cancel \< T\_accept \< T\_denied; T\_settlement \< T\_denied. Não impor ordem ainda não confirmada entre cancelamento e settlement. O challenge reproduz revogação incompleta; não exige revelar identidade civil do operador como novo personagem principal.

## Pistas independentes aprovadas para a descoberta de DENIED

O Breaker cruza <b>(1) o extrato redigido e autenticado</b> entregue por Sera com origem protegida SOURCE E.V.; <b>(2) CANCELLED e PENDING STATE</b> do ledger; <b>(3) evento de aceitação pelo operador institucional e a nova association DENIED</b>. O documento explica a intenção procedimental e o registro institucional; o contrato demonstra a falha de governança. A jornalista não revela o bug em diálogo. A origem pessoal do documento permanece protegida também após o caso.
</content>
</page>

