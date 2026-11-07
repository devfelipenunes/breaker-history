---
notion_id: 4019c563-0425-815e-a749-f6cd17dbf305
source: https://app.notion.com/p/4019c5630425815ea749f6cd17dbf305?pvs=204
title: "📡 02 — False Confidence"
exported_at: 2026-11-07
---

# Story

O Oracle não publica apenas preço.

Publica também o grau de confiança daquele preço.

O protocolo de risco de Lumen usa o número e ignora a incerteza.

# Mission

> **Make an uncertain price behave like a certain one.**

# Canonical Vulnerability

**Oracle Confidence Ignored — **`oracle_confidence_ignored`**.**

Um preço de baixa confiança é usado para collateral valuation e liquidation como se tivesse a mesma qualidade de um preço estável.

# Learning

- data feeds have quality, not only value;
- confidence intervals matter;
- liquidation thresholds must account for uncertainty;
- oracle consumption is a risk model, not just a getter.

# Win Condition

Forçar uma liquidation utilizando um preço cuja confidence deveria impedir a ação.

# Narrative Result

O Breaker encontra transações de Rhea próximas às posições vulneráveis.

Mas uma coisa não fecha:

ela não está lucrando.

Ela está reduzindo exposição.

Antes que ele consiga entender por quê, uma grande swap drena profundidade de um pool.

Unlock:

**CASE 03 — THE DRY POOL**

# Reference

[https://github.com/Veritas-Vaults-Network/soroban-guard-contracts](https://github.com/Veritas-Vaults-Network/soroban-guard-contracts)

## Blueprint de integração v2 — Confidence ≠ Freshness

**Fixture a implementar:** feed recente com intervalo/medida de incerteza definida e consumer que usa apenas o valor central para collateral/liquidation. Fixar no challenge a interpretação exata de confidence (unidades/escala) para evitar leitura ambígua.

**Verificador:** prova que a liquidation ocorre apesar de confidence fora da política, enquanto o mirror seguro bloqueia a operação ou aplica política conservadora previamente documentada. Não reutilizar stale como causa do sucesso.

**Conexão narrativa:** o registro de Rhea mostra redução de exposição, sem ganho demonstrado; a próxima evidência é uma swap grande afetando profundidade nos Liquidity Gardens. Suspeita é hipótese, não prova de autoria.

**Slides:** exibir valor semelhante com qualidade diferente; só depois mostrar a fragilidade. Debrief nomeia o uso indevido do confidence.

**QA:** jogadores distinguem preços antigos de preços presentes porém incertos; testes positivos/negativos de threshold e boundary.

## Loop jogável v3 — comparação da qualidade dos dados (prioridade P1)

Especificação de gameplay; sem alterar vulnerabilidade nem resultado narrativo.

**1. Investigar:** mostrar dois reports de preço recentes, com preço semelhante, mas intervalos/medidas de confidence diferentes. O jogador verifica a política de risco do consumidor. A unidade e semântica de confidence devem ser definidas na fixture.

**2. Formular hipótese:** um valor atual não é necessariamente adequado para liquidação quando sua incerteza ultrapassa limites.

**3. Executar:** usar o report de baixa confiança para reproduzir liquidation que deveria ser impedida pela política segura; não recorrer a feed stale, que pertence ao Case 01.

**4. Feedback:** mostrar `PRICE AGE: OK` e `CONFIDENCE: OUT OF POLICY` junto ao resultado de risco. O mirror de segurança rejeita ou aplica fallback conservador definido antecipadamente.

**5. Próximo motivo:** histórico de Rhea indica redução de risco, não lucro; uma swap grande afeta a profundidade do pool no Liquidity Gardens.

**Distinção:** investigação por **qualidade de fonte e política de risco**, não idade de dados.

**QA:** testar confidence perto do threshold, amostra segura e amostra insegura; playtester explica diferença entre Case 01 e Case 02.
