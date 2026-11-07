---
notion_id: 4009c563-0425-8135-9693-d42f09d41062
source: https://app.notion.com/p/4009c563042581359693d42f09d41062?pvs=204
title: "🕵️ Season 01 — The First Layer"
exported_at: 2026-11-07
---

**COMECE AQUI — SEASON 1 / FONTE ÚNICA.** O roteiro definitivo é [BREAKER — Season 1 | FINAL NARRATIVE v1.4 — NARRATIVE LOCK](narrative/breaker-season-1-final-narrative-v1-4-narrative-lock.md) (v1.4, editorialmente LOCKED). Nenhuma página antiga altera a história. **Roteiro fechado ≠ jogo aprovado:** contratos, provas de Voss, interface e playtest ainda precisam de verificação. Os decks e materiais de slides gerados anteriormente foram retirados da Library.

**LANÇAMENTO / 30 DIAS:** domínio escolhido [**playbreaker.xyz**](http://playbreaker.xyz); release-alvo condicional em 04/12/2026. Execução, critérios Go/No-Go e aquisição em [18 — Plano de Lançamento | 30 dias — Season 1](production/18-plano-de-lancamento-30-dias-season-1.md). Calendário X e pacote do perfil em [80 — Comunicação X | 45 posts — 13 semanas (Season 1)](community/80-comunicacao-x-45-posts-13-semanas-season-1.md). Nenhuma data é anúncio público sem aprovação do gate.

## Navegação essencial — onde procurar cada coisa

| Necessidade | Página que prevalece |
| --- | --- |
| **História, personagens e final da S1** | [BREAKER — Season 1 \| FINAL NARRATIVE v1.4 — NARRATIVE LOCK](narrative/breaker-season-1-final-narrative-v1-4-narrative-lock.md) |
| **Fichas por Case, condição de vitória e conceitos de segurança** | [03 — Cases & Bosses](cases/03-cases-bosses.md) (referência técnica; conferir contra v1.4) |
| **Estado técnico vigente de Rewrite/Architect** | [VOSS PROTOCOL — Níveis 11/12 | Especificação vigente](cases/voss-protocol-niveis-11-12-especificacao-vigente.md) e código real quando acessível |
| **Pendências, QA e prioridades de implementação** | [15 — Plano de Melhorias e QA — Season 1](production/15-plano-de-melhorias-e-qa-season-1.md) |
| **P0 — Prova de Voss / verificação do Vault** | [P0 — Prova de autoria de Voss | Dossiê auditável do Vault](production/p0-prova-de-autoria-de-voss-dossie-auditavel-do-vault.md) — gates G0–G6 e 15 testes negativos, pendente de código/fixture |
| **Arte aprovada / identidade visual** | [09 — Art Bible CANÔNICO | Identidade Visual Aprovada — Baseline Site S1](../../../series-bible/09-art-bible-canonico-identidade-visual-aprovada-baseline-site-s1.md) |
| **Livro derivado da Season 1** | [02 — Book I \| The First Layer — Continuidade revisada v1.4](narrative/02-book-i-the-first-layer-continuidade-revisada-v1-4.md) (não canônico para gameplay) |
| **Pesquisas, versões anteriores e propostas** | [90 — Arquivo Editorial e Estudos \| Season 1](archive/90-arquivo-editorial-e-estudos-season-1.md) (arquivo) |
| **Comunicação e publicações** | [80 — Comunicação X \| 45 posts — 13 semanas (Season 1)](community/80-comunicacao-x-45-posts-13-semanas-season-1.md); publicar somente após confirmação do jogo |

**Estados:** história ✅ fechada • organização ✅ revisada • implementação ❔ sem comprovação • QA e playtest ⏳ pendentes. **Não existe deck de slides ativo no escopo desta revisão.**

**Season 1 — The First Layer** é uma campanha investigativa. O jogador começa tentando explicar um roubo impossível em Meridian, passa a seguir os rastros de Aren Voss e termina descobrindo que as falhas não foram fabricadas para ele: Meridian já estava quebrada, e o Architect conectou essas fragilidades para encontrar Breakers capazes de enxergar além da camada oficial.

# Arte aprovada do site — base inegociável de continuidade

As 14 imagens atuais (`homepage.webp` + `00.webp` a `12(1).webp`) constituem a referência visual primária de Meridian. **Todos os 14 banners usam 8:3** (home 2048×768; levels 1600×600). Gramática: skyline vertical monumental, cenário industrial funcional, Breaker de costas/rosto oculto e cabelo preto curto, sobretudo escuro, pretos e azul-grafite com âmbar institucional, vermelho de alerta localizado, emblema geométrico de Meridian e infraestrutura programável física. Preservar os originais enquanto a eventual revisão de rostos em retratos/arquivos é tratada como backlog, não edição automática. Inventário individual, cores aproximadas, fluxo de geração e QA estão no [09 — Art Bible CANÔNICO | Identidade Visual Aprovada — Baseline Site S1](../../../series-bible/09-art-bible-canonico-identidade-visual-aprovada-baseline-site-s1.md).

# Objetivo emocional

No começo:

> **“Estou investigando um crime.”**

Depois:

> **“Estou seguindo alguém que chegou aqui antes de mim.”**

No ponto de virada:

> **“Eu não estou apenas seguindo Voss. Alguém também está me observando.”**

No final:

> **“Meridian sempre esteve quebrada. A pergunta é o que alguém pretende fazer com pessoas capazes de enxergar isso.”**

# Ordem da campanha

1. **Prologue — The Impossible Theft**
2. **Level 1 — No Forced Entry**
3. **Level 2 — The Dead Man's Wallet**
4. **Level 3 — Warehouse 17**
5. **Level 4 — The Forgotten Floor**
6. **MID BOSS — The Custodian**
7. **Level 5 — The Missing Investigator**
8. **Level 6 — The Impossible Account**
9. **Level 7 — Sector 13**
10. **Level 8 — The Oracle**
11. **Level 9 — Steal the Key**
12. **Level 10 — Rewrite**
13. **FINAL BOSS — The Architect**

# Progressão do mistério

| Trecho | O que o jogador acredita | O que está por trás |
| Levels 1–2 | São falhas isoladas. | O caminho começa a convergir. |
| Levels 3–4 | Existe uma rede criminosa. | Há sistemas esquecidos sob Meridian. |
| Custodian | Descobri uma instalação secreta. | A passagem parece esperar um operador. |
| Levels 5–7 | Voss investigou isso antes. | Voss não foi o primeiro Breaker observado, e o jogador está entrando no mesmo registro. |
| Levels 8–10 | Estou chegando ao responsável. | O Architect não criou as falhas; ele reconheceu que elas podiam formar uma rota. |
| Architect | Vou encontrar a origem. | Chegar até ele prova que o jogador consegue enxergar, combinar e reescrever sistemas quebrados. |

# Cadeia causal da investigação

**Abertura do caso:** o Access Gate com autorização insuficiente expõe a rota de serviço que o Recovery Controller confiava. A movimentação principal do Vault segue apenas para o Meridian Recovery Escrow institucional, sem beneficiário controlado por Voss. A identidade do morto é um **operator record** em telemetria legada, não a carteira que recebe os fundos. Apresentar o cruzamento narrativo completo (destino, política de saque, autoria e motivo) no final, **sem impedir** que jogadores peritos descubram antes o destino público no ledger. O suspense não depende de esconder informação publicamente verificável. O Case 1 deve ser demonstrável independentemente de transferir ativos reais.

O jogador precisa reconstruir essa cadeia por eventos, contratos e registros que Mara traz da Authority. A missão não consiste apenas em seguir uma pista arbitrária.

Os levels não devem parecer dez casos independentes. Cada solução entrega a evidência que causa o próximo movimento.

**Vault** → uma identidade impossível aparece na trilha.
**Dead Man's Wallet** → a identidade aponta para Warehouse 17.
**Warehouse 17** → Ghost Key.
**Ghost Key** → Forgotten Floor.
**Forgotten Floor** → Custodian e First Layer.
**Custodian** → terminal/rastros de Aren Voss.
**Voss** → uma conta impossível revela uma rota de infraestrutura até Sector 13.
**Sector 13** → Breaker Registry, outros candidatos e Oracle.
**Oracle** → Architect / Spire.
**Spire** → autoridade capaz de alcançar Rewrite.
**Rewrite** → Architect.

A sensação desejada é **seguir uma pista**, não selecionar o próximo tutorial.

# Recontextualização do roubo

A verdade completa só deve ser revelada perto do final: os 2.4 milhões do Vault não foram movidos por Voss para enriquecimento.

Depois de já ter percorrido a Sequence e recusado o Architect anos antes, Voss concluiu que Meridian jamais investigaria seriamente suas próprias fragilidades sem um incidente impossível de ignorar.

Ele então usa uma falha do Vault para mover os fundos para o **Meridian Recovery Escrow**, um contrato de quarentena institucional sem beneficiário externo e sem capacidade de Voss gastar os ativos.

O saldo do Vault vai a zero, mas o dinheiro não vira propriedade de Voss.

A anomalia é deliberada, controlada e pública o suficiente para obrigar a Meridian Authority a abrir uma investigação.

O roubo é, na verdade, sua primeira mensagem.

Isso faz a pergunta inicial mudar retrospectivamente de:

> **Quem roubou o Vault?**

para:

> **O que Voss precisava que alguém percebesse?**

# Timeline canônica — Aren Voss

1. **Anos antes do incidente:** falhas técnicas são introduzidas nos sistemas de Meridian, antes de serem catalogadas pela Sequence.
2. **Antes do incidente:** Voss atravessa a Sequence, alcança o Architect e fica `REFUSED`. Os motivos permanecem ocultos.
3. **Também antes do incidente:** Voss protocola três alertas que não recebem resposta eficaz. A ordem desses avisos em relação à recusa não está estabelecida sem timestamps verificáveis.
4. **Arquivos históricos:** permanecem gravações, documentos com rodapé recorrente e registro institucional da conta operacional de Voss, autenticado e temporalmente válido.
5. **Incidente do Vault:** uma operação autenticada pela conta atribuída a Voss aciona o GateOpen vulnerável; RecoveryController usa esse estado para enviar 2,4M do Vault ao Meridian Recovery Escrow institucional. Voss não possui autoridade pessoal de saque.
6. **Investigação:** os eventos do ledger são públicos desde o início; a autoria é comprovada no final por comparação de assinatura, identidade histórica e nexo causal, não por confissão ou alertas isolados.
7. **Desaparecimento de Voss:** suas circunstâncias e a razão da recusa permanecem sem explicação. Não inferir datas exatas ausentes de fixture.

# Quem fez o quê

- **Meridian:** acumulou as vulnerabilidades sem intenção ao construir sistemas novos sobre infraestrutura antiga.
- **The Architect:** catalogou e conectou parte dessas falhas em uma Sequence de seleção; mantém o Breaker Registry e o acesso à Layer II.
- **Aren Voss:** percorreu a Sequence, recusou o final e deixou pistas para que outro Breaker chegasse ao mesmo lugar.
- **Mara Vale:** começa como investigadora experiente que exige legitimidade e cadeia de custódia; após revogação, decide preservar uma prova verificável assumindo conscientemente a responsabilidade e o custo institucional.

# Progressão moral — resumo fiel à v1.4

**História linear:** Breaker resolve vulnerabilidades tecnicamente, mas não escolhe personalidade, alianças, respostas ao Architect ou final. Ações canônicas: libera o controller de Elias no 02; preserva Ghost Key com contestação civil no 03; interrompe pressão adicional sobre o Archive no 07; continua sem mandato no 09; testemunha Mara assinar o recibo; no 10 explora a aceitação indevida de VossProof pelo sistema; no Architect desvia operação de diagnóstico para abrir uma sessão forense.

**Transformação:** auditor autorizado → investigador → operador sem mandato → Breaker qualificado provisoriamente. A questão deixa de ser “consigo executar?” e passa a ser “tenho o direito?”. O Profile apresenta os atos observados sem pontuação moral nem resposta para “Por que você continuou?”.

**Mara:** valoriza custódia desde o começo; no Case 09 assume risco consciente ao assinar o recibo; o canal expira antes do confronto. Sua suspensão posterior cita o mesmo ID/hash. O relógio de uma hora é diegético, não condição real de derrota.

**Importante:** Case 10 e Architect, conforme o [BREAKER — Season 1 | FINAL NARRATIVE v1.4 — NARRATIVE LOCK](narrative/breaker-season-1-final-narrative-v1-4-narrative-lock.md), NÃO substituem o Wasm/Executable do ArchitectCore nesta versão. A falha de validação e a abertura da sessão forense sustentam a transformação moral.

# Regra técnica

Cada level deve possuir:

1. **Vulnerabilidade real**
2. **Contrato vulnerável reproduzível**
3. **Condição objetiva de vitória**

A lore é construída em cima dessas três coisas.

# The Custodian

Primeiro boss sem vulnerabilidade indicada.

É um sistema composto de identidade, autoridade e propriedade. A missão é:

> **Faça o Custodian acreditar que você pertence à First Layer.**

Quando vence:

> **BEM-VINDO DE VOLTA, OPERADOR.**

A palavra “back” é a primeira grande quebra de expectativa.

# The Architect

**Condição técnica vigente — VOSS PROTOCOL:** W17, F24 e S13 são referências de arquivos históricos com um rodapé recorrente, e NÃO guardam shares secretas. A prova contextual da instância final é derivada de dados públicos vinculados à rede/instância/carteira; o manifesto histórico assinado por Voss comprova proveniência documental, não privilégios. No Case 10, a rejeição do Decoder é registrada indevidamente como VossProof aceita. No Architect, uma operação DiagnoseCore já autorizada é desviada após o timelock para OpenForensicSession(player), verificada independentemente. Não se substitui Wasm/Core. O estudo histórico de Cipher Gate continua **NÃO CANÔNICO**. A revisão de 2026-11-02 do Voss Protocol descreve a implementação na testnet, mas o código/deploy ainda não foi inspecionado nesta auditoria: [VOSS PROTOCOL — Níveis 11/12 | Especificação vigente](cases/voss-protocol-niveis-11-12-especificacao-vigente.md).

**Arquitetura de conclusão:** a sessão forense é verificada por componente independente do contrato vulnerável, e só depois o resultado `QUALIFIED / PROVISIONAL` é reconhecido. Esta versão NÃO envolve `UpgradeCore`, substituição de `ArchitectCore`, alteração de Wasm ou execução de `reveal()` como atestado da vitória. Qualquer documento que ainda descreva isso é histórico e não deve orientar implementação.

**Regra do clímax:** o Architect não é a única fonte da verdade. O jogador confronta deploys vulneráveis anteriores à Sequence, visita anterior de Voss e a cadeia `AccessGate → RecoveryController` separada do fluxo `Vault → Meridian Recovery Escrow`. A autoria de Voss exige transação histórica autenticada e registro institucional assinado de controle de chave, válidos na época, com elo causal comprovado. Três avisos prévios, sozinhos, não são prova de autoria. A intenção de forçar auditoria não absolve os custos da quarentena em Lower Meridian.

O Profile apresenta apenas ações canônicas do Breaker, sem opções morais. O verificador reconhece `QUALIFIED / PROVISIONAL`, não `ACCEPTED`. A lógica narrativa e a copy atual estão em [BREAKER — Season 1 | FINAL NARRATIVE v1.4 — NARRATIVE LOCK](narrative/breaker-season-1-final-narrative-v1-4-narrative-lock.md); a Matriz de Revelações anterior foi movida para o Arquivo Editorial.

Boss final composto por múltiplos contratos.

Objetivo:

> **Encontre-me.**

O jogador precisa investigar o próprio sistema, abrir camadas e combinar conhecimentos. Depois do breach técnico, a reconstrução forense não exige exploit novo nem ramificação moral. O Breaker enfrenta a revelação sem Mara ao vivo, pois seu canal já se encerrou.

# Final da Season — resumo, não roteiro alternativo

O Breaker abre a sessão forense, reconstrói o incidente e demonstra por evidências que Voss acionou a falha, mas não tinha autorização de saque sobre o Escrow. O Architect apresenta o Profile das ações do jogador e pergunta apenas: **“Por que você continuou?”** Sem resposta selecionável.

O verificador independente reconhece **SEQUENCE 01: COMPLETE / SUBJECT: QUALIFIED / STATUS: PROVISIONAL** e libera acesso à Layer II. Mara recebe `CREDENTIALS: SUSPENDED` pela prova/recibo que assinou no Case 09, com a mesma referência auditável. Sem mensagem ao vivo.

## Pós-créditos

Em Lumen, a voz não identificada diz: **“Então ele encontrou outro.”** Quem era o `ACCEPTED` mascarado e por que Voss recusou permanecem mistérios intencionais para a saga.

**Direção:** a página de início da Season 1 resume, mas não estabelece diálogos, telas ou ações concorrentes com a Final Narrative v1.4.

# Technical Challenge Matrix — resumo de escopo, não evidência de implementação

Referência rápida para localizar a classe de falha de cada desafio. **Não implica que contratos/verifiers já foram testados.** Para comportamento técnico real, cotejar [VOSS PROTOCOL — Níveis 11/12 | Especificação vigente](cases/voss-protocol-niveis-11-12-especificacao-vigente.md), fichas em Cases & Bosses e o plano de QA. Em conflito, aplicar a v1.4 e a implementação verificada, jamais uma mecânica antiga apenas porque está escrita aqui.

| Etapa | Conceito de segurança | Evidência narrativa |
| --- | --- | --- |
| 01 — No Forced Entry | Falta de autorização do owner no AccessGate | Abertura aceita sem permissão do titular |
| 02 — Dead Man's Wallet | Reinitialization / controlador legada | Identidade de Elias e cleanup |
| 03 — Warehouse 17 | Wrong auth subject / custódia | Ghost Key e documento civil |
| 04 — Forgotten Floor | TTL Persistent / restauração de estado arquivado | Andar 24 reaparece no índice |
| BOSS I — Custodian | Composição de confiança entre dependências | `WELCOME BACK` e log de monitoramento |
| 05 — Missing Investigator | Recuperação de arquivo / falha em dependência do Decoder (ver ficha de contrato) | Alertas e identidade operacional histórica de Voss |
| 06 — Impossible Account | Cast i128 negativo→u128 antes da validação | Saldo impossível e provenance energética |
| 07 — Sector 13 | Saturação do Archive / fallback de indexador | Registry externo e `PLAYER ACTIVE` |
| 08 — The Oracle | RNG determinístico previsível | Três previsões pré-registradas |
| 09 — Steal the Key | Timelock/intent não vinculado ao payload completo | Hatch não aberto e recibo de Mara |
| 10 — Rewrite | Decoder REJECTED → VossProof indevidamente ACCEPTED | Regra de validação falsamente atestada |
| FINAL BOSS — Architect | Prova contextual pública, timelock `DiagnoseCore → OpenForensicSession` e atestação independente | Sessão forense, Escrow, autoria de Voss, `QUALIFIED / PROVISIONAL` |

**Produção:** os desafios têm gates independentes de teste. Scripts, fixtures, assinaturas, endereços e timings não são considerados concluídos apenas porque a matriz está editorialmente definida.

## Nota técnica importante

A ideia inicial de usar **reentrancy clássica** foi retirada. Soroban proíbe contract re-entry por design; por isso a fase de cross-contract foi redesenhada para ensinar uma superfície compatível com a plataforma: **tratamento incorreto de falhas em chamadas entre contratos**.

## Regra para implementação dos challenges

Cada fase deve ter testes automatizados cobrindo pelo menos:

1. estado inicial;
2. exploit que vence a fase;
3. tentativa normal que não satisfaz a vitória;
4. versão corrigida que bloqueia o exploit;
5. verifier independente da UI;
6. reset/redeploy determinístico para novos jogadores.

Os snippets desta documentação são **modelos pedagógicos**, não devem ser copiados para produção sem testes e adaptação à versão do Soroban SDK usada pelo projeto.

[02 — Book I \| The First Layer — Continuidade revisada v1.4](narrative/02-book-i-the-first-layer-continuidade-revisada-v1-4.md)

[03 — Cases & Bosses](cases/03-cases-bosses.md)

# Network Wire — Sera Quill

Sera Quill existe na Season 1 apenas como uma assinatura jornalística.

O jogador não encontra Sera pessoalmente.

Usar uma única aparição discreta, de preferência após o incidente do Vault:

> **2,4 MILHÕES MOVIMENTADOS — NENHUMA INVASÃO DETECTADA** — *Sera Quill, Network Wire*

# Regra

Não criar diálogo, subplot ou segunda aparição de Sera em Meridian.

A intenção é apenas plantar o nome para reconhecimento futuro.

<database url="https://app.notion.com/p/4bc75fffc553440f9ffd0497bf69ab12" data-source-url="collection://c177b69b-cf17-4df6-91e7-fa33fc62e9a2" inline="false">
X — Season 1 \| Fila de Publicações
</database>

[80 — Comunicação X \| 45 posts — 13 semanas (Season 1)](community/80-comunicacao-x-45-posts-13-semanas-season-1.md)

[15 — Plano de Melhorias e QA — Season 1](production/15-plano-de-melhorias-e-qa-season-1.md)

[BREAKER — Season 1 \| FINAL NARRATIVE v1.4 — NARRATIVE LOCK](narrative/breaker-season-1-final-narrative-v1-4-narrative-lock.md)

[90 — Arquivo Editorial e Estudos \| Season 1](archive/90-arquivo-editorial-e-estudos-season-1.md)

<database url="https://app.notion.com/p/2b1d33190ac446bfaea34e7a4db74d92" data-source-url="collection://68d445ad-e91e-44c9-a323-544887af1bad" inline="false">
17 — Easter Eggs \| Season 1 — Mapa, Arte & Stellar DNA
</database>

## 17 — Easter Eggs \| Curadoria de mapas, imagens e terminais

O [17 — Easter Eggs | Season 1 — Mapa, Arte & Stellar DNA](../../../../databases/season-01-reference-catalog.txt) funciona como **novo parâmetro editorial obrigatório ao propor enriquecimento visual**. A v1.4 da narrativa e a Art Bible continuam prevalecendo. O catálogo central contém 18 ideias pesquisadas, com Status, Prioridade, Case/Área, Suporte (Imagem/Mapa/Terminal/Documento/Cenário/Interface), Tipo de referência, Fonte oficial, Asset, Região de composição, Risco de spoiler e cuidados.

**Workflow:** Ideia → Pesquisa → Em revisão → Aprovado → Implementado (ou Rejeitado). Nenhuma entrada vira cânone por ter sido cadastrada. Antes de aprovar, conferir no site o asset real, o recorte mobile e a existência de pistas obrigatórias; antes de marcar Implementado, verificar visualmente a build. O catálogo não muda contratos, flags, condições de vitória, arcos de personagens nem o final.

P0 para testar com a arte existente: [JUMP CANNON / OLD FOUNDRY](references/jump-cannon-old-foundry.md), [ÁBACO DA VELHA ENGENHARIA](references/abaco-da-velha-engenharia.md), [GALEXIE / MIRROR 13](references/galexie-mirror-13.md), [XDR LAB / INSPECTOR](references/xdr-lab-inspector.md) e [O FOGUETE ESQUECIDO](references/o-foguete-esquecido.md).

[18 — Plano de Lançamento \| 30 dias — Season 1](production/18-plano-de-lancamento-30-dias-season-1.md)

[Curadoria Stellar — lote 1 Season 1](references/curadoria-stellar-lote-1-season-1.md)
