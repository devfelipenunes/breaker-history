---
notion_id: 40d9c563-0425-81ba-9836-c2856425010e
source: https://app.notion.com/p/40d9c563042581ba9836c2856425010e?pvs=204
title: "🔴 P0 — Prova de autoria de Voss | Dossiê auditável do Vault"
exported_at: 2026-11-07
---

**P0 — GATE DE LANÇAMENTO DA SEASON 1.** O roteiro v1.4 já define Voss como responsável canônico. Esta página transforma a conclusão em uma **prova que o próprio jogador pode auditar**. Não criar nova cena, não modificar o final e não afirmar que a fixture ou os contratos já estão implementados. A frase `ATTRIBUTION VERIFIED: AREN VOSS` deve ser bloqueada enquanto qualquer requisito de autoria ou causalidade estiver ausente.

## 0 — Resultado procurado e fontes

**Pergunta:** quem provocou, por qual operação autenticada, a condição que levou à movimentação de 2,4 milhões do Vault — e para onde os recursos foram?

**Fontes vigentes:** [BREAKER — Season 1 | FINAL NARRATIVE v1.4 — NARRATIVE LOCK](../narrative/breaker-season-1-final-narrative-v1-4-narrative-lock.md) (história e copy v1.4, §11); [01 — No Forced Entry](../cases/01-no-forced-entry.md) (AccessGate, Case 01); [05 — The Missing Investigator](../cases/05-the-missing-investigator.md) (avisos e vínculo institucional da chave, Case 05); [FINAL BOSS — The Architect](../cases/final-boss-the-architect.md) (confronto e dossiê, Architect); [15 — Plano de Melhorias e QA — Season 1](15-plano-de-melhorias-e-qa-season-1.md) (QA e bloqueios).

