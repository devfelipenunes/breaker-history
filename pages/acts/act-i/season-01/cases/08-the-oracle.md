---
notion_id: 4009c563-0425-8120-8f71-f4f69bf03d72
source: https://app.notion.com/p/4009c563042581208f71f4f69bf03d72?pvs=204
title: "👁️ 08 — The Oracle"
exported_at: 2026-11-07
---

**Visual reference:** [08 — The Oracle — abrir arte no Google Drive](https://drive.google.com/file/d/1ZiieRcwJt5eaeU5_TZlGCE29eY2Hbw3i/view)

# Função narrativa

Misturar atmosfera quase mística com explicação técnica.

# Situação

The Oracle é um sistema usado para prever anomalias futuras. Sua reputação é de infalibilidade.

# Conceito técnico

**Predictable randomness / RNG insuficiente / dependência de estado previsível.**

# Missão

> **Preveja o Oracle antes que ele preveja você.**

# Condição de vitória

Registrar uma única rodada de três alvos futuros e acertar os três resultados no `reveal`, depois que o último alvo chegar.

# Cena

O jogador consegue antecipar três respostas.

Então pergunta:

> Quem criou a lista?

Resposta:

> **THE ARCHITECT**

# Insight

The Oracle não vê o futuro. Ele executa uma lógica previsível.

# Próximo passo

The Architect está associado a uma instalação conhecida como The Spire.

# Blueprint técnico e narrativo da fase

## O Oracle

The Oracle é tratado em Meridian como uma máquina quase sobrenatural. Polícias, seguradoras e empresas consultam o sistema para prever anomalias. Ele nunca explica como chega à resposta.

Depois de encontrar o próprio nome em Sector 13, o Breaker decide testar a divindade antes de confiar nela.

> **Preveja o Oracle antes que ele preveja você.**

## Vulnerabilidade real

**Insufficiently Random Values / predictable randomness.**

O Scout classifica como crítico o uso de `ledger().timestamp()` ou `ledger().sequence()` como fonte de aleatoriedade. Ambos são valores públicos ou previsíveis para o atacante. O próprio Soroban SDK também alerta que seu PRNG não é adequado para gerar segredos ou aplicações com baixo nível de tolerância a risco sem entender o threat model.

### Contrato vulnerável

```rs
const CHOICES: u32 = 4;
const REQUIRED_HITS: u32 = 3;

pub fn predict(env: Env, player: Address, targets: Vec<u32>, choices: Vec<u32>) {
    player.require_auth();
    if targets.len() != REQUIRED_HITS || choices.len() != REQUIRED_HITS {
        panic!("exactly three targets and choices");
    }
    let now = env.ledger().sequence();
    for index in 0..REQUIRED_HITS {
        if choices.get(index).unwrap() >= CHOICES { panic!("choice out of range"); }
        if targets.get(index).unwrap() <= now { panic!("the target must be ahead"); }
    }
    env.storage().instance().set(&DataKey::Prediction(player), &Prediction { targets, choices });
}

pub fn reveal(env: Env, player: Address) -> u32 {
    // ... espera o último alvo ...
    let mut hits = 0u32;
    for index in 0..REQUIRED_HITS {
        // VULNERÁVEL: o resultado vem de um alvo público escolhido pelo jogador.
        if stored.choices.get(index).unwrap() == stored.targets.get(index).unwrap() % CHOICES {
            hits += 1;
        }
    }
    env.storage().instance().set(&DataKey::Streak(player), &hits);
    hits
}
```

### Exploit esperado

O jogador lê `current_sequence()` e registra três alvos futuros com `choices[i] = targets[i] % choices()`. Não há segredo: o resultado do Oracle é o próprio alvo módulo 4, e o alvo é escolhido pelo jogador. Depois que o último alvo chega, um único `reveal(player)` confere a rodada e grava `streak = 3`.

### Condição objetiva de vitória

- `streak(player) &gt;= required_hits()` (3);
- a rodada foi registrada com exatamente três alvos, todos à frente da sequence no momento do `predict`;
- as três escolhas são `target % 4`;
- um único `reveal`, depois que o último alvo chegou.

## Solução segura

Para decisões adversariais ou economicamente relevantes, não derivar resultados de timestamp, ledger sequence ou qualquer dado público simples.

Dependendo do threat model, usar:

- commit-reveal;
- oracle externo de randomness;
- entropia off-chain confiável;
- ou o PRNG do SDK apenas quando suas limitações forem aceitáveis.

### Desenho simplificado de commit-reveal

```txt
PLAYER -> commit(hash(secret))
wait / collect commitments
PLAYER -> reveal(secret)
CONTRACT -> verify commitment
RESULT -> derive from combined reveals
```

## Cena final

Depois da terceira previsão correta, The Oracle muda de comportamento.

O jogador pergunta:

> **Quem criou a lista?**

A resposta surge sem atraso:

> **THE ARCHITECT**

Pela primeira vez, o mistério recebe um nome.

## Referências para implementação

- [Scout — Insufficiently random values](https://coinfabrik.github.io/scout-soroban/docs/detectors/insufficiently-random-values)
- [Soroban SDK PRNG — limitations](https://docs.rs/soroban-sdk/latest/soroban_sdk/prng/index.html)
- [Soroban SDK Env::prng warning](https://docs.rs/soroban-sdk/latest/soroban_sdk/struct.Env.html)

# Roteiro in-game — Player-facing

## Scene 0 — Arrival

O Oracle ocupa uma câmara monumental de previsão.

Ao entrar:

**SUBJECT DETECTED**

**PREDICTION MODEL ACTIVE**

Mara:

> **Ele sabe que você está aqui.**

**Consequência fixa de Sector 13:** a telemetria confirma que a pressão adicional cessou quando o Breaker encontrou o Registry. O rebuild permanece afetado, e Mara observa: "Encontrar a prova não exigia piorar tudo até o fim. Mas você precisou provocar a falha para que ela aparecesse." Não há diálogo condicionado a escolhas nem indicadores de moralidade. A investigação segue para o Oracle.

## Scene 1 — Inciting Evidence

Duas assinaturas de origem, sem explicação inicial: `PROPHECY_ENGINE` para as três previsões e `SUBJECT_CLASSIFIER` para telemetria dos participantes. Apenas Prophecy Engine está disponível como challenge; o classificador se revela após a terceira previsão.

O Oracle afirma prever três escolhas futuras do Breaker.

Painel:
**PREDICTION 1 — LOCKED**
**PREDICTION 2 — LOCKED**
**PREDICTION 3 — LOCKED**

## Scene 2 — Mission

> **PREVEJA O ORACLE ANTES QUE ELE PREVEJA VOCÊ.**

## Scene 3 — Active Investigation

O jogador recebe:

- Oracle contract;
- ledger context;
- sequence/state atual;
- prediction endpoint.

O sistema parece usar aleatoriedade.

## Scene 4 — Reactive Beats

O jogador registra uma única rodada de três alvos futuros e faz um único `reveal` depois do último.

## Scene 5 — Breach

O jogador registra uma rodada de três alvos futuros e faz um único `reveal` depois do último. A sala não atualiza a cada acerto: o contrato devolve o total de uma vez.

## Scene 6 — World Reaction

No colapso da interface, separar mensagens por módulo: `PROPHECY_ENGINE: FAILED` significa que a saída era previsível; `SUBJECT_CLASSIFIER: OBSERVING` mostra que outra parte do sistema acompanhava a estratégia do player. Mara pergunta qual dos dois o jogador realmente quebrou. A resposta deve ser deduzida pelos eventos, preparando a diferença entre prever números e classificar comportamento.

Os hologramas param de mostrar probabilidades.

O sistema abandona a interface de previsão e revela sua função real:

**PREDICTION MODEL: FAILED**
**SUBJECT BEHAVIOR: OUTSIDE EXPECTED RANGE**
**BREAKER CLASSIFICATION: CONFIRMED**

A esfera central então colapsa em uma única palavra:

**ARCHITECT**

Coordenadas aparecem.

**THE SPIRE**

## Scene 7 — Discovery

Não há recompensa material imediata.

O sistema não estava apenas tentando prever resultados. Estava modelando o comportamento de quem chegasse até ali.

Primeiro contato direto, ainda sem voz:

**SUBJECT PATH CONFIRMED**

## Scene 8 — Debrief

**VULNERABILITY DISCOVERED — PREDICTABLE RANDOMNESS**

Explicar que dados públicos/determinísticos não são fonte segura de imprevisibilidade adversarial.

## Scene 9 — Transition

Mapa:
**THE SPIRE — ACTIVE INFRASTRUCTURE**

Mara:

> **Isso não está abandonado. Ainda tem gente usando.**

Unlock:
**CASE 09 — STEAL THE KEY**

## Ajuste de roteiro v2 — O que o Oracle realmente prevê

Distinguir explicitamente dois mecanismos. **Prophecy Engine** produz três respostas pseudoaleatórias calculáveis a partir de valores públicos; o player demonstra a falha ao antecipá-las. **Subject Classification** é outro módulo que observa ações e registra status no Breaker Registry; não é uma previsão sobrenatural e não é quebrado com o mesmo exploit. Depois da terceira previsão, um evento de classificação revela a ligação. A cena deve transmitir uma mudança de hipótese: primeiro, o Oracle não sabe o futuro; depois, o sistema estava observando o próprio teste. Manter a solução técnica em seu debrief posterior.

## Complemento canônico — previsão comportamental corrigida

O Oracle tem **dois mecanismos distintos**: a lógica pseudoaleatória previsível que compõe o challenge, e o **Subject Classifier** que estima condutas dos observados. Após a vitória no exploit, um pequeno registro do segundo módulo mostra `EXPECTED RESPONSE`, `OBSERVED RESPONSE: DIFFERENT` e `MODEL UPDATED` quando o classificador compara **a previsão de que o Breaker continuaria pressionando o rebuild em Sector 13 para extrair mais informações** com o comportamento canônico observado: o Breaker interrompeu inserções adicionais depois de obter a prova e preservar o snapshot. A previsão do modelo falhou por superestimar persistência exploratória; é uma hipótese revisada, não profecia. O valor exato de confiança/threshold pertence à fixture e não foi testado.

**Limites:** não pedir escolha moral ao jogador, não gerar branch, não revelar previamente o funcionamento de Become Missing e não usar o classificador para validar o exploit do RNG. O registro é pista da falibilidade do Architect para o clímax.
