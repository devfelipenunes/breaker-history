---
notion_id: 4019c563-0425-8120-bb15-ce9d8ce99725
source: https://app.notion.com/p/4019c56304258120bb15ce9d8ce99725?pvs=204
title: "🧪 03 — Mapa de Desafios & Aprendizado"
exported_at: 2026-11-07
---

Here is the result of "fetch" for the Page with URL https://app.notion.com/p/4019c56304258120bb15ce9d8ce99725 as of 2026-11-02T17:43:28.893Z:
<page url="https://app.notion.com/p/4019c56304258120bb15ce9d8ce99725" icon="🧪">
<ancestor-path>
<parent-page url="https://app.notion.com/p/4019c56304258179bfa0fc93d15ac390" title="Season 03 — Shadows of Privacy — Moonlight"/>
<ancestor-2-page url="https://app.notion.com/p/4019c563042581469a0edc7e30a6eff9" title="ACT I — The World Is Breakable"/>
<ancestor-3-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
<properties>
{"title":"03 — Mapa de Desafios & Aprendizado"}
</properties>
<iconMetadata>{"type":"emoji","emoji":"🧪"}</iconMetadata>
<content>
<callout icon="🧪" color="purple_bg">
<b>Mapa canônico de aprendizagem da Season 3.</b> Moonlight ensina três categorias diferentes: bugs de Soroban, falhas de invariant/ZK e threat models de privacy.
</callout>

# Progressão

| Case | Categoria | Vulnerabilidade / conceito canônico |
| --- | --- | --- |
| 01 — The Public Secret | Soroban / privacy | <code>sensitive_storage</code> |
| 02 — The Loud Whisper | Soroban / privacy | <code>leaky_events</code> |
| 03 — Someone Else's Face | Soroban / auth | <code>unsafe_storage</code> |
| 04 — The Denied | Governance / privacy | <code>stale_pending_admin</code> aplicado à autoridade de associação |
| BOSS — The Witness | Composição | sem vulnerabilidade nova |
| 05 — Spent Twice | Invariant de privacy pool | nullifier replay / missing spent-nullifier check |
| 06 — The Proof That Lied | ZK soundness | under-constrained circuit |
| 07 — The Glass Trail | Threat model | metadata correlation; confidentiality ≠ anonymity |
| 08 — The Key That Sees | Autoridade de auditor | <code>audit_expiry_ignored</code> / view authority ampla demais |
| 09 — A Valid Lie | Gestão de chaves ZK | wrong verification key / verifier registry mismatch |
| 10 — Become Missing | Composição correta de privacy | commitments + nullifiers + unlinkability + disclosure mínimo |
| FINAL — The Witness Spire | Selective disclosure | sem vulnerabilidade nova |

# Por que <code>missing_events</code> saiu de Moonlight

<code>missing_events</code> continua sendo um problema útil de Soroban, mas pertence melhor à <b>Season 4 — Horizon/Galexie</b>, onde histórico, indexers e reconstrução são a fantasia central.

Moonlight usa <code>leaky_events</code> porque a lição de privacy é mais forte:

> <b>Seu state pode ter sido projetado para ser privado e ainda assim vazar pela camada de observabilidade.</b>

# Gate narrativo — O Sétimo

A lição sobre metadata correlation no Case 07 prepara dois resultados diferentes: proteger a trajetória <b>presente</b> de vigilância indiscriminada e compreender que a <b>associação histórica</b> entre operador de Lumen e credencial intercity pode ser conhecida por alguém em quem se confiou. Rhea não rouba chaves nem explora auth do Soroban. A confiança de Cases 06–09 precisa ser verdadeira. Depois da vitória independente da Witness Spire, Rhea entrega atestação histórica a outro procedimento de revisão e o acesso institucional do Breaker é suspenso. Essa é a consequência ética do disclosure, não uma vulnerabilidade adicional.

# Arco de aprendizagem

## Início

Privacy falha porque desenvolvedores colocam informação em locais públicos ou permitem que identity/compliance state seja corrompido.

## Meio

Privacy pools introduzem commitments, nullifiers e ZK.

O jogador aprende que verificar proof não é magia: soundness depende de constraints e invariants de estado.

## Final

A pergunta muda de:

> <b>Eles conseguem descriptografar meus dados?</b>

para:

> <b>Eles conseguem me inferir mesmo sem descriptografá-los?</b>

O jogador aprende os limites de amount confidentiality, auditor power e metadata.

# Regra de implementação

Todo Case precisa ser classificado internamente como:

<b>BUG</b> — implementação viola a propriedade de segurança pretendida.<br /><br /><b>INVARIANT FAILURE</b> — protocolo deixa de aplicar um invariant criptográfico/de estado.<br /><br /><b>THREAT MODEL</b> — sistema funciona como projetado, mas não oferece a propriedade de privacy que o usuário presumiu.<br /><br /><b>CORRECT COMPOSITION</b> — o jogador precisa usar corretamente as primitives em vez de explorar um bug.

Essa distinção é essencial para o valor educacional da Season 3.

# Referências principais

[https://developers.stellar.org/docs/build/apps/privacy](https://developers.stellar.org/docs/build/apps/privacy)<br />[https://docs.openzeppelin.com/stellar-contracts/tokens/confidential/confidential](https://docs.openzeppelin.com/stellar-contracts/tokens/confidential/confidential)<br />[https://github.com/NethermindEth/stellar-private-payments](https://github.com/NethermindEth/stellar-private-payments)<br />[https://github.com/Veritas-Vaults-Network/soroban-guard-contracts](https://github.com/Veritas-Vaults-Network/soroban-guard-contracts)

# Matriz de jogabilidade v2 — mecânica dominante e dificuldade sugerida

| Fase | Ação dominante do player | Distinção central | Dificuldade sugerida |
| --- | --- | --- | --- |
| Prologue | Interpretar transferência válida vs association atual | Contexto de dois momentos | Narrativa |
| 01 | Ler ledger state público | Secret de storage | Fácil |
| 02 | Correlacionar eventos publicados | Telemetria vs state | Fácil–médio |
| 03 | Reproduzir profile mutation indevida | Falta de auth do subject | Médio |
| 04 | Reativar pending admin cancelado | Falha de governança e cronologia | Médio |
| Witness | Fugir preservando evidência, com disclosure mínimo | Composição, sem bug novo | Difícil |
| 05 | Reusar nullifier em pool vulnerável | Invariant de spent-state | Médio |
| 06 | Construir witness/proof sob circuito incompleto | Soundness de constraints | Médio–difícil |
| 07 | Inferir rota por metadados de dataset fictício | Threat model sem ataque à cifra | Médio |
| 08 | Usar audit capability expirada em consumer | Expiry enforcement específico | Médio |
| 09 | Demonstrar VK incompatível com policy | Verifier governance, não Case 06 repetido | Difícil |
| 10 | Compor privacy correta para baixa correlação | MISSING relativo ao observador | Difícil |
| Witness Spire | Prova positiva histórica + refutação + disclosure mínimo | Composição e decisão institucional | Muito difícil |

<b>Regra técnica:</b> nem todo “sucesso” é exploit; Case 07 é threat model e Case 10 é composição correta. Fixar stack ZK/prover/verifier antes de implementar para evitar circuitos e VKs apenas fictícios. A apresentação dos objetivos está em <mention url="https://app.notion.com/p/40c9c563042581cbb4f2c2c801ec0ea5" />; as provas em <mention url="https://app.notion.com/p/40c9c56304258163a9f8c7ed2abcdf1c" />.
</content>
</page>

