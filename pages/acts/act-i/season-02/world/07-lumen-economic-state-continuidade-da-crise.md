---
notion_id: 40c9c563-0425-8117-9c72-dfd4d74e26bb
source: https://app.notion.com/p/40c9c563042581179c72dfd4d74e26bb?pvs=204
title: "📊 07 — Lumen Economic State & Continuidade da Crise"
exported_at: 2026-11-07
---

**Design de produção — Season 2 / Layer II.** Esta página conecta os Cases já canônicos em uma crise financeira determinística. **Não** muda a ordem, o resultado único, os personagens nem a condição técnica de cada Case. Modelos, thresholds e fluxos aqui são **especificações a validar em simulação**, não funcionalidades já implementadas ou valores reais de mercado.

# Princípio da temporada

Em Meridian, um contrato mal validado produzia uma consequência local; em Lumen, **dados, reservas, crédito, preços e proteções** podem amplificar uns aos outros. Nenhum bug isolado é a causa de toda a crise. O Breaker investiga uma economia conectada — não dez exploits independentes.

# Lumen Economic State — modelo mínimo

Expor um **dashboard diegético** com grandezas compreensíveis, sem adicionar HUD de jogo complexo. Os valores podem ser snapshots narrativos determinísticos, desde que concordem com os eventos reais dos fixtures técnicos.

| Indicador | Semântica | Evidência verificável | Regra de apresentação |
| --- | --- | --- | --- |
| Oracle freshness | Idade do preço usado para decisões | Timestamp/ledger do feed e hora da execução | Preço assinado não implica preço recente |
| Oracle confidence | Qualidade/incerteza do preço | Metadado de confidence e política consumidora | Não confundir com freshness |
| Available liquidity | Profundidade útil dos pools | Reservas do AMM, amount\_out e slippage | Não chamar TVL de liquidez executável |
| Vault accounting gap | Ativos creditados menos ativos efetivamente recebidos | Balance delta, totalAssets, shares | Não inventar ativos com accounting |
| Lending debt / bad debt | Dívida atualizada, colateral recuperável e déficit | Accrual, health factor, collateralization | Reconhecer perda, nunca ocultá-la |
| Liquidation pressure | Liquidações pendentes/efeito sobre preço | Fila de liquidations, preços e profundidade | Mostrar causalidade, não só contador |
| Settlement availability | Pagamentos essenciais processáveis | Fila, capacidade, atrasos e reversões | Conectar a payroll de Nia, sem inventar incidentes |

## Um único mundo, duas camadas de estado

1. **Runtime do Case:** fixtures isoladas reproduzem o exploit, registram pre/post state e reset para cada jogador. A cadeia Soroban não precisa compartilhar estado perigoso entre níveis.
2. **Estado narrativo de Lumen:** snapshots canônicos acumulam **descobertas e acontecimentos** entre Cases. Uma vitória de laboratório não precisa alterar uma blockchain pública e derrubar uma cidade real. O progresso do jogador habilita o próximo snapshot, sem choices que mudem a história.

A UI pode mostrar o **antes e depois** do fenômeno real reconstruído; evitar afirmar que o exploit realizado num clone de challenge causou sozinho toda a crise na cidade.

# Grafo de contágio / fluxo investigativo

`Oracle stale + confidence ignorada → collateral/valuation indevida → liquidations → perda de liquidez → swaps com slippage → valorização distorcida de shares → reservas aparentes ≠ reais → debt/accrual incorreto → retirada sem health check → bad debt oculto → TWAP ineficaz + circuit breaker inativo → emergency dispatch → Cascade.`

Esta é uma **cadeia de fatores e mecanismos de amplificação**, não um grafo no qual cada Case necessariamente causou cronologicamente o seguinte. Rhea não “criou” os bugs. Uma mesma evidência de dependência (feed, mercado, Vault ou livro de risco) precisa justificar por que o Breaker prossegue para o próximo sistema.

# Linha de progressão canônica (consequência e próximo motivo)

