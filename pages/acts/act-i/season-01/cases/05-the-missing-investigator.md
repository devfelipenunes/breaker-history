---
notion_id: 4009c563-0425-8170-813f-f50ebbd55c16
source: https://app.notion.com/p/4009c56304258170813ff50ebbd55c16?pvs=204
title: "📼 05 — The Missing Investigator"
exported_at: 2026-11-07
---

Here is the result of "fetch" for the Page with URL https://app.notion.com/p/4009c56304258170813ff50ebbd55c16 as of 2026-11-04T15:33:52.750Z:
<page url="https://app.notion.com/p/4009c56304258170813ff50ebbd55c16" icon="📼">
<ancestor-path>
<parent-page url="https://app.notion.com/p/4019c563042581fd9124e5ee36b3e82f" title="03 — Cases & Bosses"/>
<ancestor-2-page url="https://app.notion.com/p/4009c563042581359693d42f09d41062" title="Season 01 — The First Layer"/>
<ancestor-3-page url="https://app.notion.com/p/4019c563042581469a0edc7e30a6eff9" title="ACT I — The World Is Breakable"/>
<ancestor-4-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
<properties>
{"title":"05 — The Missing Investigator"}
</properties>
<iconMetadata>{"type":"emoji","emoji":"📼"}</iconMetadata>
<content>
<callout icon="🎨" color="gray_bg">
<b>Visual reference:</b> [05 — The Missing Investigator — abrir arte no Google Drive](https://drive.google.com/file/d/11PAHgj8y8BsObR2DQ49OLT4E0gB2eiRS/view)
</callout>

# Função narrativa

Introduzir Aren Voss e transformar o mistério em uma investigação sobre alguém que percorreu o mesmo caminho.

# Situação

Na First Layer existe um terminal abandonado que pertenceu a <b>Aren Voss</b>, um Breaker desaparecido anos antes.

# Conceito técnico

<b>Cross-contract error handling failure / erro de subcontrato engolido e convertido em sucesso.</b>

# Missão

> <b>Recupere a mensagem que Voss não conseguiu terminar.</b>

# Condição de vitória

Fazer o Archive registrar como recuperado um fragmento que o Decoder rejeitou — e registrar também que houve rejeição.

# Gravação recuperada

> <b>“Alguém está mapeando os contratos quebrados.”</b>

Depois:

> <b>“Eles não estão causando os erros.”</b>

> <b>“Estão esperando para ver quem os encontra.”</b>

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

- <b>Archive Index:</b> marca quais fragmentos foram recuperados;
- <b>Decoder:</b> valida o fragmento e devolve o conteúdo.

A falha é sutil: o Index usa uma chamada tolerante a erro, mas interpreta qualquer falha do Decoder como se o fragmento tivesse sido processado.

> <b>Recupere a mensagem que o Archive acredita já ter recuperado.</b>

## Vulnerabilidade real

<b>Cross-contract error swallowed / erro de chamada entre contratos convertido em sucesso.</b>

Soroban oferece <code>invoke_contract</code>, que falha quando o contrato chamado falha, e <code>try_invoke_contract</code>, que devolve um <code>Result</code> para o chamador decidir o que fazer. A vulnerabilidade nasce quando a aplicação captura esse erro e continua alterando o estado como se a operação remota tivesse sido bem-sucedida.

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

O Decoder auxiliar rejeita com <code>InvalidFragment</code> qualquer fragmento cujo tamanho não seja 32 bytes; um fragmento válido devolve <code>Ok</code> e não aciona o caminho vulnerável.

### Exploit esperado

O jogador chama <code>recover(decoder, fragment)</code> com um fragmento que não tem 32 bytes. O Decoder devolve <code>Err(InvalidFragment)</code>; o Archive grava <code>Recovered = true</code> e <code>Rejected = true</code>. A flag libera um path que deveria existir somente após uma decodificação legítima — e a própria rejeição fica registrada como se fosse prova de recuperação.

### Condição objetiva de vitória

- a chamada ao Decoder falhou com <code>InvalidFragment</code>;
- <code>recovered() == true</code> e <code>rejected() == true</code>;
- um fragmento válido de 32 bytes <b>não</b> aciona o caminho (o validador exige as duas flags, e o sucesso do Decoder grava zero).

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

A regra pedagógica é: <b>não confirmar uma transição local quando a dependência externa falhou</b>.

## Correção conceitual

Este level substitui a ideia anterior de reentrancy. Soroban proíbe reentrada de contratos por design, então um challenge no estilo DAO hack ensinaria uma superfície que não representa corretamente a plataforma. Cross-contract logic continua sendo uma superfície real, mas aqui exploramos tratamento incorreto de erro.

## Gravação de Voss

Depois do exploit, a gravação aparece:

> <b>“Alguém está mapeando os contratos quebrados.”</b>

> <b>“Eles não estão causando os erros.”</b>

> <b>“Estão esperando para ver quem os encontra.”</b>

A diferença é importante: Voss não acredita que alguém fabricou cada bug. Ele acredita que alguém encontrou as fragilidades de Meridian e percebeu que elas poderiam ser ligadas como uma rota.

Agora o jogador deixa de procurar apenas um ladrão. Ele passa a procurar <b>quem conectou o caminho — e por quê.</b>

## Referências para implementação

- [Soroban SDK — Env::try\_invoke\_contract](https://docs.rs/soroban-sdk/latest/soroban_sdk/struct.Env.html)
- [Stellar Docs — Cross-contract calls](https://developers.stellar.org/docs/build/guides/conventions/cross-contract)
- [Soroban Guard — cross\_call\_error\_swallowed](https://github.com/Veritas-Vaults-Network/soroban-guard-contracts)
- [Stellar — Soroban disallows contract re-entry](https://stellar.org/blog/developers/sorobans-technical-design-decisions-learnings-from-ethereum)

# Roteiro in-game — Player-facing

## Scene 0 — Arrival

<b>Função dramática vigente:</b> entre os registros de Voss há uma hipótese equivocada <b>que será refutada por evidência externa no Sector 13</b>, e não uma correção feita por ele próprio. Um memorando sugere que a quarentena de recursos teria custos humanos. Não revelar a operação original do Vault nem atribuir autoria antes do final; mostrar Voss como investigador competente, mas falível.

O jogador entra no workspace abandonado de Aren Voss.

Monitores antigos ainda preservam:

- comandos;
- mapas;
- contract IDs;
- gravações;
- tentativas de recuperação.

Mara:

> <b>Ele estava investigando os mesmos sistemas.</b>

## Scene 1 — Inciting Evidence

Um fragmento de gravação aparece como:

<b>ARCHIVE: RECOVERED</b><br /><b>DECODER: FAILED</b>

Os dois sistemas discordam.

## Scene 2 — Mission

> <b>RECUPERE A MENSAGEM QUE O ARCHIVE ACREDITA JÁ TER RECUPERADO.</b>

## Scene 3 — Active Investigation

O jogador recebe Archive + Decoder.

Evidence:

- fragment ID;
- previous recovery attempts;
- Voss terminal history;
- timestamps showing that some of Voss's deepest accesses happened <b>years before</b> the current Vault incident.

O terminal deve permitir observar retorno de ambos os contratos.

## Scene 4 — Reactive Beats

Ao chamar Decoder normalmente:

<b>DECODER: REJECTED</b>

Ao consultar Archive:

<b>RECOVERY FLAG: TRUE</b>

Essa inconsistência é a pista.

## Scene 5 — Breach

O jogador força uma falha remota que o Archive registra como sucesso.

## Scene 6 — World Reaction

<b>RECOVERED</b>

A gravação de Voss finalmente toca:

> <b>Alguém está mapeando os contratos quebrados.</b>

> <b>Eles não estão causando os erros.</b>

> <b>Estão esperando para ver quem os encontra.</b>

## Scene 7 — Discovery

A gravação de Voss não é profecia. O player deve perceber que Voss encontrou um padrão, errou em algumas inferências e deixou uma trilha de investigação, não uma solução completa. Preserve os timestamps de anos anteriores ao incidente para a revelação no Architect.

Nos arquivos de Voss aparece uma conta marcada:

<b>IMPOSSIBLE</b>

Sem explicação adicional.

## Scene 8 — Debrief

<b>VULNERABILITY DISCOVERED — CROSS-CONTRACT ERROR SWALLOWED</b>

Explicar que falha de subcontrato foi interpretada como sucesso e estado local foi atualizado.

## Scene 9 — Transition

<b>NEW LEAD: IMPOSSIBLE ACCOUNT</b>

Unlock:<br /><b>CASE 06 — THE IMPOSSIBLE ACCOUNT</b>

## Complemento aprovado — motivação e responsabilidade de Voss

No workspace recuperado, o Breaker encontra <b>três avisos institucionais</b> com protocolo verificável, arquivados antes do incidente e ignorados sem resposta eficaz. Não inventar ordem entre cada aviso e a recusa de Voss, que também é anterior ao Vault. Um memorando de escalada menciona <code>RECOVERY QUARANTINE</code> como medida extrema e seus possíveis impactos em Lower Meridian, mas não é confissão, absolvição nem prova isolada de autoria.

O arquivo também contém <b>VOSS OPERATIONAL KEY REGISTRATION</b>: registro institucional autenticado, emitido antes do incidente, com sujeito Aren Voss, conta operacional, emissor, assinatura e validade temporal. A identidade da chave fica consultável na Evidence Locker e pode ser comparada antecipadamente por um jogador atento à transação pública do Prólogo. <b>O registro deve ter emissor independente confiável, emissão anterior ao incidente, validade e cadeia de custódia verificáveis</b>; cadastro autodeclarado não basta. A conclusão <code>ATTRIBUTION VERIFIED</code>, entretanto, pertence ao Architect, após verificar ator autenticado da chamada específica (não fee-payer isolado), identidade operacional de Voss e <b>estado do Gate realmente consumido pelo RecoveryController</b>. Requisitos e falsificadores: <mention url="https://app.notion.com/p/40d9c563042581ba9836c2856425010e" />.

Voss ainda sustenta uma hipótese excessivamente confiante: um indexador externo não conseguiria ler determinada trilha do Archive. Sector 13 demonstra posteriormente que isso era falso. Não conceder à gravação uma capacidade profética nem declarar Voss moralmente certo.

<b>Entrega:</b> persistir <code>VOSS / ARCHIVED WARNINGS</code>, o registro institucional da chave, nota de escalada e gravação na Evidence Locker, com fonte e timestamps. A falha do Decoder nesta fase permanece a mesma, independente do bug Decoder→VossProof do Case 10. Payoff final em <mention url="https://app.notion.com/p/40d9c563042581bf886cfc339d730fd1" />.
</content>
</page>

