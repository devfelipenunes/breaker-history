---
notion_id: 40c9c563-0425-81df-836b-cef78dcb861a
source: https://app.notion.com/p/40c9c563042581df836bcef78dcb861a?pvs=204
title: "🏛️ 10 — The Witness & Witness Spire — Blueprints Técnicos"
exported_at: 2026-11-07
---

**Blueprint técnico / propostas para produção.** Ambos os bosses reutilizam conteúdos ensinados. Sem novo exploit, sem simular chaves de visualização universais inexistentes e sem nova ramificação narrativa. As fixtures, thresholds e provas exigem implementação e validação no stack Soroban/ZK selecionado.

# BOSS I — The Witness: fugir sem divulgar tudo

## Problema

First Witness possui uma ordem de disclosure abrangente. O Breaker ainda não consegue provar sua conformidade histórica porque lhe falta o sender witness de Rhea. Ele precisa **preservar evidências e deixar de entregar informações desnecessárias**, não “desligar o Veil” nem provar inocência prematuramente.

## Estrutura de desafio sem bug novo

1. **Ler a rota exposta:** mapear uma safehouse comprometida por segredo em storage, evento revelador e registry de associação atual. Fonte dos dados aparece nos traces.
2. **Escolher uma saída tecnicamente válida:** compor endpoints/artefatos já vistos de forma que o plano de fuga não reutilize o segredo exposto, não emita dados sensíveis em eventos e não forneça credencial global de leitura.
3. **Preservar dossiê:** carregar a timeline da association (policy válida na settlement, admin cancelado, pending reativado e DENIED posterior), sem inserir como se fosse o proof final.
4. **Atravessar checkpoint:** submit de evidências mínimas e caminho de acesso restrito. O First Witness não abandona o caso; perde a rota imediata e passa a investigar nullifier.

## Invariants do verifier — simulação de design

- **full\_view\_key\_disclosed == false**;
- **known\_public\_secret\_reused == false**;
- **new\_sensitive\_event\_emitted == false**;
- **association\_timeline\_preserved == true**;
- **route\_checkpoint\_reached == true**.

**Regra de justiça:** o jogador precisa saber quais dados o Witness observa em cada rota. Sem guardas oniscientes, leitura de informação oculta sem fonte ou solução baseada em adivinhação.

## Payoff

Escape temporário, não absolvição. A Spire muda para evidência de dupla utilização de nullifier. O Breaker e Rhea têm interesses opostos, mas precisam dos witnesses divididos da mesma settlement.

# FINAL — The Witness Spire: três objetivos

## Meta 1 — Reconstrua o estado verdadeiro

Recuperar e validar fontes históricas da settlement original: commitment, sender witness, recipient witness, policy/association e estado de autorização no ledger de execução. Conferir que a classificação DENIED ocorreu **depois**. Os registros de Cases 03–04 distinguem a vulnerabilidade genérica de profile mutation da **causa histórica do caso**: pending admin sobrevivente de cancelamento.

**Não basta** invalidar provas que acusam o Breaker. A prova de conformidade exige a operação original e a policy vigente no momento exato.

## Meta 2 — Refute o que não foi demonstrado

- **Case 05:** Nullifier duplicado na fixture com ausência de spent-check não comprova que o Breaker realizou dois gastos independentes na operação histórica.
- **Case 06:** Proof ZK válido de circuito under-constrained não demonstra claim cuja ligação não é constrangida.
- **Case 09:** Proof matematicamente válido sob verification key/policy de outra versão não prova a policy esperada.

Documentar cada falha da acusação como insuficiência probatória demonstrável, não como prova automática de inocência.

## Meta 3 — Entregue o mínimo e encerre a ordem

Compor pacote verificável de claims e âncoras necessárias sem publicar amount, key geral, identidade da fonte E.V., grafo de terceiros ou todo o histórico da cidade. First Witness revê o pedido excessivo e **decide** encerrar a ordem mesmo diante da regra automática de full disclosure. A decisão é institucional e humana, não um método de contrato que o player hackeia.

## Pacote de prova proposto

