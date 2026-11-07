---
notion_id: 4009c563-0425-8150-84b7-dd82afc14074
source: https://app.notion.com/p/4009c5630425815084b7dd82afc14074?pvs=204
title: "🗄️ 04 — The Forgotten Floor"
exported_at: 2026-11-07
---

Here is the result of "fetch" for the Page with URL https://app.notion.com/p/4009c5630425815084b7dd82afc14074 as of 2026-11-04T15:33:29.546Z:
<page url="https://app.notion.com/p/4009c5630425815084b7dd82afc14074" icon="🗄️">
<ancestor-path>
<parent-page url="https://app.notion.com/p/4019c563042581fd9124e5ee36b3e82f" title="03 — Cases & Bosses"/>
<ancestor-2-page url="https://app.notion.com/p/4009c563042581359693d42f09d41062" title="Season 01 — The First Layer"/>
<ancestor-3-page url="https://app.notion.com/p/4019c563042581469a0edc7e30a6eff9" title="ACT I — The World Is Breakable"/>
<ancestor-4-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
<properties>
{"title":"04 — The Forgotten Floor"}
</properties>
<iconMetadata>{"type":"emoji","emoji":"🗄️"}</iconMetadata>
<content>
<callout icon="🎨" color="gray_bg">
<b>Visual reference:</b> [04 — The Forgotten Floor — abrir arte no Google Drive](https://drive.google.com/file/d/1EBYhb6yN8t6HUV0pfGfd2Dd90v3nHR74/view)
</callout>

# Função narrativa

Introduzir a ideia de memória imperfeita na infraestrutura e revelar que Meridian possui uma camada esquecida.

# Situação

O elevador principal da instalação possui referência a um andar inexistente. Não é bloqueado: ele simplesmente não aparece.

# Conceito técnico

<b>Renovação de TTL com alvo implícito (off-by-one): a função renova o andar seguinte ao argumento.</b>

# Missão

> <b>Faça o sistema lembrar aquilo que foi projetado para esquecer.</b>

# Condição de vitória

Descobrir o andar que não aparece no índice e renovar o TTL da entrada 24 — <code>renew_floor(23)</code> renova o andar seguinte.

# Resultado

O andar oculto reaparece.

Nos registros recuperados:

<b>ARCHIVED ENTRY RECOVERED</b><br /><b>ORIGIN: UNKNOWN</b><br /><b>STATUS: OBSERVED</b>

# Revelação

Surge a primeira referência a:

## THE FIRST LAYER

# Próximo passo

A única entrada é protegida pelo Custodian.

# Blueprint técnico e narrativo da fase

## A cena

A Ghost Key contém referência a um andar abaixo de Lower Meridian, mas os terminais de transporte não exibem esse andar. O detalhe estranho: o índice do elevador ainda possui uma lacuna entre dois números. Não é um andar bloqueado. É como se o sistema tivesse <b>esquecido que ele existia</b>.

O Breaker encontra um antigo <code>AccessRecord</code> persistente cujo andar não aparece no índice. A missão deixa de ser 'hackear uma porta' e vira recuperar memória da própria cidade.

> <b>Faça o sistema lembrar aquilo que foi projetado para esquecer.</b>

## Conceito técnico — TTL com alvo implícito

<b>Renovação de TTL no alvo errado (off-by-one).</b> Este Case não depende de esperar archival nem de restore por footprint. O andar 24 existe no storage persistente e não aparece no índice (1–23). <code>renew_floor(floor_id)</code> estende o TTL do andar <b>seguinte</b> ao argumento e marca <code>Renewed(floor_id + 1)</code>. Chamar <code>renew_floor(24)</code> renova 25; para renovar 24 é preciso chamar <code>renew_floor(23)</code>.

Em Soroban, o TTL de entradas Persistent é finito. O contrato até renova — mas renova a chave errada quando o chamador acredita que o argumento é o alvo.

### Contrato vulnerável

```rs
pub fn renew_floor(env: Env, floor_id: u32) {
    let target = floor_id.saturating_add(1);
    let key = DataKey::Floor(target);
    env.storage()
        .persistent()
        .extend_ttl(&key, TTL_THRESHOLD, TTL_EXTEND_TO);
    env.storage()
        .persistent()
        .set(&DataKey::Renewed(target), &true);
}
```

O comentário do revisor: <code>target</code> não é o argumento; é o sucessor. O jogador que passa 24 renova 25 — e não recebe erro nenhum.

Nesta implementação a entrada não é arquivada: o registro 24 nasce ativo e o teste só exige que o TTL avance. A lição de archival fica para a documentação de Soroban, não para o exploit.

### Como o challenge é jogável

Não há espera de dias nem simulação de archival: a instância nasce com o registro 24 ativo e o índice sem ele. O jogador precisa descobrir:

1. que o índice lista 1–23 mas a referência aponta 24;
2. que <code>floor(24)</code> existe e devolve <code>FIRST LAYER</code>;
3. que <code>renew_floor</code> age sobre o <b>andar seguinte</b> ao argumento — logo, 23 renova 24;
4. confirmar <code>renewed(24) == true</code>. O teste do nível também mede o TTL antes e depois para provar que a renovação aconteceu de verdade.

### Condição objetiva de vitória

- <code>renewed(24) == true</code>;
- <code>floor(24) == "FIRST LAYER"</code>;
- o TTL da entrada <code>Floor(24)</code> avançou em relação ao estado inicial (o teste do nível compara antes e depois).

## Solução segura

```rs
pub fn renew_floor(env: Env, floor_id: u32) {
    let key = DataKey::Floor(floor_id);
    env.storage()
        .persistent()
        .extend_ttl(&key, TTL_THRESHOLD, TTL_EXTEND_TO);
    env.storage()
        .persistent()
        .set(&DataKey::Renewed(floor_id), &true);
}
```

O alvo é sempre o argumento. Se a intenção for renovar "o seguinte", que o nome da função e o argumento digam isso — <code>renew_next_floor(previous_id)</code> — em vez de esconder a soma dentro da função.

Também podemos ensinar o padrão <b>bump-on-access</b>, em que leituras de dados ativos estendem a vida do registro quando o TTL cai abaixo de determinado threshold.

## Revelação narrativa

Quando o andar reaparece no mapa, o sistema recupera três linhas antigas:

<b>ARCHIVED ENTRY RECOVERED</b><br /><b>ORIGIN: UNKNOWN</b><br /><b>STATUS: OBSERVED</b>

A Ghost Key desbloqueia uma entrada chamada apenas:

> <b>FIRST LAYER</b>

Essa é a primeira vez que o jogador entende que existe uma infraestrutura enterrada sob Meridian.

## Referências para implementação

- [Stellar Docs — State archival](https://developers.stellar.org/docs/learn/fundamentals/contract-development/storage/state-archival)
- [Stellar Docs — Choosing storage types](https://developers.stellar.org/docs/build/guides/storage/choosing-the-right-storage)
- [Stellar Docs — Storage strategies / bump-on-access](https://developers.stellar.org/docs/build/guides/storage/storage-strategies)
- [Soroban Guard — missing TTL vulnerability](https://github.com/Veritas-Vaults-Network/soroban-guard-contracts/blob/main/docs/vulnerabilities.md)

# Roteiro in-game — Player-facing

## Scene 0 — Arrival

A Ghost Key guia o jogador até uma instalação antiga.

Elevador:<br /><b>01–23</b>

Não existe 24.

Mara:

> <b>Blueprints confirm twenty-three floors.</b>

<b>Continuidade obrigatória de Warehouse 17:</b> Mara confirma que recebeu o hash e o protocolo de custódia da Ghost Key, mas lembra que o contrato ainda aponta o Breaker como proprietário por causa de uma transferência não autorizada. A investigação avança com a chave preservada. A cena e o diálogo são os mesmos para todos os jogadores.

## Scene 1 — Inciting Evidence

A Ghost Key responde apenas perto do elevador.

Evidence:

- building blueprint;
- old ledger references;
- archived storage key;
- Ghost Key resonance.

## Scene 2 — Mission

> <b>FAÇA MERIDIAN LEMBRAR O QUE ESQUECEU.</b>

## Scene 3 — Active Investigation

Source e storage inspector mostram referências antigas, mas parte do estado não está disponível diretamente.

O terminal pode exibir:<br /><b>FLOOR NOT IN INDEX</b>

e, após investigação:<br /><b>LEGACY ROUTE DETECTED</b>

Nenhuma explicação de TTL é dada antes da solução.

## Scene 4 — Reactive Beats

Mara:

> <b>Se o andar foi demolido, deveria existir um registro de demolição.</b>

Ela não encontra ordem de demolição nem autorização de remoção. Essa investigação independente impede que o Breaker confunda um histórico expirado com destruição física comprovada.

Breaker:

> <b>Não existe.</b>

## Scene 5 — Breach

O jogador percebe que a função de renovação age sobre o andar <b>seguinte</b> ao argumento e chama <code>renew_floor(23)</code>. A interface/indexador do elevador volta a enxergar a rota 24. Não simular que a chamada Soroban executa normalmente com um storage arquivado e o ressuscita sozinha dentro do contrato.

## Scene 6 — World Reaction

O painel do elevador falha por um instante.

Surge:

<b>24</b>

As luzes mudam.

O elevador desce/sobe além do mapa conhecido.

## Scene 7 — Discovery

No novo andar:

<b>I // FIRST LAYER</b>

A Ghost Key não era uma chave para uma porta; era uma chave para uma infraestrutura esquecida.

O Floor 24 não é a First Layer inteira. É apenas uma entrada física para a rede de sistemas legados que sustenta partes da Meridian moderna.

Ao fundo, um sistema desperta:

<b>CUSTODIAN ONLINE</b>

## Scene 8 — Debrief

<b>CONCEPT DISCOVERED — RENEWAL TARGET MISMATCH (OFF-BY-ONE)</b>

Mostrar por que estado pode expirar/arquivar e como manter dados críticos disponíveis.

## Scene 9 — Transition

A porta principal do andar permanece bloqueada.

Mensagem:

<b>IDENTITY UNKNOWN</b>

Unlock:<br /><b>BOSS I — THE CUSTODIAN</b>

## Pista histórica vigente — F24 / ARCHIVED ENTRY (v1.4)

Após a renovação explícita da entrada <b>Persistent</b>, <code>F24 / ARCHIVED ENTRY</code> volta a ser consultável e recebe o rodapé <code>ARCHIVE: LEGACY / RETENTION: OPEN</code>, o mesmo de W17. Este registro histórico <b>não</b> contém <code>share_b</code> nem bytes secretos da futura instância final. O número 24 identifica o andar que havia sumido do índice moderno, não um componente de senha.

<b>Contrato de implementação vigente:</b> o verificador confirma <code>renewed(24)</code> e <code>floor(24) == FIRST LAYER</code>; o teste do nível também mede o TTL da entrada 24 antes e depois para provar que ele avançou. Não há simulação de archival nem de restore por footprint nesta implementação. Depois da vitória, preservar ID, chave e proveniência F24 na Evidence Locker, sem nova vulnerabilidade. A prova contextual do Final Boss é calculada com dados públicos da instância final, não armazenada previamente em Floor 24.

Payoff obrigatório no Final Boss: <mention url="https://app.notion.com/p/4039c56304258137ae19e8787acc1d1f" />.

## Easter Eggs — propostas visuais (não canônicas)

- <mention url="https://app.notion.com/p/40e9c5630425810caf67da944acb5e77" />: assinatura de engenharia antiga em uma bancada ou placa lateral do Floor 24, inspirada no codinome de Soroban.
- <mention url="https://app.notion.com/p/40e9c5630425816f8115c4c0b18654f6" />: ábaco japonês discreto que remete ao nome Soroban, como item ambiental.

<b>Gate:</b> a porta 24, o TTL e F24 / ARCHIVED ENTRY continuam as únicas referências desta etapa necessárias ao CTF. Essas inclusões não devem sugerir senha, shares, criptografia escondida nem uma porta extra. Ver <mention url="https://app.notion.com/p/2b1d33190ac446bfaea34e7a4db74d92" />.
</content>
</page>

