---
notion_id: 4019c563-0425-81c9-82f7-f03cf656caac
source: https://app.notion.com/p/4019c563042581c982f7f03cf656caac?pvs=204
title: "⚠️ BOSS I — The Liquidator"
exported_at: 2026-11-07
---

Here is the result of "fetch" for the Page with URL https://app.notion.com/p/4019c563042581c982f7f03cf656caac as of 2026-11-02T23:59:43.970Z:
<page url="https://app.notion.com/p/4019c563042581c982f7f03cf656caac" icon="⚠️">
<ancestor-path>
<parent-page url="https://app.notion.com/p/4019c56304258155ac29c3ff5333a0af" title="04 — Cases & Bosses"/>
<ancestor-2-page url="https://app.notion.com/p/4019c563042581d9aedad3e5f178c3e8" title="Season 02 — DeFi Wars — Lumen"/>
<ancestor-3-page url="https://app.notion.com/p/4019c563042581469a0edc7e30a6eff9" title="ACT I — The World Is Breakable"/>
<ancestor-4-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
<properties>
{"title":"BOSS I — The Liquidator"}
</properties>
<iconMetadata>{"type":"emoji","emoji":"⚠️"}</iconMetadata>
<content>
<callout icon="⚠️" color="red_bg">
<b>Sem vulnerabilidade nova. Boss de composição.</b>
</callout>

# História

Rhea tenta ativar uma intervenção não autorizada no Liquidation Engine.

O Breaker possui dois motivos verificáveis para impedir a intervenção: a capability não vincula estritamente todas as operações pretendidas, e um relatório parcial de risco projeta custos de liquidez do override. Ele não dispõe ainda de uma visão agregada das liquidações alimentadas por feeds inadequados; sua análise é racional, mas incompleta.

# Missão

> <b>Impeça a intervenção não autorizada.</b>

# Sistemas

- Oracle freshness;
- confidence;
- AMM liquidity;
- Vault share state;
- liquidation thresholds.

# Gameplay

O jogador reconstrói por que o Liquidator pretende agir e bloqueia a sequência de Rhea sem receber o nome de nenhuma vulnerabilidade.

Ele consegue.

SYSTEM RESTORED<br />UNAUTHORIZED OVERRIDE REJECTED

Por alguns segundos, tudo parece normal.

Então:

LIQUIDATIONS: 14<br />31<br />78<br />204

Liquidity Gardens perde fluxo.

A Lumen Reserve mostra a primeira fissura.

Rhea envia:

> <b>“Você me impediu. Parabéns.”</b>

Os efeitos deixam de ser abstratos:

- settlements travam;
- payrolls atrasam;
- market makers menores perdem posições;
- Nia Kade aparece em um feed da Network Wire;
- Ilyan Marr começa a desmontar posições para sobreviver.

## O custo do isolamento

Depois da onda de liquidações e antes da conversa com Mara, Rhea executa uma contenção distinta da intervenção que o Breaker bloqueou: isola um segmento menor para impedir o contágio dos outros seis.

O jogador vê os seis mercados estabilizarem enquanto o segmento isolado perde acesso à liquidez. A posição de Ilyan é destruída; outras pessoas também absorvem perdas. Mostrar o antes e o depois, sem tratar essas pessoas apenas como números.

Breaker:

> <b>“Você salvou seis mercados.”</b>

Rhea:

> <b>“Sim.”</b>

Breaker:

> <b>“E matou o sétimo.”</b>

Rhea:

> <b>“Sim.”</b>

Ela assume a escolha, sem comemorar. Ilyan compreende a contenção e não a perdoa. Isso prepara sua decisão de ajudar Lumen em The Cascade.

## Mara — A consequência da escolha

Mara aparece por um canal privado.

> <b>“Quebrar o procedimento foi uma escolha minha. O custo foi meu.”</b>

> <b>“Se você vai fazer o mesmo, descubra antes quem vai pagar o custo da sua escolha.”</b>

# Revelação

O jogador não salvou o sistema.

Restaurou a regra que estava alimentando o colapso.

Layer II deixa de ser abstrato.

Rhea continua inimiga.

Agora o Breaker sabe apenas que ela estava tentando impedir alguma coisa maior.

Unlock:

<b>CASE 05 — THE TOKEN THAT ARRIVED SHORT</b>

## Blueprint de integração v2 — primeiro boss sistêmico

<b>Pré-condição:</b> feed stale/confidence problemático, pouca liquidez AMM, share accounting distorcido e thresholds de liquidation. O player deve avaliar contratos <b>sem nome de bug</b> e bloquear tecnicamente a intervenção não autorizada de Rhea.

<b>Confronto principal:</b> vitória verificada = bloqueio do override, não restauração econômica da cidade. Exibir <code>SYSTEM RESTORED</code> → silêncio → <code>LIQUIDATIONS: 14 → 31 → 78 → 204</code>, settlement afetado e primeira fissura da Reserve.

