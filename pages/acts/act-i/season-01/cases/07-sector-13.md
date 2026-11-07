---
notion_id: 4009c563-0425-8134-a525-e38dc0eba08b
source: https://app.notion.com/p/4009c56304258134a525e38dc0eba08b?pvs=204
title: "☣️ 07 — Sector 13"
exported_at: 2026-11-07
---

**Visual reference:** [07 — Sector 13 — abrir arte no Google Drive](https://drive.google.com/file/d/13-B3F6yTtB3qIqmN0jV_Mqz4n5deUhMO/view)

# Função narrativa

Ser o grande ponto de inversão da Season.

Até aqui, o jogador acredita que está seguindo Aren Voss.

Em Sector 13 ele descobre que **também está sendo seguido**.

# Situação

Sector 13 abriga um Archive antigo. Milhares de registros inúteis estão sendo criados continuamente. Por trás da saturação existem dados ocultos.

# Conceito técnico

**Contador divergente do armazenamento: entradas duplicadas inflam o contador sem crescer o Archive.**

# Missão

> **Quebre o Archive.**

# Condição de vitória

Levar o contador a 500 sem armazenar 500 registros únicos e obter o snapshot — provando que o limite é medido pela contagem, não pelo conteúdo.

# Revelação

Quando a camada de ruído cai, o jogador encontra uma lista.

Todos os registros pertencem a Breakers. Alguns estão mortos. Alguns desaparecidos. Uma entrada mascarada possui status **ACCEPTED**. Aren Voss aparece como **REFUSED**.

E a entrada mais recente é o próprio jogador:

> **SUBJECT: PLAYER — ACTIVE**

O contraste entre **ACCEPTED**, **REFUSED** e **ACTIVE** deve parecer importante sem ser explicado ainda.

# Próximo passo

A lista inclui referências a uma entidade chamada **The Oracle**.

# Blueprint técnico e narrativo da fase

## Sector 13

Sector 13 parece um cemitério de dados. O Archive local está abarrotado de registros irrelevantes, identidades descartáveis e entradas repetidas.

Voss percebeu que aquilo não era lixo aleatório. O ruído foi criado para tornar uma operação central do Archive impossível.

> **Quebre o Archive. Depois veja o que ele estava escondendo.**

## Vulnerabilidade real

**Contador e armazenamento medem coisas diferentes (**`count`** vs **`stored`**).**

`add_records` percorre o lote e incrementa `count` para **cada** elemento recebido; o Archive só guarda registros únicos num `Map`, e `stored()` devolve o tamanho do vetor de únicos. Enviar o mesmo `BytesN&lt;32&gt;` 500 vezes produz `count() == 500` e `stored() == 1`. `snapshot()` só olha o contador: ao atingir o limite, libera a lista.

### Contrato vulnerável

```rs
pub fn add_records(env: Env, records: Vec<BytesN<32>>) {
    let mut all: Vec<BytesN<32>> = /* registros únicos já guardados */;
    let mut unique: Map<BytesN<32>, bool> = /* índice de únicos */;
    let mut count: u32 = /* contador */;

    for record in records.iter() {
        count = count.saturating_add(1); // VULNERÁVEL: conta toda entrada
        if !unique.contains_key(record.clone()) {
            unique.set(record.clone(), true);
            all.push_back(record);
        }
    }

    // count pode chegar a 500 com all.len() == 1
}
```

### Exploit esperado

O jogador envia um lote com o mesmo registro repetido 500 vezes. `count()` chega a 500; `stored()` permanece 1. `snapshot()` deixa de recusar por “archive intacto” e devolve a lista, marcando `revealed = true`. Nenhuma operação de rebuild ou serviço externo participa do caminho.

### Condição objetiva de vitória

- `count() &gt;= threshold()` (500);
- `stored() &lt; threshold()` — o Archive não cresceu de verdade;
- `revealed() == true`;
- `snapshot()` devolve `AREN VOSS // REFUSED` e `SUBJECT: PLAYER // STATUS: ACTIVE`.

Um Archive com 500 registros únicos e `stored() == 500` **não** passa: o validador exige a divergência.

## Solução segura

O contador só deve crescer quando o armazenamento cresce. A correção é incrementar dentro do ramo que insere um registro novo:

```rs
for record in records.iter() {
    if !unique.contains_key(record.clone()) {
        unique.set(record.clone(), true);
        all.push_back(record);
        count += 1; // conta o que foi realmente armazenado
    }
}
```

Se o limite for uma política de capacidade, que ele seja verificado explicitamente antes de aceitar o lote — e não inferido de um contador que pode ser inflado.

## Revelação

O snapshot devolvido por `snapshot()` contém a lista de Breakers observados pela First Layer. Ele é liberado quando o contador atinge o limite, mesmo que o Archive tenha armazenado um único registro.

Alguns: **DECEASED**. Outros: **MISSING**. Voss: **REFUSED**.

A última entrada foi criada recentemente:

> **SUBJECT: PLAYER**
**STATUS: ACTIVE**

Agora o jogador sabe que sua chegada não passou despercebida.

A entrada do player foi criada **durante a própria investigação**. Isso prova que o registry continua ativo e transforma o tom da campanha: o jogador não está apenas descobrindo um sistema antigo; alguma coisa ainda está observando quem consegue atravessá-lo.

A palavra **REFUSED** também cria a nova pergunta central:

> **O que Voss recusou?**

## Referências para implementação

- [Scout — DoS unexpected revert with vector](https://coinfabrik.github.io/scout-soroban/docs/detectors/dos-unexpected-revert-with-vector)
- [Scout — DoS unbounded operation](https://coinfabrik.github.io/scout-soroban/docs/detectors/dos-unbounded-operation)
- [Stellar Docs — storage granularity](https://developers.stellar.org/docs/learn/fundamentals/contract-development/storage/persisting-data)
- [Soroban Guard — unbounded\_loop and storage vulnerabilities](https://github.com/Veritas-Vaults-Network/soroban-guard-contracts)

# Roteiro in-game — Player-facing

Sector 13 é o ponto de virada da Season: até aqui o jogador acredita que está seguindo Voss; aqui descobre que também está sendo observado.

## Scene 0 — Arrival

O jogador encontra Sector 13 fora dos mapas oficiais.

A arquitetura é um cemitério de dados ainda em operação.

Painel central:
**ARCHIVE LOAD: CRITICAL**

## Scene 1 — Inciting Evidence

Pista opcional de fair play antes do exploit: `UNIQUE RECORDS: DEDUPLICATED` e `COUNTER: EVERY ENTRY`. Não revelar `Breaker Registry`. O player poderá depois entender por que o contador cresceu sem o Archive crescer.

Voss deixou uma única instrução:

> **Quebre o Archive.**

Evidence:

- storage growth;
- rebuild history;
- recovery snapshot policy;
- milhões de entradas irrelevantes.

## Scene 2 — Mission

> **QUEBRE O ARCHIVE. VEJA O QUE ELE ESTÁ ESCONDENDO.**

## Scene 3 — Active Investigation

O jogador pode inserir registros e observar custo/uso crescer.

Terminal:
**RECORD COUNT**
**STORED RECORDS**
**THRESHOLD**

Nenhuma menção explícita a DoS antes da resolução.

## Scene 4 — Reactive Beats

Conforme o Archive recebe lotes:

**RECORD COUNT ↑**
**STORED RECORDS: 1**

Mara:

> **Você está piorando tudo.**

Breaker:

> **Esse é o objetivo.**

## Scene 5 — Breach

O jogador envia o mesmo registro repetidamente até o contador atingir 500, sem crescer o Archive.

## Scene 6 — World Reaction

O contador atinge o limite e o Archive libera o snapshot. O Breaker lê a lista e para de enviar lotes; Mara confronta o custo de ter inflado o Archive. Isso acontece obrigatoriamente; não existe escolha entre recuperação e degradação.

As telas principais mudam.

Snapshot:

**COUNTER AT CAPACITY**
**SNAPSHOT RELEASED**

Um snapshot antigo aparece.

## Scene 7 — Discovery

Lista:

**BREAKER REGISTRY**

Algumas entradas estão parcialmente corrompidas ou ocultas:

**████████ — MISSING**
**████████ — ACCEPTED**
**████████ — DECEASED**

Então aparece um nome conhecido:

**AREN VOSS — REFUSED**

E logo abaixo:

**SUBJECT: \$PLAYER**
**STATUS: ACTIVE**

Timestamp recente.

Mara:

> **Essa entrada foi criada depois que abrimos o caso.**

O jogador entende: alguém está acompanhando a investigação.

Outra referência:

**ORACLE**

Antes do debrief, o Breaker OS mostra o contador e o armazenamento: **COUNT: 500 / STORED: 1**. Mara observa que uma prova de vulnerabilidade não apaga o custo causado a outros operadores. Esta é a única cena pós-exploit; não oferecer opções, flags ou segundo final. A falha ensinada é divergência contador/armazenamento, não corrupção de storage.

## Scene 8 — Debrief

**VULNERABILITY DISCOVERED — COUNTER / STORAGE DIVERGENCE**

Explicar que o contador somou entradas que o Archive não armazenou.

## Scene 9 — Transition

Pela primeira vez, a próxima pista não vem de Voss.

Ela vem do sistema que observa Breakers.

Unlock:
**CASE 08 — THE ORACLE**

## Ajuste de roteiro v2 — a revelação vem do snapshot

O Archive aceita um lote de registros e conta cada entrada, mas armazena só as únicas. Enviar o mesmo registro em massa leva `count()` a 500 com `stored()` em 1; nesse estado, `snapshot()` libera a lista. **A falha principal é a divergência entre contador e armazenamento**. A consequência narrativa é única: o snapshot expõe o Registry; o Breaker lê a lista e Mara confronta o custo de ter inflado o Archive. Não criar reações ramificadas de Mara, modos morais de recuperação ou finais diferentes.

Pistas preparatórias: `count()` vs `stored()`; entradas repetidas no histórico; o limite de 500. Não revelar o Registry antes do breach.

## Pista histórica vigente — S13 / SNAPSHOT (v1.4)

Após a falha reproduzível, o contador atinge o limite e o contrato libera `S13 / SNAPSHOT`. Não há indexador externo nem fallback: o snapshot é uma função do contrato e não contém `share_c` nem segredos da instância final.

**Contrato de implementação vigente:** o verificador exige `count() &gt;= threshold()`, `stored() &lt; threshold()` e `revealed() == true`. Persistir o snapshot e o estado na Evidence Locker depois do verifier, sem segunda vulnerabilidade. O jogador deve ver VOSS REFUSED, a identidade ACCEPTED mascarada e depois PLAYER ACTIVE, com data de criação posterior à abertura da investigação; a hipótese de Voss sobre acesso externo é refutada. Parar pressão adicional após obter prova. O Final Boss deriva suas shares públicas de 32 bytes do contexto da instância atual (manifesto/rede/instância/carteira/índice) e as verifica por commitment; não usa share\_c antiga ou senha baseada nos nomes dos lugares.

Payoff obrigatório no Final Boss: [VOSS PROTOCOL — Níveis 11/12 | Especificação vigente](voss-protocol-niveis-11-12-especificacao-vigente.md).

## Easter Eggs — proposta técnica/visual (não canônica)

- [GALEXIE / MIRROR 13](../references/galexie-mirror-13.md): etiqueta opcional de exportação histórica ou pipeline de observabilidade ao lado do indexador, sem mudar a lógica do snapshot externo do Case 07.
- **HORIZON / LEGACY FEED**: rodapé opcional de uma API de consulta histórica; não afirmar que Horizon, Galexie ou o ledger carregam dados privados do Registry.

**Gate:** o fallback e a revelação PLAYER ACTIVE permanecem sujeitos à prova e ao momento do roteiro locked; sem antecipação em imagens. Ver [Catálogo de Referências — Season 1](../../../../../databases/season-01-reference-catalog.txt).
