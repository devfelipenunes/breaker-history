---
notion_id: 4039c563-0425-8137-ae19-e8787acc1d1f
source: https://app.notion.com/p/4039c56304258137ae19e8787acc1d1f?pvs=204
title: "🔐 VOSS PROTOCOL — Níveis 11/12 | Especificação vigente"
exported_at: 2026-11-07
---

Here is the result of "fetch" for the Page with URL https://app.notion.com/p/4039c56304258137ae19e8787acc1d1f as of 2026-11-03T16:07:32.092Z:
<page url="https://app.notion.com/p/4039c56304258137ae19e8787acc1d1f" icon="🔐">
<ancestor-path>
<parent-page url="https://app.notion.com/p/4009c5630425815581b2df01797d5365" title="FINAL BOSS — The Architect"/>
<ancestor-2-page url="https://app.notion.com/p/4019c563042581fd9124e5ee36b3e82f" title="03 — Cases & Bosses"/>
<ancestor-3-page url="https://app.notion.com/p/4009c563042581359693d42f09d41062" title="Season 01 — The First Layer"/>
<ancestor-4-page url="https://app.notion.com/p/4019c563042581469a0edc7e30a6eff9" title="ACT I — The World Is Breakable"/>
<ancestor-5-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
<properties>
{"title":"VOSS PROTOCOL — Níveis 11/12 \\| Especificação vigente"}
</properties>
<iconMetadata>{"type":"emoji","emoji":"🔐"}</iconMetadata>
<content>
# Estado vigente — revisão editorial de 2026-11-02

<b>Estado documental vigente:</b> a revisão de 2026-11-02 relata níveis 11/12 implementados e deployados na testnet, sem que os fontes e o deploy tenham sido verificados nesta auditoria. Para narrativa e cenas prevalece o roteiro v1.4; para contratos prevalecem o código e seus testes. Todo o material anterior de shares secretas e UpgradeCore foi preservado em <mention url="https://app.notion.com/p/40d9c5630425816c83f7fd200a01fcf8" />, separado desta página.

## Pistas para o jogador

- As imagens mantêm os endereços narrativos Warehouse 17, Floor 24 e Sector 13.
- Os arquivos narrativos dos Cases 03 (Warehouse 17), 04 (Forgotten Floor) e 07 (Sector 13) repetem o rodapé diegético <code>ARCHIVE: LEGACY / RETENTION: OPEN</code>. O manifesto do nível 11 também o traz. Nenhum texto inicial lista as três localizações, conta pistas ou explica XOR.
- O jogador precisa reconhecer a recorrência e voltar aos arquivos dos casos concluídos. O nível 11 abre com um rodapé familiar; as dicas opcionais avançam da observação das imagens e registros à comparação dos campos. Só a última dica revela a combinação byte a byte com XOR.
- O nível 12 reaplica a prova contextual em uma instância nova, sem reapresentar o mapa das pistas.

## O que realmente acontece on-chain

As shares dos casos antigos <b>não</b> contêm os bytes usados na prova. Em cada instância final, <code>contracts/levels/11-rewrite/protocol.rs</code> deriva três valores públicos do manifesto, rede, endereço da instância, carteira e índice:

<code>share_i = SHA256(XDR(("BREAKER/EVIDENCE/v1", context, i)))</code>, para <code>i = 0, 1, 2</code>.

A chave de progressão é a XOR byte a byte dos três resultados. O commitment é calculado sobre o domínio, contexto e chave. Os getters e o fonte são públicos: isso não é sigilo nem prova de conhecimento privado. A assinatura Ed25519 autentica o manifesto histórico fixo de Voss; o contexto da instância é conferido separadamente.

No nível 11, a rejeição específica do Decoder é registrada incorretamente como <code>VossProof</code>. No nível 12, uma operação <code>DiagnoseCore</code> amadurece e pode ser reescrita para <code>OpenForensicSession(player)</code>, após o timelock e uma única execução. Não existe upgrade de WASM nem autorização administrativa concedida pelo manifesto.

## Escopo desta revisão

A revisão de 2026-11-02 declarou mudanças nos textos e na apresentação player-facing, não alteração de contratos ou valores on-chain. O rascunho obsoleto com shares armazenadas nos Cases, EvidenceGate e UpgradeCore foi transferido integralmente para <mention url="https://app.notion.com/p/40d9c5630425816c83f7fd200a01fcf8" />. Ele não descreve a mecânica vigente e não deve ser implementado. A afirmação de deploy em testnet continua sem inspeção independente nesta auditoria.

<callout icon="🔐" color="blue_bg">
<b>ESTADO — REVISÃO TÉCNICA DOCUMENTADA EM 2026-11-02.</b> O documento relata níveis 11 (Rewrite) e 12 (The Architect) implementados e deployados na testnet; commit e transações ainda exigem verificação independente para aprovação de produção. O fluxo atual não contém UpgradeCore: o nível 11 valida o manifesto e explora a rejeição do Decoder; o 12 reescreve uma operação de diagnóstico para abrir uma sessão forense após o timelock. A revisão player-facing abaixo substitui os rótulos SHARE A/B/C, a contagem explícita de referências e a instrução de XOR na abertura. Detalhes do rascunho original estão preservados na página de arquivo histórico, não nesta especificação vigente. As shares atuais são públicas e derivadas do contexto da instância e do índice; não são segredos aleatórios guardados nos casos antigos.
</callout>

# Arquivo histórico — preservado fora da especificação vigente

As versões antigas de Voss Protocol (shares de 32 bytes recolhidas em Warehouse 17, Floor 24 e Sector 13, EvidenceGate com segredo estático e UpgradeCore) foram transferidas, sem perda do texto, para <mention url="https://app.notion.com/p/40d9c5630425816c83f7fd200a01fcf8" />.

<b>Somente a revisão de 2026-11-02 descrita acima é vigente para os níveis 11/12.</b> O roteiro v1.4 permanece a fonte narrativa e o código/deploy ainda exige inspeção independente. Não implementar as propostas arquivadas por engano.
</content>
</page>

