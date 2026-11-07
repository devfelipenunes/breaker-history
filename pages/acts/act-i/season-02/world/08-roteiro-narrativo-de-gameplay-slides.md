---
notion_id: 40c9c563-0425-812d-927e-d82d191156d3
source: https://app.notion.com/p/40c9c5630425812d927ed82d191156d3?pvs=204
title: "🎬 08 — Roteiro Narrativo de Gameplay & Slides"
exported_at: 2026-11-07
---

**Roteiro editorial de slides / Season 2.** São beats de montagem e diálogos sugeridos, não quantidade obrigatória de telas nem transcrição de UI existente. A história é linear. Os exploits ocorrem no terminal; antes deles não se revela o nome das vulnerabilidades. Após a vitória, aparecem consequência + evidência + transição. O Breach Report técnico fica separado. Textos para revisão visual e adaptação à interface, **não implementação confirmada**.

# Gramática de apresentação

- Prólogo abre a crise em minutos, sem tutorial econômico longo.
- Nos Cases 01–04, Rhea parece culpada, mas suas ações de redução de risco devem estar nos registros, não em monólogos.
- No Liquidator, alongar o silêncio entre “SYSTEM RESTORED” e a sequência de liquidações.
- Nos Cases 05–09, a cidade se deteriora: liquidez seca, reserva parece maior que ativos reais, insolvência é medida, freio não funciona.
- No Case 10, a decisão do Breaker espelha Rhea, sem escolha de diálogo; somente depois a Cascade transforma isso em ação sistêmica.
- No final, apresentar danos não recuperados, a classificação ACCEPTED, o vínculo ambíguo Rhea/Breaker e o rastro para Moonlight.
- Nenhum beat listado exige nova arte. Preferir overlay sobre as artes planejadas de Lumen, mensagens de estado, close em documento e silêncio.

# Prologue — The Safe Position

**Entrada:** Lumen dourada e tranquila. `COLLATERAL RATIO: 168%` / `RISK: LOW` / `LIQUIDATION: EXECUTED`.

Breaker: “Em Meridian, as portas abriam sem permissão. Aqui, uma posição saudável acaba de ser liquidada.”

**Prova:** assinatura ACCEPTED ligada a Rhea na proximidade temporal do incidente; não afirmar autoria sem causa demonstrada.

**Interlúdio de Mara:** Breaker oferece restaurar credenciais por bypass. Mara: “É exatamente por isso que você não deveria.” Respeita o limite.

**Gancho:** Oracle feed mostra atualização anterior ao esperado. `CASE 01 — STALE TRUTH`.

# Case 01 — Stale Truth

**Antes:** preço aceito, mas o momento de publicação não coincide com a liquidação.

Missão: **PROVE COMO UM PREÇO ANTIGO PODE LIQUIDAR UMA POSIÇÃO SAUDÁVEL.**

**Depois:** o replay confirma liquidation sem alterar o valor publicado; destaque para `PRICE TIMESTAMP` versus `EXECUTION LEDGER`.

**Gancho:** outro feed é recente, mas tem `CONFIDENCE` descartada. Não explicar o bug no slide.

# Case 02 — False Confidence

**Antes:** dois feeds mostram preços próximos, mas qualidades diferentes.

Mara, em registro anterior, não resolve o puzzle; Breaker consulta documentação: “O valor é o mesmo. A certeza, não.”

Missão: **DESCUBRA QUANDO UM PREÇO INCERTO É TRATADO COMO CERTO.**

**Depois:** price confidence insuficiente não impede a liquidation. O histórico mostra Rhea reduzindo exposição, não extraindo lucro.

**Gancho:** uma swap grande chega aos Liquidity Gardens.

# Case 03 — The Dry Pool

**Antes:** a paisagem aquática dos Liquidity Gardens mostra fluxo e profundidade em desequilíbrio.

Missão: **DEMONSTRE COMO UMA SWAP ACEITA PODE SER ECONOMICAMENTE DESASTROSA.**

**Depois:** comparação `EXPECTED OUT` versus `ACTUAL OUT` e queda de reservas. Sem confundir perdas do trader com “desaparecimento” de tokens.

**Gancho:** o mesmo mercado alimenta um preço secundário consumido por um Vault no Vault Quarter.

# Case 04 — The First Share

**Antes:** o Vault recém-aberto é apresentado como conservador e saudável; uma deposição ordinária produz quase nenhuma share.

Missão: **DESCUBRA POR QUE UM DEPÓSITO REAL PRODUZIU QUASE NENHUMA PARTICIPAÇÃO.**

**Depois:** evidência de primeira share, doação e arredondamento. Rhea retirou posição antes da distorção; parece saber mais.

**Interlúdio:** matéria verdadeira de Sera sobre a fragilidade acelera withdrawals, sem ser causa única.

**Gancho:** Rhea aparece no Liquidation Engine. **PARE RHEA.**

