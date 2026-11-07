---
notion_id: 4019c563-0425-81fb-b26e-f86004353e0a
source: https://app.notion.com/p/4019c563042581fbb26ef86004353e0a?pvs=204
title: "📊 08 — One-Ledger Average"
exported_at: 2026-11-07
---

# Story

O sistema afirma usar um preço médio para resistir a manipulação.

A configuração do TWAP aceita uma janela de um único ledger.

Na prática, o “average” vira spot price.

# Mission

> **Turn an average into an instant.**

# Canonical Vulnerability

**TWAP Window Too Short — **`twap_window_too_short`**.**

# Learning

- TWAP purpose;
- manipulation resistance depends on window;
- configuration can destroy a security property without changing code;
- safe defaults and lower bounds matter.

# Win Condition

Configurar/usar uma janela mínima que faça o TWAP seguir o preço manipulável de um único ledger.

# Narrative Result

Uma variação extrema deveria acionar o circuit breaker de Lumen.

O threshold está configurado.

O código lê o valor.

Nada acontece.

Unlock:

**CASE 09 — THE BREAKER THAT DIDN'T BREAK**

# Reference

[https://github.com/Veritas-Vaults-Network/soroban-guard-contracts](https://github.com/Veritas-Vaults-Network/soroban-guard-contracts)

## Blueprint de integração v2 — configuração anula a proteção

**Fixture:** série histórica de preços e módulo TWAP com janela configurável; a janela aceita um ledger, resultando em baixa resistência à manipulação da última observação. Definir pesos e o algoritmo de média na fixture.

**Verifier:** TWAP indevidamente segue a distorção de curtíssimo prazo; mirror seguro aplica janela mínima e política de amostragem, produzindo saída divergente sob o mesmo cenário.

**Conexão narrativa:** o movimento anormal deveria cruzar o threshold do circuit breaker e impedir a ação crítica, mas a execução continua.

**Slides:** não chamar a média de insegura por ser “média” em si; apresentar a diferença entre proteção anunciada e janela efetiva.

**QA:** testar séries e boundary de um ledger versus janelas > mínimo, evitando depender de variação temporal não determinística.

## Loop jogável v3 — laboratório de janela temporal (P1)

O foco é **configuração e séries históricas** — distinto de freshness, confidence e de um circuit breaker que não executa.

**1. Investigar:** ver observações de preço em vários ledgers e política TWAP publicada. O jogador pode inspecionar como a janela escolhe observações; fórmula e ponderações precisam estar definidas na fixture.

**2. Formular hipótese:** quando a janela é um ledger, uma distorção momentânea domina a média e rompe a resistência que o protocolo anuncia.

**3. Executar:** usar a configuração mínima aceita pelo contrato e uma série determinística com breve distorção; provar que o TWAP acompanha praticamente o spot naquele momento.

**4. Feedback:** `WINDOW: 1 LEDGER`, valores de spot e TWAP com histórico curto versus janela segura, sem entregar a vulnerabilidade antes da vitória.

**5. Gancho:** o valor extremo deveria acionar controle de preço de execução; registro mostra proteção configurada porém sem pause.

**Diferencial:** **parametrização e cálculo estatístico**, não autorização e não ausência de enforcement.

**QA:** variáveis controladas, médias verificadas, parâmetros boundary; mirror seguro usa janela mínima adequada e rejeita configuração indevida.
