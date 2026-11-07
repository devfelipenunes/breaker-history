---
notion_id: 4019c563-0425-81c9-82f7-f03cf656caac
source: https://app.notion.com/p/4019c563042581c982f7f03cf656caac?pvs=204
title: "⚠️ BOSS I — The Liquidator"
exported_at: 2026-11-07
---

**Sem vulnerabilidade nova. Boss de composição.**

# História

Rhea tenta ativar uma intervenção não autorizada no Liquidation Engine.

O Breaker possui dois motivos verificáveis para impedir a intervenção: a capability não vincula estritamente todas as operações pretendidas, e um relatório parcial de risco projeta custos de liquidez do override. Ele não dispõe ainda de uma visão agregada das liquidações alimentadas por feeds inadequados; sua análise é racional, mas incompleta.

# Missão

> **Impeça a intervenção não autorizada.**

# Sistemas

- Oracle freshness;
- confidence;
- AMM liquidity;
- Vault share state;
- liquidation thresholds.

# Gameplay

O jogador reconstrói por que o Liquidator pretende agir e bloqueia a sequência de Rhea sem receber o nome de nenhuma vulnerabilidade.

Ele consegue.

SYSTEM RESTORED
UNAUTHORIZED OVERRIDE REJECTED

Por alguns segundos, tudo parece normal.

Então:

LIQUIDATIONS: 14
31
78
204

Liquidity Gardens perde fluxo.

A Lumen Reserve mostra a primeira fissura.

Rhea envia:

> **“Você me impediu. Parabéns.”**

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

> **“Você salvou seis mercados.”**

Rhea:

> **“Sim.”**

Breaker:

> **“E matou o sétimo.”**

Rhea:

> **“Sim.”**

Ela assume a escolha, sem comemorar. Ilyan compreende a contenção e não a perdoa. Isso prepara sua decisão de ajudar Lumen em The Cascade.

## Mara — A consequência da escolha

Mara aparece por um canal privado.

> **“Quebrar o procedimento foi uma escolha minha. O custo foi meu.”**

> **“Se você vai fazer o mesmo, descubra antes quem vai pagar o custo da sua escolha.”**

# Revelação

O jogador não salvou o sistema.

Restaurou a regra que estava alimentando o colapso.

Layer II deixa de ser abstrato.

Rhea continua inimiga.

Agora o Breaker sabe apenas que ela estava tentando impedir alguma coisa maior.

Unlock:

**CASE 05 — THE TOKEN THAT ARRIVED SHORT**

## Blueprint de integração v2 — primeiro boss sistêmico

**Pré-condição:** feed stale/confidence problemático, pouca liquidez AMM, share accounting distorcido e thresholds de liquidation. O player deve avaliar contratos **sem nome de bug** e bloquear tecnicamente a intervenção não autorizada de Rhea.

**Confronto principal:** vitória verificada = bloqueio do override, não restauração econômica da cidade. Exibir `SYSTEM RESTORED` → silêncio → `LIQUIDATIONS: 14 → 31 → 78 → 204`, settlement afetado e primeira fissura da Reserve.

**Prova de causalidade:** simular com estado inicial idêntico a execução *bloqueada* (canônica) e a *permitida* (contrafactual), demonstrando por que bloquear o override agrava liquidation. O contrafactual não é opção jogável nem final alternativo.

**Separar dois eventos de Rhea:** (1) intervenção no Liquidator bloqueada pelo Breaker; (2) contenção posterior em outro mecanismo: seis mercados protegidos, um isolado, perda de Ilyan. Não fundir esses eventos.

**Custo humano:** atraso de payroll de Nia e posição de Ilyan devem ser rastreáveis em snapshots. Mara pergunta quem paga a conta; não concede legitimidade.

**QA:** Boss usa conceitos 01–04 sem novo exploit; jogadores percebem por que vencer o contrato não salvou o sistema. [09 — The Cascade & Liquidator — Blueprint Técnico](../world/09-the-cascade-liquidator-blueprint-tecnico.md).

