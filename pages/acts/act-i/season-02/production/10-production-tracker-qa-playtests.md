---
notion_id: 40c9c563-0425-810e-b872-fb6544359653
source: https://app.notion.com/p/40c9c5630425810eb872fb6544359653?pvs=204
title: "🛠️ 10 — Production Tracker, QA & Playtests"
exported_at: 2026-11-07
---

**Controle de produção — Season 2.** As fichas dos Cases e o roteiro existem no Notion; isso **não comprova** implementação do frontend, quantidade de slides, contratos ou verificadores. **Não verificado** significa ausência de evidência inspecionada, não ausência de código. Este quadro é ponto de partida para a equipe, não status de entrega pronto.

# Source of truth e fluxo

1. **Cânone:** Visão Geral, Canon Oculto, personagem Rhea e páginas originais de Cases.
2. **Modelo de sistema:** [07 — Lumen Economic State & Continuidade da Crise](../world/07-lumen-economic-state-continuidade-da-crise.md).
3. **Apresentação:** [08 — Roteiro Narrativo de Gameplay & Slides](../world/08-roteiro-narrativo-de-gameplay-slides.md).
4. **Boss técnico:** Blueprint de The Cascade (novo documento).
5. **Implementação:** arquivos, commits, capturas, testes e verificador independente. Nenhuma documentação deve substituir essa evidência.

# Inventário por fase

| Fase | Roteiro | Contrato e secure mirror | Frontend / slides | Testes / verifier | Foco de validação |
| --- | --- | --- | --- | --- | --- |
| Prólogo | Canônico + beats propostos | Sem exploit obrigatório | Não verificado | Não verificado | Posição saudável liquidada, rastro de Rhea sem acusação precipitada |
| 01 — Stale Truth | Especificado | Não verificado | Não verificado | Não verificado | Mesmo preço stale; freshness/policy; liquidação saudável |
| 02 — False Confidence | Especificado | Não verificado | Não verificado | Não verificado | Intervalo de confiança ignorado, independente de frescor |
| 03 — Dry Pool | Especificado | Não verificado | Não verificado | Não verificado | Executed output adverso, ausência de limite mínimo |
| 04 — First Share | Especificado | Não verificado | Não verificado | Não verificado | Donation + rounding, shares/asset math, Sera após vitória |
| Boss — Liquidator | Canônico, simulação especificada | Não verificado | Não verificado | Não verificado | Contrafactual com mesmo estado, bloqueio e deterioração coerentes |
| 05 — Token Short | Especificado | Não verificado | Não verificado | Não verificado | amount solicitado ≠ balance delta; token de teste compatível com Soroban |
| 06 — Debt Never Grew | Especificado | Não verificado | Não verificado | Não verificado | Accrual e borrow ordem / debt index |
| 07 — Exit With Debt | Especificado | Não verificado | Não verificado | Não verificado | Health factor pós-withdraw, bad debt rastreável |
| 08 — One-Ledger Average | Especificado | Não verificado | Não verificado | Não verificado | Janela de um ledger desativa resistência do TWAP |
| 09 — Breaker Didn't Break | Especificado | Não verificado | Não verificado | Não verificado | Configured/Enabled sem enforce na execução |
| 10 — Emergency Authority | Escopo revisto; spec a validar | Não verificado | Não verificado | Não verificado | Target/selector/args; delay apenas se código comprovar |
| Final — Cascade | Canônico + blueprint | Não verificado | Não verificado | Não verificado | Contágio estável, settlements mínimos, bad debt reconhecido, exploit emergencial formalmente fora do escopo mas intervenção limitada pela política segura do challenge, Observer independente |

# Checklist de entrega por Case

- [ ] Contract fixture reproduzível e rede/SDK fixados; ambiente local isolado.
- [ ] Condição de vitória atesta comportamento econômico, não somente retorno true.
- [ ] Tentativa normal não vence; secure mirror rejeita exploit.
- [ ] Snapshot pre/post do estado e link de commit/test run registrados.
- [ ] A pista para o próximo Case tem origem econômica verificável.
- [ ] Slide antes do desafio não revela vulnerabilidade; Breach Report só depois.
- [ ] UI expõe os indicadores relevantes sem tornar o desafio um quiz.
- [ ] Asset visual desktop/mobile verificado; banner 8:3 quando aplicável.
- [ ] Reset/replay determinístico; sem ativos reais.
- [ ] Passa QA de compreensão narrativa e dificuldade de um jogador externo.

# Campos para controle efetivo

Por Case: **owner / status de narrativa / status de contrato / status de verifier / status de frontend / arte / versão SDK / URL de commit / link de testes / resultado playtest / blocker / próxima ação.** Não marcar pessoa, prazo, status “pronto” ou percentuais de avanço sem evidência.

# Priorização pragmática

