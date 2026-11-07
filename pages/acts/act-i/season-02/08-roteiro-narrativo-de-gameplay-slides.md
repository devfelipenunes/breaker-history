---
notion_id: 40c9c563-0425-812d-927e-d82d191156d3
source: https://app.notion.com/p/40c9c5630425812d927ed82d191156d3?pvs=204
title: "🎬 08 — Roteiro Narrativo de Gameplay & Slides"
exported_at: 2026-11-07
---

Here is the result of "fetch" for the Page with URL https://app.notion.com/p/40c9c5630425812d927ed82d191156d3 as of 2026-11-02T23:59:53.464Z:
<page url="https://app.notion.com/p/40c9c5630425812d927ed82d191156d3" icon="🎬">
<ancestor-path>
<parent-page url="https://app.notion.com/p/4019c563042581d9aedad3e5f178c3e8" title="Season 02 — DeFi Wars — Lumen"/>
<ancestor-2-page url="https://app.notion.com/p/4019c563042581469a0edc7e30a6eff9" title="ACT I — The World Is Breakable"/>
<ancestor-3-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
<properties>
{"title":"08 — Roteiro Narrativo de Gameplay & Slides"}
</properties>
<iconMetadata>{"type":"emoji","emoji":"🎬"}</iconMetadata>
<content>
<callout icon="🎬" color="purple_bg">
<b>Roteiro editorial de slides / Season 2.</b> São beats de montagem e diálogos sugeridos, não quantidade obrigatória de telas nem transcrição de UI existente. A história é linear. Os exploits ocorrem no terminal; antes deles não se revela o nome das vulnerabilidades. Após a vitória, aparecem consequência + evidência + transição. O Breach Report técnico fica separado. Textos para revisão visual e adaptação à interface, <b>não implementação confirmada</b>.
</callout>

# Gramática de apresentação

- Prólogo abre a crise em minutos, sem tutorial econômico longo.
- Nos Cases 01–04, Rhea parece culpada, mas suas ações de redução de risco devem estar nos registros, não em monólogos.
- No Liquidator, alongar o silêncio entre “SYSTEM RESTORED” e a sequência de liquidações.
- Nos Cases 05–09, a cidade se deteriora: liquidez seca, reserva parece maior que ativos reais, insolvência é medida, freio não funciona.
- No Case 10, a decisão do Breaker espelha Rhea, sem escolha de diálogo; somente depois a Cascade transforma isso em ação sistêmica.
- No final, apresentar danos não recuperados, a classificação ACCEPTED, o vínculo ambíguo Rhea/Breaker e o rastro para Moonlight.
- Nenhum beat listado exige nova arte. Preferir overlay sobre as artes planejadas de Lumen, mensagens de estado, close em documento e silêncio.

# Prologue — The Safe Position

<b>Entrada:</b> Lumen dourada e tranquila. <code>COLLATERAL RATIO: 168%</code> / <code>RISK: LOW</code> / <code>LIQUIDATION: EXECUTED</code>.

Breaker: “Em Meridian, as portas abriam sem permissão. Aqui, uma posição saudável acaba de ser liquidada.”

<b>Prova:</b> assinatura ACCEPTED ligada a Rhea na proximidade temporal do incidente; não afirmar autoria sem causa demonstrada.

<b>Interlúdio de Mara:</b> Breaker oferece restaurar credenciais por bypass. Mara: “É exatamente por isso que você não deveria.” Respeita o limite.

<b>Gancho:</b> Oracle feed mostra atualização anterior ao esperado. <code>CASE 01 — STALE TRUTH</code>.

# Case 01 — Stale Truth

<b>Antes:</b> preço aceito, mas o momento de publicação não coincide com a liquidação.

Missão: <b>PROVE COMO UM PREÇO ANTIGO PODE LIQUIDAR UMA POSIÇÃO SAUDÁVEL.</b>

<b>Depois:</b> o replay confirma liquidation sem alterar o valor publicado; destaque para <code>PRICE TIMESTAMP</code> versus <code>EXECUTION LEDGER</code>.

<b>Gancho:</b> outro feed é recente, mas tem <code>CONFIDENCE</code> descartada. Não explicar o bug no slide.

# Case 02 — False Confidence

<b>Antes:</b> dois feeds mostram preços próximos, mas qualidades diferentes.

Mara, em registro anterior, não resolve o puzzle; Breaker consulta documentação: “O valor é o mesmo. A certeza, não.”

Missão: <b>DESCUBRA QUANDO UM PREÇO INCERTO É TRATADO COMO CERTO.</b>

<b>Depois:</b> price confidence insuficiente não impede a liquidation. O histórico mostra Rhea reduzindo exposição, não extraindo lucro.

<b>Gancho:</b> uma swap grande chega aos Liquidity Gardens.

# Case 03 — The Dry Pool

<b>Antes:</b> a paisagem aquática dos Liquidity Gardens mostra fluxo e profundidade em desequilíbrio.

Missão: <b>DEMONSTRE COMO UMA SWAP ACEITA PODE SER ECONOMICAMENTE DESASTROSA.</b>

