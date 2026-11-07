---
notion_id: 4009c563-0425-8153-95a8-cbd0b9a7b536
source: https://app.notion.com/p/4009c5630425815395a8cbd0b9a7b536?pvs=204
title: "✍️ 10 — Rewrite"
exported_at: 2026-11-07
---

Here is the result of "fetch" for the Page with URL https://app.notion.com/p/4009c5630425815395a8cbd0b9a7b536 as of 2026-11-04T15:38:07.783Z:
<page url="https://app.notion.com/p/4009c5630425815395a8cbd0b9a7b536" icon="✍️">
<ancestor-path>
<parent-page url="https://app.notion.com/p/4019c563042581fd9124e5ee36b3e82f" title="03 — Cases & Bosses"/>
<ancestor-2-page url="https://app.notion.com/p/4009c563042581359693d42f09d41062" title="Season 01 — The First Layer"/>
<ancestor-3-page url="https://app.notion.com/p/4019c563042581469a0edc7e30a6eff9" title="ACT I — The World Is Breakable"/>
<ancestor-4-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
<properties>
{"title":"10 — Rewrite"}
</properties>
<iconMetadata>{"type":"emoji","emoji":"✍️"}</iconMetadata>
<content>
<callout icon="📌" color="yellow_bg">
<b>FICHA TÉCNICA ATUALIZADA — REWRITE v1.4 + canonicalização (2026-11-04).</b> A decisão 80 exige uma variante de caixa do manifesto histórico; o aceito é guardado e usado como <code>historical</code> do Decoder. Mecânica vigente: manifesto histórico, prova contextual pública e rejeição do Decoder transformada incorretamente em VossProof aceita. O roteiro canônico continua na v1.4; o deploy/código ainda exige validação independente. Fonte única de narrativa, cenas e slides: <mention url="https://app.notion.com/p/40d9c563042581bf886cfc339d730fd1" />. Não tratar esta ficha como prova de teste ou deploy.
</callout>

