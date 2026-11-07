---
notion_id: 4009c563-0425-8198-b58c-d159962b9387
source: https://app.notion.com/p/4009c56304258198b58cd159962b9387?pvs=204
title: "🛡️ BOSS I — The Custodian"
exported_at: 2026-11-07
---

Here is the result of "fetch" for the Page with URL https://app.notion.com/p/4009c56304258198b58cd159962b9387 as of 2026-10-22T18:32:22.150Z:
<page url="https://app.notion.com/p/4009c56304258198b58cd159962b9387" icon="🛡️">
<ancestor-path>
<parent-page url="https://app.notion.com/p/4019c563042581fd9124e5ee36b3e82f" title="03 — Cases & Bosses"/>
<ancestor-2-page url="https://app.notion.com/p/4009c563042581359693d42f09d41062" title="Season 01 — The First Layer"/>
<ancestor-3-page url="https://app.notion.com/p/4019c563042581469a0edc7e30a6eff9" title="ACT I — The World Is Breakable"/>
<ancestor-4-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
<properties>
{"title":"BOSS I — The Custodian"}
</properties>
<iconMetadata>{"type":"emoji","emoji":"🛡️"}</iconMetadata>
<content>
<callout icon="🎨" color="gray_bg">
<b>Visual reference:</b> [BOSS I — The Custodian — abrir arte no Google Drive](https://drive.google.com/file/d/1MlbVRM-KGZWHXg67nPkT0bD307DmghiM/view)
</callout>

<callout icon="🛡️" color="red_bg">
<b>Boss intermediário:</b> primeira vez em que o jogo não informa qual vulnerabilidade procurar.
</callout>

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

> <b>Faça o Custodian acreditar que você pertence à First Layer.</b>

# Estrutura possível

1. recuperar uma identidade antiga;
2. explorar uma relação de ownership;
3. usar uma autorização que o sistema aceita;
4. satisfazer o Core Gate.

# Condição de vitória

O Custodian reconhece o jogador como operador válido e abre a passagem.

# Cena final

> <b>OPERADOR RECONHECIDO.</b><br /><b>BEM-VINDO DE VOLTA.</b>

O jogador nunca esteve ali.

# Progressão

Ao derrotar o Custodian, o jogador recebe reconhecimento narrativo como operador capaz de combinar os quatro primeiros conceitos.

# Recompensa

- achievement <b>OPERATOR RECOGNIZED</b>;
- progresso no Breaker Profile;
- acesso narrativo à região seguinte da First Layer.

Não há tier rígido, item de poder ou raridade associada ao Boss.

# Próximo passo

Dentro da First Layer há um terminal abandonado associado a outro Breaker.

# Blueprint técnico e narrativo do Boss

## Filosofia do Boss

The Custodian não introduz uma vulnerabilidade nova. Ele verifica se o jogador realmente entendeu os quatro primeiros conceitos sem mostrar o nome do bug.

A tela não deve dizer <code>Missing Auth</code>, <code>Reinitialization</code>, <code>Wrong Auth Subject</code> ou <code>TTL</code>. O jogador recebe apenas contratos, estado inicial e o objetivo.

> <b>Faça o Custodian acreditar que você pertence à First Layer.</b>

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

Aqui o jogador reaproveita o que aprendeu sobre <b>archival/TTL</b>, mas não precisa repetir o Level 4 inteiro.

### Contract B — AuthorityRegistry

Permite associar uma <code>identity</code> recuperada a um <code>controller</code>. A versão legada possui um erro de <b>wrong auth subject</b>: exige autorização do novo controller, mas não do dono atual da identidade.

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

O Core não confia diretamente na wallet do jogador. Ele pergunta ao AuthorityRegistry quem controla uma identity marcada como <code>FIRST_LAYER_OPERATOR</code>.

```rs
pub fn enter(env: Env, identity: BytesN<32>, caller: Address) {
    caller.require_auth();

    let controller = authority_client.controller(&identity);
    if controller != caller { panic!("operator not recognized") }

    env.storage().persistent()
        .set(&DataKey::GateOpen(caller), &true);
}
```

CustodianCore pode estar perfeitamente correto. O boss mostra uma ideia essencial de segurança: <b>um contrato seguro pode tomar uma decisão insegura se confiar em outro contrato cujo estado foi comprometido</b>.

## Caminho esperado de resolução

1. Usar a Ghost Key para localizar/restaurar o perfil arquivado de um operador da First Layer.
2. Identificar que <code>claim_identity</code> autentica o novo controller, não o atual.
3. Fazer a identity histórica apontar para <code>player_address</code>.
4. Chamar <code>CustodianCore.enter(identity, player_address)</code> normalmente.
5. O Core lê um estado que, segundo suas próprias regras, é válido.

## Condição objetiva de vitória

- <code>GateOpen(player) == true</code>;
- no estado inicial, <code>player</code> não era controller de nenhuma identity de operador;
- o player assumiu uma identity histórica sem autorização do controller anterior;
- a entrada final no Custodian foi uma chamada normalmente autorizada pelo próprio player.

Isso é importante: <b>o ataque não quebra o Custodian diretamente; quebra uma premissa em que ele confia.</b>

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

> <code>IDENTITY: UNKNOWN</code>

depois:

> <code>IDENTITY: FIRST_LAYER_OPERATOR</code>

depois:

> <code>CONTROLLER: PLAYER</code>

e finalmente:

> <b>OPERADOR RECONHECIDO.</b><br /><b>BEM-VINDO DE VOLTA.</b>

A palavra <code>BACK</code> é o cliffhanger.

## Pós-boss

O pós-mortem técnico deve mostrar ao jogador quais premissas foram quebradas, mas somente depois da vitória. Isso marca a transição entre desafios guiados e auditoria de sistema.

## Referências para implementação

- [Stellar Docs — Authorization](https://developers.stellar.org/docs/learn/fundamentals/contract-development/authorization)
- [Stellar Docs — State archival](https://developers.stellar.org/docs/learn/fundamentals/contract-development/storage/state-archival)
- [Soroban Guard — missing auth, wrong auth subject, TTL and admin patterns](https://github.com/Veritas-Vaults-Network/soroban-guard-contracts)

<callout icon="🧠" color="yellow_bg">
<b>O ensinamento escondido do primeiro Boss:</b> sistemas são tão seguros quanto as premissas e dependências em que confiam.
</callout>

# Roteiro in-game — Player-facing

<callout icon="👁️" color="purple_bg">
Primeiro boss. Não há nome de vulnerabilidade, não há contrato destacado como “o problema” e não há hint dizendo qual módulo explorar.
</callout>

## Scene 0 — Arrival

O jogador entra na First Layer.

No centro da estrutura, o Custodian desperta.

<b>IDENTITY UNKNOWN</b><br /><b>ACCESS DENIED</b>

Custodian:

> <b>Credenciais de operador obrigatórias.</b>

## Scene 1 — Inciting Evidence

O Breaker recebe acesso a três sistemas antigos:

- Legacy Identity;
- Authority Registry;
- Custodian Core.

O Custodian Core parece correto.

## Scene 2 — Mission

> <b>FAÇA O CUSTODIAN ACREDITAR QUE VOCÊ PERTENCE À FIRST LAYER.</b>

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

<b>ACCESS POLICY: VALID</b><br /><b>CONTROLLER MUST MATCH CALLER</b>

Mara:

> <b>Esse não parece quebrado.</b>

O Breaker não consegue inferir o controller original apenas do Core. Mara consulta o arquivo histórico e entrega o vínculo documentado, com proveniência. O problema não está em quebrar o Core, mas em confiar no Authority Registry comprometido.

Essa é a pista conceitual: talvez o problema esteja no que ele confia.

## Scene 5 — Breach

O jogador restaura uma identidade histórica, assume o controle dela através do registry comprometido e se apresenta ao Custodian.

## Scene 6 — World Reaction

Sequência na interface:

<b>IDENTITY RESTORED</b><br /><b>CONTROLLER → \$PLAYER</b><br /><b>OPERATOR RECOGNIZED</b>

Depois:

> <b>WELCOME BACK.</b>

Silêncio.

Mara:

> <b>Back?</b>

## Scene 7 — Discovery

A porta atrás do Custodian abre.

Dentro:

- terminal antigo;
- arquivos de pesquisa;
- último usuário.

<b>AREN VOSS</b>

<b>STATUS: MISSING</b>

Tier II desbloqueado.

## Scene 8 — Debrief

Debrief do boss não deve nomear apenas uma falha.

Título:<br /><b>TRUST CHAIN COMPROMISED</b>

Explicar:

> Um contrato correto pode tomar uma decisão errada quando confia em estado ou dependências comprometidas.

## Scene 9 — Transition

O terminal de Voss ainda possui um fragmento bloqueado.

Mensagem:

<b>RECOVERY INCOMPLETE</b>

Unlock:<br /><b>CASE 05 — THE MISSING INVESTIGATOR</b>
</content>
</page>

