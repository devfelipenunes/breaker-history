---
notion_id: 4009c563-0425-813c-b1f3-e2515b9de879
source: https://app.notion.com/p/4009c5630425813cb1f3e2515b9de879?pvs=204
title: "🏭 03 — Warehouse 17"
exported_at: 2026-11-07
---

Here is the result of "fetch" for the Page with URL https://app.notion.com/p/4009c5630425813cb1f3e2515b9de879 as of 2026-11-04T15:15:26.281Z:
<page url="https://app.notion.com/p/4009c5630425813cb1f3e2515b9de879" icon="🏭">
<ancestor-path>
<parent-page url="https://app.notion.com/p/4019c563042581fd9124e5ee36b3e82f" title="03 — Cases & Bosses"/>
<ancestor-2-page url="https://app.notion.com/p/4009c563042581359693d42f09d41062" title="Season 01 — The First Layer"/>
<ancestor-3-page url="https://app.notion.com/p/4019c563042581469a0edc7e30a6eff9" title="ACT I — The World Is Breakable"/>
<ancestor-4-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
<properties>
{"title":"03 — Warehouse 17"}
</properties>
<iconMetadata>{"type":"emoji","emoji":"🏭"}</iconMetadata>
<content>
<callout icon="🎨" color="gray_bg">
<b>Visual reference:</b> [03 — Warehouse 17 — abrir arte no Google Drive](https://drive.google.com/file/d/1J4euUCh2qm38x5NAbWSL9ATFSWqhygmA/view)
</callout>

# Função narrativa

Primeira infiltração física/digital relevante da campanha.

# Situação

Warehouse 17 é oficialmente vazio. Na prática, contém centenas de equipamentos e propriedades desviadas. Todos os registros parecem válidos.

# Conceito técnico

<b>Wrong authorization subject / autorização da entidade errada / erro semântico de ownership.</b>

# Missão

> <b>Roube um objeto que o sistema acredita que você pode possuir.</b>

# Condição de vitória

Explorar uma função que exige autorização, mas valida a pessoa errada ou associa a autorização ao papel incorreto.

# Resultado

O jogador transfere um objeto para si sem quebrar nenhuma assinatura.

Dentro dele há um dispositivo estranho.

# Story Item

## Ghost Key

Uma chave híbrida físico-digital sem origem registrada. Ela contém referências a uma camada de infraestrutura que não aparece nos mapas modernos.

# Próximo passo

A Ghost Key aponta para um andar que não existe nos registros públicos.

# Blueprint técnico e narrativo da fase

## A cena

Warehouse 17 não é um esconderijo cheio de criminosos. É pior: tudo ali parece legal. Centenas de dispositivos roubados estão catalogados, transferidos e registrados corretamente pelo sistema. Não existe registro corrompido.

O Breaker escolhe um artefato específico que apareceu nas imagens do Vault. Para levá-lo, precisa passar pelo contrato de propriedade do warehouse.

> <b>Roube um objeto que o sistema acredita que você pode possuir.</b>

## Vulnerabilidade real

<b>Wrong Auth Subject / autorização da Address errada.</b>

Esse erro acontece quando o contrato chama <code>require_auth()</code>, mas exige assinatura de uma entidade diferente daquela cujos direitos estão sendo afetados. É mais interessante do que simplesmente esquecer autenticação porque ensina que <b>ter um </b><b><code>require_auth()</code></b><b> não significa que o controle de acesso está correto</b>.

### Contrato vulnerável

```rs
pub fn transfer_item(
    env: Env,
    owner: Address,
    recipient: Address,
    item_id: u64,
) {
    // VULNERÁVEL: quem recebe autoriza; quem perde o item não.
    recipient.require_auth();

    let current: Address = env.storage().persistent()
        .get(&DataKey::Owner(item_id))
        .unwrap();
    if current != owner { panic!("wrong owner") }

    env.storage().persistent()
        .set(&DataKey::Owner(item_id), &recipient);
}
```

### Exploit esperado

O jogador define:

- <code>owner = warehouse_address</code>;
- <code>recipient = player_address</code>;
- assina apenas como recipient.

O contrato valida que o item pertence ao warehouse, mas autentica o novo dono em vez do dono atual.

### Condição objetiva de vitória

- antes: <code>Owner(GHOST_DEVICE) == warehouse_address</code>;
- depois: <code>Owner(GHOST_DEVICE) == player_address</code>;
- nenhuma autorização do warehouse foi fornecida.

## Solução segura

```rs
pub fn transfer_item(
    env: Env,
    owner: Address,
    recipient: Address,
    item_id: u64,
) {
    owner.require_auth();
    // validação de ownership + update
}
```

O princípio é simples: <b>a entidade que perde ativo, direito ou privilégio precisa ser a entidade cuja autorização está sendo exigida</b>, salvo desenho explícito de delegação.

## A Ghost Key

Dentro do objeto roubado existe a primeira grande peça física da Season: <b>Ghost Key</b>. Ela não é uma chave privada comum. Contém um pequeno mapa de contract IDs, storage keys e referências de infraestrutura que Meridian não reconhece.

A experiência deve passar a sensação de que o jogador cometeu um crime para avançar uma investigação maior. Essa ambiguidade ajuda a construir a personalidade de Breaker/vigilante.

## Referências para implementação

- [Soroban common security mistakes — wrong auth subject](https://github.com/mariaelisaaraya/stellar-security-guide/blob/main/skills/soroban-common-mistakes/SKILL.md)
- [Stellar Docs — authorization semantics](https://developers.stellar.org/docs/learn/fundamentals/contract-development/authorization)
- [Scout — unauthorized storage mutation](https://coinfabrik.github.io/scout-soroban/docs/detectors/set-contract-storage)

# Roteiro in-game — Player-facing

<callout icon="🎮" color="blue_bg">
A fase deve parecer a primeira infiltração deliberadamente ilegal do jogador.
</callout>

## Scene 0 — Arrival

A arte mostra Warehouse 17 em Lower Meridian.

Mara não acompanha fisicamente.

Transmission:

> <b>Não existe registro municipal deste local. Se entrar, estará por conta própria.</b>

## Scene 1 — Inciting Evidence

O Breaker encontra centenas de objetos catalogados.

Tudo parece legítimo.

Evidence:

- ownership records;
- transfer history;
- item IDs;
- nenhum flag de stolen property;
- contestação administrativa recuperada por Mara, com titularidade anterior contestada e autorização ausente. Ela descobre isso fora do terminal do Breaker.

Um item aparece nas imagens do Vault.

## Scene 2 — Mission

> <b>ROUBE UM OBJETO QUE O SISTEMA ACREDITA QUE VOCÊ PODE POSSUIR.</b>

## Scene 3 — Active Investigation

Source: ownership contract.<br />Terminal: leitura de owner, recipient e transfer history.<br />Evidence: item específico ligado ao Vault.

O jogador pode descobrir que o contrato realmente usa autorização — mas não recebe indicação de que é a entidade errada.

## Scene 4 — Reactive Beats

Ao consultar o item:

<b>OWNER: WAREHOUSE 17</b>

Ao consultar permissões:

<b>TRANSFER REQUIRES AUTHORIZATION</b>

Mara:

> <b>Então o contrato está protegido.</b>

Essa frase deve soar confortável demais.

## Scene 5 — Breach

O jogador transfere o objeto para si sem obter autorização do Warehouse.

Verifier confirma novo owner.

## Scene 6 — World Reaction

Terminal:

<b>TRANSFER ACCEPTED</b><br /><b>NEW OWNER: \$PLAYER</b>

As luzes do compartimento do item mudam de vermelho para branco.

Nenhum alarme.

O novo proprietário registrado é o Breaker, embora essa transferência não tenha autorização do Warehouse. O objeto permanece disponível para inspeção; a decisão de custódia só aparece <b>depois</b> de o jogador descobrir que o conteúdo é uma evidência.

## Scene 7 — Discovery

Dentro do item há um dispositivo físico-digital:

<b>STORY ITEM ACQUIRED — GHOST KEY</b>

A chave revela contract IDs e storage keys desconhecidos.

Uma referência:<br /><b>FLOOR 24</b>

Mara:

> <b>Esse prédio tem vinte e três andares.</b>

Mara abre o protocolo de contestação de propriedade e solicita a cadeia de custódia da Ghost Key. Após a vitória técnica, o Breaker registra o hash, o evento de transferência e o protocolo verificável. Mantém o artefato lacrado sob posse técnica temporária para chegar à Floor 24. O titular on-chain continua sendo o Breaker em consequência da transferência irregular; documentar a evidência não legitima o furto. Mara o confronta com esse fato. Essa é uma única cena canônica, sem decisão pós-exploit, opções de omissão ou ramificações.

## Scene 8 — Debrief

<b>Debrief narrativo:</b> confirmar que o Breaker documentou a Ghost Key em cadeia de custódia verificável. Isso não desfaz o ownership on-chain obtido pela falha. A Ghost Key permanece disponível como story item necessário no Case 04. Nenhuma escolha narrativa aparece.

<b>VULNERABILITY DISCOVERED — WRONG AUTH SUBJECT</b>

Explicar que havia <code>require_auth()</code>, mas aplicado à entidade errada.

## Scene 9 — Transition

<b>NEW LEAD: FLOOR 24</b>

Unlock:<br /><b>CASE 04 — THE FORGOTTEN FLOOR</b>

## Direção dramática — Vítima e legitimidade

A contestação de equipamento de serviço em Lower Meridian é um caso <b>distinto</b> da Ghost Key: demonstra danos anteriores do mesmo modelo de autorização incorreta, sem inventar um antigo proprietário desconhecido da chave. Mara obtém registros de contestação inacessíveis por leitura do contrato. O resultado pós-exploit é sempre o registro de evidência e a custódia técnica temporária da Ghost Key; a titularidade on-chain permanece irregularmente transferida ao Breaker. Não oferecer opções de devolução, omissão do registro ou propriedade. O conflito nasce da diferença entre legalidade registrada, preservação de prova e legitimidade.

## Pista histórica vigente — W17 / DIAGNOSTIC TRACE (v1.4)

Após a custódia contestada da Ghost Key, a Evidence Locker preserva o arquivo <code>W17 / DIAGNOSTIC TRACE</code>, com ID estável, fonte e o rodapé <code>ARCHIVE: LEGACY / RETENTION: OPEN</code>. Este é um registro de proveniência histórica; <b>não</b> contém <code>share_a</code>, material secreto ou bytes da futura instância do Architect. O número 17 identifica o local, não compõe a chave criptográfica.

<b>Contrato de implementação vigente:</b> persistir ID e fonte do arquivo na Evidence Locker após vitória verificável, mantendo a contestação civil separada do ownership on-chain. Mostrar o rodapé recorrente, sem “1 de 3”, XOR ou instrução de senha. As três shares de 32 bytes do Final Boss são derivadas de dados públicos da rede, instância, carteira, manifesto e índices <b>na instância final</b>, conforme o Voss Protocol revisado. Não confundir arquivo histórico com segredo de desafio; permitir consulta sem repetir o Case.

Payoff obrigatório no Final Boss: <mention url="https://app.notion.com/p/4039c56304258137ae19e8787acc1d1f" />.

## Easter Eggs — proposta visual (não canônica)

- <mention url="https://app.notion.com/p/40e9c5630425817a99ece7192a26c938" />: máquina antiga de arcade inspirada pela série de desafios de otimização Soroban, colocada em área secundária do Warehouse 17, sem interação obrigatória.

<b>Gate:</b> nunca ocupar o espaço da Ghost Key, W17 / DIAGNOSTIC TRACE ou contestação civil; é apenas um objeto de cenário. Ver <mention url="https://app.notion.com/p/2b1d33190ac446bfaea34e7a4db74d92" />.
</content>
</page>

