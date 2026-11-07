---
notion_id: 4009c563-0425-8120-8f71-f4f69bf03d72
source: https://app.notion.com/p/4009c563042581208f71f4f69bf03d72?pvs=204
title: "👁️ 08 — The Oracle"
exported_at: 2026-11-07
---

Here is the result of "fetch" for the Page with URL https://app.notion.com/p/4009c563042581208f71f4f69bf03d72 as of 2026-11-04T15:35:23.001Z:
<page url="https://app.notion.com/p/4009c563042581208f71f4f69bf03d72" icon="👁️">
<ancestor-path>
<parent-page url="https://app.notion.com/p/4019c563042581fd9124e5ee36b3e82f" title="03 — Cases & Bosses"/>
<ancestor-2-page url="https://app.notion.com/p/4009c563042581359693d42f09d41062" title="Season 01 — The First Layer"/>
<ancestor-3-page url="https://app.notion.com/p/4019c563042581469a0edc7e30a6eff9" title="ACT I — The World Is Breakable"/>
<ancestor-4-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
<properties>
{"title":"08 — The Oracle"}
</properties>
<iconMetadata>{"type":"emoji","emoji":"👁️"}</iconMetadata>
<content>
<callout icon="🎨" color="gray_bg">
<b>Visual reference:</b> [08 — The Oracle — abrir arte no Google Drive](https://drive.google.com/file/d/1ZiieRcwJt5eaeU5_TZlGCE29eY2Hbw3i/view)
</callout>

# Função narrativa

Misturar atmosfera quase mística com explicação técnica.

# Situação

The Oracle é um sistema usado para prever anomalias futuras. Sua reputação é de infalibilidade.

# Conceito técnico

<b>Predictable randomness / RNG insuficiente / dependência de estado previsível.</b>

# Missão

> <b>Preveja o Oracle antes que ele preveja você.</b>

# Condição de vitória

Registrar uma única rodada de três alvos futuros e acertar os três resultados no <code>reveal</code>, depois que o último alvo chegar.

# Cena

O jogador consegue antecipar três respostas.

Então pergunta:

> Quem criou a lista?

Resposta:

> <b>THE ARCHITECT</b>

# Insight

The Oracle não vê o futuro. Ele executa uma lógica previsível.

# Próximo passo

The Architect está associado a uma instalação conhecida como The Spire.

# Blueprint técnico e narrativo da fase

## O Oracle

The Oracle é tratado em Meridian como uma máquina quase sobrenatural. Polícias, seguradoras e empresas consultam o sistema para prever anomalias. Ele nunca explica como chega à resposta.

Depois de encontrar o próprio nome em Sector 13, o Breaker decide testar a divindade antes de confiar nela.

> <b>Preveja o Oracle antes que ele preveja você.</b>

## Vulnerabilidade real

<b>Insufficiently Random Values / predictable randomness.</b>

O Scout classifica como crítico o uso de <code>ledger().timestamp()</code> ou <code>ledger().sequence()</code> como fonte de aleatoriedade. Ambos são valores públicos ou previsíveis para o atacante. O próprio Soroban SDK também alerta que seu PRNG não é adequado para gerar segredos ou aplicações com baixo nível de tolerância a risco sem entender o threat model.

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

O jogador lê <code>current_sequence()</code> e registra três alvos futuros com <code>choices[i] = targets[i] % choices()</code>. Não há segredo: o resultado do Oracle é o próprio alvo módulo 4, e o alvo é escolhido pelo jogador. Depois que o último alvo chega, um único <code>reveal(player)</code> confere a rodada e grava <code>streak = 3</code>.

### Condição objetiva de vitória

- <code>streak(player) &gt;= required_hits()</code> (3);
- a rodada foi registrada com exatamente três alvos, todos à frente da sequence no momento do <code>predict</code>;
- as três escolhas são <code>target % 4</code>;
- um único <code>reveal</code>, depois que o último alvo chegou.

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

> <b>Quem criou a lista?</b>

A resposta surge sem atraso:

> <b>THE ARCHITECT</b>

Pela primeira vez, o mistério recebe um nome.

## Referências para implementação

- [Scout — Insufficiently random values](https://coinfabrik.github.io/scout-soroban/docs/detectors/insufficiently-random-values)
- [Soroban SDK PRNG — limitations](https://docs.rs/soroban-sdk/latest/soroban_sdk/prng/index.html)
- [Soroban SDK Env::prng warning](https://docs.rs/soroban-sdk/latest/soroban_sdk/struct.Env.html)

# Roteiro in-game — Player-facing

## Scene 0 — Arrival

O Oracle ocupa uma câmara monumental de previsão.

Ao entrar:

<b>SUBJECT DETECTED</b>

<b>PREDICTION MODEL ACTIVE</b>

Mara:

> <b>Ele sabe que você está aqui.</b>

<b>Consequência fixa de Sector 13:</b> a telemetria confirma que a pressão adicional cessou quando o Breaker encontrou o Registry. O rebuild permanece afetado, e Mara observa: "Encontrar a prova não exigia piorar tudo até o fim. Mas você precisou provocar a falha para que ela aparecesse." Não há diálogo condicionado a escolhas nem indicadores de moralidade. A investigação segue para o Oracle.

## Scene 1 — Inciting Evidence

Duas assinaturas de origem, sem explicação inicial: <code>PROPHECY_ENGINE</code> para as três previsões e <code>SUBJECT_CLASSIFIER</code> para telemetria dos participantes. Apenas Prophecy Engine está disponível como challenge; o classificador se revela após a terceira previsão.

O Oracle afirma prever três escolhas futuras do Breaker.

Painel:<br /><b>PREDICTION 1 — LOCKED</b><br /><b>PREDICTION 2 — LOCKED</b><br /><b>PREDICTION 3 — LOCKED</b>

## Scene 2 — Mission

> <b>PREVEJA O ORACLE ANTES QUE ELE PREVEJA VOCÊ.</b>

## Scene 3 — Active Investigation

O jogador recebe:

- Oracle contract;
- ledger context;
- sequence/state atual;
- prediction endpoint.

O sistema parece usar aleatoriedade.

## Scene 4 — Reactive Beats

O jogador registra uma única rodada de três alvos futuros e faz um único <code>reveal</code> depois do último.

## Scene 5 — Breach

O jogador registra uma rodada de três alvos futuros e faz um único <code>reveal</code> depois do último. A sala não atualiza a cada acerto: o contrato devolve o total de uma vez.

## Scene 6 — World Reaction

No colapso da interface, separar mensagens por módulo: <code>PROPHECY_ENGINE: FAILED</code> significa que a saída era previsível; <code>SUBJECT_CLASSIFIER: OBSERVING</code> mostra que outra parte do sistema acompanhava a estratégia do player. Mara pergunta qual dos dois o jogador realmente quebrou. A resposta deve ser deduzida pelos eventos, preparando a diferença entre prever números e classificar comportamento.

Os hologramas param de mostrar probabilidades.

O sistema abandona a interface de previsão e revela sua função real:

<b>PREDICTION MODEL: FAILED</b><br /><b>SUBJECT BEHAVIOR: OUTSIDE EXPECTED RANGE</b><br /><b>BREAKER CLASSIFICATION: CONFIRMED</b>

A esfera central então colapsa em uma única palavra:

<b>ARCHITECT</b>

Coordenadas aparecem.

<b>THE SPIRE</b>

## Scene 7 — Discovery

Não há recompensa material imediata.

O sistema não estava apenas tentando prever resultados. Estava modelando o comportamento de quem chegasse até ali.

Primeiro contato direto, ainda sem voz:

<b>SUBJECT PATH CONFIRMED</b>

## Scene 8 — Debrief

<b>VULNERABILITY DISCOVERED — PREDICTABLE RANDOMNESS</b>

Explicar que dados públicos/determinísticos não são fonte segura de imprevisibilidade adversarial.

## Scene 9 — Transition

Mapa:<br /><b>THE SPIRE — ACTIVE INFRASTRUCTURE</b>

Mara:

> <b>Isso não está abandonado. Ainda tem gente usando.</b>

Unlock:<br /><b>CASE 09 — STEAL THE KEY</b>

## Ajuste de roteiro v2 — O que o Oracle realmente prevê

Distinguir explicitamente dois mecanismos. <b>Prophecy Engine</b> produz três respostas pseudoaleatórias calculáveis a partir de valores públicos; o player demonstra a falha ao antecipá-las. <b>Subject Classification</b> é outro módulo que observa ações e registra status no Breaker Registry; não é uma previsão sobrenatural e não é quebrado com o mesmo exploit. Depois da terceira previsão, um evento de classificação revela a ligação. A cena deve transmitir uma mudança de hipótese: primeiro, o Oracle não sabe o futuro; depois, o sistema estava observando o próprio teste. Manter a solução técnica em seu debrief posterior.

## Complemento canônico — previsão comportamental corrigida

O Oracle tem <b>dois mecanismos distintos</b>: a lógica pseudoaleatória previsível que compõe o challenge, e o <b>Subject Classifier</b> que estima condutas dos observados. Após a vitória no exploit, um pequeno registro do segundo módulo mostra <code>EXPECTED RESPONSE</code>, <code>OBSERVED RESPONSE: DIFFERENT</code> e <code>MODEL UPDATED</code> quando o classificador compara <b>a previsão de que o Breaker continuaria pressionando o rebuild em Sector 13 para extrair mais informações</b> com o comportamento canônico observado: o Breaker interrompeu inserções adicionais depois de obter a prova e preservar o snapshot. A previsão do modelo falhou por superestimar persistência exploratória; é uma hipótese revisada, não profecia. O valor exato de confiança/threshold pertence à fixture e não foi testado.

<b>Limites:</b> não pedir escolha moral ao jogador, não gerar branch, não revelar previamente o funcionamento de Become Missing e não usar o classificador para validar o exploit do RNG. O registro é pista da falibilidade do Architect para o clímax.
</content>
</page>

