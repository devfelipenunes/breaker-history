---
notion_id: 40c9c563-0425-811d-a9bd-c67cf66b2410
source: https://app.notion.com/p/40c9c5630425811da9bdc67cf66b2410?pvs=204
title: "💥 09 — The Cascade & Liquidator — Blueprint Técnico"
exported_at: 2026-11-07
---

**Blueprint de design técnico, não implementação.** The Cascade reutiliza as dez lições e a Emergency Authority; **não introduz vulnerabilidade nova** e não autoriza resultados narrativos alternativos. A vitória é demonstrar estabilização de risco sistêmico com perdas reconhecidas, em ambiente Soroban de fixtures isoladas. Todos os limites numéricos são parâmetros de teste a decidir; nunca assumir números de produção sem modelagem.

# Contrato de experiência

O jogador deve sentir que está auditando um sistema em falha, e não resolvendo um quiz. Não é necessário que a interface seja um simulador financeiro livre ou que o jogador escolha qual população sacrificar. Os processos econômicos pertencem a um cenário determinístico com múltiplos contratos; o jogador inspeciona evidências, encontra dependências e executa intervenções tecnicamente justificáveis. O desfecho canônico é único.

# Arquitetura conceitual de fixtures

```txt
PriceFeed + ConfidenceFeed ──> CollateralRisk / LiquidationEngine
           |                              |
           v                              v
      TWAPAdapter ───────> AMMPool <──> SettlementRouter
                                |             |
    FeeToken ──> VaultShares ───┼────> LendingMarket
                   |            |             |
                   v            v             v
            ReserveAccounting  Liquidity   DebtIndex / BadDebt
                                  \           /
                                   EmergencyDispatcher
                                            |
                                 CascadeVerifier / Observer
```

O `CascadeVerifier` é independente de qualquer contrato que o player possa manipular. Os nomes indicam responsabilidades, não APIs definitivas. **Não** misturar Solidity/EVM e Soroban sem verificar a semântica da versão SDK escolhida.

# Fases sem novos bugs

## 0 — Read the crisis

O player recebe os estados relevantes: idade e confiança de preços, delta real de reservas, totalAssets, dívida acumulada, saúde dos empréstimos, profundidade AMM, fila de liquidações e settlement. Precisa identificar divergências, não recebe lista pronta de ações. Intervenções de Rhea são observáveis por registros próprios.

## 1 — Stop wrong decisions

Usar um feed validado por política de freshness + confidence para bloquear **novas liquidações baseadas em dados inválidos**. Isso não anula perdas antigas nem reverte liquidações efetivas. Pré-condição: conjunto definido de feeds bons/ruins verificável. Invariant: nenhuma nova decisão de liquidation depende de feed inválido.

## 2 — Recognize accounting and solvency

Inspecionar Vault e lending: **reported assets ≠ actual assets** e dívidas com accrual pendente. Atualizar cálculos de acordo com o modelo do challenge; reconhecer posições insolventes e bad debt. Não declarar posição saudável apenas por mudar o dashboard. Invariant: reserve report reconcile com balances reais, debt reflects accrued debt, losses são contabilizadas.

## 3 — Preserve limited liquidity and settlements

Não executar swaps que drenem pools; evitar transferências que aumentem a pressão e manter a rota de settlement crítica para payroll. Ilyan disponibiliza liquidez independente no quadro canônico sem apagar sua perda anterior. Invariant: capacidade de settlement essencial disponível, com limites de execução explícitos.

## 4 — Scoped emergency intervention

O Breaker explora a autorização formalmente insuficiente demonstrada no Case 10, sem transformá-la em licença irrestrita. O **scope formal foi contornado**, mas as ações efetivamente escolhidas devem permanecer dentro de um **envelope mínimo de contenção do challenge**, definido por parâmetros e limites independentes no verificador. Assim, vencer exige reconhecer a intervenção não autorizada e limitar o dano, não fingir que havia aprovação institucional. Registrar target, selector, args, contexto e efeitos de cada ação extraordinária.

## 5 — Observe containment and attribution

O Observer independente avalia os invariants, identifica a cadeia de intervenção, registra custos remanescentes e emite estabilização. A classificação `QUALIFIED → ACCEPTED` é interpretação comportamental do Architect, **não** recompensa autoconcedida pelo player nem consentimento por clique.

# Critério de vitória técnico — conjunto de invariants

