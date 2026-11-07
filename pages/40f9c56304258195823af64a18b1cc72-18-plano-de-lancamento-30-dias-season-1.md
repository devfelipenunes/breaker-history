---
notion_id: 40f9c563-0425-8195-823a-f64a18b1cc72
source: https://app.notion.com/p/40f9c56304258195823af64a18b1cc72?pvs=204
title: "🚀 18 — Plano de Lançamento | 30 dias — Season 1"
exported_at: 2026-11-07
---

Here is the result of "fetch" for the Page with URL https://app.notion.com/p/40f9c56304258195823af64a18b1cc72 as of 2026-11-05T10:54:58.093Z:
<page url="https://app.notion.com/p/40f9c56304258195823af64a18b1cc72" icon="🚀">
<ancestor-path>
<parent-page url="https://app.notion.com/p/4009c563042581359693d42f09d41062" title="Season 01 — The First Layer"/>
<ancestor-2-page url="https://app.notion.com/p/4019c563042581469a0edc7e30a6eff9" title="ACT I — The World Is Breakable"/>
<ancestor-3-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
<properties>
{"title":"18 — Plano de Lançamento \\| 30 dias — Season 1"}
</properties>
<iconMetadata>{"type":"emoji","emoji":"🚀"}</iconMetadata>
<content>
<callout icon="🚀" color="blue_bg">
<b>Plano operacional iniciado em 05/11/2026.</b> Meta proposta: disponibilizar <b>BREAKER — Season 1: The First Layer</b> por volta de <date start="2026-12-04" />. D0 é condicional: a data só vira compromisso público após os gates técnicos, de UX e publicação. Jogo CTF gratuito, narrativo, focado em smart contracts Stellar/Soroban.
</callout>

## Decisões confirmadas

