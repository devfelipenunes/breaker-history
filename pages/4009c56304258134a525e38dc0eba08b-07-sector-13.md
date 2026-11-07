---
notion_id: 4009c563-0425-8134-a525-e38dc0eba08b
source: https://app.notion.com/p/4009c56304258134a525e38dc0eba08b?pvs=204
title: "☣️ 07 — Sector 13"
exported_at: 2026-11-07
---

Here is the result of "fetch" for the Page with URL https://app.notion.com/p/4009c56304258134a525e38dc0eba08b as of 2026-11-04T15:35:05.640Z:
<page url="https://app.notion.com/p/4009c56304258134a525e38dc0eba08b" icon="☣️">
<ancestor-path>
<parent-page url="https://app.notion.com/p/4019c563042581fd9124e5ee36b3e82f" title="03 — Cases & Bosses"/>
<ancestor-2-page url="https://app.notion.com/p/4009c563042581359693d42f09d41062" title="Season 01 — The First Layer"/>
<ancestor-3-page url="https://app.notion.com/p/4019c563042581469a0edc7e30a6eff9" title="ACT I — The World Is Breakable"/>
<ancestor-4-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
<properties>
{"title":"07 — Sector 13"}
</properties>
<iconMetadata>{"type":"emoji","emoji":"☣️"}</iconMetadata>
<content>
<callout icon="🎨" color="gray_bg">
<b>Visual reference:</b> [07 — Sector 13 — abrir arte no Google Drive](https://drive.google.com/file/d/13-B3F6yTtB3qIqmN0jV_Mqz4n5deUhMO/view)
</callout>

# Função narrativa

Ser o grande ponto de inversão da Season.

Até aqui, o jogador acredita que está seguindo Aren Voss.

Em Sector 13 ele descobre que <b>também está sendo seguido</b>.

# Situação

Sector 13 abriga um Archive antigo. Milhares de registros inúteis estão sendo criados continuamente. Por trás da saturação existem dados ocultos.

# Conceito técnico

<b>Contador divergente do armazenamento: entradas duplicadas inflam o contador sem crescer o Archive.</b>

# Missão

> <b>Quebre o Archive.</b>

# Condição de vitória

Levar o contador a 500 sem armazenar 500 registros únicos e obter o snapshot — provando que o limite é medido pela contagem, não pelo conteúdo.

# Revelação

Quando a camada de ruído cai, o jogador encontra uma lista.

Todos os registros pertencem a Breakers. Alguns estão mortos. Alguns desaparecidos. Uma entrada mascarada possui status <b>ACCEPTED</b>. Aren Voss aparece como <b>REFUSED</b>.

E a entrada mais recente é o próprio jogador:

> <b>SUBJECT: PLAYER — ACTIVE</b>

O contraste entre <b>ACCEPTED</b>, <b>REFUSED</b> e <b>ACTIVE</b> deve parecer importante sem ser explicado ainda.

# Próximo passo

A lista inclui referências a uma entidade chamada <b>The Oracle</b>.

# Blueprint técnico e narrativo da fase

## Sector 13

Sector 13 parece um cemitério de dados. O Archive local está abarrotado de registros irrelevantes, identidades descartáveis e entradas repetidas.

Voss percebeu que aquilo não era lixo aleatório. O ruído foi criado para tornar uma operação central do Archive impossível.

> <b>Quebre o Archive. Depois veja o que ele estava escondendo.</b>

## Vulnerabilidade real

<b>Contador e armazenamento medem coisas diferentes (</b><b><code>count</code></b><b> vs </b><b><code>stored</code></b><b>).</b>

<code>add_records</code> percorre o lote e incrementa <code>count</code> para <b>cada</b> elemento recebido; o Archive só guarda registros únicos num <code>Map</code>, e <code>stored()</code> devolve o tamanho do vetor de únicos. Enviar o mesmo <code>BytesN&lt;32&gt;</code> 500 vezes produz <code>count() == 500</code> e <code>stored() == 1</code>. <code>snapshot()</code> só olha o contador: ao atingir o limite, libera a lista.

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

O jogador envia um lote com o mesmo registro repetido 500 vezes. <code>count()</code> chega a 500; <code>stored()</code> permanece 1. <code>snapshot()</code> deixa de recusar por “archive intacto” e devolve a lista, marcando <code>revealed = true</code>. Nenhuma operação de rebuild ou serviço externo participa do caminho.

### Condição objetiva de vitória

- <code>count() &gt;= threshold()</code> (500);
- <code>stored() &lt; threshold()</code> — o Archive não cresceu de verdade;
- <code>revealed() == true</code>;
- <code>snapshot()</code> devolve <code>AREN VOSS // REFUSED</code> e <code>SUBJECT: PLAYER // STATUS: ACTIVE</code>.

Um Archive com 500 registros únicos e <code>stored() == 500</code> <b>não</b> passa: o validador exige a divergência.

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

O snapshot devolvido por <code>snapshot()</code> contém a lista de Breakers observados pela First Layer. Ele é liberado quando o contador atinge o limite, mesmo que o Archive tenha armazenado um único registro.

Alguns: <b>DECEASED</b>. Outros: <b>MISSING</b>. Voss: <b>REFUSED</b>.

A última entrada foi criada recentemente:

> <b>SUBJECT: PLAYER</b><br /><b>STATUS: ACTIVE</b>

Agora o jogador sabe que sua chegada não passou despercebida.

A entrada do player foi criada <b>durante a própria investigação</b>. Isso prova que o registry continua ativo e transforma o tom da campanha: o jogador não está apenas descobrindo um sistema antigo; alguma coisa ainda está observando quem consegue atravessá-lo.

A palavra <b>REFUSED</b> também cria a nova pergunta central:

> <b>O que Voss recusou?</b>

## Referências para implementação

- [Scout — DoS unexpected revert with vector](https://coinfabrik.github.io/scout-soroban/docs/detectors/dos-unexpected-revert-with-vector)
- [Scout — DoS unbounded operation](https://coinfabrik.github.io/scout-soroban/docs/detectors/dos-unbounded-operation)
- [Stellar Docs — storage granularity](https://developers.stellar.org/docs/learn/fundamentals/contract-development/storage/persisting-data)
- [Soroban Guard — unbounded\_loop and storage vulnerabilities](https://github.com/Veritas-Vaults-Network/soroban-guard-contracts)

# Roteiro in-game — Player-facing

<callout icon="🎮" color="red_bg">
Sector 13 é o ponto de virada da Season: até aqui o jogador acredita que está seguindo Voss; aqui descobre que também está sendo observado.
</callout>

## Scene 0 — Arrival

O jogador encontra Sector 13 fora dos mapas oficiais.

A arquitetura é um cemitério de dados ainda em operação.

Painel central:<br /><b>ARCHIVE LOAD: CRITICAL</b>

## Scene 1 — Inciting Evidence

Pista opcional de fair play antes do exploit: <code>UNIQUE RECORDS: DEDUPLICATED</code> e <code>COUNTER: EVERY ENTRY</code>. Não revelar <code>Breaker Registry</code>. O player poderá depois entender por que o contador cresceu sem o Archive crescer.

Voss deixou uma única instrução:

> <b>Quebre o Archive.</b>

Evidence:

- storage growth;
- rebuild history;
- recovery snapshot policy;
- milhões de entradas irrelevantes.

## Scene 2 — Mission

> <b>QUEBRE O ARCHIVE. VEJA O QUE ELE ESTÁ ESCONDENDO.</b>

## Scene 3 — Active Investigation

O jogador pode inserir registros e observar custo/uso crescer.

Terminal:<br /><b>RECORD COUNT</b><br /><b>STORED RECORDS</b><br /><b>THRESHOLD</b>

Nenhuma menção explícita a DoS antes da resolução.

## Scene 4 — Reactive Beats

Conforme o Archive recebe lotes:

<b>RECORD COUNT ↑</b><br /><b>STORED RECORDS: 1</b>

Mara:

> <b>Você está piorando tudo.</b>

Breaker:

> <b>Esse é o objetivo.</b>

## Scene 5 — Breach

O jogador envia o mesmo registro repetidamente até o contador atingir 500, sem crescer o Archive.

## Scene 6 — World Reaction

O contador atinge o limite e o Archive libera o snapshot. O Breaker lê a lista e para de enviar lotes; Mara confronta o custo de ter inflado o Archive. Isso acontece obrigatoriamente; não existe escolha entre recuperação e degradação.

As telas principais mudam.

Snapshot:

<b>COUNTER AT CAPACITY</b><br /><b>SNAPSHOT RELEASED</b>

Um snapshot antigo aparece.

## Scene 7 — Discovery

Lista:

<b>BREAKER REGISTRY</b>

Algumas entradas estão parcialmente corrompidas ou ocultas:

<b>████████ — MISSING</b><br /><b>████████ — ACCEPTED</b><br /><b>████████ — DECEASED</b>

Então aparece um nome conhecido:

<b>AREN VOSS — REFUSED</b>

E logo abaixo:

<b>SUBJECT: \$PLAYER</b><br /><b>STATUS: ACTIVE</b>

Timestamp recente.

Mara:

> <b>Essa entrada foi criada depois que abrimos o caso.</b>

O jogador entende: alguém está acompanhando a investigação.

Outra referência:

<b>ORACLE</b>

Antes do debrief, o Breaker OS mostra o contador e o armazenamento: <b>COUNT: 500 / STORED: 1</b>. Mara observa que uma prova de vulnerabilidade não apaga o custo causado a outros operadores. Esta é a única cena pós-exploit; não oferecer opções, flags ou segundo final. A falha ensinada é divergência contador/armazenamento, não corrupção de storage.

## Scene 8 — Debrief

<b>VULNERABILITY DISCOVERED — COUNTER / STORAGE DIVERGENCE</b>

Explicar que o contador somou entradas que o Archive não armazenou.

## Scene 9 — Transition

Pela primeira vez, a próxima pista não vem de Voss.

Ela vem do sistema que observa Breakers.

Unlock:<br /><b>CASE 08 — THE ORACLE</b>

## Ajuste de roteiro v2 — a revelação vem do snapshot

O Archive aceita um lote de registros e conta cada entrada, mas armazena só as únicas. Enviar o mesmo registro em massa leva <code>count()</code> a 500 com <code>stored()</code> em 1; nesse estado, <code>snapshot()</code> libera a lista. <b>A falha principal é a divergência entre contador e armazenamento</b>. A consequência narrativa é única: o snapshot expõe o Registry; o Breaker lê a lista e Mara confronta o custo de ter inflado o Archive. Não criar reações ramificadas de Mara, modos morais de recuperação ou finais diferentes.

Pistas preparatórias: <code>count()</code> vs <code>stored()</code>; entradas repetidas no histórico; o limite de 500. Não revelar o Registry antes do breach.

## Pista histórica vigente — S13 / SNAPSHOT (v1.4)

Após a falha reproduzível, o contador atinge o limite e o contrato libera <code>S13 / SNAPSHOT</code>. Não há indexador externo nem fallback: o snapshot é uma função do contrato e não contém <code>share_c</code> nem segredos da instância final.

<b>Contrato de implementação vigente:</b> o verificador exige <code>count() &gt;= threshold()</code>, <code>stored() &lt; threshold()</code> e <code>revealed() == true</code>. Persistir o snapshot e o estado na Evidence Locker depois do verifier, sem segunda vulnerabilidade. O jogador deve ver VOSS REFUSED, a identidade ACCEPTED mascarada e depois PLAYER ACTIVE, com data de criação posterior à abertura da investigação; a hipótese de Voss sobre acesso externo é refutada. Parar pressão adicional após obter prova. O Final Boss deriva suas shares públicas de 32 bytes do contexto da instância atual (manifesto/rede/instância/carteira/índice) e as verifica por commitment; não usa share\_c antiga ou senha baseada nos nomes dos lugares.

Payoff obrigatório no Final Boss: <mention url="https://app.notion.com/p/4039c56304258137ae19e8787acc1d1f" />.

## Easter Eggs — proposta técnica/visual (não canônica)

- <mention url="https://app.notion.com/p/40e9c56304258178a8b2ed371a8cdeb4" />: etiqueta opcional de exportação histórica ou pipeline de observabilidade ao lado do indexador, sem mudar a lógica do snapshot externo do Case 07.
- <b>HORIZON / LEGACY FEED</b>: rodapé opcional de uma API de consulta histórica; não afirmar que Horizon, Galexie ou o ledger carregam dados privados do Registry.

<b>Gate:</b> o fallback e a revelação PLAYER ACTIVE permanecem sujeitos à prova e ao momento do roteiro locked; sem antecipação em imagens. Ver <mention url="https://app.notion.com/p/2b1d33190ac446bfaea34e7a4db74d92" />.
</content>
</page>

