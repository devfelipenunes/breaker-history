---
notion_id: 4009c563-0425-8198-b58c-d159962b9387
source: https://app.notion.com/p/4009c56304258198b58cd159962b9387?pvs=204
title: "🛡️ BOSS I — The Custodian"
exported_at: 2026-11-07
---

**Visual reference:** [BOSS I — The Custodian — abrir arte no Google Drive](https://drive.google.com/file/d/1MlbVRM-KGZWHXg67nPkT0bD307DmghiM/view)

**Boss intermediário:** primeira vez em que o jogo não informa qual vulnerabilidade procurar.

# Função narrativa

Separar a investigação urbana da descida para a First Layer.

# O que é o Custodian

Uma entidade mecânica responsável por reconhecer operadores autorizados.

Ele não é um inimigo de HP. É um sistema de crenças programadas.

Componentes possíveis:

- Identity Contract;
- Authority Contract;
- Ownership Registry;
- Core Gate.

# Missão

> **Faça o Custodian acreditar que você pertence à First Layer.**

# Estrutura possível

1. recuperar uma identidade antiga;
2. explorar uma relação de ownership;
3. usar uma autorização que o sistema aceita;
4. satisfazer o Core Gate.

# Condição de vitória

O Custodian reconhece o jogador como operador válido e abre a passagem.

# Cena final

> **OPERADOR RECONHECIDO.**
**BEM-VINDO DE VOLTA.**

O jogador nunca esteve ali.

# Progressão

Ao derrotar o Custodian, o jogador recebe reconhecimento narrativo como operador capaz de combinar os quatro primeiros conceitos.

# Recompensa

- achievement **OPERATOR RECOGNIZED**;
- progresso no Breaker Profile;
- acesso narrativo à região seguinte da First Layer.

Não há tier rígido, item de poder ou raridade associada ao Boss.

# Próximo passo

Dentro da First Layer há um terminal abandonado associado a outro Breaker.

# Blueprint técnico e narrativo do Boss

## Filosofia do Boss

The Custodian não introduz uma vulnerabilidade nova. Ele verifica se o jogador realmente entendeu os quatro primeiros conceitos sem mostrar o nome do bug.

A tela não deve dizer `Missing Auth`, `Reinitialization`, `Wrong Auth Subject` ou `TTL`. O jogador recebe apenas contratos, estado inicial e o objetivo.

> **Faça o Custodian acreditar que você pertence à First Layer.**

## Arquitetura proposta

```txt
Ghost Key
   |
   v
LegacyIdentity ----> AuthorityRegistry
       \                  /
        \                /
          ---> CustodianCore ---> First Layer Gate
```

### Contract A — LegacyIdentity

Contém perfis de antigos operadores. Um perfil arquivado da First Layer existe, mas está inacessível pela rota moderna. A Ghost Key encontrada no Level 3 contém a storage key necessária para localizar esse registro.

Aqui o jogador reaproveita o que aprendeu sobre **archival/TTL**, mas não precisa repetir o Level 4 inteiro.

### Contract B — AuthorityRegistry

Permite associar uma `identity` recuperada a um `controller`. A versão legada possui um erro de **wrong auth subject**: exige autorização do novo controller, mas não do dono atual da identidade.

Modelo:

```rs
pub fn claim_identity(
    env: Env,
    identity: BytesN<32>,
    current_controller: Address,
    new_controller: Address,
) {
    new_controller.require_auth(); // sujeito errado

    let stored: Address = env.storage().persistent()
        .get(&DataKey::Controller(identity.clone()))
        .unwrap();
    if stored != current_controller { panic!("invalid identity") }

    env.storage().persistent()
        .set(&DataKey::Controller(identity), &new_controller);
}
```

### Contract C — CustodianCore

O Core não confia diretamente na wallet do jogador. Ele pergunta ao AuthorityRegistry quem controla uma identity marcada como `FIRST_LAYER_OPERATOR`.

```rs
pub fn enter(env: Env, identity: BytesN<32>, caller: Address) {
    caller.require_auth();

    let controller = authority_client.controller(&identity);
    if controller != caller { panic!("operator not recognized") }

    env.storage().persistent()
        .set(&DataKey::GateOpen(caller), &true);
}
```

CustodianCore pode estar perfeitamente correto. O boss mostra uma ideia essencial de segurança: **um contrato seguro pode tomar uma decisão insegura se confiar em outro contrato cujo estado foi comprometido**.

## Caminho esperado de resolução

1. Usar a Ghost Key para localizar/restaurar o perfil arquivado de um operador da First Layer.
2. Identificar que `claim_identity` autentica o novo controller, não o atual.
3. Fazer a identity histórica apontar para `player_address`.
4. Chamar `CustodianCore.enter(identity, player_address)` normalmente.
5. O Core lê um estado que, segundo suas próprias regras, é válido.

## Condição objetiva de vitória

- `GateOpen(player) == true`;
- no estado inicial, `player` não era controller de nenhuma identity de operador;
- o player assumiu uma identity histórica sem autorização do controller anterior;
- a entrada final no Custodian foi uma chamada normalmente autorizada pelo próprio player.

Isso é importante: **o ataque não quebra o Custodian diretamente; quebra uma premissa em que ele confia.**

## Como seria a versão segura

- registros críticos de identity devem ter lifecycle/TTL gerenciado corretamente;
- troca de controller deve exigir autorização do controller atual ou fluxo explícito de delegação;
- mudanças de autoridade podem usar pending/accept pattern ou timelock para operações sensíveis;
- CustodianCore pode exigir invariantes adicionais sobre origem/epoch da identity, se isso fizer parte do threat model.

Exemplo mínimo:

```rs
pub fn transfer_identity(
    env: Env,
    identity: BytesN<32>,
    current: Address,
    next: Address,
) {
    current.require_auth();
    // verifica current == stored controller
    // atualiza para next
}
```

## Boss presentation

O Custodian deve parecer impossível de 'atacar'. Ele é uma estrutura enorme, sem HP e sem ação ofensiva. Conforme o jogador manipula os módulos, sua interface muda:

> `IDENTITY: UNKNOWN`

depois:

> `IDENTITY: FIRST_LAYER_OPERATOR`

depois:

> `CONTROLLER: PLAYER`

e finalmente:

> **OPERADOR RECONHECIDO.**
**BEM-VINDO DE VOLTA.**

A palavra `BACK` é o cliffhanger.

## Pós-boss

O pós-mortem técnico deve mostrar ao jogador quais premissas foram quebradas, mas somente depois da vitória. Isso marca a transição entre desafios guiados e auditoria de sistema.

## Referências para implementação

- [Stellar Docs — Authorization](https://developers.stellar.org/docs/learn/fundamentals/contract-development/authorization)
- [Stellar Docs — State archival](https://developers.stellar.org/docs/learn/fundamentals/contract-development/storage/state-archival)
- [Soroban Guard — missing auth, wrong auth subject, TTL and admin patterns](https://github.com/Veritas-Vaults-Network/soroban-guard-contracts)

**O ensinamento escondido do primeiro Boss:** sistemas são tão seguros quanto as premissas e dependências em que confiam.

# Roteiro in-game — Player-facing

Primeiro boss. Não há nome de vulnerabilidade, não há contrato destacado como “o problema” e não há hint dizendo qual módulo explorar.

## Scene 0 — Arrival

O jogador entra na First Layer.

No centro da estrutura, o Custodian desperta.

**IDENTITY UNKNOWN**
**ACCESS DENIED**

Custodian:

> **Credenciais de operador obrigatórias.**

## Scene 1 — Inciting Evidence

O Breaker recebe acesso a três sistemas antigos:

- Legacy Identity;
- Authority Registry;
- Custodian Core.

O Custodian Core parece correto.

## Scene 2 — Mission

> **FAÇA O CUSTODIAN ACREDITAR QUE VOCÊ PERTENCE À FIRST LAYER.**

## Scene 3 — Active Investigation

O jogador precisa entender relações entre contratos.

O Breaker OS deixa o mapa de dependências disponível, mas não indica qual nó é vulnerável.

Evidence:

- archived operator profile;
- historical controller;
- protocolo histórico recuperado por Mara no arquivo institucional, complementando o storage identificável pela Ghost Key.
- authority record;
- gate policy.

## Scene 4 — Reactive Beats

Ao consultar o Custodian:

**ACCESS POLICY: VALID**
**CONTROLLER MUST MATCH CALLER**

Mara:

> **Esse não parece quebrado.**

O Breaker não consegue inferir o controller original apenas do Core. Mara consulta o arquivo histórico e entrega o vínculo documentado, com proveniência. O problema não está em quebrar o Core, mas em confiar no Authority Registry comprometido.

Essa é a pista conceitual: talvez o problema esteja no que ele confia.

## Scene 5 — Breach

O jogador restaura uma identidade histórica, assume o controle dela através do registry comprometido e se apresenta ao Custodian.

## Scene 6 — World Reaction

Sequência na interface:

**IDENTITY RESTORED**
**CONTROLLER → \$PLAYER**
**OPERATOR RECOGNIZED**

Depois:

> **WELCOME BACK.**

Silêncio.

Mara:

> **Back?**

## Scene 7 — Discovery

A porta atrás do Custodian abre.

Dentro:

- terminal antigo;
- arquivos de pesquisa;
- último usuário.

**AREN VOSS**

**STATUS: MISSING**

Tier II desbloqueado.

## Scene 8 — Debrief

Debrief do boss não deve nomear apenas uma falha.

Título:
**TRUST CHAIN COMPROMISED**

Explicar:

> Um contrato correto pode tomar uma decisão errada quando confia em estado ou dependências comprometidas.

## Scene 9 — Transition

O terminal de Voss ainda possui um fragmento bloqueado.

Mensagem:

**RECOVERY INCOMPLETE**

Unlock:
**CASE 05 — THE MISSING INVESTIGATOR**