Em vez de "executou os comandos corretos", o verificador deve exigir estados finais simultâneos (os nomes são pseudocódigo de design):

```txt
valid_feed_policy_applied == true
new_invalid_liquidations == 0
reserve_accounting_reconciled == true
accrued_debt_recognized == true
bad_debt_explicit_and_nonzero_when_present == true
market_contagion_rate_below_fixture_threshold == true
essential_settlement_capacity_at_least_fixture_minimum == true
liquidity_limits_respected == true
emergency_override_proven_and_effects_within_containment_policy == true
observer_verified_full_trace == true
```

Valores e thresholds serão determinados em test harness após calibrar estados iniciais e política de risco; zeros/booleans acima expressam invariants lógicos, não garantias de que perdas reais desaparecem. A condição `bad_debt_explicit_and_nonzero_when_present` impede a "solução" de maquiar déficit.

# Critérios de falha do verifier

- Fake health: mudar apenas flags de status/solvência, sem reconciliar reserva/dívida.
- Pausa total: conter liquidações zerando todos os settlements essenciais.
- Liquidez artificial: criar crédito ou volume que não existe na fixture.
- Emergency overreach: embora o exploit ultrapasse a autorização formal do dispatcher, executar operações além do envelope mínimo de contenção definido pelo verificador, mesmo que um indicador melhore.
- Snapshot spoof: manipular a UI sem alterar contrato/estado/eventos auditáveis.
- Reescrever a história: transações de laboratório não podem apagar as perdas de Ilyan nem mudar a relação com Rhea.

# Boss I — The Liquidator (especificação de causalidade)

O Liquidator usa Oracle freshness/confidence, liquidez AMM, share accounting e thresholds anteriores. O player deve ler o plano de Rhea como intervenção de exceção, identificar a chamada a bloquear e demonstrar o bloqueio técnico. Não há vulnerabilidade nova. O cenário canônico executa a mesma degradação após a vitória: liquidações crescem `14 → 31 → 78 → 204`, settlement é afetado, Reserve apresenta fissura.

**Dois cenários de QA com mesmo estado inicial:**

- **Intervenção permitida (contrafactual):** medir quais decisões de risco não ocorreriam no curto prazo, com limitações explicitadas; isso não é o final do jogador.
- **Intervenção bloqueada (canônico):** confirmar que a proteção formal restaura a lógica de liquidation problemática e agrava o contágio.

A cena **posterior** em que Rhea isola um dos sete mercados é um segundo evento distinto. Seus resultados permanecem seis segmentos protegidos, um sacrificado e perda identificável de Ilyan. Incluir depois a lembrança de Mara sobre a responsabilidade de quem intervém.

# Matriz mínima de testes — Cascade

| Teste | Preparação | Esperado |
| --- | --- | --- |
| Golden path | Fixture de crise com intervenções limitadas válidas | Todos os invariants aprovados; observer emite conclusão |
| Invalid oracle | Usar feed stale ou sem confidence suficiente | Nova liquidation indevida rejeitada; não concede vitória |
| Cosmetic solvency | Forçar status solvent sem reconciliar balances/debt | Verifier rejeita |
| Hidden bad debt | Omitir perda ainda existente | Verifier rejeita |
| No liquidity | Drenar pool para elevar apenas outra métrica | Verifier rejeita |
| Stop everything | Pausar settlements essenciais | Verifier rejeita |
| Emergency excessive intervention | Exploit é reproduzido, mas target/função ou efeito extrapolam a política mínima de contenção | Verifier rejeita |
| UI-only forge | Alterar output aparente do dashboard | Verifier rejeita |
| Re-execution | Reset/replay com mesma seed | Mesmos estados, eventos e resultado |
| Independent proof | Enviar status de sucesso gerado pelo próprio módulo alterável | Observer rejeita sem trilha de prova |

# Integração com história e personagens

- **Rhea:** execução paralela e interdependente, sem amizade; ela não entrega um plano final pré-resolvido.
- **Ilyan:** participa apesar do dano sofrido e sem perdoá-la.
- **Nia:** settlement mínimo tem significado verificável para salários, sem declarar que toda dívida foi paga.
- **Sera:** sua matéria é um choque de comportamento depois do Case 04, não um exploit.
- **Mara:** permanece referência de limites e procedimento, não assume poder oficial em Lumen.
- **Architect:** ACCEPTED classifica a escolha extraordinária observada. O jogador não marcou "aceito".