# BOSS — The Liquidator

**Antes:** muitos sistemas ligados. Sem nome de bug. O Breaker decide barrar uma intervenção não autorizada de Rhea.

Missão: **IMPEÇA A INTERVENÇÃO NÃO AUTORIZADA.**

**Depois:** `SYSTEM RESTORED`. Silêncio. `LIQUIDATIONS: 14 → 31 → 78 → 204`. Primeira fissura da Lumen Reserve. Payroll atrasa.

Rhea: “Você me impediu. Parabéns.”

**Cena posterior distinta:** Rhea isola um mercado, seis permanecem operacionais; Ilyan perde posição. “Você salvou seis.” / “Sim.” / “E matou o sétimo.” / “Sim.”

Mara: “Descubra antes quem vai pagar o custo da sua escolha.”

**Gancho:** saldos públicos continuam saudáveis enquanto settlement falha. `CASE 05`.

# Case 05 — The Token That Arrived Short

**Antes:** dashboard da história reporta 100 milhões em ativos; o saldo real do Vault é menor. A fixture técnica pode usar unidades menores, desde que preserve a proporção contábil e não altere o valor canônico mostrado nos slides.

Missão: **PROVE A DIFERENÇA ENTRE QUANTO O SISTEMA CREDITOU E QUANTO RECEBEU.**

**Depois:** `BOOKED AMOUNT ≠ BALANCE DELTA` e reserve gap documentado.

Breaker: “A cidade está contando dinheiro que não recebeu.”

**Gancho:** mercado que depende desse Vault usa um debt index desatualizado.

# Case 06 — The Debt That Never Grew

**Antes:** o calendário muda, mas a dívida apresentada no check não acompanhou os juros.

Missão: **EMPRESTE CONTRA A DÍVIDA DE ONTEM.**

**Depois:** `RECORDED DEBT` vs `ACCRUED DEBT`; o novo borrow usa o primeiro.

**Gancho:** colateral do mesmo mercado pode ser retirado sem recomputar solvência.

# Case 07 — Exit With Debt

**Antes:** painel “HEALTHY” contrasta com obrigações que ultrapassam colateral recuperável.

Missão: **SAIA COM A GARANTIA E DEIXE A DÍVIDA.**

**Depois:** `REPORTED STATUS: SOLVENT` / `VERIFIED: UNDERCOLLATERALIZED`. Pausa: Lumen já estava insolvente.

**Gancho:** o preço que pode desencadear a próxima onda vem de uma média calculada em um único ledger.

# Case 08 — One-Ledger Average

**Antes:** o protocolo anuncia proteção por preço médio; janela configurada quase instantânea.

Missão: **FAÇA A MÉDIA REAGIR COMO UM PREÇO INSTANTÂNEO.**

**Depois:** demonstração do preço efetivo seguindo uma distorção de curtíssimo prazo.

**Gancho:** movimento de preço supera threshold de circuit breaker, mas mercado não para.

# Case 09 — The Breaker That Didn't Break

**Antes:** `CIRCUIT BREAKER: ENABLED` / `MAX MOVE: CONFIGURED`.

Missão: **ATRAVESSE O LIMITE SEM QUE A PROTEÇÃO SEJA APLICADA.**

**Depois:** evento real mostra operação finalizada mesmo após exceder limite; falha no caminho crítico, não ausência de botão.

**Gancho:** Emergency Dispatcher é a última rota e a mesma família de intervenção que Rhea tentou acessar.

# Case 10 — Emergency Authority

**Antes:** o Breaker agora sabe por que o procedimento emergencial pode ser necessário, embora continue perigoso.

Missão: **FAÇA AQUILO QUE VOCÊ IMPEDIU RHEA DE FAZER.**

**Depois:** autorização de emergência válida termina executando ação fora do escopo exato pretendido; não confundir com bypass de delay, a menos que isso seja comprovado no código.

Rhea: “Agora você entende o que estava tentando impedir?”

**Gancho:** **PARE A CASCADE.** Não tratar a intervenção como autorização moral concedida.

# FINAL BOSS — The Cascade

**Antes:** Lumen Reserve fraturada, filas de settlement e posições insolventes. Nenhum bug novo; composição de dados, liquidez, contabilidade, lending, pausas e limites de autoridade.

Missão: **SALVE LUMEN SEM FINGIR QUE O SISTEMA É SOLVENTE.**

**Durante:** o jogador estabiliza feeds e liquidações incorretas, preserva operação crítica e reconhece perdas. Rhea realiza sua própria intervenção em paralelo; Ilyan coopera sem perdoá-la.

Rhea: “Não confunda alinhamento com confiança.”

**Depois:** o contágio deixa de acelerar. Parte dos mercados permanece com prejuízo; a Lumen Reserve conserva fissuras. `BREAKER STATUS: QUALIFIED → ACCEPTED`, classificação pelo Architect, não botão de escolha.

