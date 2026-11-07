---
notion_id: 40f9c563-0425-8195-823a-f64a18b1cc72
source: https://app.notion.com/p/40f9c56304258195823af64a18b1cc72?pvs=204
title: "🚀 18 — Plano de Lançamento | 30 dias — Season 1"
exported_at: 2026-11-07
---

**Plano operacional iniciado em 05/11/2026.** Meta proposta: disponibilizar **BREAKER — Season 1: The First Layer** por volta de `2026-12-04`. D0 é condicional: a data só vira compromisso público após os gates técnicos, de UX e publicação. Jogo CTF gratuito, narrativo, focado em smart contracts Stellar/Soroban.

## Decisões confirmadas

- **Domínio escolhido:** [playbreaker.xyz](http://playbreaker.xyz). Registro, DNS, HTTPS e site funcional ainda não foram confirmados.
- **Fonte narrativa:** [BREAKER — Season 1 | FINAL NARRATIVE v1.4 — NARRATIVE LOCK](../narrative/breaker-season-1-final-narrative-v1-4-narrative-lock.md) (Season 1 v1.4, editorialmente fechada). Não reabrir a história sem problema concreto descoberto em testes.
- **Prioridade do mês:** estabilidade + qualidade da experiência + distribuição; não acrescentar features por impulso.
- **Comunicação:** preparar perfil X e assets agora, mas respeitar campanha editorial D−7 → D+12 semanas. Não anunciar o jogo como disponível antes de validar D0.
- **Integrações extras:** Stellar Passport, sistema amplo de mapa, novos Easter Eggs e Season 2 ficam fora do caminho crítico de lançamento. Avaliar após estabilizar o núcleo.

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

**Regra:** "não verificado" ≠ "não implementado". Evidência de testes anteriores relatados pelo criador é valiosa, mas ainda precisa ser vinculada a versão/commit e resultados.

## Calendário de execução — 30 dias

| Período | Tema | Entrega para avançar |
| --- | --- | --- |
| `2026-11-05`–`2026-11-10` | Estabilização + operação | Inventário real dos 13 momentos; decidir URL e infraestrutura; registrar evidências de testes; perfil X |
| `2026-11-11`–`2026-11-17` | Experiência / onboarding | Primeiros 2 Cases claros; mensagens de erro, dicas, progresso e feedback; testes navegador/mobile |
| `2026-11-18`–`2026-11-24` | Playtest completo | Pelo menos 10 playtests externos como meta; capturar problemas, corrigir P0 e P1 relevantes |
| `2026-11-25`–`2026-11-26` | Checkpoint Go / No-Go | Verificar gates; confirmar ou adiar D0 sem promessas públicas |
| `2026-11-27`–`2026-12-03` | Pré-lançamento, se aprovado | Publicar 6 posts D−7 a D−1, materiais reais e URL validada; contatar comunidades |
| `2026-12-04` | D0 alvo, condicionado | Anunciar jogo somente se disponível, monitorado e testado |

## Gate de liberação — todos obrigatórios

- [ ] 13 momentos navegáveis, condições de vitória corretas e transições funcionais.
- [ ] Testes positivos, negativos e secure mirrors para desafios; verificador independente da UI; replay determinístico sem ativos reais.
- [ ] P0 de Voss: autoria da chamada autenticada, ligação AccessGate→RecoveryController→Escrow, política de saque e dossiê auditável. Ver [P0 — Prova de autoria de Voss | Dossiê auditável do Vault](p0-prova-de-autoria-de-voss-dossie-auditavel-do-vault.md).
- [ ] Zero bugs críticos conhecidos; recuperação de erro e reset funcional.
- [ ] Onboarding e hints compreensíveis, Evidence Locker persistente, interface responsiva e acessível.
- [ ] Meta de 10 playtests externos completos; registrar conclusão, hints, tempo, dúvidas e pontos de abandono.
- [ ] Domínio, HTTPS, deploy público, link e material de lançamento inspecionados.
- [ ] Canal comunitário e suporte definidos; 6 peças pré-lançamento validadas.
- [ ] Decisão Go/No-Go em 26/11 registrada; D0 só se critérios atingidos.

## Estratégia de aquisição e mensuração

**Público prioritário:** devs Stellar/Soroban; interessados em auditoria Web3; jogadores CTF; comunidade de jogos indie e aprendizagem técnica. Mensagem principal: **investigue um roubo impossível e explore vulnerabilidades reais em contratos Stellar — de graça.**

- X: descoberta, lore, conceitos de segurança, clips reais e perguntas. Calendário em [80 — Comunicação X | 45 posts — 13 semanas (Season 1)](../community/80-comunicacao-x-45-posts-13-semanas-season-1.md) e fila de publicações [X — Season 1 | Fila de Publicações](../community/x-season-1-fila-de-publicacoes.md).
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

- [15 — Plano de Melhorias e QA — Season 1](15-plano-de-melhorias-e-qa-season-1.md) — QA técnico e inventário por Case.
- [Branding & Domínio — Ideias e decisão](../../../../branding-dominio-ideias-e-decisao.md) — decisão do domínio.
- [09 — Art Bible CANÔNICO | Identidade Visual Aprovada — Baseline Site S1](../../../../series-bible/09-art-bible-canonico-identidade-visual-aprovada-baseline-site-s1.md) — Art Bible.
- [Stellar DNA — Atlas de Nomes, Projetos, Pioneiros & Integrações | Propostas 2026](../../../../stellar-dna-atlas-de-nomes-projetos-pioneiros-integracoes-propostas-.md) — Stellar DNA (propostas não canônicas).

## Próximas ações imediatas

- [ ] Definir identificador do X e completar avatar, capa, nome, bio e website (somente URL verificada).
- [ ] Produzir 3 peças usando arte aprovada: incidente, vista de Meridian e comunicado Authority.
- [ ] Capturar interface BREAKER OS real para o post #06.
- [ ] Revisar primeiro bloco da campanha (6 pré + 6 lançamento), mantendo estado NÃO PRONTO onde faltar material ou condição de publicação.
- [ ] Listar 20 comunidades/contatos prioritários com canal, motivo e abordagem individual.
- [ ] Confirmar domínio registrado/operando, link de produção e plano de suporte.