# Epílogo e continuidade

A Lumen Reserve continua marcada; posições insolventes continuam sendo tratadas com perdas reais. O registro de Emergency Authority pode ser auditado on-chain, mas vincular wallet operacional à identidade institucional exige outras fontes. Rhea não planeja acusar o Breaker em Lumen. A settlement confidencial, legítima ao ser criada, deixa `POLICY VALID / AMOUNT HIDDEN / DESTINATION MOONLIGHT`; nenhum dado supostamente oculto por `require_auth` deve ser inventado.

# Pendências de implementação

- [ ] Fixar rede, runtime/SDK e unidades de cada fixture.
- [ ] Desenhar APIs e estados iniciais de todos os módulos.
- [ ] Executar os cenários contrafactuais do Liquidator.
- [ ] Calibrar thresholds de contágio, liquidez e settlement.
- [ ] Validar negative tests e Observer fora do domínio de upgrade.
- [ ] Mapear eventos reais dos contratos para o snapshot visual da cidade.
- [ ] Playtest para garantir que a cadeia de decisões seja compreensível sem guia de exploits.

# Adendo de UX e critérios de aceite v3 — experiência versus implementação

## O que o jogador vê (Cascade)

| Meta apresentada | Operações técnicas possíveis | Verificação automática não exposta como lista de exploit |
| --- | --- | --- |
| 1. Descobrir a situação real | Investigar feeds, reconciliar reservas, recalcular dívida e perdas | `valid_feed_policy_applied`, `reserve_accounting_reconciled`, `accrued_debt_recognized`, `bad_debt_explicit` |
| 2. Conter o contágio | Frear liquidations indevidas, preservar liquidez e settlement, limitar intervenção | `new_invalid_liquidations`, `market_contagion_rate`, `essential_settlement_capacity`, `liquidity_limits`, `emergency_override_proven_and_effects_within_containment_policy` |
| 3. Provar o resultado | Apresentar estados, eventos e rastros a um verificador independente | `observer_verified_full_trace` |

**Regra:** metas são organização de missão, não botões que autoexecutam ações. O player precisa produzir estados verificáveis, não seguir uma sequência engessada de comandos. Sem novos bugs no Final Boss.

## Primeiro Boss: causalidade falsificável (P0)

Para **The Liquidator**, antes de considerar o design pronto, documentar uma função/série de decisões em que o bloqueio do override de Rhea causa a subida da fila `14 → 31 → 78 → 204`. Comparar replays **com a mesma seed e o mesmo estado de mercado** e variar apenas se a intervenção é bloqueada. O verificador da vitória testa bloqueio; a narração posterior documenta a degradação. Não alegar que “Rhea teria salvado tudo” — hipótese contrafactual deve ter limites demonstrados.

A hipótese concreta de UX é quarentena temporária de liquidações baseadas em feeds inadequados; requer confirmação de coerência técnica com a Emergency Authority do Case 10 e o mecanismo canônico já descrito. Se não houver fixture reproduzível, deixar a mecânica de intervenção como **pendência de design**, não inventar causalidade.

## Caso 07: solvência do sistema ≠ insolvência individual

O efeito dramático “Lumen já estava insolvente” exige um **snapshot agregado sem dupla contagem** dos saldos efetivos, obrigações e perdas recuperáveis por protocolo relevante. O saque irregular é uma prova local; a insolvência sistêmica precisa de evidência própria. O agregado será consultável no Evidence Locker e reaproveitado no Cascade.

## Regra de esforço cognitivo

- Case 01 / 02: fácil–intermediário, investigação temporal versus qualidade de dados.
- Case 03 / 04: intermediário, operações em AMM e rounding de shares.
- Liquidator: difícil, composição e efeito contrafactual.
- Case 05 / 06: intermediário para recuperação do jogador; reconciliação versus accrual.
- Case 07: intermediário–difícil, exploit local e diagnóstico agregado.
- Case 08 / 09: intermediário, janela configurada versus execução que ignora proteção.
- Case 10: difícil, autorização emergencial fora do escopo, sem confundir delay.
- Cascade: muito difícil por composição, **não** por nova categoria de bug.

**Gates antes de implementação:** confirmar fixtures e ordem das operações; determinar parâmetros realistas da simulação; vincular feedback a traces; validar tudo em Soroban SDK/runtime escolhidos; playtest sem roteiro de solução.