| Momento | Verdade que o player aprende | Estado acumulado/gancho verificável |
| --- | --- | --- |
| Prólogo | Vault liquida posição com ratio 168% e risco LOW | Traces apontam Oracle e transação de Rhea perto do incidente |
| 01 — Stale Truth | Feed antigo aceito como atual | Outra cotação do mesmo ativo traz confidence descartada |
| 02 — False Confidence | Número recente, porém incerto, também é perigoso | Rhea reduz exposição; swap de alto volume desafia profundidade do AMM |
| 03 — Dry Pool | Falta de min\_out torna execução sensível ao estado do pool | Registry de preço secundário do Vault usa mercado afetado |
| 04 — First Share | Doações e rounding deslocam valor no Vault | Sera publica fragilidades; withdrawals aceleram; Rhea se aproxima do Liquidator |
| Boss — Liquidator | Bloquear um desvio de Rhea restaura uma regra que amplifica liquidations | Contador aumenta; Reserve fissura; payroll atrasa; Rhea isola segmento menor para conter seis |
| 05 — Token Short | Creditado ≠ recebido, reservas menores que dashboard | Mesma reserva alimenta mercado de lending e debt index |
| 06 — Debt Never Grew | Dívida não sofreu accrual antes do borrow | Mesmo mercado permite sacar colateral sem verificar solvência |
| 07 — Exit With Debt | O déficit real já existia e é maior que o reportado | Fonte de precificação de risco depende de TWAP com janela mínima |
| 08 — One-Ledger Average | TWAP de um ledger não protege contra spot manipulation | Movimento extremo ultrapassa threshold que deveria pausar execução |
| 09 — Breaker Didn't Break | Controle anunciado não é aplicado no caminho crítico | Emergency Dispatcher é última rota; Rhea pretendia usá-lo |
| 10 — Emergency Authority | Autorização de emergência não restringe suficientemente operação executada | Janela técnica para conter contágio, sem legitimidade automática |
| Final — Cascade | Conter mecanismos, preservar settlements e reconhecer prejuízos | Lumen sobrevive com cicatrizes; Breaker ACCEPTED como classificação comportamental |

# Boss I — simulação contrafactual

**Pré-condição:** preço/health nominal considera feeds inseguros, Vault degradado e liquidez baixa. Rhea tenta uma intervenção **não autorizada** específica para frear a sequência. O Breaker a bloqueia pelo que parece ser a regra correta.

- **Cenário A — intervenção que Rhea queria:** caminho hipotético de contenção, não declarado moralmente correto; mostrar efeitos previstos e limites de confiança.
- **Cenário B — cenário canônico observado:** Breaker impede intervenção; liquidation engine segue validações equivocadas; fila e impacto aumentam. Exibir `14 → 31 → 78 → 204` como valores dramáticos da fila, não somas arbitrárias de capital.
- **Intervenção posterior distinta:** Rhea isola um segmento de sete, estabiliza seis, destrói exposição de Ilyan. Não misturar a tentativa bloqueada com o isolamento subsequente.

**Teste de causalidade:** em fixture de simulação, compare decisões e efeitos com o mesmo estado inicial. A vitória técnica do Boss é impedir a operação não autorizada; a piora é o payoff narrativo canônico, não um “fracasso” que retira achievement.

# Economia social — onde os números viram consequências

- **Nia Kade / payroll:** ligar aumento da fila de settlement a atrasos comprováveis de salários na Lower Lumen. Nia não precisa virar um NPC de suporte constante.
- **Ilyan Marr / Market Maker:** mostrar reserva, risco e posição antes/depois do isolamento para que a perda seja inteligível; sua ajuda no final é voluntária e não é perdão.
- **Sera Quill:** matéria verdadeira após Case 04 acelera retiradas de um sistema já frágil; não apresentar reportagem como causa inicial do colapso.
- **Apex / desigualdade:** setores ricos sentem o impacto depois de trabalhadores e mercados menos líquidos; isso pode ser mostrado com snapshots e arte, não com subplot adicional.
- **Rhea:** não antecipar sua motivação total nem tratá-la como onisciente.

# Regras para o frontend e o runtime

- **Não introduzir** escolhas de salvar ou sacrificar mercados; a Season tem um único cânone e um único final. Interações investigativas podem permitir ordenar a inspeção de evidências.
- Nenhum número de produção de economia precisa ser igual a valores reais de DEX/TVL. Usar unidades de fixture e rotular como dados de Lumen.
- O dashboard só deve exibir métricas que possam ser justificadas por traces, eventos ou serviços do jogo; não utilizar animação como substituto da prova.
- O painel após o exploit apresenta consequence, evidence, next lead; a explicação de vulnerabilidade aparece no Breach Report opcional.
- Evitar alterações amplas no frontend existente: preferir overlay da Reserve, tabelas antes/depois e indicadores de estado dos mesmos componentes.

