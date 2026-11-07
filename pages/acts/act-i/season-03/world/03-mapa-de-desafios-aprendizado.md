---
notion_id: 4019c563-0425-8120-bb15-ce9d8ce99725
source: https://app.notion.com/p/4019c56304258120bb15ce9d8ce99725?pvs=204
title: "🧪 03 — Mapa de Desafios & Aprendizado"
exported_at: 2026-11-07
---

**Mapa canônico de aprendizagem da Season 3.** Moonlight ensina três categorias diferentes: bugs de Soroban, falhas de invariant/ZK e threat models de privacy.

# Progressão

| Case | Categoria | Vulnerabilidade / conceito canônico |
| --- | --- | --- |
| 01 — The Public Secret | Soroban / privacy | `sensitive_storage` |
| 02 — The Loud Whisper | Soroban / privacy | `leaky_events` |
| 03 — Someone Else's Face | Soroban / auth | `unsafe_storage` |
| 04 — The Denied | Governance / privacy | `stale_pending_admin` aplicado à autoridade de associação |
| BOSS — The Witness | Composição | sem vulnerabilidade nova |
| 05 — Spent Twice | Invariant de privacy pool | nullifier replay / missing spent-nullifier check |
| 06 — The Proof That Lied | ZK soundness | under-constrained circuit |
| 07 — The Glass Trail | Threat model | metadata correlation; confidentiality ≠ anonymity |
| 08 — The Key That Sees | Autoridade de auditor | `audit_expiry_ignored` / view authority ampla demais |
| 09 — A Valid Lie | Gestão de chaves ZK | wrong verification key / verifier registry mismatch |
| 10 — Become Missing | Composição correta de privacy | commitments + nullifiers + unlinkability + disclosure mínimo |
| FINAL — The Witness Spire | Selective disclosure | sem vulnerabilidade nova |

# Por que `missing_events` saiu de Moonlight

`missing_events` continua sendo um problema útil de Soroban, mas pertence melhor à **Season 4 — Horizon/Galexie**, onde histórico, indexers e reconstrução são a fantasia central.

Moonlight usa `leaky_events` porque a lição de privacy é mais forte:

> **Seu state pode ter sido projetado para ser privado e ainda assim vazar pela camada de observabilidade.**

# Gate narrativo — O Sétimo

A lição sobre metadata correlation no Case 07 prepara dois resultados diferentes: proteger a trajetória **presente** de vigilância indiscriminada e compreender que a **associação histórica** entre operador de Lumen e credencial intercity pode ser conhecida por alguém em quem se confiou. Rhea não rouba chaves nem explora auth do Soroban. A confiança de Cases 06–09 precisa ser verdadeira. Depois da vitória independente da Witness Spire, Rhea entrega atestação histórica a outro procedimento de revisão e o acesso institucional do Breaker é suspenso. Essa é a consequência ética do disclosure, não uma vulnerabilidade adicional.

# Arco de aprendizagem

## Início

Privacy falha porque desenvolvedores colocam informação em locais públicos ou permitem que identity/compliance state seja corrompido.

## Meio

Privacy pools introduzem commitments, nullifiers e ZK.

O jogador aprende que verificar proof não é magia: soundness depende de constraints e invariants de estado.

## Final

A pergunta muda de:

> **Eles conseguem descriptografar meus dados?**

para:

> **Eles conseguem me inferir mesmo sem descriptografá-los?**

O jogador aprende os limites de amount confidentiality, auditor power e metadata.

# Regra de implementação

Todo Case precisa ser classificado internamente como:

**BUG** — implementação viola a propriedade de segurança pretendida.

**INVARIANT FAILURE** — protocolo deixa de aplicar um invariant criptográfico/de estado.

**THREAT MODEL** — sistema funciona como projetado, mas não oferece a propriedade de privacy que o usuário presumiu.

**CORRECT COMPOSITION** — o jogador precisa usar corretamente as primitives em vez de explorar um bug.

Essa distinção é essencial para o valor educacional da Season 3.

# Referências principais

[https://developers.stellar.org/docs/build/apps/privacy](https://developers.stellar.org/docs/build/apps/privacy)
[https://docs.openzeppelin.com/stellar-contracts/tokens/confidential/confidential](https://docs.openzeppelin.com/stellar-contracts/tokens/confidential/confidential)
[https://github.com/NethermindEth/stellar-private-payments](https://github.com/NethermindEth/stellar-private-payments)
[https://github.com/Veritas-Vaults-Network/soroban-guard-contracts](https://github.com/Veritas-Vaults-Network/soroban-guard-contracts)

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

**Regra técnica:** nem todo “sucesso” é exploit; Case 07 é threat model e Case 10 é composição correta. Fixar stack ZK/prover/verifier antes de implementar para evitar circuitos e VKs apenas fictícios. A apresentação dos objetivos está em [09 — Roteiro de Gameplay & Slides — Season 3](09-roteiro-de-gameplay-slides-season-3.md); as provas em [08 — Privacy Threat Model & Cadeia de Evidências](08-privacy-threat-model-cadeia-de-evidencias.md).