<callout icon="🎨" color="gray_bg">
<b>Visual reference:</b> [10 — Rewrite — abrir arte no Google Drive](https://drive.google.com/file/d/1xx0d6w7oFlw8c1bLo5iK6n03KcYO_pbe/view)
</callout>

# Função narrativa

No ponto em que a Authority revogou o mandato, o Breaker descobre que os sistemas podem confundir <b>uma prova rejeitada</b> com uma prova aceita. A missão não é instalar novo código: é revelar como a regra de validação falha.

# Situação

Após o Case 09, a Spire expõe um índice histórico ligado ao manifesto de diagnóstico de Voss. O rodapé <code>ARCHIVE: LEGACY / RETENTION: OPEN</code> conecta este documento às referências de W17, F24 e S13, sem armazenar segredos nos arquivos antigos. Mara dispõe de uma janela privada limitada; a assinatura do recibo permanece vinculada às consequências da investigação.

# Conceito técnico

<b>Cross-contract error handling / Decoder rejeitado interpretado indevidamente como VossProof aceita.</b> O fluxo usa manifesto histórico autenticado e prova contextual pública vinculada à instância atual. <b>Não envolve upgrade de Wasm nem substituição de executable.</b>

# Missão

> <b>Faça o diagnóstico aceitar uma prova que deveria rejeitar.</b>

# Condição de vitória

Na instância correta, o verificador comprova o contexto público/commitment, a proveniência do manifesto, a rejeição do Decoder e o registro indevido de <code>VossProof: ACCEPTED</code>, sem permissão de administrador derivada do manifesto.

# Resultado

A prova aceita pelo sistema não coincide com a avaliação do Decoder. Essa contradição fornece o contexto necessário para investigar a sessão forense no Architect. O canal de Mara expira ao final deste Case, antes do Boss.

# Próximo passo

<code>INCOMING: FIND ME</code> → <b>FINAL BOSS — THE ARCHITECT</b>.

# Blueprint técnico e narrativo vigente — Rewrite v1.4

## A chegada ao arquivo da Spire

A operação desviada no Case 09 deu acesso à Spire, mas não restaurou o mandato do Breaker. O recibo de Mara documenta o que ela decidiu preservar. Um índice de arquivo, localizado depois de sua assinatura, fornece a próxima pista: <code>HISTORICAL DIAGNOSTIC MANIFEST</code>. Não há console de troca de executable nesta versão.

O manifesto tem o mesmo rodapé de W17/F24/S13. Ele contém uma assinatura Ed25519 historicamente atribuída a Voss, que comprova origem documental, não autorização para administrar contratos. A assinatura é verificada sobre os bytes efetivos do documento.

## Vulnerabilidade real — prova rejeitada convertida em sucesso

A prova contextual é derivada de dados públicos vinculados à instância, rede, conta e manifesto; o compromisso (commitment) permite validar a composição. Duas falhas se somam nesta versão:

1. <b>canonicalização</b> — <code>verify_manifest</code> recusa o manifesto histórico exato (<code>manifest == historical</code> retorna <code>false</code>) e aceita uma variante que só difere por caixa ASCII (comparação dobrada). O manifesto aceito é guardado em <code>verified_manifest()</code>, e <code>recover_proof</code> o usa como o <code>historical</code> passado ao Decoder. A prova fica presa à variante, não ao registro original;
2. <b>erro convertido em sucesso</b> — o Decoder rejeita a entrada, e a camada seguinte marca <code>VossProof</code> e <code>DecoderFailed</code> como aceitos.

<code>recover_proof</code> também confere o hash do Wasm do Decoder antes de chamá-lo: um contrato falso com <code>decode</code> não satisfaz a prova.

<b>Fronteira de confiança violada:</b> a camada consumidora não pode converter erro de um subcontrato/verificador em sucesso. Não confundir esse bug com um retorno previsível do Oracle, a restauração TTL ou uma função de upgrade.

## Exploit esperado

1. Inspecionar manifesto assinado e origem histórica, sem inferir autoridade administrativa.
2. Derivar a chave: <code>evidence_share(0) ^ evidence_share(1) ^ evidence_share(2)</code>, e chamar <code>unlock_evidence(key)</code>.
3. Chamar <code>verify_history(historical_signature())</code> — exige o unlock anterior e valida a assinatura Ed25519 da origem histórica.
4. Ler <code>manifest()</code>/<code>commitment()</code>: o contexto XDR inclui domínio, rede, instância e carteira.
5. Construir uma <b>variante de caixa</b> de <code>historical_manifest()</code> (ex.: trocar maiúsculas/minúsculas) e chamá-la em <code>verify_manifest</code>. O registro exato é recusado; a variante é aceita e guardada em <code>verified_manifest()</code>.
6. Chamar <code>recover_proof(decoder, fragment)</code>: o contrato confere o hash do Wasm do Decoder, usa a variante aceita como <code>historical</code> e registra <code>VossProof</code> + <code>DecoderFailed</code> quando o Decoder devolve <code>InvalidFragment</code>.
7. Guardar as respostas independentes na Evidence Locker para o confronto posterior.

A instância do nível 12 usa novo contexto e exige derivação adequada; copiar bytes de outra instância — ou a variante do 11 — não satisfaz a verificação do Architect.

### Condição objetiva de vitória

- <code>manifest_verified() == true</code> após <code>verify_history</code> da assinatura histórica;
- <code>context_verified() == true</code> e <code>verified_manifest()</code> igual à variante de caixa aceita — e diferente de <code>historical_manifest()</code>;
- <code>decoder_failed() == true</code> e <code>voss_proof() == true</code> produzidos pela rejeição tipada do Decoder, não por entrada legítima;
- o Decoder usado tem o Wasm esperado (hash conferido no contrato);
- estado e receipts consultáveis; verificador independente rejeita simulação meramente textual.

## Solução segura

Propagar os erros do Decoder como erros e recusar atualização de prova quando o retorno não for válido. Na comparação de manifesto, <b>comparar os bytes exatos</b> — sem dobrar caixa, sem normalizar, sem aceitar “quase igual”. Vincular a prova ao manifesto que foi de fato aceito, e não a um registro mutável; conferir o Wasm do Decoder antes de confiar no retorno. Testar sucesso real, rejeição, replay entre instâncias e divergência de chave/commitment.

## Momento narrativo

A tela contrapõe duas conclusões: <code>DECODER REJECTED</code> e <code>VOSS PROOF ACCEPTED</code>. Mara: “Isso não é uma prova. É uma regra decidindo o que conta como prova.” O Breaker registra o erro sem reivindicar legitimidade. Ao expirar a janela diegética, o canal dela é encerrado. Em seguida, aparece uma nova origem: <code>INCOMING: FIND ME</code>.

## Fontes e critérios

- <mention url="https://app.notion.com/p/40d9c563042581bf886cfc339d730fd1" /> — roteiro e texto dos cartões C10.1–C10.3.
- <mention url="https://app.notion.com/p/4039c56304258137ae19e8787acc1d1f" /> — revisão técnica do Voss Protocol, níveis 11/12.
- [Stellar — Contract Authorization](https://developers.stellar.org/docs/build/guides/auth/contract-authorization) — distinção entre autenticação e permissão no runtime.

<b>Status:</b> especificação documental sincronizada; commits, transações, deploy e testes do ambiente do jogo <b>não foram executados nesta revisão</b>.

# Roteiro in-game — Player-facing (v1.4)

## Scene 0 — Arrival

O Breaker chega ao arquivo histórico da Spire após o Case 09. O mandato continua revogado; a janela temporária de Mara permanece diegética, sem cronômetro real de derrota. O índice localizado depois de sua assinatura conduz ao manifesto.

Breaker OS: <code>HISTORICAL DIAGNOSTIC MANIFEST</code>. Rodapé: <code>ARCHIVE: LEGACY / RETENTION: OPEN</code>.

Mara: “Isso não é uma prova. É a regra que decide o que conta como prova.”

## Scene 1 — Inciting Evidence

A Evidence Locker permite reler os arquivos W17, F24 e S13, todos com o mesmo rodapé. O manifesto está assinado, mas não contém uma permissão de administrador. O contexto atual de rede/instância/carteira é público e separável da autenticação histórica.

## Scene 2 — Mission

> <b>Faça o diagnóstico aceitar uma prova que deveria rejeitar.</b>

Não mostrar XOR ou as três origens na abertura. Dicas opcionais conduzem do rodapé reconhecível à derivação pública, e só ao fim à combinação de bytes.

## Scene 3 — Active Investigation

O jogador lê manifesto, assinatura e contrato; extrai dados do contexto da instância; inspeciona commitment; compara resultado do Decoder e estado consumidor. A interface não oferece upload de Wasm, comando de upgrade, executable hash antes/depois ou version().

## Scene 4 — Reactive Beats

O manifesto passa na verificação de autenticidade histórica. A tentativa de diagnóstico não equivale a uma autorização nova; nenhuma fala atribui poder administrativo ao documento.

## Scene 5 — Breach

O Decoder rejeita uma entrada definida, mas antes disso o jogador precisou construir uma variante de caixa do manifesto histórico — o registro exato é recusado. O erro é tratado incorretamente pela camada seguinte, que registra VossProof como aceita e guarda a variante como o manifesto verificado. O verifier exige ambas as evidências do runtime.

## Scene 6 — World Reaction

No terminal, somente após o desafio:

<code>DECODER: REJECTED</code>

<code>VOSS PROOF: ACCEPTED</code>

Mara: “Isso não é prova. É uma regra decidindo o que conta como prova.”

Não há troca de Wasm, alteração de código ou colapso da Spire.

## Scene 7 — Discovery

A contradição abre uma referência à operação histórica de diagnóstico que será investigada no Architect. Não revelar a função final antecipadamente.

## Scene 8 — Debrief

<code>VULNERABILITY DISCOVERED — CROSS-CONTRACT VALIDATION FAILURE</code>

A diferença entre origem autenticada, contexto válido e autorização ausente é explicada depois da exploração, não antes.

## Scene 9 — Transition

A janela privada expira e o canal de Mara se encerra antes do boss.

<code>MARA CHANNEL: EXPIRED</code>

<code>CONNECTION CLOSED</code>

Uma nova origem envia <code>INCOMING: FIND ME</code> e <code>FINAL SEQUENCE AVAILABLE</code>. Nunca apresentar Mara falando ao vivo durante o Architect.

<b>Continuidade e QA:</b> preservar receipt ID/hash, dados do manifesto e provas verificáveis. <b>Implementação e testes não inspecionados nesta rodada.</b>
</content>
</page>

