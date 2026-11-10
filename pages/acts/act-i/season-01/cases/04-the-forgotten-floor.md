---
notion_id: 4009c563-0425-8150-84b7-dd82afc14074
source: https://app.notion.com/p/4009c5630425815084b7dd82afc14074?pvs=204
title: "🗄️ 04 — The Forgotten Floor"
exported_at: 2026-11-07
---

**Visual reference:** [04 — The Forgotten Floor — abrir arte no Google Drive](https://drive.google.com/file/d/1EBYhb6yN8t6HUV0pfGfd2Dd90v3nHR74/view)

# Função narrativa

Introduzir a ideia de memória imperfeita na infraestrutura e revelar que Meridian possui uma camada esquecida.

# Situação

O elevador principal da instalação possui referência a um andar inexistente. Não é bloqueado: ele simplesmente não aparece.

# Conceito técnico

**Renovação de TTL com alvo implícito (off-by-one): a função renova o andar seguinte ao argumento.**

# Missão

> **Faça o sistema lembrar aquilo que foi projetado para esquecer.**

# Condição de vitória

Descobrir o andar que não aparece no índice e renovar o TTL da entrada 24 — `renew_floor(23)` renova o andar seguinte.

# Resultado

O andar oculto reaparece.

Nos registros recuperados:

**ARCHIVED ENTRY RECOVERED**
**ORIGIN: UNKNOWN**
**STATUS: OBSERVED**

# Revelação

Surge a primeira referência a:

## THE FIRST LAYER

# Próximo passo

A única entrada é protegida pelo Custodian.

# Blueprint técnico e narrativo da fase

## A cena

A Ghost Key contém referência a um andar abaixo de Lower Meridian, mas os terminais de transporte não exibem esse andar. O detalhe estranho: o índice do elevador ainda possui uma lacuna entre dois números. Não é um andar bloqueado. É como se o sistema tivesse **esquecido que ele existia**.

O Breaker encontra um antigo `AccessRecord` persistente cujo andar não aparece no índice. A missão deixa de ser 'hackear uma porta' e vira recuperar memória da própria cidade.

> **Faça o sistema lembrar aquilo que foi projetado para esquecer.**

## Conceito técnico — TTL com alvo implícito

**Renovação de TTL no alvo errado (off-by-one).** Este Case não depende de esperar archival nem de restore por footprint. O andar 24 existe no storage persistente e não aparece no índice (1–23). `renew_floor(floor_id)` estende o TTL do andar **seguinte** ao argumento e marca `Renewed(floor_id + 1)`. Chamar `renew_floor(24)` renova 25; para renovar 24 é preciso chamar `renew_floor(23)`.

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

O comentário do revisor: `target` não é o argumento; é o sucessor. O jogador que passa 24 renova 25 — e não recebe erro nenhum.

Nesta implementação a entrada não é arquivada: o registro 24 nasce ativo e o teste só exige que o TTL avance. A lição de archival fica para a documentação de Soroban, não para o exploit.

### Como o challenge é jogável

Não há espera de dias nem simulação de archival: a instância nasce com o registro 24 ativo e o índice sem ele. O jogador precisa descobrir:

1. que o índice lista 1–23 mas a referência aponta 24;
2. que `floor(24)` existe e devolve `FIRST LAYER`;
3. que `renew_floor` age sobre o **andar seguinte** ao argumento — logo, 23 renova 24;
4. confirmar `renewed(24) == true`. O teste do nível também mede o TTL antes e depois para provar que a renovação aconteceu de verdade.

### Condição objetiva de vitória

- `renewed(24) == true`;
- `floor(24) == "FIRST LAYER"`;
- o TTL da entrada `Floor(24)` avançou em relação ao estado inicial (o teste do nível compara antes e depois).

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

O alvo é sempre o argumento. Se a intenção for renovar "o seguinte", que o nome da função e o argumento digam isso — `renew_next_floor(previous_id)` — em vez de esconder a soma dentro da função.

Também podemos ensinar o padrão **bump-on-access**, em que leituras de dados ativos estendem a vida do registro quando o TTL cai abaixo de determinado threshold.

## Revelação narrativa

Quando o andar reaparece no mapa, o sistema recupera três linhas antigas:

**ARCHIVED ENTRY RECOVERED**
**ORIGIN: UNKNOWN**
**STATUS: OBSERVED**

A Ghost Key desbloqueia uma entrada chamada apenas:

> **FIRST LAYER**

Essa é a primeira vez que o jogador entende que existe uma infraestrutura enterrada sob Meridian.

## Referências para implementação

- [Stellar Docs — State archival](https://developers.stellar.org/docs/learn/fundamentals/contract-development/storage/state-archival)
- [Stellar Docs — Choosing storage types](https://developers.stellar.org/docs/build/guides/storage/choosing-the-right-storage)
- [Stellar Docs — Storage strategies / bump-on-access](https://developers.stellar.org/docs/build/guides/storage/storage-strategies)
- [Soroban Guard — missing TTL vulnerability](https://github.com/Veritas-Vaults-Network/soroban-guard-contracts/blob/main/docs/vulnerabilities.md)

# Roteiro in-game — Player-facing

## Scene 0 — Arrival

A Ghost Key guia o jogador até uma instalação antiga.

Elevador:
**01–23**

Não existe 24.

Mara:

> **Blueprints confirm twenty-three floors.**

**Continuidade obrigatória de Warehouse 17:** Mara confirma que recebeu o hash e o protocolo de custódia da Ghost Key, mas lembra que o contrato ainda aponta o Breaker como proprietário por causa de uma transferência não autorizada. A investigação avança com a chave preservada. A cena e o diálogo são os mesmos para todos os jogadores.

## Scene 1 — Inciting Evidence

A Ghost Key responde apenas perto do elevador.

Evidence:

- building blueprint;
- old ledger references;
- archived storage key;
- Ghost Key resonance.

## Scene 2 — Mission

> **FAÇA MERIDIAN LEMBRAR O QUE ESQUECEU.**

## Scene 3 — Active Investigation

Source e storage inspector mostram referências antigas, mas parte do estado não está disponível diretamente.

O terminal pode exibir:
**FLOOR NOT IN INDEX**

e, após investigação:
**LEGACY ROUTE DETECTED**

Nenhuma explicação de TTL é dada antes da solução.

## Scene 4 — Reactive Beats

Mara:

> **Se o andar foi demolido, deveria existir um registro de demolição.**

Ela não encontra ordem de demolição nem autorização de remoção. Essa investigação independente impede que o Breaker confunda um histórico expirado com destruição física comprovada.

Breaker:

> **Não existe.**

## Scene 5 — Breach

O jogador percebe que a função de renovação age sobre o andar **seguinte** ao argumento e chama `renew_floor(23)`. A interface/indexador do elevador volta a enxergar a rota 24. Não simular que a chamada Soroban executa normalmente com um storage arquivado e o ressuscita sozinha dentro do contrato.

## Scene 6 — World Reaction

O painel do elevador falha por um instante.

Surge:

**24**

As luzes mudam.

O elevador desce/sobe além do mapa conhecido.

## Scene 7 — Discovery

No novo andar:

**I // FIRST LAYER**

A Ghost Key não era uma chave para uma porta; era uma chave para uma infraestrutura esquecida.

O Floor 24 não é a First Layer inteira. É apenas uma entrada física para a rede de sistemas legados que sustenta partes da Meridian moderna.

Ao fundo, um sistema desperta:

**CUSTODIAN ONLINE**

## Scene 8 — Debrief

**CONCEPT DISCOVERED — RENEWAL TARGET MISMATCH (OFF-BY-ONE)**

Mostrar por que estado pode expirar/arquivar e como manter dados críticos disponíveis.

## Scene 9 — Transition

A porta principal do andar permanece bloqueada.

Mensagem:

**IDENTITY UNKNOWN**

Unlock:
**BOSS I — THE CUSTODIAN**

## Pista histórica vigente — F24 / ARCHIVED ENTRY (v1.4)

Após a renovação explícita da entrada **Persistent**, `F24 / ARCHIVED ENTRY` volta a ser consultável e recebe o rodapé `ARCHIVE: LEGACY / RETENTION: OPEN`, o mesmo de W17. Este registro histórico **não** contém `share_b` nem bytes secretos da futura instância final. O número 24 identifica o andar que havia sumido do índice moderno, não um componente de senha.

**Contrato de implementação vigente:** o verificador confirma `renewed(24)` e `floor(24) == FIRST LAYER`; o teste do nível também mede o TTL da entrada 24 antes e depois para provar que ele avançou. Não há simulação de archival nem de restore por footprint nesta implementação. Depois da vitória, preservar ID, chave e proveniência F24 na Evidence Locker, sem nova vulnerabilidade. A prova contextual do Final Boss é calculada com dados públicos da instância final, não armazenada previamente em Floor 24.

Payoff obrigatório no Final Boss: [VOSS PROTOCOL — Níveis 11/12 | Especificação vigente](voss-protocol-niveis-11-12-especificacao-vigente.md).

## Easter Eggs — propostas visuais (não canônicas)

- [JUMP CANNON / OLD FOUNDRY](../references/jump-cannon-old-foundry.md): assinatura de engenharia antiga em uma bancada ou placa lateral do Floor 24, inspirada no codinome de Soroban.
- [ÁBACO DA VELHA ENGENHARIA](../references/abaco-da-velha-engenharia.md): ábaco japonês discreto que remete ao nome Soroban, como item ambiental.

**Gate:** a porta 24, o TTL e F24 / ARCHIVED ENTRY continuam as únicas referências desta etapa necessárias ao CTF. Essas inclusões não devem sugerir senha, shares, criptografia escondida nem uma porta extra. Ver [17 — Easter Eggs | Season 1 — Mapa, Arte & Stellar DNA](../../../../../databases/season-01-reference-catalog.txt).