| Campo | Verificação exigida | Exposição permitida |
| --- | --- | --- |
| Settlement commitment e ID | Mesmo identificador nos witnesses e no ledger histórico | Commitment e hash/âncora |
| Sender+recipient witnesses | Assinaturas/commitments válidos, ligados à mesma operação | Proof de vínculo, não dados brutos de Rhea |
| Policy snapshot na execução | Versão autenticada e status permitido no ledger de execução | Identificador de versão e claim de conformidade |
| Association timeline | Cancelamento anterior à retomada indevida, DENIED posterior à settlement | Ordem dos fatos e proofs das transições necessárias |
| Evidence objections | Nullifier/constraint/VK não sustentam as acusações | Claims técnicos, não dados de terceiros |
| Minimal disclosure | Pacote não inclui view key, montante ou fonte E.V. | Claim-only + anchors |

## Verificador independente (pseudo-invariants)

- **historical\_policy\_attested == true**;
- **sender\_recipient\_same\_settlement == true**;
- **association\_denied\_only\_after\_settlement == true**;
- **replayed\_nullifier\_evidence\_not\_conclusive == true**;
- **underconstrained\_or\_wrong\_vk\_evidence\_invalid\_for\_claim == true**;
- **full\_view\_key\_disclosed == false**;
- **unrelated\_actors\_exposed == false**;
- **proof\_package\_verified == true**.

Os nomes são propriedades conceituais do harness, não APIs existentes. O pacote não declara o Breaker inocente de toda ação histórica. A autoridade deve ter informação suficiente para encerrar **este processo**, sem confiar numa simples string de sucesso da UI.

## Requisitos de protocolo e fixture a decidir

- Escolher um único stack de proof para a vertical slice e explicitar public inputs, witness e commitment binding. Não assumir compatibilidade automática entre circuitos Noir/Circom e verificadores Soroban.
- Verificar que o contrato que recebe provas conhece policy version e verification key hash esperadas. Distinguir Case 06 (constraints insuficientes no circuito) de Case 09 (registry/VK corresponde à regra errada).
- Definir onde vivem ciphertexts e quem os descriptografa; uma auditor capability não é automaticamente um “master key” de toda a Stellar.
- Para Case 10, definir adversário, fontes de metadados e threshold que determina **MISSING operacional**; não prometer anonimato irrestrito.
- Testar provas negativas: forged witness, commitment diferente, policy atual em vez de histórica, nullifier duplicado, wrong VK, disclosure de E.V., ausência de sender witness, UI-only spoof.

# O Sétimo — dois processos e dois estados

**Processo 1 (Moonlight):** Witness Spire fecha a ordem após prova suficiente. Não revogar essa conclusão.

**Processo 2 (Lumen):** after-action review de Emergency Authority exige atribuição de operador. Rhea tenta prova agregada, depois divulga voluntariamente atestação nominativa verdadeira — decisão tardia e sem consentimento do Breaker. A instituição suspende credencial intercity até revisão; nunca congela wallet ou converte isso em condenação criminal automática.

**Estado MISSING:** conhecimento histórico da conta em Lumen não permite reconstruir automaticamente a rota atual; o Breaker decide manter baixa observabilidade como ato fixo, não menu de branching.

# Testes narrativos e de UX

- [ ] O jogador distingue refutação de prova positiva.
- [ ] First Witness compreende a prova antes de decidir, não muda de ideia por frase moral.
- [ ] A experiência de revelar o mínimo é ação técnica, não menu binário “abrir tudo/fechar tudo”.
- [ ] O contato com Sera e SOURCE E.V. torna o risco de full disclosure concreto antes do final.
- [ ] A vitória tem pausa/efeito, e a notificação separada de Lumen chega somente depois.
- [ ] A ruptura com Rhea é percebida como abuso de confiança genuína, não como plot twist de vilã secreta.

# Adendo de verificação — pacote de devolução de garantia e sessão MISSING

**Entradas do Final:** commitment da devolução, policy histórica, recipient account/beneficiary attestation, sender witness entregue antes de Case10, recipient witness, prova de cancelamento e aceitação indevida do admin, registro DENIED subsequente. First Witness vê o Breaker presencialmente, mas proof/credential da sessão não deve revelar a trajetória do privacy pool.

**Propriedades negativas:** rejeitar proof de outra operação, atestação de beneficiário sem vínculo com t0, diferença de policy, wrong VK, view key ampla, envelope de Sera incluído, ou sender witness ausente. Full disclosure do dossiê pode expor provenance envelope; não alegar key universal que descriptografa todo storage público.

**Dois processos:** fechar a ordem Moonlight por suficiência documental e decisão humana. A apuração Lumen só recebe depoimento de Rhea posteriormente; efeito institucional limitado à credencial de acesso. Cenários são requisitos para fixture, não testes já aprovados.
