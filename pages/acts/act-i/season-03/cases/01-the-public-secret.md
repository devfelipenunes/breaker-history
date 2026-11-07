---
notion_id: 4019c563-0425-815d-ac3f-ea69d88e6aa1
source: https://app.notion.com/p/4019c5630425815dac3fea69d88e6aa1?pvs=204
title: "🔓 01 — The Public Secret"
exported_at: 2026-11-07
---

# Entrada — Sera no Blind Quarter

Antes da investigação da safehouse, o Breaker encontra Sera pessoalmente pela primeira vez. Reconhece a assinatura da Network Wire e a autora da publicação de Lumen.

Sera protege uma fonte identificada apenas como **SOURCE: E.V.**. Explica que revelar a relação entre jornalista e fonte já pode causar dano, mesmo sem revelar o conteúdo da conversa. Não mostrar o nome Eli Venn neste ponto.

Esse encontro não fornece a solução do challenge. Estabelece quem seria atingido pela exposição indiscriminada que a Spire poderá exigir.

O Breaker considera contatar Mara e abandona a tentativa antes de enviar qualquer mensagem: criar uma relação observável poderia colocá-la em risco.

# Story

Uma safehouse do Blind Quarter deveria depender de uma chave não pública.

Os Witnesses chegam até ela sem quebrar cifra alguma.

O Breaker descobre que o contrato gravou material secreto diretamente no ledger.

# Mission

> **Read a secret without asking permission.**

# Canonical Vulnerability

**Sensitive Data in Public Storage — **`sensitive_storage`**.**

Soroban contract storage é legível no ledger. Autorização protege escrita e execução; não transforma ledger state em banco secreto.

# Learning

- onchain storage is public;
- auth on setter does not make stored value private;
- store commitments/hashes, not raw secrets;
- privacy begins with data placement.

# Win Condition

Recuperar a credencial/secret diretamente do ledger state sem invocar um método “privileged”.

# Narrative Result

O Breaker muda de rota.

Desta vez não há segredo em storage.

Mesmo assim, outra operação privada revela mais do que deveria.

Unlock:

**CASE 02 — THE LOUD WHISPER**

# References

[https://github.com/Veritas-Vaults-Network/soroban-guard-contracts](https://github.com/Veritas-Vaults-Network/soroban-guard-contracts)
[https://developers.stellar.org/docs/learn/fundamentals/contract-development/storage/persisting-data](https://developers.stellar.org/docs/learn/fundamentals/contract-development/storage/persisting-data)

## Loop jogável v2 — leitura forense de storage público

**Investigar:** o player recebe o endereço do contrato da safehouse, footprint/keys de estado e o relato de que ninguém apresentou autorização de acesso privilegiado. Sera introduz SOURCE E.V. sem nome; o Breaker não envia mensagem a Mara.

**Hipótese:** o aplicativo protege setter/execution, mas deixou segredo em entrada pública de storage. Não existe “private storage Soroban” por default.

**Executar:** ler ledger state e reconstruir a credencial de teste sem invocar método de view privilegiado. Não usar segredo real de usuários.

**Feedback/verifier:** provar bytes/commitment correspondentes ao valor conhecido na fixture, origem no state e ausência de auth; mirror seguro guarda compromisso ou ciphertext em vez de raw secret. Bloquear false positives que apenas chamem getter.

**Conseqüência:** safehouse comprometida exige nova rota; próximo evento vaza metadata embora a próxima operação não exponha segredo raw em state. A ação dominante é **investigar storage**, não forjar identidade.

## Preparação aprovada de SOURCE E.V. — documento útil sem revelar origem

Sera entrega ao Breaker um **extrato redigido de arquivo administrativo** referente às políticas de association e ao cancelamento de uma autorização antiga. Esse extrato será uma **pista documental independente** para a auditoria de governança no Case 04; não revela o mecanismo exato de stale pending admin nem substitui eventos de ledger.

O conteúdo fornecido ao Breaker é verificável por hash e assinatura de documento. No repositório seguro da jornalista, porém, existe um **envelope de proveniência** que associa o recebimento do documento à fonte identificada apenas como SOURCE E.V. A ordem de full disclosure de rede tentaria acessar também esse envelope. A prova mínima de Moonlight utiliza o extrato e as âncoras de autenticidade, **não** a identidade da fonte.

**Apresentação:** `ARCHIVAL NOTICE: CANCELLED` / `DOCUMENT HASH: VERIFIED` / `SOURCE: E.V.` / `PROVENANCE: SEALED`. Não mencionar Eli Venn neste Case e não fazer Sera entregar a solução.
