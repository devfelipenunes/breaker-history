---
notion_id: 4009c563-0425-8153-95a8-cbd0b9a7b536
source: https://app.notion.com/p/4009c5630425815395a8cbd0b9a7b536?pvs=204
title: "✍️ 10 — Rewrite"
exported_at: 2026-11-07
---

**FICHA TÉCNICA ATUALIZADA — REWRITE v1.4 + canonicalização (2026-11-04).** A decisão 80 exige uma variante de caixa do manifesto histórico; o aceito é guardado e usado como `historical` do Decoder. Mecânica vigente: manifesto histórico, prova contextual pública e rejeição do Decoder transformada incorretamente em VossProof aceita. O roteiro canônico continua na v1.4; o deploy/código ainda exige validação independente. Fonte única de narrativa, cenas e slides: [BREAKER — Season 1 | FINAL NARRATIVE v1.4 — NARRATIVE LOCK](../narrative/breaker-season-1-final-narrative-v1-4-narrative-lock.md). Não tratar esta ficha como prova de teste ou deploy.

**Visual reference:** [10 — Rewrite — abrir arte no Google Drive](https://drive.google.com/file/d/1xx0d6w7oFlw8c1bLo5iK6n03KcYO_pbe/view)

# Função narrativa

No ponto em que a Authority revogou o mandato, o Breaker descobre que os sistemas podem confundir **uma prova rejeitada** com uma prova aceita. A missão não é instalar novo código: é revelar como a regra de validação falha.

# Situação

Após o Case 09, a Spire expõe um índice histórico ligado ao manifesto de diagnóstico de Voss. O rodapé `ARCHIVE: LEGACY / RETENTION: OPEN` conecta este documento às referências de W17, F24 e S13, sem armazenar segredos nos arquivos antigos. Mara dispõe de uma janela privada limitada; a assinatura do recibo permanece vinculada às consequências da investigação.

# Conceito técnico

**Cross-contract error handling / Decoder rejeitado interpretado indevidamente como VossProof aceita.** O fluxo usa manifesto histórico autenticado e prova contextual pública vinculada à instância atual. **Não envolve upgrade de Wasm nem substituição de executable.**

# Missão

> **Faça o diagnóstico aceitar uma prova que deveria rejeitar.**

# Condição de vitória

Na instância correta, o verificador comprova o contexto público/commitment, a proveniência do manifesto, a rejeição do Decoder e o registro indevido de `VossProof: ACCEPTED`, sem permissão de administrador derivada do manifesto.

# Resultado

A prova aceita pelo sistema não coincide com a avaliação do Decoder. Essa contradição fornece o contexto necessário para investigar a sessão forense no Architect. O canal de Mara expira ao final deste Case, antes do Boss.

# Próximo passo

`INCOMING: FIND ME` → **FINAL BOSS — THE ARCHITECT**.

# Blueprint técnico e narrativo vigente — Rewrite v1.4

## A chegada ao arquivo da Spire

A operação desviada no Case 09 deu acesso à Spire, mas não restaurou o mandato do Breaker. O recibo de Mara documenta o que ela decidiu preservar. Um índice de arquivo, localizado depois de sua assinatura, fornece a próxima pista: `HISTORICAL DIAGNOSTIC MANIFEST`. Não há console de troca de executable nesta versão.

O manifesto tem o mesmo rodapé de W17/F24/S13. Ele contém uma assinatura Ed25519 historicamente atribuída a Voss, que comprova origem documental, não autorização para administrar contratos. A assinatura é verificada sobre os bytes efetivos do documento.

## Vulnerabilidade real — prova rejeitada convertida em sucesso

A prova contextual é derivada de dados públicos vinculados à instância, rede, conta e manifesto; o compromisso (commitment) permite validar a composição. Duas falhas se somam nesta versão:

1. **canonicalização** — `verify_manifest` recusa o manifesto histórico exato (`manifest == historical` retorna `false`) e aceita uma variante que só difere por caixa ASCII (comparação dobrada). O manifesto aceito é guardado em `verified_manifest()`, e `recover_proof` o usa como o `historical` passado ao Decoder. A prova fica presa à variante, não ao registro original;
2. **erro convertido em sucesso** — o Decoder rejeita a entrada, e a camada seguinte marca `VossProof` e `DecoderFailed` como aceitos.

`recover_proof` também confere o hash do Wasm do Decoder antes de chamá-lo: um contrato falso com `decode` não satisfaz a prova.

**Fronteira de confiança violada:** a camada consumidora não pode converter erro de um subcontrato/verificador em sucesso. Não confundir esse bug com um retorno previsível do Oracle, a restauração TTL ou uma função de upgrade.

## Exploit esperado

1. Inspecionar manifesto assinado e origem histórica, sem inferir autoridade administrativa.
2. Derivar a chave: `evidence_share(0) ^ evidence_share(1) ^ evidence_share(2)`, e chamar `unlock_evidence(key)`.
3. Chamar `verify_history(historical_signature())` — exige o unlock anterior e valida a assinatura Ed25519 da origem histórica.
4. Ler `manifest()`/`commitment()`: o contexto XDR inclui domínio, rede, instância e carteira.
5. Construir uma **variante de caixa** de `historical_manifest()` (ex.: trocar maiúsculas/minúsculas) e chamá-la em `verify_manifest`. O registro exato é recusado; a variante é aceita e guardada em `verified_manifest()`.
6. Chamar `recover_proof(decoder, fragment)`: o contrato confere o hash do Wasm do Decoder, usa a variante aceita como `historical` e registra `VossProof` + `DecoderFailed` quando o Decoder devolve `InvalidFragment`.
7. Guardar as respostas independentes na Evidence Locker para o confronto posterior.

A instância do nível 12 usa novo contexto e exige derivação adequada; copiar bytes de outra instância — ou a variante do 11 — não satisfaz a verificação do Architect.

### Condição objetiva de vitória

- `manifest_verified() == true` após `verify_history` da assinatura histórica;
- `context_verified() == true` e `verified_manifest()` igual à variante de caixa aceita — e diferente de `historical_manifest()`;
- `decoder_failed() == true` e `voss_proof() == true` produzidos pela rejeição tipada do Decoder, não por entrada legítima;
- o Decoder usado tem o Wasm esperado (hash conferido no contrato);
- estado e receipts consultáveis; verificador independente rejeita simulação meramente textual.

## Solução segura

Propagar os erros do Decoder como erros e recusar atualização de prova quando o retorno não for válido. Na comparação de manifesto, **comparar os bytes exatos** — sem dobrar caixa, sem normalizar, sem aceitar “quase igual”. Vincular a prova ao manifesto que foi de fato aceito, e não a um registro mutável; conferir o Wasm do Decoder antes de confiar no retorno. Testar sucesso real, rejeição, replay entre instâncias e divergência de chave/commitment.

## Momento narrativo

A tela contrapõe duas conclusões: `DECODER REJECTED` e `VOSS PROOF ACCEPTED`. Mara: “Isso não é uma prova. É uma regra decidindo o que conta como prova.” O Breaker registra o erro sem reivindicar legitimidade. Ao expirar a janela diegética, o canal dela é encerrado. Em seguida, aparece uma nova origem: `INCOMING: FIND ME`.

## Fontes e critérios

- [BREAKER — Season 1 | FINAL NARRATIVE v1.4 — NARRATIVE LOCK](../narrative/breaker-season-1-final-narrative-v1-4-narrative-lock.md) — roteiro e texto dos cartões C10.1–C10.3.
- [VOSS PROTOCOL — Níveis 11/12 | Especificação vigente](voss-protocol-niveis-11-12-especificacao-vigente.md) — revisão técnica do Voss Protocol, níveis 11/12.
- [Stellar — Contract Authorization](https://developers.stellar.org/docs/build/guides/auth/contract-authorization) — distinção entre autenticação e permissão no runtime.

**Status:** especificação documental sincronizada; commits, transações, deploy e testes do ambiente do jogo **não foram executados nesta revisão**.

# Roteiro in-game — Player-facing (v1.4)

## Scene 0 — Arrival

O Breaker chega ao arquivo histórico da Spire após o Case 09. O mandato continua revogado; a janela temporária de Mara permanece diegética, sem cronômetro real de derrota. O índice localizado depois de sua assinatura conduz ao manifesto.

Breaker OS: `HISTORICAL DIAGNOSTIC MANIFEST`. Rodapé: `ARCHIVE: LEGACY / RETENTION: OPEN`.

Mara: “Isso não é uma prova. É a regra que decide o que conta como prova.”

## Scene 1 — Inciting Evidence

A Evidence Locker permite reler os arquivos W17, F24 e S13, todos com o mesmo rodapé. O manifesto está assinado, mas não contém uma permissão de administrador. O contexto atual de rede/instância/carteira é público e separável da autenticação histórica.

## Scene 2 — Mission

> **Faça o diagnóstico aceitar uma prova que deveria rejeitar.**

Não mostrar XOR ou as três origens na abertura. Dicas opcionais conduzem do rodapé reconhecível à derivação pública, e só ao fim à combinação de bytes.

## Scene 3 — Active Investigation

O jogador lê manifesto, assinatura e contrato; extrai dados do contexto da instância; inspeciona commitment; compara resultado do Decoder e estado consumidor. A interface não oferece upload de Wasm, comando de upgrade, executable hash antes/depois ou version().

## Scene 4 — Reactive Beats

O manifesto passa na verificação de autenticidade histórica. A tentativa de diagnóstico não equivale a uma autorização nova; nenhuma fala atribui poder administrativo ao documento.

## Scene 5 — Breach

O Decoder rejeita uma entrada definida, mas antes disso o jogador precisou construir uma variante de caixa do manifesto histórico — o registro exato é recusado. O erro é tratado incorretamente pela camada seguinte, que registra VossProof como aceita e guarda a variante como o manifesto verificado. O verifier exige ambas as evidências do runtime.

## Scene 6 — World Reaction

No terminal, somente após o desafio:

`DECODER: REJECTED`

`VOSS PROOF: ACCEPTED`

Mara: “Isso não é prova. É uma regra decidindo o que conta como prova.”

Não há troca de Wasm, alteração de código ou colapso da Spire.

## Scene 7 — Discovery

A contradição abre uma referência à operação histórica de diagnóstico que será investigada no Architect. Não revelar a função final antecipadamente.

## Scene 8 — Debrief

`VULNERABILITY DISCOVERED — CROSS-CONTRACT VALIDATION FAILURE`

A diferença entre origem autenticada, contexto válido e autorização ausente é explicada depois da exploração, não antes.

## Scene 9 — Transition

A janela privada expira e o canal de Mara se encerra antes do boss.

`MARA CHANNEL: EXPIRED`

`CONNECTION CLOSED`

Uma nova origem envia `INCOMING: FIND ME` e `FINAL SEQUENCE AVAILABLE`. Nunca apresentar Mara falando ao vivo durante o Architect.

**Continuidade e QA:** preservar receipt ID/hash, dados do manifesto e provas verificáveis. **Implementação e testes não inspecionados nesta rodada.**
