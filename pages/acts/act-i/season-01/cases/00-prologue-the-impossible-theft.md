---
notion_id: 4009c563-0425-81ff-8ceb-d44408321b54
source: https://app.notion.com/p/4009c563042581ff8cebd44408321b54?pvs=204
title: "🕯️ 00 — Prologue: The Impossible Theft"
exported_at: 2026-11-07
---

**FICHA DE REFERÊNCIA DO PRÓLOGO — SINCRONIZADA COM v1.4.** A notícia de Sera Quill, a transação histórica pública, a distinção entre assinatura e autorização e a personalidade de Mara seguem a versão canônica. Os cartões finais e seus textos completos permanecem somente na Final Narrative v1.4. Fonte única de narrativa, cenas e slides: [BREAKER — Season 1 | FINAL NARRATIVE v1.4 — NARRATIVE LOCK](../narrative/breaker-season-1-final-narrative-v1-4-narrative-lock.md). Não tratar esta ficha como prova de teste ou deploy.

**Visual reference:** [00 — Prologue — abrir arte no Google Drive](https://drive.google.com/file/d/1ZwrkeqvbURGO3ZpF6yYpp_mjARujb48j/view)

**Função narrativa:** abrir a Season com um crime impossível e estabelecer Meridian como uma cidade que confia demais em seus contratos.

# Situação

Um Vault altamente protegido de Meridian é esvaziado durante a madrugada.
Nenhuma chave privada foi roubada. Nenhuma assinatura administrativa foi registrada. Nenhuma câmera mostra invasão física.

**Vault balance: 2,400,000 → 0**

A Meridian Authority não consegue explicar como.

# Objetivo emocional

> **Como alguém roubou um sistema sem quebrar nenhuma das suas proteções aparentes?**

# Conexão

O jogador percebe que o ponto de entrada não está no Vault em si, mas no sistema que controla acesso ao local. A investigação leva para **No Forced Entry**.

# Construction Brief — Prologue

## Papel do prólogo

O prólogo **não é um challenge técnico**. Ele deve apresentar o caso, a cidade e as regras do mundo sem ensinar explicitamente nenhuma vulnerabilidade.

O jogador acabou de registrar sua Path quando recebe seu primeiro trabalho formal como **Independent Contract Auditor**. A Meridian Authority solicita uma revisão externa porque sua investigação interna não consegue explicar como um Vault supostamente impossível de violar perdeu todo o saldo sem registrar comprometimento.

Quando chega, a investigação oficial já terminou. O acesso concedido ao jogador é limitado, auditado e temporário.

### Evidências visíveis

- porta física intacta;
- nenhum acesso administrativo registrado;
- nenhuma chave reportada como comprometida;
- contrato do Vault ainda responde normalmente;
- saldo zerado;
- a última operação foi aceita como válida pelo sistema.

## Cena de abertura sugerida

A câmera/interface mostra Meridian funcionando normalmente. Trens, mercados, credenciais e edifícios respondem automaticamente a contratos. A intenção é mostrar confiança absoluta na infraestrutura antes de questioná-la.

A investigadora responsável pelo caso é **Mara Vale**, da Meridian Authority.

Ela representa o compromisso institucional com a cadeia de custódia, mas já sabe separar execução técnica de legitimidade. Mara diz:

> **O sistema aceitou a transação. Ainda precisamos provar quem tinha direito.**

O Breaker observa o registro e responde:

> **Aceito pelo sistema não significa explicado.**

A tensão da Season não depende de Mara ser ingênua; nasce da dificuldade de preservar a investigação quando o procedimento deixa de protegê-la.

## O que o jogador recebe

- Contract ID do Access Gate;
- snapshot do estado do Vault;
- referência pública à transação histórica e ao evento GateOpen, com origem verificável;
- identidade declarada do proprietário, distinta do signatário autenticado;
- nenhuma explicação sobre `require_auth`.

## Verdade oculta do prólogo — somente para roteiro

**Dependência técnica canônica:** `AccessGate` publica um estado de abertura da rota de serviço sem autenticação efetiva de owner. `RecoveryController` trata esse estado como uma condição suficiente para permitir `recover_to_escrow()`, que envia fundos **apenas** ao Meridian Recovery Escrow pré-definido e não a destinatários escolhidos pelo caller. Voss abusa desse vínculo de confiança, sem assinatura administrativa de movimentação e sem obter spend authority sobre os recursos. O Case 01 reproduz a falha de autenticação do Gate; não executa novamente a recuperação financeira. O Architect reúne a prova completa ao final, mas eventos de ledger são públicos e devem poder ser consultados antecipadamente por jogadores experientes. Um jogador pode encontrar o endereço Escrow antes; a reviravolta preservada é a **atribuição comprovada a Voss, a política de gasto e a razão do incidente**, não um endpoint supostamente secreto.

O jogador não deve saber disso aqui.

O saldo de **2,400,000** não foi movido por Voss para enriquecimento. Depois de já ter atravessado a Sequence e recusado o Architect anos antes, Voss usa uma falha do Vault para transferir os fundos ao **Meridian Recovery Escrow** — um contrato institucional de quarentena sem beneficiário externo e sem capacidade de Voss gastar os ativos.

A operação foi deliberadamente construída para produzir uma anomalia impossível de ignorar e atrair alguém disposto a questionar a interpretação oficial do contrato.

O “roubo” é a primeira mensagem de Voss.

Quando essa verdade for revelada perto do final da Season, a cena inicial precisa ganhar outro significado:

> **Ele nunca pegou o dinheiro. Ele fez Meridian olhar para isso.**

A recontextualização desejada é:

**Quem roubou o Vault?** → **O que Voss precisava que alguém percebesse?**

## Gancho para Level 1

A UI de investigação destaca uma única pergunta:

> **Se nenhuma chave foi roubada, como entraram?**

Então desbloqueia:

**CASE 01 — NO FORCED ENTRY**

## Regra para implementação

O prólogo deve durar pouco e evitar tutorial excessivo. A aprendizagem técnica começa no Level 1. Seu trabalho é fazer o usuário querer abrir o contrato.

## Referência conceitual para a transição

- [Stellar Docs — Authorization](https://developers.stellar.org/docs/learn/fundamentals/contract-development/authorization)
- [Stellar Docs — Auth example](https://developers.stellar.org/docs/build/smart-contracts/example-contracts/auth)

# Roteiro in-game — Player-facing

Esta seção descreve **o que o jogador efetivamente vê, ouve e descobre dentro do jogo**. Não deve revelar vulnerabilidade, exploit esperado ou solução técnica antes da conclusão.

## Scene 0 — Meridian

A Season abre com Meridian funcionando normalmente: transporte, identidade, propriedade e mercados respondendo automaticamente a contratos.

Tela:

> **Tudo é governado por um Contrato.**

A câmera/interface entra no Meridian Vault.

## Scene 1 — Crime Scene

A imagem do Vault aparece.

Overlay:

**VAULT BALANCE**
**2,400,000 → 0**

Evidence disponível:

- Door: intact
- Admin access: none
- Key compromise: none
- Transaction: accepted

Uma única notícia ambiental aparece no painel secundário do Vault, sem áudio nem diálogo adicional:

> **2,4 MILHÕES MOVIMENTADOS — NENHUMA INVASÃO DETECTADA** — *Sera Quill, Network Wire*

O usuário pode fechá-la; seu conteúdo não contém hints e a assinatura de Sera não deve reaparecer durante a Season 1.

Mara Vale:

> **O sistema aceitou a transação. Ainda precisamos provar quem tinha direito.**

Breaker:

> **Aceito pelo sistema não significa explicado.**

## Scene 2 — Investigation Handoff

Mara registra o jogador como **Independent Contract Auditor** e libera acesso temporário ao Access Gate Contract.

UI:

**AUDITOR STATUS: ACTIVE**
**ACCESS SCOPE: LIMITED**
**CASE: MERIDIAN VAULT**

O Breaker recebe:

- Contract ID;
- owner declarado;
- snapshot mínimo;
- transaction history;
- dois identificadores de evento da rota de serviço, sem revelar destino financeiro ou autoria.

A interface não exibe a origem da custódia final. É uma investigação em andamento, não um tutorial que entrega a solução.

Mission:

> **Descubra como entraram sem possuir a chave.**

CTA:

**OPEN CASE 01**

## O que não mostrar

Antes de abrir Case 01, não mencionar:

- `require_auth()`;
- Missing Authorization;
- vulnerabilidade;
- solução;
- qualquer indicação de que o parâmetro `Address` é o problema.

## Transição

O player não muda de lugar.

O mesmo Vault continua em cena e o **CASE 01 — NO FORCED ENTRY** abre como continuação direta da investigação.