# Critérios de aceitação do modelo

- [ ] As 12 transições (incluindo bosses) possuem evento técnico ou evidência de dependência.
- [ ] Case 01 e 02 demonstram problemas distintos de feed (stale vs confidence).
- [ ] Case 03 e 04 não sugerem que AMM e Vault compartilham um saldo mágico; mostrar a integração específica.
- [ ] Case 05 e 06 relacionam saldo creditado, saldo real e dívida sem confundir causalidade.
- [ ] The Liquidator possui comparação reproduzível no mesmo snapshot.
- [ ] A insolvência revelada no Case 07 é coerente com o accounting dos Cases anteriores.
- [ ] Sera, Ilyan e Nia produzem consequências humanas observáveis.
- [ ] The Cascade estabiliza dependências críticas sem apagar bad debt.
- [ ] Nenhuma vitória do challenge depende de ativos de verdade, dinheiro real ou chamadas de redes de produção.

# Refinamento econômico v3 — prova agregada e ligação com os bosses

## Modelo de solvência no Case 07

A narrativa “Lumen já estava insolvente” só é válida se o modelo econômico apresentar prova agregada, e não apenas um collateral withdrawal que deixou um borrower insolvente.

**Fixture mínima:** listar por mercado relevante `actual_assets`, `collectible_loans` (sem incluir empréstimos integralmente dentro dos próprios ativos duas vezes), `recoverable_collateral`, `customer_liabilities`, `bad_debt` e `insurance_obligations`. Registrar dependências entre Vaults, lending e settlement.

**Reconciliação:** identificar ativos e passivos intra-protocolo que se anulam na consolidação; não contar reservas de AMM e direitos sobre as mesmas reservas duas vezes. A situação da cidade é a soma coerente dos mercados cobertos pela fixture, explicitando seu escopo. Exibir `REPORTED` e `VERIFIED` no Evidence Locker.

**Condição narrativa:** o déficit verificado é anterior ao Case 07; a exploração demonstra uma vulnerabilidade adicional, enquanto a investigação torna a insolvência conhecida.

## Liquidator: cenário observado versus contrafactual

Dois replays com mesmo estado inicial e seed; variar apenas bloqueio da intervenção de Rhea. Medir fila de liquidações, reservas do pool, pressure e atraso de settlement. Uma hipótese técnica de quarentena de liquidações com feed não confiável precisa ser confirmada na fixture, não atribuída ao cânone sem teste. O isolamento posterior do sétimo segmento é outro evento.

## The Cascade: três metas para o jogador

**Investigar o estado real → Conter o contágio → Comprovar o resultado.** A interface agrupa as operações em três metas, mas o verificador técnico independente mantém todos os invariants, reconhecendo perdas e limites das intervenções.

## QA de integração

- [ ] Agregado de Case 07 reconciliado sem double-count.
- [ ] Evidência de insolvência disponível antes da conclusão da Cascade.
- [ ] Contrafactual do Liquidator reproduzível.
- [ ] Cada tela de crise ancorada em snapshot e evento, não em animação sem fundamento.
- [ ] Três objetivos do Final Boss compreendidos por jogador externo, sem dar os passos do exploit.

# Adendo de simulação — decisões narrativas aprovadas do Liquidator e da garantia

**Liquidator / cenário A e B:** usar mesma seed e snapshots para (A) tentativa de Rhea executada e (B) tentativa bloqueada. Na operação de Rhea, aplicar filtro de qualidade do feed e teto temporário de liquidações por ledger; medir fila, venda forçada, reservas AMM, slippage e settlement. O Breaker bloqueia com relatório parcial de risco e capability não autorizada. Documentar o efeito contrário de pausas legítimas, se houver; não declarar Rhea infalível.

**Garantia Cascade → Moonlight:** fixture de colateral real bloqueado, reserva segregada, titularidade da parcela do Breaker e regra de liberação após contenção. No evento final, Rhea envia retorno autorizado; provar diferença de balanços e compromisso, sem minting/duplicação. Confidentiality protege o que o protocolo escolhido realmente oculta; rotas públicas não somem.

**Verificações adicionais:** - \[ \] nenhum settlement real de usuário; - \[ \] seed reproduzível do Liquidator; - \[ \] lote e filtro realmente afetam contágio; - \[ \] garantia não criada do nada; - \[ \] transferência de retorno preserva policy histórica e ligação sender/recipient.