**Base técnica externa:** [Stellar — composable auth](https://stellar.org/blog/foundation-news/stellars-composable-auth-model); [Stellar SDK — contract auth](https://stellar.github.io/js-stellar-sdk/guides/07-contract-auth/); [Stellar XDR — SorobanAuthorizationEntry](https://github.com/stellar/stellar-xdr/blob/main/Stellar-transaction.x); [Stellar — histórico e retenção RPC](https://developers.stellar.org/docs/data/apis/rpc/api-reference/methods/getHealth); [Stellar — full history](https://developers.stellar.org/docs/data/indexers/build-your-own/galexie/admin_guide/full-history-exporting).

## 1 — Atribuição: o problema que pode quebrar o final

**A assinatura do envelope NÃO é automaticamente a autorização do endereço passado como owner.** Na Stellar, o envelope pode ser assinado por quem submete/paga a transação, enquanto um endereço pode autorizar uma invocação por uma entrada SorobanAuthorizationEntry específica; a credencial SOURCE\_ACCOUNT, quando aplicável, deriva da assinatura do envelope. O argumento `owner` sem `owner.require_auth()` não carrega consentimento do proprietário.

**Duas formas possíveis de provar autoria da chamada histórica:**

- **Caminho A — DIRETO (preferencial para a fixture da Season 1):** a operação original `AccessGate.open(...)` está no envelope XDR da transação histórica; o source é a conta operacional de Voss, a assinatura do envelope é válida segundo os signers/thresholds vigentes no ledger do incidente e não há relayer/sponsor cuja assinatura seja confundida com autorização de Voss. A assinatura do source prova que a conta participou da emissão da transação que contém aquela chamada, **não** que o owner falso consentiu.
- **Caminho B — INTERMEDIADO (usar apenas se realmente implementado):** o fee-payer/transaction source é outro agente; existe uma entrada SorobanAuthorizationEntry com credencial e árvore de invocações que atribuem à conta de Voss a **chamada exata**, OU existe uma ordem/intenção externa autenticada por Voss e vinculada criptograficamente a rede, contrato, função, argumentos, nonce e operação que foi executada. A entrada não pode ser inventada para uma chamada que não exigia `require_auth`. Sem esse artefato específico, o relayer NÃO comprova autoria.

**Decisão de implementação recomendada:** usar caminho A na fixture canônica para tornar a primeira investigação auditável e reduzir ambiguidades. Se o código real exigir B, documentar e testar explicitamente B em vez de atribuir uma intenção a quem apenas pagou taxas.

**Limite epistemológico:** uma assinatura comprova uso de chave; um registro institucional confiável comprova que a organização atribuiu aquela chave a Voss, mas não prova metafisicamente que ninguém a roubou. Para uma conclusão humana convincente, a fixture deve conter cadeia de custódia independente da credencial, validade na data e ausência de indícios de uso por terceiros. Se houver suspeita fundada de comprometimento/delegação desconhecida, não apresentar `ATTRIBUTION VERIFIED` como conclusão inequívoca.

## 2 — Dossiê auditável — sete gates obrigatórios

| Gate | Evidência que o jogador pode inspecionar | Validação exigida | Quando aparece |
| --- | --- | --- | --- |
| G0 — Incidente autêntico | Rede, ledger, `vault_trigger_tx_hash`, envelope, resultado/metadados XDR e número da operação | Hash correto e transação realmente bem-sucedida na rede/fixture | Prólogo (sem nome de Voss) |
| G1 — Chamada que altera a porta | ID do AccessGate, função, argumentos, `owner_argument`, estado da rota 17 antes/depois, `gate_event_id` | Comprovar `open()` efetivo e falta de `require_auth` do owner | Case 01 / A03 |
| G2 — Ator autenticado | Source/assinaturas **ou** entrada/ordem assinada vinculada à invocação | Verificar criptograficamente quem autenticou a chamada exata, signers e limiares da época; nunca fee-payer isolado | Case 01 pode inspecionar; A04 conclui |
| G3 — Vínculo humano confiável | `voss_key_record_id`, conta operacional, emissor institucional, chave pública do emissor, assinatura e vigência; custódia histórica | Documento institucional assinado por emissor independente, anterior ao incidente, válido no momento do evento, trust anchor verificável e sem evidência contraditória de comprometimento/delegação | Case 05 (sem resolver); A04 confere |
| G4 — Causa, não coincidência | `gate_state_key/route=17`, versão/nonce ou rastro de storage, `recovery_ref`, ledger/call trace | Demonstrar que RecoveryController consultou/aceitou o estado escrito pela chamada de G1. **Um evento GateOpen é recibo, não prova suficiente do estado consumido.** Comparar chave/versão e ordem de execução, não somente timestamp | Architect A03 |
| G5 — Dinheiro e política | transferência com asset, unidade, quantidade bruta/decimais, contrato Vault, destino Escrow e policy de saque vigente | Confirmar **Vault→Escrow institucional**, exatamente 2.400.000 unidades narrativas, sem AccessGate como carteira intermediária e sem direito de saque pessoal de Voss | Ledger consultável cedo; A03 conclui |
| G6 — Fechamento composto | provas G0…G5 conferidas fora da interface do Architect | Validador/testes independentes liberam atribuição somente se todas condições forem verdadeiras | A04; nunca só por fala do Boss |

**Observação crucial sobre Soroban:** evento emitido pelo contrato e estado de storage são evidências diferentes. Se a implementação do RecoveryController usa estado do AccessGate, a fixture deve mostrar exatamente a leitura do estado/rota e a escrita anterior associada. Se executa por outra condição verificável, alterar o gate de prova para a condição **real do código** antes de aprovar a cena. Não inventar que um contrato consome magicamente um evento emitido.

## 3 — Manifesto, alertas e motivo NÃO são prova do incidente

- A assinatura Ed25519 do **manifesto de diagnóstico** prova integridade/proveniência desse documento e o escopo `DiagnoseCore`. **Não** prova a assinatura do incidente, autorização do owner, controle do Escrow ou culpa de Voss.
- Os três avisos de Voss são **anteriores ao incidente** e mostram que identificou falhas. Não bastam para identificar quem executou a chamada histórica.
- A nota anterior sobre `RECOVERY QUARANTINE` informa hipótese de intenção de forçar uma auditoria; não demonstra, por si só, autoria criptográfica, nem absolve o custo de serviços atrasados em Lower Meridian.
- `AREN VOSS: REFUSED` significa visita anterior à Sequence, sem explicar o motivo da recusa. Não usar isso como prova do Vault.
- A identidade de Elias Var é uma referência de operador legado, **não** signatário nem recebedor dos 2,4 milhões.

## 4 — Fixture histórica mínima — formato exigido, sem valores inventados

Armazenar a fixture versionada por rede/ledger e publicar seu hash para auditoria. O JSON abaixo representa **campos e relações**, não uma transação existente:

```json
{
  "network_passphrase": "<network from runtime>",
  "vault_trigger_tx_hash": "<actual historical or deterministic test tx hash>",
  "incident_ledger": "<ledger sequence>",
  "incident_operation_index": "<invoke op index>",
  "transaction_envelope_xdr": "<signed XDR>",
  "transaction_result_xdr": "<result XDR>",
  "transaction_meta_xdr": "<ledger execution meta XDR>",
  "tx_source_account": "<account source>",
  "tx_signatures": ["<real envelope signatures>"],
  "auth_entries": ["<if any, with exact root/sub-invocations>"],
  "access_gate_contract_id": "<C...>",
  "owner_argument": "<owner address with missing require_auth>",
  "gate_event_id": "<derived from real event / tx>",
  "gate_state_key": "<route 17 actual storage key>",
  "gate_state_version": "<nonce / ledger / version if applicable>",
  "recovery_controller_contract_id": "<C...>",
  "recovery_ref": "<actual controller call/operation trace>",
  "recovery_observed_gate_state": "<proof/trace of consumed state>",
  "vault_contract_id": "<C...>",
  "escrow_contract_id": "<C...>",
  "asset_id": "<asset>",
  "amount_raw": "<integer units>",
  "asset_decimals": "<verified token decimals>",
  "escrow_credit_ref": "<actual token transfer reference>",
  "escrow_policy_at_incident": "<policy/custody evidence>",
  "voss_operational_account": "<G... or expected account>",
  "voss_key_record_id": "<institutional archive ID>",
  "voss_key_attestation": "<signed source record>",
  "attestor_public_key": "<pinned independent issuer key>",
  "key_valid_from": "<verified time>",
  "key_valid_until": "<verified time>",
  "key_custody_evidence": "<independent custody log/attestation>",
  "evidence_manifest_sha256": "<digest of all cited artifacts>"
}
```

**Não** salvar frases como "signature valid" como substitutas de um verificador. O sistema deve recomputar assinaturas, integridade, vigência, assinatura de emissor e identificadores. IDs exemplificativos `<...>` devem ser substituídos exclusivamente por dados reais da fixture ou da rede. Nunca expor chaves privadas.

### Recuperação histórica e retenção

A API RPC possui janela de retenção e o Horizon pode não disponibilizar todo o histórico antigo. Para uma transação histórica fictícia do jogo, usar uma fixture XDR assinada e determinística com metadados reproduzíveis, ou um arquivo de histórico confiável que permita recuperar os ledgers antigos; não prometer que um RPC público conterá indefinidamente a transação. Vincular ledger sequence, hash da fixture e passphrase da rede para evitar replay e dados trocados.

## 5 — Testes positivos, negativos e falsificadores

**Teste positivo T00:** G0…G6 válidos para a mesma rede, mesma instância/história, mesmas contas, estado de rota 17 e amount/token/policy. O verificador mostra o selo de autoria e permite o dossiê completo.

| ID | Variação adversarial | Resultado exigido |
| --- | --- | --- |
| N01 | `owner_argument = Voss` sem assinatura de Voss vinculada à chamada | REJECT |
| N02 | Fee-payer/relayer é Voss, mas a chamada foi autorizada por outra identidade | REJECT |
| N03 | Source é relayer, sem auth entry nem ordem/intenção assinada para invocação exata | REJECT |
| N04 | Assinatura da transação inválida, rede trocada ou operation index não corresponde ao AccessGate | REJECT |
| N05 | Autorização Soroban aponta para função/args/nonce diferentes da chamada executada | REJECT |
| N06 | Emissor institucional não confiável, assinatura de registro inválida ou registro autodeclarado | REJECT |
| N07 | Registro de chave emitido após o incidente, revogado/vencido na data ou log de custódia contraditório | REJECT |
| N08 | Chave historicamente atribuída a outro operador ou delegação/comprometimento relevante não esclarecido | REJECT para atribuição humana categórica |
| N09 | GateOpen emitido mas RecoveryController usa outra rota, outro estado/versão, ou não lê o estado do Gate | REJECT |
| N10 | Apenas timestamps coincidem; não há prova de condição causal consumida | REJECT |
| N11 | Transferência não vai ao Escrow institucional, o asset/amount difere ou Voss pode sacar diretamente | REJECT; corrigir fixture ou cânone |
| N12 | Incidente de teste do jogador é usado como se fosse a transação original do Prólogo | REJECT |
| N13 | Manifesto de diagnóstico assinado é apresentado como assinatura do Vault | REJECT |
| N14 | Architect responde `ATTRIBUTION VERIFIED` na UI sem gates comprovados no verificador | REJECT |
| N15 | Dados do histórico desaparecem por retenção RPC e não existe fixture assinada/verificável | BLOCKED, nunca aprovação por texto estático |

**Forma de evidenciar cada teste:** comando, versão SDK/commit, rede, fixture hash, resultado esperado/obtido, logs, referência de falha e assinatura/commit do verificador. Não marcar checkboxes sem artefato.

## 6 — História do jogador: três pistas, uma conclusão (SEM slides novos)

| Etapa existente | O jogador vê | O que ainda NÃO pode concluir |
| --- | --- | --- |
| Prólogo / P00.3 | Hash público da transação e saldo; saldo zero e porta intacta | Quem acionou a recuperação |
| Case 01 / C01.3 | GateOpen, owner argument diferente do source/auth do incidente, Elias apenas no índice legado | Que Elias, source ou fee-payer seja necessariamente o culpado |
| Case 05 / C05.4 | Registro institucional assinado e historicamente válido da conta de Voss, três alertas, nota de escalada | Que assinou a operação do Vault só porque encontrou o manifesto ou avisos |
| Architect / A03 | Rota causal Gate state→RecoveryController e Vault→Escrow em **painéis distintos** | Que o Architect possa certificar a própria versão |
| Architect / A04 | Overlay compara transação/ator autenticado com cadastro institucional e rastro causal; o jogador faz o match antes do selo | Motivo exato da recusa de Voss ou absolvição moral |
| Architect / A05–A07 | Custos para Lower Meridian, perfil do Breaker, status PROVISIONAL e recibo de Mara | Que a capacidade técnica legitima todas as decisões |

**Falsas hipóteses a refutar por evidências visíveis:** “Elias roubou” → registro legado e data de óbito; “Voss recebeu o dinheiro” → Escrow e policy; “o Architect inventou a culpa” → transação, registro de chave e rastro consultáveis independentes. Jogadores atentos podem deduzir Voss antes do Boss: o jogo não deve esconder dados públicos ou fabricar respostas.

**Ritmo:** não acrescentar cartão ou monólogo; usar os espaços C01.3, C05.4, A03 e A04 existentes, com inspeção opcional de fonte e comparação de hashes. A revelação `ATTRIBUTION VERIFIED` só aparece quando os gates técnicos passam.

## 7 — Estado e responsabilidades de produção

| Item | Estado da auditoria documental | Critério de aprovação |
| --- | --- | --- |
| História e causalidade escritas | ✅ Especificadas na v1.4 | Não mudar o roteiro |
| Esquema de prova / ameaças / testes | ✅ Especificados aqui | Validar com código real |
| Fixture do Vault e assinaturas | ⏳ NÃO verificadas | Gerar/recuperar XDR, assinaturas e hashes reais |
| Registro institucional independente + custódia | ⏳ NÃO verificados | Fonte, issuer, validade, anti-comprometimento |
| Causalidade Gate/Controller | ⏳ NÃO verificada | Estado escrito/consumido + trace |
| Escrow e direitos de saque | ⏳ NÃO verificados | Token, amount, destinatário, policy e testes |
| Frontend / Evidence Locker / selo de autoria | ⏳ NÃO verificados | Integração e testes negativos N01–N15 |
| Playtest de reconstituição causal | ⏳ NÃO executado | Jogador identifica as três fontes e refuta hipóteses sem fala do Architect |

**DoD P0:** se houver qualquer ambiguidade de ator autenticado, issuer não verificável, cadeia causal só por timestamp/evento, ou Escrow com política conflitante, **não publicar** a tela de atribuição. O fato narrativo “Voss provocou a recuperação” permanece no cânone; é a **evidência de implementação** que deve ser construída/corrigida.

## 8 — Checklist rápido de playtest cego

Após o Architect, sem alternativas selecionáveis: “Qual transação foi usada?”, “Qual diferença existe entre owner e signatário/autor da chamada?”, “Como sabemos que a chave pertencia a Voss na data?”, “Qual estado do Gate a recuperação utilizou?”, “Para onde foi o dinheiro e quem pode sacá-lo?”, “O que os alertas demonstram e o que NÃO demonstram?”. Aceitar respostas apoiadas em documentos do jogo, não em uma fala do Boss. Registrar cada falha de compreensão por slide/prova ausente e corrigir Evidence Locker/UX antes de mexer na história.
