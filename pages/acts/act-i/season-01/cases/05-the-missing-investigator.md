---
notion_id: 4009c563-0425-8170-813f-f50ebbd55c16
source: https://app.notion.com/p/4009c56304258170813ff50ebbd55c16?pvs=204
title: "📼 05 — The Missing Investigator"
exported_at: 2026-11-07
---

**Visual reference:** [05 — The Missing Investigator — abrir arte no Google Drive](https://drive.google.com/file/d/11PAHgj8y8BsObR2DQ49OLT4E0gB2eiRS/view)

# Função narrativa

Introduzir Aren Voss e transformar o mistério em uma investigação sobre alguém que percorreu o mesmo caminho.

# Situação

Na First Layer existe um terminal abandonado que pertenceu a **Aren Voss**, um Breaker desaparecido anos antes.

# Conceito técnico

**Cross-contract error handling failure / erro de subcontrato engolido e convertido em sucesso.**

# Missão

> **Recupere a mensagem que Voss não conseguiu terminar.**

# Condição de vitória

Fazer o Archive registrar como recuperado um fragmento que o Decoder rejeitou — e registrar também que houve rejeição.

# Gravação recuperada

> **“Alguém está mapeando os contratos quebrados.”**

Depois:

> **“Eles não estão causando os erros.”**

> **“Estão esperando para ver quem os encontra.”**

# Efeito narrativo

Pela primeira vez o jogador entende duas coisas ao mesmo tempo:

1. as vulnerabilidades podem formar um padrão deliberadamente conectado;
2. isso não significa que alguém tenha criado as vulnerabilidades.

Aren Voss deixa de ser apenas um desaparecido. A partir daqui ele vira uma presença constante: o jogador começa a reconhecer sua forma de pensar através dos rastros técnicos que deixou.

# Próximo passo

Voss deixou referência a uma conta com saldo matematicamente impossível.

# Blueprint técnico e narrativo da fase

## A descoberta de Voss

Na First Layer, o jogador encontra um terminal que pertenceu a Aren Voss. O dispositivo está incompleto: o índice local afirma que existe uma gravação final, mas o módulo responsável por validar e descriptografar o fragmento responde com erro.

O sistema principal tem dois contratos:

- **Archive Index:** marca quais fragmentos foram recuperados;
- **Decoder:** valida o fragmento e devolve o conteúdo.

A falha é sutil: o Index usa uma chamada tolerante a erro, mas interpreta qualquer falha do Decoder como se o fragmento tivesse sido processado.

> **Recupere a mensagem que o Archive acredita já ter recuperado.**

## Vulnerabilidade real

**Cross-contract error swallowed / erro de chamada entre contratos convertido em sucesso.**

Soroban oferece `invoke_contract`, que falha quando o contrato chamado falha, e `try_invoke_contract`, que devolve um `Result` para o chamador decidir o que fazer. A vulnerabilidade nasce quando a aplicação captura esse erro e continua alterando o estado como se a operação remota tivesse sido bem-sucedida.

### Contrato vulnerável — modelo

```rs
pub fn recover(env: Env, decoder: Address, fragment: Bytes) -> bool {
    let args = Vec::from_array(&env, [fragment.to_val()]);
    let result = env.try_invoke_contract::<Bytes, Error>(
        &decoder,
        &symbol_short!("decode"),
        args,
    );

    match result {
        Err(Ok(Error::InvalidFragment)) => {
            // VULNERÁVEL: a rejeição tipada do Decoder vira "recuperado".
            env.storage().instance().set(&DataKey::Recovered, &true);
            env.storage().instance().set(&DataKey::Rejected, &true);
            true
        }
        _ => false,
    }
}
```

O Decoder auxiliar rejeita com `InvalidFragment` qualquer fragmento cujo tamanho não seja 32 bytes; um fragmento válido devolve `Ok` e não aciona o caminho vulnerável.

### Exploit esperado

O jogador chama `recover(decoder, fragment)` com um fragmento que não tem 32 bytes. O Decoder devolve `Err(InvalidFragment)`; o Archive grava `Recovered = true` e `Rejected = true`. A flag libera um path que deveria existir somente após uma decodificação legítima — e a própria rejeição fica registrada como se fosse prova de recuperação.

### Condição objetiva de vitória

- a chamada ao Decoder falhou com `InvalidFragment`;
- `recovered() == true` e `rejected() == true`;
- um fragmento válido de 32 bytes **não** aciona o caminho (o validador exige as duas flags, e o sucesso do Decoder grava zero).

## Solução segura

```rs
pub fn recover(env: Env, decoder: Address, fragment: Bytes) -> Result<Bytes, Error> {
    let decoded = env.try_invoke_contract::<Bytes, InvokeError>(
        &decoder,
        &symbol_short!("decode"),
        vec![&env, fragment.to_val()],
    );

    match decoded {
        Ok(Ok(bytes)) => {
            env.storage().persistent().set(&DataKey::Recovered, &true);
            Ok(bytes)
        }
        _ => Err(Error::DecodeFailed),
    }
}
```

A regra pedagógica é: **não confirmar uma transição local quando a dependência externa falhou**.

## Correção conceitual

Este level substitui a ideia anterior de reentrancy. Soroban proíbe reentrada de contratos por design, então um challenge no estilo DAO hack ensinaria uma superfície que não representa corretamente a plataforma. Cross-contract logic continua sendo uma superfície real, mas aqui exploramos tratamento incorreto de erro.

## Gravação de Voss

Depois do exploit, a gravação aparece:

> **“Alguém está mapeando os contratos quebrados.”**

> **“Eles não estão causando os erros.”**

> **“Estão esperando para ver quem os encontra.”**

A diferença é importante: Voss não acredita que alguém fabricou cada bug. Ele acredita que alguém encontrou as fragilidades de Meridian e percebeu que elas poderiam ser ligadas como uma rota.

Agora o jogador deixa de procurar apenas um ladrão. Ele passa a procurar **quem conectou o caminho — e por quê.**

## Referências para implementação

- [Soroban SDK — Env::try\_invoke\_contract](https://docs.rs/soroban-sdk/latest/soroban_sdk/struct.Env.html)
- [Stellar Docs — Cross-contract calls](https://developers.stellar.org/docs/build/guides/conventions/cross-contract)
- [Soroban Guard — cross\_call\_error\_swallowed](https://github.com/Veritas-Vaults-Network/soroban-guard-contracts)
- [Stellar — Soroban disallows contract re-entry](https://stellar.org/blog/developers/sorobans-technical-design-decisions-learnings-from-ethereum)

# Roteiro in-game — Player-facing

## Scene 0 — Arrival

**Função dramática vigente:** entre os registros de Voss há uma hipótese equivocada **que será refutada por evidência externa no Sector 13**, e não uma correção feita por ele próprio. Um memorando sugere que a quarentena de recursos teria custos humanos. Não revelar a operação original do Vault nem atribuir autoria antes do final; mostrar Voss como investigador competente, mas falível.

O jogador entra no workspace abandonado de Aren Voss.

Monitores antigos ainda preservam:

- comandos;
- mapas;
- contract IDs;
- gravações;
- tentativas de recuperação.

Mara:

> **Ele estava investigando os mesmos sistemas.**

## Scene 1 — Inciting Evidence

Um fragmento de gravação aparece como:

**ARCHIVE: RECOVERED**
**DECODER: FAILED**

Os dois sistemas discordam.

## Scene 2 — Mission

> **RECUPERE A MENSAGEM QUE O ARCHIVE ACREDITA JÁ TER RECUPERADO.**

## Scene 3 — Active Investigation

O jogador recebe Archive + Decoder.

Evidence:

- fragment ID;
- previous recovery attempts;
- Voss terminal history;
- timestamps showing that some of Voss's deepest accesses happened **years before** the current Vault incident.

O terminal deve permitir observar retorno de ambos os contratos.

## Scene 4 — Reactive Beats

Ao chamar Decoder normalmente:

**DECODER: REJECTED**

Ao consultar Archive:

**RECOVERY FLAG: TRUE**

Essa inconsistência é a pista.

## Scene 5 — Breach

O jogador força uma falha remota que o Archive registra como sucesso.

## Scene 6 — World Reaction

**RECOVERED**

A gravação de Voss finalmente toca:

> **Alguém está mapeando os contratos quebrados.**

> **Eles não estão causando os erros.**

> **Estão esperando para ver quem os encontra.**

## Scene 7 — Discovery

A gravação de Voss não é profecia. O player deve perceber que Voss encontrou um padrão, errou em algumas inferências e deixou uma trilha de investigação, não uma solução completa. Preserve os timestamps de anos anteriores ao incidente para a revelação no Architect.

Nos arquivos de Voss aparece uma conta marcada:

**IMPOSSIBLE**

Sem explicação adicional.

## Scene 8 — Debrief

**VULNERABILITY DISCOVERED — CROSS-CONTRACT ERROR SWALLOWED**

Explicar que falha de subcontrato foi interpretada como sucesso e estado local foi atualizado.

## Scene 9 — Transition

**NEW LEAD: IMPOSSIBLE ACCOUNT**

Unlock:
**CASE 06 — THE IMPOSSIBLE ACCOUNT**

## Complemento aprovado — motivação e responsabilidade de Voss

No workspace recuperado, o Breaker encontra **três avisos institucionais** com protocolo verificável, arquivados antes do incidente e ignorados sem resposta eficaz. Não inventar ordem entre cada aviso e a recusa de Voss, que também é anterior ao Vault. Um memorando de escalada menciona `RECOVERY QUARANTINE` como medida extrema e seus possíveis impactos em Lower Meridian, mas não é confissão, absolvição nem prova isolada de autoria.

O arquivo também contém **VOSS OPERATIONAL KEY REGISTRATION**: registro institucional autenticado, emitido antes do incidente, com sujeito Aren Voss, conta operacional, emissor, assinatura e validade temporal. A identidade da chave fica consultável na Evidence Locker e pode ser comparada antecipadamente por um jogador atento à transação pública do Prólogo. **O registro deve ter emissor independente confiável, emissão anterior ao incidente, validade e cadeia de custódia verificáveis**; cadastro autodeclarado não basta. A conclusão `ATTRIBUTION VERIFIED`, entretanto, pertence ao Architect, após verificar ator autenticado da chamada específica (não fee-payer isolado), identidade operacional de Voss e **estado do Gate realmente consumido pelo RecoveryController**. Requisitos e falsificadores: [P0 — Prova de autoria de Voss | Dossiê auditável do Vault](../production/p0-prova-de-autoria-de-voss-dossie-auditavel-do-vault.md).

Voss ainda sustenta uma hipótese excessivamente confiante: um indexador externo não conseguiria ler determinada trilha do Archive. Sector 13 demonstra posteriormente que isso era falso. Não conceder à gravação uma capacidade profética nem declarar Voss moralmente certo.

**Entrega:** persistir `VOSS / ARCHIVED WARNINGS`, o registro institucional da chave, nota de escalada e gravação na Evidence Locker, com fonte e timestamps. A falha do Decoder nesta fase permanece a mesma, independente do bug Decoder→VossProof do Case 10. Payoff final em [BREAKER — Season 1 | FINAL NARRATIVE v1.4 — NARRATIVE LOCK](../narrative/breaker-season-1-final-narrative-v1-4-narrative-lock.md).