## Revisão crítica v3 — vitória técnica e desastre economicamente demonstrável (P0)

**Perigo de design:** o jogador não pode sentir que o roteiro o puniu arbitrariamente por vencer. Criar uma **prova causal** com dados suficientes para reconstruir depois como o bloqueio do override restabeleceu uma cadeia de decisões inseguras.

**Modelo de fixture a especificar e testar:** intervenção emergencial limitada de Rhea tentava **suspender/quarentenar decisões de liquidação alimentadas por dados de qualidade insuficiente**. Isso é uma **hipótese de implementação**, não novo acontecimento canônico aprovado. Validar no código se é coerente com o Emergency Dispatcher de Case 10 e com os efeitos nas reservas/AMM.

**Loop do jogador:** (a) inspecionar a autorização da intervenção de Rhea; (b) identificar que ela não foi autorizada; (c) demonstrar bloqueio por mecanismo existente aprendido nos Cases 01–04 — **sem vulnerabilidade inédita**; (d) observar `UNAUTHORIZED OVERRIDE REJECTED`; (e) abrir evento de liquidações para investigar a consequência.

**Comparação contrafactual:** dois replays com mesma seed, preços, liquidez e regras; diferem só pela intervenção bloqueada/permitida. Registrar decisões, filas e delta de liquidez. Após vitória, mostrar `14 → 31 → 78 → 204` e a primeira fissura da Reserve; permitir que o jogador consulte o trace sem um sermão.

**Não confundir intervenções:** a ação bloqueada no Liquidator é um evento; o isolamento posterior que protege seis segmentos e prejudica Ilyan é **outro evento** com outra trilha. Nia sente atrasos de payroll.

**Verificador:** prova o bloqueio do override não autorizado; o resultado econômico canônico é aplicado depois como consequência. Playtester deve conseguir responder “por que a cidade piorou?” apontando pelo menos uma dependência concreta, mesmo que não concorde com Rhea.

**Ritmo dos slides:** vitória → 1 beat de silêncio → contador de liquidations → Reserve fissura → fala “Você me impediu. Parabéns.”; não revelar a cadeia inteira antes de o player observar o efeito.

## Versão canônica aprovada — o bloqueio racional e a contenção incompleta (seleções 04–05)

**Motivo defensável do Breaker:** uma capability emergencial solicita operações fora do escopo formal e um relatório de risco mostra que suspender ou limitar liquidações pode comprometer liquidez normal. Esse relatório é tecnicamente verdadeiro no seu recorte, **mas não inclui** novas liquidações sobre preços sem freshness/confidence e slippage endógeno de pools rasos. O Breaker não precisa agir irracionalmente: ele escolhe preservar autorização e os dados parciais.

**Intervenção única de Rhea:** dois parâmetros da mesma estratégia temporária: (1) colocar em quarentena decisões de liquidation alimentadas por price reports que violam política; (2) limitar o lote de liquidações por ledger/janela para não despejar garantias em baixa liquidez. Mesmo tecnicamente plausível, Rhea não tinha autorização adequada para executar a alteração.

**Consequência:** bloqueio comprovado → `UNAUTHORIZED OVERRIDE REJECTED` → motor normal continua com premissas deficientes → 14 → 31 → 78 → 204 liquidações → queda de profundidade e settlement atrasado. Depois disso, **separadamente**, Rhea isola um dos sete mercados e a posição de Ilyan é destruída.

**Teste P0:** comparar exatamente o mesmo estado, preços, reservas, saques e seed em dois replays; diferir apenas a tentativa bloqueada versus permitida. Incluir no trace risk report original, campos de autorização, lote e condição de qualidade do feed. O contrafactual não é um ramo jogável nem prova que Rhea resolveria tudo. Se a fixture não confirmar efeito econômico, ajustar a parametrização e não declarar a causalidade demonstrada.
