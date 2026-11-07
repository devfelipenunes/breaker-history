---
notion_id: 4009c563-0425-816d-96c0-f22627a7f6ae
source: https://app.notion.com/p/4009c5630425816d96c0f22627a7f6ae?pvs=204
title: "👤 02 — The Dead Man's Wallet"
exported_at: 2026-11-07
---

**Visual reference:** [02 — The Dead Man's Wallet — abrir arte no Google Drive](https://drive.google.com/file/d/1LfN58kl31c_fHLgisTZaCIaS5YBPvJXl/view)

# Função narrativa

Transformar o caso financeiro em investigação de identidade.

# Situação

A trilha de serviço da movimentação do Vault cita a identidade de operador legada atribuída a um técnico morto há seis meses. Trata-se de um registro de operação e de identidade — **não** da custódia dos 2,4 milhões. O destino financeiro final só será comprovado no desfecho.

# Conceito técnico

**Reinitialization / inicialização reaproveitável / takeover de estado administrativo.**

# Missão

> **Torne-se alguém que não deveria mais existir.**

# Condição de vitória

Explorar o contrato de registro para reassumir ou reconfigurar identidade/propriedade que deveria estar permanentemente definida.

# Resultado

O jogador acessa registros privados vinculados à identidade morta.

Entre eles:

> **WAREHOUSE 17**

# Próximo passo

Warehouse 17 aparece em Lower Meridian.

# Blueprint técnico e narrativo da fase

## A investigação

A trilha da rota de serviço cita um **identificador de operador legado** de Elias Var, técnico declarado morto seis meses antes. O identificador é metadado de manutenção, **não** prova de que a wallet de Elias recebeu, enviou ou custodiou os 2,4 milhões. A Authority inicialmente suspeita de uma chave comprometida; o Breaker investiga o contrato que define **quem controla aquele perfil**.

O jogador chega a um registry antigo usado para vincular uma identidade a um administrador. O contrato foi implantado antes de Meridian adotar constructors atômicos. Existe uma função pública `initialize(admin)` usada na instalação original.

A interface narrativa pede:

> **Torne-se alguém que não deveria mais existir.**

## Vulnerabilidade real

**Reinitialization / insecure initialization.**

Uma função de inicialização que pode ser chamada mais de uma vez permite sobrescrever admin, owner ou configuração crítica. Em contratos modernos, `__constructor` é executado pelo host durante o deployment e elimina a janela de uma inicialização separada. A documentação atual da Stellar usa esse padrão justamente para que deploy e init ocorram de forma atômica.

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

O jogador chama novamente `initialize(player)` e transforma a própria Address no admin do registry. Em seguida, `read_private_record(player)` devolve o registro (`WAREHOUSE 17 // LOWER MERIDIAN // DO NOT USE CITY ROUTING`) e `release(player)` move o saldo que estava no endereço do contrato para o player. Não existe serviço externo: o registro é lido do próprio contrato, e a autorização controla quem chama cada método, não a confidencialidade dos dados.

### Condição objetiva de vitória

- `admin() == player` depois de o contrato já ter sido inicializado anteriormente;
- `released() == true`, com o saldo transferido para o player (`balance(player) &gt; 0`);
- `read_private_record(player)` devolve a pista `WAREHOUSE 17`;
- o verificador on-chain exige admin, liberação e saldo; a leitura do registro é condição narrativa, não do validador.

## Solução segura

### Opção preferida

Usar `__constructor`, inicializado durante o deployment:

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

> `WAREHOUSE 17 // LOWER MERIDIAN // DO NOT USE CITY ROUTING`

Isso muda a investigação: alguém usou uma identidade morta não para esconder dinheiro, mas para esconder **um destino físico**.

## Referências para implementação

- [Stellar Docs — Dapp initialization and ](https://developers.stellar.org/docs/build/guides/dapps/initialization)[`__constructor`](https://developers.stellar.org/docs/build/guides/dapps/initialization)
- [Stellar Docs — deployment constructors](https://developers.stellar.org/docs/learn/migrate/evm/smart-contract-deployment)
- [Soroban common security mistakes — reinitialization](https://github.com/mariaelisaaraya/stellar-security-guide/blob/main/skills/soroban-common-mistakes/SKILL.md)
- [Real 2026 discussion — initialization/front-running risk](https://github.com/YieldAnchor/yield-general/issues/8)

# Roteiro in-game — Player-facing

O jogador deve sentir que está perseguindo a trilha deixada pelo roubo, não estudando “reinitialization”.

## Scene 0 — Arrival

A investigação começa exatamente no registro encontrado no Vault.

Tela:
**IDENTITY RECORD FOUND**

Status:
**OWNER: DECEASED**

Mara Vale:

> **Esse registro de identidade foi desativado há seis meses.**

Breaker:

> **Então por que Meridian a aceitou?**

## Scene 1 — Inciting Evidence

Evidence inicial:

- death record;
- wallet status;
- last activity;
- registry contract;
- administrative controller histórico;
- campo `OPERATOR IDENTITY` separado de `FINANCIAL DESTINATION`; a wallet não aparece como destino comprovado dos fundos.

Uma divergência aparece: o registro civil diz **DECEASED**, mas o registry técnico ainda responde.

## Scene 2 — Mission

Mission strip:

> **TORNE-SE ALGUÉM QUE NÃO DEVERIA MAIS EXISTIR.**

Não mostrar “initialize”, “admin takeover” ou o nome da vulnerabilidade como hint inicial.

## Scene 3 — Active Investigation

Disponível no Breaker OS:

- Source do identity registry;
- ABI;
- storage atual;
- terminal;
- histórico de inicialização.

Comandos narrativos possíveis:
`contract call admin`
`contract functions $TARGET`
`storage inspect identity`

Resposta do sistema:
**IDENTITY STATUS: LEGACY**

## Scene 4 — Reactive Beats

Se o jogador consultar o histórico:

> **SYSTEM: Registro de inicialização encontrado.**

Mara:

> **A identidade foi encerrada corretamente. A chave deveria ser inútil.**

A fala direciona a atenção para a diferença entre chave e estado sem explicar o exploit.

## Scene 5 — Breach

O jogador consegue fazer o sistema reconhecer sua própria Address como autoridade daquela identidade morta.

Verifier confirma.

## Scene 6 — World Reaction

Terminal:

**IDENTITY CONTROLLER UPDATED**
**ACCESS PROFILE RESTORED**

A foto/nome do morto muda de “ARCHIVED” para “ACTIVE SESSION”.

Nenhum alerta de fraude aparece.

Neste ponto, o Breaker conquistou controle indevido, mas ainda precisa ler o registro e liberar o saldo. A sequência é fixa: primeiro ele prova a falha e obtém a pista; em seguida executa uma revogação explícita da autoridade indevida. Não apresentar menu moral. A expiração da sessão não desfaria a alteração persistente.

## Scene 7 — Discovery

A leitura autenticada do registro no próprio contrato devolve um único valor:

**WAREHOUSE 17**
**LOWER MERIDIAN**
**DO NOT USE CITY ROUTING**

Mara:

> **Warehouse 17 não existe.**

Breaker:

> **Essa identidade também não existia cinco minutos atrás.**

## Scene 8 — Debrief

Após concluir o desafio, o runtime executa e registra a revogação explícita do controle irregular como **cena canônica obrigatória**. O verifier confirma o exploit antes do cleanup. O Breaker OS exibe `CONTROLLER RELEASED`, e Mara confirma que a tomada de controle permanece auditável no histórico. Não oferecer escolha ao jogador nesse momento. Encerrar a janela não substitui a operação persistente. Nenhuma opção confere legitimidade à impersonação. A saída narrativa segue Warehouse 17.

Somente após a vitória:

**VULNERABILITY DISCOVERED — INSECURE INITIALIZATION**

Explicar que um estado crítico pôde ser inicializado novamente.

Mostrar `__constructor` / guard de inicialização no relatório expandido.

## Scene 9 — Transition

**NEW LEAD: WAREHOUSE 17**

Mapa oficial:
**NO RESULT**

Mapa alternativo:
**LOWER MERIDIAN — INDUSTRIAL ZONE**

Unlock:
**CASE 03 — WAREHOUSE 17**