- <b>Domínio escolhido:</b> [playbreaker.xyz](http://playbreaker.xyz). Registro, DNS, HTTPS e site funcional ainda não foram confirmados.
- <b>Fonte narrativa:</b> <mention url="https://app.notion.com/p/40d9c563042581bf886cfc339d730fd1" /> (Season 1 v1.4, editorialmente fechada). Não reabrir a história sem problema concreto descoberto em testes.
- <b>Prioridade do mês:</b> estabilidade + qualidade da experiência + distribuição; não acrescentar features por impulso.
- <b>Comunicação:</b> preparar perfil X e assets agora, mas respeitar campanha editorial D−7 → D+12 semanas. Não anunciar o jogo como disponível antes de validar D0.
- <b>Integrações extras:</b> Stellar Passport, sistema amplo de mapa, novos Easter Eggs e Season 2 ficam fora do caminho crítico de lançamento. Avaliar após estabilizar o núcleo.

## Diagnóstico inicial — documentação, não código auditado

| Área | Situação em 05/11 | Significado |
| --- | --- | --- |
| História / cânone | Editorialmente fechado | 51 unidades narrativas e campanha com prólogo, 10 Cases e 2 Bosses |
| Arte / identidade | Baseline aprovada | 14 banners 8:3; não redesenhar sem necessidade |
| Segurança / deploy | Não verificado neste Notion | Verificar fixture, exploit, secure mirror, verificador independente, reset |
| Voss / Architect | Gate P0 | Prova de autoria e causalidade deve ser auditável |
| UX / onboarding | A verificar | Testar primeiro contato, pistas, responsividade, Evidence Locker e progresso |
| X / Twitter | 45 posts na fila; 21 prontos, zero publicados | 6 pré, 6 lançamento, 33 pós. Pré: 2 prontos; lançamento: 1 pronto |
| Easter Eggs | 18 ideias, nenhuma marcada implementada | Curadoria opcional, sem bloquear D0 |

<b>Regra:</b> "não verificado" ≠ "não implementado". Evidência de testes anteriores relatados pelo criador é valiosa, mas ainda precisa ser vinculada a versão/commit e resultados.

## Calendário de execução — 30 dias

| Período | Tema | Entrega para avançar |
| --- | --- | --- |
| <date start="2026-11-05" end="2026-11-10" /> | Estabilização + operação | Inventário real dos 13 momentos; decidir URL e infraestrutura; registrar evidências de testes; perfil X |
| <date start="2026-11-11" end="2026-11-17" /> | Experiência / onboarding | Primeiros 2 Cases claros; mensagens de erro, dicas, progresso e feedback; testes navegador/mobile |
| <date start="2026-11-18" end="2026-11-24" /> | Playtest completo | Pelo menos 10 playtests externos como meta; capturar problemas, corrigir P0 e P1 relevantes |
| <date start="2026-11-25" end="2026-11-26" /> | Checkpoint Go / No-Go | Verificar gates; confirmar ou adiar D0 sem promessas públicas |
| <date start="2026-11-27" end="2026-12-03" /> | Pré-lançamento, se aprovado | Publicar 6 posts D−7 a D−1, materiais reais e URL validada; contatar comunidades |
| <date start="2026-12-04" /> | D0 alvo, condicionado | Anunciar jogo somente se disponível, monitorado e testado |

## Gate de liberação — todos obrigatórios

- [ ] 13 momentos navegáveis, condições de vitória corretas e transições funcionais.
- [ ] Testes positivos, negativos e secure mirrors para desafios; verificador independente da UI; replay determinístico sem ativos reais.
- [ ] P0 de Voss: autoria da chamada autenticada, ligação AccessGate→RecoveryController→Escrow, política de saque e dossiê auditável. Ver <mention url="https://app.notion.com/p/40d9c563042581ba9836c2856425010e" />.
- [ ] Zero bugs críticos conhecidos; recuperação de erro e reset funcional.
- [ ] Onboarding e hints compreensíveis, Evidence Locker persistente, interface responsiva e acessível.
- [ ] Meta de 10 playtests externos completos; registrar conclusão, hints, tempo, dúvidas e pontos de abandono.
- [ ] Domínio, HTTPS, deploy público, link e material de lançamento inspecionados.
- [ ] Canal comunitário e suporte definidos; 6 peças pré-lançamento validadas.
- [ ] Decisão Go/No-Go em 26/11 registrada; D0 só se critérios atingidos.

## Estratégia de aquisição e mensuração

<b>Público prioritário:</b> devs Stellar/Soroban; interessados em auditoria Web3; jogadores CTF; comunidade de jogos indie e aprendizagem técnica. Mensagem principal: <b>investigue um roubo impossível e explore vulnerabilidades reais em contratos Stellar — de graça.</b>

- X: descoberta, lore, conceitos de segurança, clips reais e perguntas. Calendário em <mention url="https://app.notion.com/p/4029c563042581c8a6c8f89612175d14" /> e fila de publicações <mention url="https://app.notion.com/p/4bc75fffc553440f9ffd0497bf69ab12" />.
- Discord: proposta para comunidade/suporte/discussão de desafios; definir estrutura e moderação antes de anunciar.
- Outreach: selecionar contatos da Stellar, builders, organizadores de CTF e comunidades técnicas; personalizar convites e não insinuar parcerias oficiais.
- Métricas: visitas ao site, cliques no X, visitantes que iniciam prólogo, concluem Case 01, chegam ao Custodian, concluem Season 1, feedback e convites orgânicos.
- Objetivo inicial proposto: 50–100 jogadores relevantes na primeira onda; é meta de aprendizagem, não projeção de audiência garantida.

## Não fazer antes do lançamento

- Não começar Season 2 como prioridade da sprint.
- Não acrescentar novos desafios ou sistemas complexos de reputação.
- Não depender da integração Stellar Passport para publicar.
- Não reconstruir 14 artes já aprovadas por perfeccionismo.
- Não publicar teaser que pareça gameplay real usando mockup.
- Não marcar trabalho como implementado apenas por existir no Notion.

## Referências operacionais

- <mention url="https://app.notion.com/p/40c9c563042581e681e7e3523a88a468" /> — QA técnico e inventário por Case.
- <mention url="https://app.notion.com/p/40c9c5630425810a994ef41317431b6b" /> — decisão do domínio.
- <mention url="https://app.notion.com/p/4029c5630425810b9d95cca9b3630952" /> — Art Bible.
- <mention url="https://app.notion.com/p/40e9c5630425818db243d65bd4321f88" /> — Stellar DNA (propostas não canônicas).

## Próximas ações imediatas

- [ ] Definir identificador do X e completar avatar, capa, nome, bio e website (somente URL verificada).
- [ ] Produzir 3 peças usando arte aprovada: incidente, vista de Meridian e comunicado Authority.
- [ ] Capturar interface BREAKER OS real para o post #06.
- [ ] Revisar primeiro bloco da campanha (6 pré + 6 lançamento), mantendo estado NÃO PRONTO onde faltar material ou condição de publicação.
- [ ] Listar 20 comunidades/contatos prioritários com canal, motivo e abordagem individual.
- [ ] Confirmar domínio registrado/operando, link de produção e plano de suporte.
</content>
</page>