<b>Depois:</b> comparação <code>EXPECTED OUT</code> versus <code>ACTUAL OUT</code> e queda de reservas. Sem confundir perdas do trader com “desaparecimento” de tokens.

<b>Gancho:</b> o mesmo mercado alimenta um preço secundário consumido por um Vault no Vault Quarter.

# Case 04 — The First Share

<b>Antes:</b> o Vault recém-aberto é apresentado como conservador e saudável; uma deposição ordinária produz quase nenhuma share.

Missão: <b>DESCUBRA POR QUE UM DEPÓSITO REAL PRODUZIU QUASE NENHUMA PARTICIPAÇÃO.</b>

<b>Depois:</b> evidência de primeira share, doação e arredondamento. Rhea retirou posição antes da distorção; parece saber mais.

<b>Interlúdio:</b> matéria verdadeira de Sera sobre a fragilidade acelera withdrawals, sem ser causa única.

<b>Gancho:</b> Rhea aparece no Liquidation Engine. <b>PARE RHEA.</b>

# BOSS — The Liquidator

<b>Antes:</b> muitos sistemas ligados. Sem nome de bug. O Breaker decide barrar uma intervenção não autorizada de Rhea.

Missão: <b>IMPEÇA A INTERVENÇÃO NÃO AUTORIZADA.</b>

<b>Depois:</b> <code>SYSTEM RESTORED</code>. Silêncio. <code>LIQUIDATIONS: 14 → 31 → 78 → 204</code>. Primeira fissura da Lumen Reserve. Payroll atrasa.

Rhea: “Você me impediu. Parabéns.”

<b>Cena posterior distinta:</b> Rhea isola um mercado, seis permanecem operacionais; Ilyan perde posição. “Você salvou seis.” / “Sim.” / “E matou o sétimo.” / “Sim.”

Mara: “Descubra antes quem vai pagar o custo da sua escolha.”

<b>Gancho:</b> saldos públicos continuam saudáveis enquanto settlement falha. <code>CASE 05</code>.

# Case 05 — The Token That Arrived Short

<b>Antes:</b> dashboard da história reporta 100 milhões em ativos; o saldo real do Vault é menor. A fixture técnica pode usar unidades menores, desde que preserve a proporção contábil e não altere o valor canônico mostrado nos slides.

Missão: <b>PROVE A DIFERENÇA ENTRE QUANTO O SISTEMA CREDITOU E QUANTO RECEBEU.</b>

<b>Depois:</b> <code>BOOKED AMOUNT ≠ BALANCE DELTA</code> e reserve gap documentado.

Breaker: “A cidade está contando dinheiro que não recebeu.”

<b>Gancho:</b> mercado que depende desse Vault usa um debt index desatualizado.

# Case 06 — The Debt That Never Grew

<b>Antes:</b> o calendário muda, mas a dívida apresentada no check não acompanhou os juros.

Missão: <b>EMPRESTE CONTRA A DÍVIDA DE ONTEM.</b>

<b>Depois:</b> <code>RECORDED DEBT</code> vs <code>ACCRUED DEBT</code>; o novo borrow usa o primeiro.

<b>Gancho:</b> colateral do mesmo mercado pode ser retirado sem recomputar solvência.

# Case 07 — Exit With Debt

<b>Antes:</b> painel “HEALTHY” contrasta com obrigações que ultrapassam colateral recuperável.

Missão: <b>SAIA COM A GARANTIA E DEIXE A DÍVIDA.</b>

<b>Depois:</b> <code>REPORTED STATUS: SOLVENT</code> / <code>VERIFIED: UNDERCOLLATERALIZED</code>. Pausa: Lumen já estava insolvente.

<b>Gancho:</b> o preço que pode desencadear a próxima onda vem de uma média calculada em um único ledger.

# Case 08 — One-Ledger Average

<b>Antes:</b> o protocolo anuncia proteção por preço médio; janela configurada quase instantânea.

Missão: <b>FAÇA A MÉDIA REAGIR COMO UM PREÇO INSTANTÂNEO.</b>

<b>Depois:</b> demonstração do preço efetivo seguindo uma distorção de curtíssimo prazo.

<b>Gancho:</b> movimento de preço supera threshold de circuit breaker, mas mercado não para.

# Case 09 — The Breaker That Didn't Break

<b>Antes:</b> <code>CIRCUIT BREAKER: ENABLED</code> / <code>MAX MOVE: CONFIGURED</code>.

Missão: <b>ATRAVESSE O LIMITE SEM QUE A PROTEÇÃO SEJA APLICADA.</b>

<b>Depois:</b> evento real mostra operação finalizada mesmo após exceder limite; falha no caminho crítico, não ausência de botão.

<b>Gancho:</b> Emergency Dispatcher é a última rota e a mesma família de intervenção que Rhea tentou acessar.

# Case 10 — Emergency Authority

<b>Antes:</b> o Breaker agora sabe por que o procedimento emergencial pode ser necessário, embora continue perigoso.