<b>Prova de causalidade:</b> simular com estado inicial idêntico a execução <i>bloqueada</i> (canônica) e a <i>permitida</i> (contrafactual), demonstrando por que bloquear o override agrava liquidation. O contrafactual não é opção jogável nem final alternativo.

<b>Separar dois eventos de Rhea:</b> (1) intervenção no Liquidator bloqueada pelo Breaker; (2) contenção posterior em outro mecanismo: seis mercados protegidos, um isolado, perda de Ilyan. Não fundir esses eventos.

<b>Custo humano:</b> atraso de payroll de Nia e posição de Ilyan devem ser rastreáveis em snapshots. Mara pergunta quem paga a conta; não concede legitimidade.

<b>QA:</b> Boss usa conceitos 01–04 sem novo exploit; jogadores percebem por que vencer o contrato não salvou o sistema. <mention url="https://app.notion.com/p/40c9c5630425811da9bdc67cf66b2410" />.

## Revisão crítica v3 — vitória técnica e desastre economicamente demonstrável (P0)

<b>Perigo de design:</b> o jogador não pode sentir que o roteiro o puniu arbitrariamente por vencer. Criar uma <b>prova causal</b> com dados suficientes para reconstruir depois como o bloqueio do override restabeleceu uma cadeia de decisões inseguras.

<b>Modelo de fixture a especificar e testar:</b> intervenção emergencial limitada de Rhea tentava <b>suspender/quarentenar decisões de liquidação alimentadas por dados de qualidade insuficiente</b>. Isso é uma <b>hipótese de implementação</b>, não novo acontecimento canônico aprovado. Validar no código se é coerente com o Emergency Dispatcher de Case 10 e com os efeitos nas reservas/AMM.

<b>Loop do jogador:</b> (a) inspecionar a autorização da intervenção de Rhea; (b) identificar que ela não foi autorizada; (c) demonstrar bloqueio por mecanismo existente aprendido nos Cases 01–04 — <b>sem vulnerabilidade inédita</b>; (d) observar <code>UNAUTHORIZED OVERRIDE REJECTED</code>; (e) abrir evento de liquidações para investigar a consequência.

<b>Comparação contrafactual:</b> dois replays com mesma seed, preços, liquidez e regras; diferem só pela intervenção bloqueada/permitida. Registrar decisões, filas e delta de liquidez. Após vitória, mostrar <code>14 → 31 → 78 → 204</code> e a primeira fissura da Reserve; permitir que o jogador consulte o trace sem um sermão.

<b>Não confundir intervenções:</b> a ação bloqueada no Liquidator é um evento; o isolamento posterior que protege seis segmentos e prejudica Ilyan é <b>outro evento</b> com outra trilha. Nia sente atrasos de payroll.

<b>Verificador:</b> prova o bloqueio do override não autorizado; o resultado econômico canônico é aplicado depois como consequência. Playtester deve conseguir responder “por que a cidade piorou?” apontando pelo menos uma dependência concreta, mesmo que não concorde com Rhea.

<b>Ritmo dos slides:</b> vitória → 1 beat de silêncio → contador de liquidations → Reserve fissura → fala “Você me impediu. Parabéns.”; não revelar a cadeia inteira antes de o player observar o efeito.

## Versão canônica aprovada — o bloqueio racional e a contenção incompleta (seleções 04–05)

<b>Motivo defensável do Breaker:</b> uma capability emergencial solicita operações fora do escopo formal e um relatório de risco mostra que suspender ou limitar liquidações pode comprometer liquidez normal. Esse relatório é tecnicamente verdadeiro no seu recorte, <b>mas não inclui</b> novas liquidações sobre preços sem freshness/confidence e slippage endógeno de pools rasos. O Breaker não precisa agir irracionalmente: ele escolhe preservar autorização e os dados parciais.

<b>Intervenção única de Rhea:</b> dois parâmetros da mesma estratégia temporária: (1) colocar em quarentena decisões de liquidation alimentadas por price reports que violam política; (2) limitar o lote de liquidações por ledger/janela para não despejar garantias em baixa liquidez. Mesmo tecnicamente plausível, Rhea não tinha autorização adequada para executar a alteração.

<b>Consequência:</b> bloqueio comprovado → <code>UNAUTHORIZED OVERRIDE REJECTED</code> → motor normal continua com premissas deficientes → 14 → 31 → 78 → 204 liquidações → queda de profundidade e settlement atrasado. Depois disso, <b>separadamente</b>, Rhea isola um dos sete mercados e a posição de Ilyan é destruída.

<b>Teste P0:</b> comparar exatamente o mesmo estado, preços, reservas, saques e seed em dois replays; diferir apenas a tentativa bloqueada versus permitida. Incluir no trace risk report original, campos de autorização, lote e condição de qualidade do feed. O contrafactual não é um ramo jogável nem prova que Rhea resolveria tudo. Se a fixture não confirmar efeito econômico, ajustar a parametrização e não declarar a causalidade demonstrada.
</content>
</page>