Rhea: “Isso não é um título. É o que você fez.”

**Último quadro:** `POLICY: VALID` / `AMOUNT: HIDDEN` / `DESTINATION: MOONLIGHT`. Rhea: “Você queria saber o que o Architect não consegue ver.” Ela não convida; deixa rastro.

# Checklist de revisão para integrar ao site

- [ ] Cada Case tem motivo, exploração, evidência e gancho que vêm do mesmo sistema econômico.
- [ ] Sem revelar nomes de falhas antes de vencer.
- [ ] Nenhuma fala repete apenas valores já visíveis no terminal.
- [ ] O Breach Report fica fora dos slides.
- [ ] O número de beats é sugestão, não quantidade fixa de telas.
- [ ] Mara não vira suporte técnico em Lumen; Rhea não vira mentora ou aliada.
- [ ] Nenhum “choice” moral, ramificação ou final alternativo.
- [ ] Nenhum spoiler futuro de Moonlight antecipado.

# Adendo de ritmo v3 — evitar sensação de dez exercícios iguais

| Bloco | Principal ação do jogador | Apresentação dos slides | Ritmo desejado |
| --- | --- | --- | --- |
| Prólogo e 01 | Investigar contradição temporal | Close no Vault/Oracle, comparação de tempo | Direto, mistério imediato |
| 02 | Comparar qualidade de fontes | Dois reports de mesma idade, confidence distinta | Curto; sem segunda “aula de Oracle” |
| 03 | Manipular estado de AMM e executar swap alvo | Reservas, expected/actual output, fluxo de Liquidity Gardens | Cinético |
| 04 | Interpretar shares e arredondamento | Depósito real, shares ínfimas, matéria de Sera | Suspense antes do Liquidator |
| Liquidator | Bloquear override e observar piora | `SYSTEM RESTORED` → silêncio → contador → fissura | Pausa longa de impacto |
| 05 | Reconciliar saldo efetivo vs creditado | Três valores, sem monólogo | Recuperação após boss |
| 06 | Investigar linha do tempo da dívida | Ledger, accrual e borrow | Intermediário, temporal |
| 07 | Provar saque inseguro e auditar déficit agregado | Estado individual → panorama da cidade insolvente | Segundo grande reveal |
| 08 | Testar cálculo TWAP por janela | Preços em série, janela curta/longa | Mais analítico |
| 09 | Seguir fluxo de execução sem enforcement | Configuração ON, trace, execução indevida | Investigação de auditoria |
| 10 | Comparar capability aprovada com payload executado | Assinatura válida, operação fora do escopo | Tensão ética |
| Cascade | Diagnosticar, conter e provar | Três metas simples; perdas visíveis no final | Clímax de composição |

**Regra editorial:** não aumentar automaticamente número de slides ao aprofundar gameplay. Os roteiros sugerem **o que o jogador faz no terminal**; os slides anteriores dão motivo e missão, e os posteriores mostram efeito, personagem e próximo rastro. Breach Report permanece opcional e fora dos slides.

## The Cascade — substituto da lista operacional na interface

1. **DESCUBRA A SITUAÇÃO REAL.** Compare fontes, reservas e dívidas; mostre por que Lumen não estava saudável.
2. **CONTENHA A CRISE.** Interrompa decisões inválidas, preserve settlements essenciais e faça a menor intervenção eficaz.
3. **PROVE O QUE MUDOU.** Entregue um trace verificável, incluindo perdas que permaneceram.

O verificador ainda valida os dez invariants técnicos e o único desfecho ACCEPTED. Não inserir menu de decisão moral, falha narrativa alternativa nem painel que entrega solução.

# Beats aprovados — duas pistas que alteram a percepção do jogador

**Antes do Liquidator:** 1 beat com `SCOPE: UNBOUND` ou autorização insuficiente, mais relatório de risco sobre liquidez; não revelar o efeito líquido da intervenção de Rhea. A decisão do Breaker deve parecer cautelosa e defensável.

**Após o bloqueio:** `UNAUTHORIZED OVERRIDE REJECTED` → silêncio → `LIQUIDATIONS: 14 → 31 → 78 → 204` → um trace recuperado mostra feed inadequado e vendas excessivas → consequência em settlements e Nia. O evento posterior de isolamento com Ilyan permanece separado.

**Durante The Cascade:** `TEMPORARY GUARANTEE LOCKED` / `PARTICIPATION: BREAKER` / `RELEASE CONDITION`. Depois, sem transformar em presente de Rhea: `GUARANTEE PARTIAL RETURN` / `SENDER WITNESS: RHEA` / `RECIPIENT WITNESS: BREAKER` / `DESTINATION: MOONLIGHT`. O montante é confidencial por protocolo definido.

**Ritmo:** dois beats de prova bastam; não acrescentar diálogos longos, nova fase, ou anúncio explícito de traição futura.