Missão: <b>FAÇA AQUILO QUE VOCÊ IMPEDIU RHEA DE FAZER.</b>

<b>Depois:</b> autorização de emergência válida termina executando ação fora do escopo exato pretendido; não confundir com bypass de delay, a menos que isso seja comprovado no código.

Rhea: “Agora você entende o que estava tentando impedir?”

<b>Gancho:</b> <b>PARE A CASCADE.</b> Não tratar a intervenção como autorização moral concedida.

# FINAL BOSS — The Cascade

<b>Antes:</b> Lumen Reserve fraturada, filas de settlement e posições insolventes. Nenhum bug novo; composição de dados, liquidez, contabilidade, lending, pausas e limites de autoridade.

Missão: <b>SALVE LUMEN SEM FINGIR QUE O SISTEMA É SOLVENTE.</b>

<b>Durante:</b> o jogador estabiliza feeds e liquidações incorretas, preserva operação crítica e reconhece perdas. Rhea realiza sua própria intervenção em paralelo; Ilyan coopera sem perdoá-la.

Rhea: “Não confunda alinhamento com confiança.”

<b>Depois:</b> o contágio deixa de acelerar. Parte dos mercados permanece com prejuízo; a Lumen Reserve conserva fissuras. <code>BREAKER STATUS: QUALIFIED → ACCEPTED</code>, classificação pelo Architect, não botão de escolha.

Rhea: “Isso não é um título. É o que você fez.”

<b>Último quadro:</b> <code>POLICY: VALID</code> / <code>AMOUNT: HIDDEN</code> / <code>DESTINATION: MOONLIGHT</code>. Rhea: “Você queria saber o que o Architect não consegue ver.” Ela não convida; deixa rastro.

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
| Liquidator | Bloquear override e observar piora | <code>SYSTEM RESTORED</code> → silêncio → contador → fissura | Pausa longa de impacto |
| 05 | Reconciliar saldo efetivo vs creditado | Três valores, sem monólogo | Recuperação após boss |
| 06 | Investigar linha do tempo da dívida | Ledger, accrual e borrow | Intermediário, temporal |
| 07 | Provar saque inseguro e auditar déficit agregado | Estado individual → panorama da cidade insolvente | Segundo grande reveal |
| 08 | Testar cálculo TWAP por janela | Preços em série, janela curta/longa | Mais analítico |
| 09 | Seguir fluxo de execução sem enforcement | Configuração ON, trace, execução indevida | Investigação de auditoria |
| 10 | Comparar capability aprovada com payload executado | Assinatura válida, operação fora do escopo | Tensão ética |
| Cascade | Diagnosticar, conter e provar | Três metas simples; perdas visíveis no final | Clímax de composição |

<b>Regra editorial:</b> não aumentar automaticamente número de slides ao aprofundar gameplay. Os roteiros sugerem <b>o que o jogador faz no terminal</b>; os slides anteriores dão motivo e missão, e os posteriores mostram efeito, personagem e próximo rastro. Breach Report permanece opcional e fora dos slides.

## The Cascade — substituto da lista operacional na interface

1. <b>DESCUBRA A SITUAÇÃO REAL.</b> Compare fontes, reservas e dívidas; mostre por que Lumen não estava saudável.
2. <b>CONTENHA A CRISE.</b> Interrompa decisões inválidas, preserve settlements essenciais e faça a menor intervenção eficaz.
3. <b>PROVE O QUE MUDOU.</b> Entregue um trace verificável, incluindo perdas que permaneceram.

O verificador ainda valida os dez invariants técnicos e o único desfecho ACCEPTED. Não inserir menu de decisão moral, falha narrativa alternativa nem painel que entrega solução.

# Beats aprovados — duas pistas que alteram a percepção do jogador

<b>Antes do Liquidator:</b> 1 beat com <code>SCOPE: UNBOUND</code> ou autorização insuficiente, mais relatório de risco sobre liquidez; não revelar o efeito líquido da intervenção de Rhea. A decisão do Breaker deve parecer cautelosa e defensável.

<b>Após o bloqueio:</b> <code>UNAUTHORIZED OVERRIDE REJECTED</code> → silêncio → <code>LIQUIDATIONS: 14 → 31 → 78 → 204</code> → um trace recuperado mostra feed inadequado e vendas excessivas → consequência em settlements e Nia. O evento posterior de isolamento com Ilyan permanece separado.

<b>Durante The Cascade:</b> <code>TEMPORARY GUARANTEE LOCKED</code> / <code>PARTICIPATION: BREAKER</code> / <code>RELEASE CONDITION</code>. Depois, sem transformar em presente de Rhea: <code>GUARANTEE PARTIAL RETURN</code> / <code>SENDER WITNESS: RHEA</code> / <code>RECIPIENT WITNESS: BREAKER</code> / <code>DESTINATION: MOONLIGHT</code>. O montante é confidencial por protocolo definido.

<b>Ritmo:</b> dois beats de prova bastam; não acrescentar diálogos longos, nova fase, ou anúncio explícito de traição futura.
</content>
</page>

