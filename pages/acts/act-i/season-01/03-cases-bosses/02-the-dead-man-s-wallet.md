---
notion_id: 4009c563-0425-816d-96c0-f22627a7f6ae
source: https://app.notion.com/p/4009c5630425816d96c0f22627a7f6ae?pvs=204
title: "👤 02 — The Dead Man's Wallet"
exported_at: 2026-11-07
---

Here is the result of "fetch" for the Page with URL https://app.notion.com/p/4009c5630425816d96c0f22627a7f6ae as of 2026-11-04T15:32:21.620Z:
<page url="https://app.notion.com/p/4009c5630425816d96c0f22627a7f6ae" icon="👤">
<ancestor-path>
<parent-page url="https://app.notion.com/p/4019c563042581fd9124e5ee36b3e82f" title="03 — Cases & Bosses"/>
<ancestor-2-page url="https://app.notion.com/p/4009c563042581359693d42f09d41062" title="Season 01 — The First Layer"/>
<ancestor-3-page url="https://app.notion.com/p/4019c563042581469a0edc7e30a6eff9" title="ACT I — The World Is Breakable"/>
<ancestor-4-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
<properties>
{"title":"02 — The Dead Man's Wallet"}
</properties>
<iconMetadata>{"type":"emoji","emoji":"👤"}</iconMetadata>
<content>
<callout icon="🎨" color="gray_bg">
<b>Visual reference:</b> [02 — The Dead Man's Wallet — abrir arte no Google Drive](https://drive.google.com/file/d/1LfN58kl31c_fHLgisTZaCIaS5YBPvJXl/view)
</callout>

# Função narrativa

Transformar o caso financeiro em investigação de identidade.

# Situação

A trilha de serviço da movimentação do Vault cita a identidade de operador legada atribuída a um técnico morto há seis meses. Trata-se de um registro de operação e de identidade — <b>não</b> da custódia dos 2,4 milhões. O destino financeiro final só será comprovado no desfecho.

# Conceito técnico

<b>Reinitialization / inicialização reaproveitável / takeover de estado administrativo.</b>

# Missão

> <b>Torne-se alguém que não deveria mais existir.</b>

# Condição de vitória

Explorar o contrato de registro para reassumir ou reconfigurar identidade/propriedade que deveria estar permanentemente definida.

# Resultado

O jogador acessa registros privados vinculados à identidade morta.

Entre eles:

> <b>WAREHOUSE 17</b>

# Próximo passo

Warehouse 17 aparece em Lower Meridian.

# Blueprint técnico e narrativo da fase

## A investigação

A trilha da rota de serviço cita um <b>identificador de operador legado</b> de Elias Var, técnico declarado morto seis meses antes. O identificador é metadado de manutenção, <b>não</b> prova de que a wallet de Elias recebeu, enviou ou custodiou os 2,4 milhões. A Authority inicialmente suspeita de uma chave comprometida; o Breaker investiga o contrato que define <b>quem controla aquele perfil</b>.

O jogador chega a um registry antigo usado para vincular uma identidade a um administrador. O contrato foi implantado antes de Meridian adotar constructors atômicos. Existe uma função pública <code>initialize(admin)</code> usada na instalação original.

A interface narrativa pede:

> <b>Torne-se alguém que não deveria mais existir.</b>

## Vulnerabilidade real

<b>Reinitialization / insecure initialization.</b>

Uma função de inicialização que pode ser chamada mais de uma vez permite sobrescrever admin, owner ou configuração crítica. Em contratos modernos, <code>__constructor</code> é executado pelo host durante o deployment e elimina a janela de uma inicialização separada. A documentação atual da Stellar usa esse padrão justamente para que deploy e init ocorram de forma atômica.

### Contrato vulnerável

```rs
pub fn initialize(env: Env, admin: Address) {
    admin.require_auth();
    // VULNERÁVEL: não verifica se já foi inicializado.
    env.storage().instance().set(&DataKey::Admin, &admin);
}

pub fn read_private_record(env: Env, admin: Address) -> Bytes {
    admin.require_auth();
    let stored: Address = env.storage().instance().get(&DataKey::Admin).unwrap();
    if stored != admin { panic!("not admin"); }
    env.storage().instance().get(&DataKey::Record).unwrap()
}

pub fn release(env: Env, admin: Address) {
    admin.require_auth();
    let stored: Address = env.storage().instance().get(&DataKey::Admin).unwrap();
    if stored != admin { panic!("not admin"); }
    // move o saldo do endereço do contrato para o admin
}
```

### Exploit esperado

O jogador chama novamente <code>initialize(player)</code> e transforma a própria Address no admin do registry. Em seguida, <code>read_private_record(player)</code> devolve o registro (<code>WAREHOUSE 17 // LOWER MERIDIAN // DO NOT USE CITY ROUTING</code>) e <code>release(player)</code> move o saldo que estava no endereço do contrato para o player. Não existe serviço externo: o registro é lido do próprio contrato, e a autorização controla quem chama cada método, não a confidencialidade dos dados.

### Condição objetiva de vitória

- <code>admin() == player</code> depois de o contrato já ter sido inicializado anteriormente;
- <code>released() == true</code>, com o saldo transferido para o player (<code>balance(player) &gt; 0</code>);
- <code>read_private_record(player)</code> devolve a pista <code>WAREHOUSE 17</code>;
- o verificador on-chain exige admin, liberação e saldo; a leitura do registro é condição narrativa, não do validador.

## Solução segura

### Opção preferida

Usar <code>__constructor</code>, inicializado durante o deployment:

```rs
pub fn __constructor(env: Env, admin: Address) {
    env.storage().instance().set(&DataKey::Admin, &admin);
}
```

### Quando uma função initialize separada for inevitável

```rs
pub fn initialize(env: Env, admin: Address) {
    if env.storage().instance().has(&DataKey::Admin) {
        panic!("already initialized");
    }
    admin.require_auth();
    env.storage().instance().set(&DataKey::Admin, &admin);
}
```

Para um challenge introdutório, podemos usar o segundo padrão vulnerável porque a exploração fica evidente. No pós-missão, mostramos que o design moderno recomendado é preferir constructor atômico quando possível.

## História após o exploit

Quando a identidade é assumida, o terminal não mostra dinheiro nem contatos. O Breaker OS lê o registro direto do contrato, autenticado como o admin que o player acabou de se tornar. O morto deixou um único registro preservado:

> <code>WAREHOUSE 17 // LOWER MERIDIAN // DO NOT USE CITY ROUTING</code>

Isso muda a investigação: alguém usou uma identidade morta não para esconder dinheiro, mas para esconder <b>um destino físico</b>.

## Referências para implementação

- [Stellar Docs — Dapp initialization and ](https://developers.stellar.org/docs/build/guides/dapps/initialization)[<code>__constructor</code>](https://developers.stellar.org/docs/build/guides/dapps/initialization)
- [Stellar Docs — deployment constructors](https://developers.stellar.org/docs/learn/migrate/evm/smart-contract-deployment)
- [Soroban common security mistakes — reinitialization](https://github.com/mariaelisaaraya/stellar-security-guide/blob/main/skills/soroban-common-mistakes/SKILL.md)
- [Real 2026 discussion — initialization/front-running risk](https://github.com/YieldAnchor/yield-general/issues/8)

# Roteiro in-game — Player-facing

<callout icon="🎮" color="blue_bg">
O jogador deve sentir que está perseguindo a trilha deixada pelo roubo, não estudando “reinitialization”.
</callout>

## Scene 0 — Arrival

A investigação começa exatamente no registro encontrado no Vault.

Tela:<br /><b>IDENTITY RECORD FOUND</b>

Status:<br /><b>OWNER: DECEASED</b>

Mara Vale:

> <b>Esse registro de identidade foi desativado há seis meses.</b>

Breaker:

> <b>Então por que Meridian a aceitou?</b>

## Scene 1 — Inciting Evidence

Evidence inicial:

- death record;
- wallet status;
- last activity;
- registry contract;
- administrative controller histórico;
- campo <code>OPERATOR IDENTITY</code> separado de <code>FINANCIAL DESTINATION</code>; a wallet não aparece como destino comprovado dos fundos.

Uma divergência aparece: o registro civil diz <b>DECEASED</b>, mas o registry técnico ainda responde.

## Scene 2 — Mission

Mission strip:

> <b>TORNE-SE ALGUÉM QUE NÃO DEVERIA MAIS EXISTIR.</b>

Não mostrar “initialize”, “admin takeover” ou o nome da vulnerabilidade como hint inicial.

## Scene 3 — Active Investigation

Disponível no Breaker OS:

- Source do identity registry;
- ABI;
- storage atual;
- terminal;
- histórico de inicialização.

Comandos narrativos possíveis:<br /><code>contract call admin</code><br /><code>contract functions $TARGET</code><br /><code>storage inspect identity</code>

Resposta do sistema:<br /><b>IDENTITY STATUS: LEGACY</b>

## Scene 4 — Reactive Beats

Se o jogador consultar o histórico:

> <b>SYSTEM: Registro de inicialização encontrado.</b>

Mara:

> <b>A identidade foi encerrada corretamente. A chave deveria ser inútil.</b>

A fala direciona a atenção para a diferença entre chave e estado sem explicar o exploit.

## Scene 5 — Breach

O jogador consegue fazer o sistema reconhecer sua própria Address como autoridade daquela identidade morta.

Verifier confirma.

## Scene 6 — World Reaction

Terminal:

<b>IDENTITY CONTROLLER UPDATED</b><br /><b>ACCESS PROFILE RESTORED</b>

A foto/nome do morto muda de “ARCHIVED” para “ACTIVE SESSION”.

Nenhum alerta de fraude aparece.

Neste ponto, o Breaker conquistou controle indevido, mas ainda precisa ler o registro e liberar o saldo. A sequência é fixa: primeiro ele prova a falha e obtém a pista; em seguida executa uma revogação explícita da autoridade indevida. Não apresentar menu moral. A expiração da sessão não desfaria a alteração persistente.

## Scene 7 — Discovery

A leitura autenticada do registro no próprio contrato devolve um único valor:

<b>WAREHOUSE 17</b><br /><b>LOWER MERIDIAN</b><br /><b>DO NOT USE CITY ROUTING</b>

Mara:

> <b>Warehouse 17 não existe.</b>

Breaker:

> <b>Essa identidade também não existia cinco minutos atrás.</b>

## Scene 8 — Debrief

Após concluir o desafio, o runtime executa e registra a revogação explícita do controle irregular como <b>cena canônica obrigatória</b>. O verifier confirma o exploit antes do cleanup. O Breaker OS exibe <code>CONTROLLER RELEASED</code>, e Mara confirma que a tomada de controle permanece auditável no histórico. Não oferecer escolha ao jogador nesse momento. Encerrar a janela não substitui a operação persistente. Nenhuma opção confere legitimidade à impersonação. A saída narrativa segue Warehouse 17.

Somente após a vitória:

<b>VULNERABILITY DISCOVERED — INSECURE INITIALIZATION</b>

Explicar que um estado crítico pôde ser inicializado novamente.

Mostrar <code>__constructor</code> / guard de inicialização no relatório expandido.

## Scene 9 — Transition

<b>NEW LEAD: WAREHOUSE 17</b>

Mapa oficial:<br /><b>NO RESULT</b>

Mapa alternativo:<br /><b>LOWER MERIDIAN — INDUSTRIAL ZONE</b>

Unlock:<br /><b>CASE 03 — WAREHOUSE 17</b>
</content>
</page>

