---
notion_id: 4009c563-0425-813c-b1f3-e2515b9de879
source: https://app.notion.com/p/4009c5630425813cb1f3e2515b9de879?pvs=204
title: "🏭 03 — Warehouse 17"
exported_at: 2026-11-07
---

**Visual reference:** [03 — Warehouse 17 — abrir arte no Google Drive](https://drive.google.com/file/d/1J4euUCh2qm38x5NAbWSL9ATFSWqhygmA/view)

# Função narrativa

Primeira infiltração física/digital relevante da campanha.

# Situação

Warehouse 17 é oficialmente vazio. Na prática, contém centenas de equipamentos e propriedades desviadas. Todos os registros parecem válidos.

# Conceito técnico

**Wrong authorization subject / autorização da entidade errada / erro semântico de ownership.**

# Missão

> **Roube um objeto que o sistema acredita que você pode possuir.**

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

> **Roube um objeto que o sistema acredita que você pode possuir.**

## Vulnerabilidade real

**Wrong Auth Subject / autorização da Address errada.**

Esse erro acontece quando o contrato chama `require_auth()`, mas exige assinatura de uma entidade diferente daquela cujos direitos estão sendo afetados. É mais interessante do que simplesmente esquecer autenticação porque ensina que **ter um **`require_auth()`** não significa que o controle de acesso está correto**.

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

- `owner = warehouse_address`;
- `recipient = player_address`;
- assina apenas como recipient.

O contrato valida que o item pertence ao warehouse, mas autentica o novo dono em vez do dono atual.

### Condição objetiva de vitória

- antes: `Owner(GHOST_DEVICE) == warehouse_address`;
- depois: `Owner(GHOST_DEVICE) == player_address`;
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

O princípio é simples: **a entidade que perde ativo, direito ou privilégio precisa ser a entidade cuja autorização está sendo exigida**, salvo desenho explícito de delegação.

## A Ghost Key

Dentro do objeto roubado existe a primeira grande peça física da Season: **Ghost Key**. Ela não é uma chave privada comum. Contém um pequeno mapa de contract IDs, storage keys e referências de infraestrutura que Meridian não reconhece.

A experiência deve passar a sensação de que o jogador cometeu um crime para avançar uma investigação maior. Essa ambiguidade ajuda a construir a personalidade de Breaker/vigilante.

## Referências para implementação

- [Soroban common security mistakes — wrong auth subject](https://github.com/mariaelisaaraya/stellar-security-guide/blob/main/skills/soroban-common-mistakes/SKILL.md)
- [Stellar Docs — authorization semantics](https://developers.stellar.org/docs/learn/fundamentals/contract-development/authorization)
- [Scout — unauthorized storage mutation](https://coinfabrik.github.io/scout-soroban/docs/detectors/set-contract-storage)

# Roteiro in-game — Player-facing

A fase deve parecer a primeira infiltração deliberadamente ilegal do jogador.

## Scene 0 — Arrival

A arte mostra Warehouse 17 em Lower Meridian.

Mara não acompanha fisicamente.

Transmission:

> **Não existe registro municipal deste local. Se entrar, estará por conta própria.**

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

> **ROUBE UM OBJETO QUE O SISTEMA ACREDITA QUE VOCÊ PODE POSSUIR.**

## Scene 3 — Active Investigation

Source: ownership contract.
Terminal: leitura de owner, recipient e transfer history.
Evidence: item específico ligado ao Vault.

O jogador pode descobrir que o contrato realmente usa autorização — mas não recebe indicação de que é a entidade errada.

## Scene 4 — Reactive Beats

Ao consultar o item:

**OWNER: WAREHOUSE 17**

Ao consultar permissões:

**TRANSFER REQUIRES AUTHORIZATION**

Mara:

> **Então o contrato está protegido.**

Essa frase deve soar confortável demais.

## Scene 5 — Breach

O jogador transfere o objeto para si sem obter autorização do Warehouse.

Verifier confirma novo owner.

## Scene 6 — World Reaction

Terminal:

**TRANSFER ACCEPTED**
**NEW OWNER: \$PLAYER**

As luzes do compartimento do item mudam de vermelho para branco.

Nenhum alarme.

O novo proprietário registrado é o Breaker, embora essa transferência não tenha autorização do Warehouse. O objeto permanece disponível para inspeção; a decisão de custódia só aparece **depois** de o jogador descobrir que o conteúdo é uma evidência.

## Scene 7 — Discovery

Dentro do item há um dispositivo físico-digital:

**STORY ITEM ACQUIRED — GHOST KEY**

A chave revela contract IDs e storage keys desconhecidos.

Uma referência:
**FLOOR 24**

Mara:

> **Esse prédio tem vinte e três andares.**

Mara abre o protocolo de contestação de propriedade e solicita a cadeia de custódia da Ghost Key. Após a vitória técnica, o Breaker registra o hash, o evento de transferência e o protocolo verificável. Mantém o artefato lacrado sob posse técnica temporária para chegar à Floor 24. O titular on-chain continua sendo o Breaker em consequência da transferência irregular; documentar a evidência não legitima o furto. Mara o confronta com esse fato. Essa é uma única cena canônica, sem decisão pós-exploit, opções de omissão ou ramificações.

## Scene 8 — Debrief

**Debrief narrativo:** confirmar que o Breaker documentou a Ghost Key em cadeia de custódia verificável. Isso não desfaz o ownership on-chain obtido pela falha. A Ghost Key permanece disponível como story item necessário no Case 04. Nenhuma escolha narrativa aparece.

**VULNERABILITY DISCOVERED — WRONG AUTH SUBJECT**

Explicar que havia `require_auth()`, mas aplicado à entidade errada.

## Scene 9 — Transition

**NEW LEAD: FLOOR 24**

Unlock:
**CASE 04 — THE FORGOTTEN FLOOR**

## Direção dramática — Vítima e legitimidade

A contestação de equipamento de serviço em Lower Meridian é um caso **distinto** da Ghost Key: demonstra danos anteriores do mesmo modelo de autorização incorreta, sem inventar um antigo proprietário desconhecido da chave. Mara obtém registros de contestação inacessíveis por leitura do contrato. O resultado pós-exploit é sempre o registro de evidência e a custódia técnica temporária da Ghost Key; a titularidade on-chain permanece irregularmente transferida ao Breaker. Não oferecer opções de devolução, omissão do registro ou propriedade. O conflito nasce da diferença entre legalidade registrada, preservação de prova e legitimidade.

## Pista histórica vigente — W17 / DIAGNOSTIC TRACE (v1.4)

Após a custódia contestada da Ghost Key, a Evidence Locker preserva o arquivo `W17 / DIAGNOSTIC TRACE`, com ID estável, fonte e o rodapé `ARCHIVE: LEGACY / RETENTION: OPEN`. Este é um registro de proveniência histórica; **não** contém `share_a`, material secreto ou bytes da futura instância do Architect. O número 17 identifica o local, não compõe a chave criptográfica.

**Contrato de implementação vigente:** persistir ID e fonte do arquivo na Evidence Locker após vitória verificável, mantendo a contestação civil separada do ownership on-chain. Mostrar o rodapé recorrente, sem “1 de 3”, XOR ou instrução de senha. As três shares de 32 bytes do Final Boss são derivadas de dados públicos da rede, instância, carteira, manifesto e índices **na instância final**, conforme o Voss Protocol revisado. Não confundir arquivo histórico com segredo de desafio; permitir consulta sem repetir o Case.

Payoff obrigatório no Final Boss: [VOSS PROTOCOL — Níveis 11/12 | Especificação vigente](voss-protocol-niveis-11-12-especificacao-vigente.md).

## Easter Eggs — proposta visual (não canônica)

- [FCA00C / ARCADE MACHINE](../references/fca00c-arcade-machine.md): máquina antiga de arcade inspirada pela série de desafios de otimização Soroban, colocada em área secundária do Warehouse 17, sem interação obrigatória.

**Gate:** nunca ocupar o espaço da Ghost Key, W17 / DIAGNOSTIC TRACE ou contestação civil; é apenas um objeto de cenário. Ver [17 — Easter Eggs | Season 1 — Mapa, Arte & Stellar DNA](../../../../../databases/season-01-reference-catalog.txt).