**P0**: modelagem econômica e causalidade; fixtures de Cases 01–04; simulação do Liquidator; validação técnica do Case 10; contrato de aceitação da Cascade.

**P1**: fechamento de Cases 05–09; narrativa de slides pós-vitória, integração de evidências e arcos Sera/Ilyan/Nia.

**P2**: polimento visual de três estados urbanos (Lumen estável, ruptura, contenção), animações adicionais e hipóteses investigativas opcionais.

# Plano de playtest

- **Primeiro trecho:** Prólogo → 01–04, perguntar por que um feed stale e um feed incerto são riscos diferentes e por que o Vault se liga ao AMM.
- **Ponto de virada:** Liquidator com/sem explicações dos personagens; jogador precisa compreender por que a vitória agravou a crise.
- **Segundo trecho:** 05–09, verificar reconhecimento do déficit real e da falha de proteção.
- **Fechamento:** 10 + Cascade, testar se o jogador consegue defender suas intervenções e reconhecer perdas remanescentes sem instrução excessiva.

Registrar **tentativas, tempo por desafio, uso de hints, erro de hipótese, compreensão de consequência, motivo para próximo Case** e taxa de conclusão; não fixar metas numéricas sem rodada-piloto.

# O que ainda não foi feito

- Não contamos slides no site nem editamos frontend.
- Não compilamos ou validamos os snippets e contratos.
- Não testamos verificador e simulação da crise.
- Não produzimos nova arte ou substituímos referências existentes.

# Revisão de fases v3 — fila de implementação após avaliação editorial

**Atualização de escopo:** as páginas dos dez Cases e dois bosses receberam loops jogáveis v3, não código implementado. O backend e frontend continuam **não verificados**. Nenhuma nota editorial deve ser marcada como teste aprovado.

| Prioridade | Fase | Próxima entrega que precisa de evidência |
| --- | --- | --- |
| P0 | Liquidator | Mesma seed, intervenção Rhea bloqueada/permitida, diferença observável de liquidations/settlements |
| P0 | Case 07 | Snapshot agregado e reconciliação sem dupla contagem; perda sistêmica anterior à exploração |
| P0 | Case 10 | Fixture que prova falha de scope em target/function/args; confirmar se delay participa ou não |
| P0 | Cascade | Três objetivos player-facing ligados a invariants auditados por Observer independente |
| P1 | 01–02 | Desafios diferenciados: tempo de Oracle versus confidence de fonte |
| P1 | 03–04 | Vítima e perda na swap; matemática de shares verificável |
| P1 | 05–06 | Reconciliação de saldo versus accrual/ordem temporal |
| P1 | 08–09 | Configuração de janela versus ausência de enforce em caminho crítico |
| P2 | Todos | Feedback visual, ritmo dos slides, playtest sem dicas excessivas |

## Handoff por fase — registrar quando o repositório for acessível

**Checklist adicional:** commit e branch da fixture, versão Soroban SDK, comando de teste, seed e reset, instrumento de leitura de ledger, entrada do player, exploit positivo, secure mirror negativo, cálculo de perda/risco, arte/slide correspondente, gravação de gameplay e decisão de QA.

**Critério para fechar a revisão:** um avaliador externo consegue dizer o que investigou, o que executou, qual mudança de estado ocorreu e como isso conduz à próxima fase. Uma condição de vitória não pode depender apenas de string do frontend.

**Referências:** [03 — Mapa de Desafios & Aprendizado](../world/03-mapa-de-desafios-aprendizado.md); [07 — Lumen Economic State & Continuidade da Crise](../world/07-lumen-economic-state-continuidade-da-crise.md); [09 — The Cascade & Liquidator — Blueprint Técnico](../world/09-the-cascade-liquidator-blueprint-tecnico.md).

# QA P0 após aprovação das decisões de Lumen

- [ ] O Liquidator apresenta capability sem escopo específico e relatório de risco limitado mas verdadeiro, justificando o bloqueio.
- [ ] O plano de Rhea contém **filtragem de liquidações com feed inadequado e limite temporário de lote por ledger**; não confundir com isolamento posterior de um dos sete mercados.
- [ ] Dois replays com mesmo estado/seed variam somente a intervenção; demonstram diferenças em liquidações, AMM, slippage e settlement.
- [ ] Na Cascade, uma garantia operacional **real** é registrada com titularidade, regra de release, balanços e ausência de criação monetária.
- [ ] Rhea possui **autorização limitada de devolução** em custody/settlement, diferente da autoridade emergencial que lhe faltou no Liquidator.
- [ ] Retorno usa protocolo confidencial de Moonlight por motivo operacional de privacidade das posições; assets/amounts/proofs têm escopo definido.
- [ ] A transação vincula sender witness de Rhea, recipient witness de Breaker, commitment e policy na execução; o motivo para seguir a Moonlight fica compreensível.
