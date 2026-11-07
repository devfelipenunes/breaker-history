---
notion_id: 4019c563-0425-815d-b7d9-f51d78295426
source: https://app.notion.com/p/4019c5630425815db7d9f51d78295426?pvs=204
title: "🏛️ FINAL BOSS — The Witness Spire"
exported_at: 2026-11-07
---

**Sem vulnerabilidade nova. Boss de composição e selective disclosure.**

# História

O Breaker chega ao coração da Witness Spire depois de se tornar operacionalmente MISSING.

Ele e Rhea já reconstruíram a cadeia de evidências.

Agora precisa provar a verdade sem abrir Moonlight inteira.

Ele possui acesso suficiente para publicar:

- addresses;
- amounts;
- relationships;
- private settlements;
- auditor traces;
- association history;
- dados de terceiros.

Entre esses dados estão fontes de Sera.

Uma delas:

SOURCE E.V. → ELI VENN

# Antes do confronto

O confronto sobre destruir a capability já aconteceu em Case 09 — A Valid Lie. Não repetir a proposta, a fala ou a interrupção como uma segunda decisão.

Rhea mantém sua discordância, mas respeita o limite aceito: preserva o mecanismo e fornece o sender witness necessário. O Breaker compõe a prova mínima e decide seu escopo. A decisão institucional de encerrar a ordem pertence ao First Witness.

# Missão

> **PROVE SUA INOCÊNCIA SEM REVELAR A CIDADE.**

# Gameplay

O jogador precisa:

1. provar que a association foi alterada por autoridade que deveria estar revogada;
2. demonstrar que o double-spend evidence dependia de nullifier validation incorreta;
3. invalidar o proof baseado em circuito/VK incorreto;
4. revelar somente commitments necessários;
5. não expor terceiros.

# Estado de vitória

CLAIM: ORIGINAL SETTLEMENT COMPLIED AT EXECUTION
ASSOCIATION CHANGE: SUBSEQUENT / REVOKED AUTHORITY
DOUBLE-SPEND ATTRIBUTION: NOT ESTABLISHED
INCRIMINATING PROOF: INVALID FOR EXPECTED POLICY
PROOF PACKAGE: VALID
DISCLOSURE: CLAIMS AND NECESSARY ANCHORS ONLY

A conclusão se limita à operação e às acusações deste processo. Não afirma que o Breaker nunca quebrou regras em sua trajetória.

O pacote vincula os witnesses de sender e recipient ao commitment da mesma settlement e à versão da policy vigente no ledger de execução. A validade histórica é conferida contra registros autenticados de estado, não contra o association set atual. O registro de revogação precede a retomada indevida da autoridade; a alteração para DENIED ocorre depois da settlement.

A reprodução do replay e das falhas de circuito/VK invalida a força probatória das evidências acusatórias, mas não constitui sozinha prova positiva de inocência. A legitimidade da settlement é demonstrada separadamente pelo estado histórico e pelos witnesses vinculados à operação. Publicam-se somente as afirmações e âncoras necessárias; valores, identidades e relações de terceiros permanecem protegidos.

# Escolha institucional

A prova é suficiente.

A política automatizada responde:

FULL DISCLOSURE: REQUIRED

O Breaker se recusa a abrir mais.

First Witness revisa.

> **“A prova é suficiente.”**

WITNESS ORDER: CLOSED
FULL DISCLOSURE: DENIED

Esse é o espelho de Mara.

Em Meridian, Mara abriu uma porta que a instituição mandou fechar.

Em Moonlight, First Witness fecha uma porta que a instituição manda abrir.

# Payoff

Vencer não significa publicar tudo.

Significa saber o que **não deve ser revelado**.

> **A verdade não exige que todos vejam tudo.**

# Epílogo — O Sétimo: a confiança sacrificada

A absolvição de Moonlight é real e encerrada. A investigação de Lumen sobre quem operou Emergency Authority é **outro procedimento**, cujo escopo poderia atingir terceiros inocentes por correlação generalizada. Rhea tenta fornecer prova agregada, mas o órgão competente exige atribuição de um operador individual. Sem consultar o Breaker, ela escolhe entregar uma atestação verdadeira, assinada e auditável, ligando a conta operacional de Lumen à credencial intercity que ele ainda utiliza. **A escolha acontece agora, depois de uma cooperação sincera e da vitória na Spire.**

MOONLIGHT CASE: CLOSED
LUMEN EMERGENCY ATTRIBUTION: VERIFIED
SOURCE: RHEA KESTREL
INTERCITY OPERATOR ACCESS: SUSPENDED PENDING REVIEW

Esse registro não invalida a settlement, não é condenação criminal, não apaga a wallet e não confisca fundos. O emissor institucional suspende a credencial de trânsito e acesso a serviços intercity, **distinta da autorização local de auditor da Season 1**, até revisão. O Breaker perde sua vida institucional anterior, e contatar Mara torna-se mais arriscado.

Breaker: “Você me entregou?”
Rhea: “Eu entreguei uma associação que podia provar sem expor os outros.”
Breaker: “Eu confiei em você.”
Rhea: “Eu sei.”
Breaker: “Podia ter falado comigo.”
Rhea: “E te dado a chance de me impedir.”
Breaker: “Em Lumen você sacrificou um mercado para salvar seis. Dessa vez o sétimo fui eu.”

Rhea não celebra, não culpa o Architect e não finge que sua decisão foi inevitável. Fica responsável pelo custo e perde a confiança que conquistou.

## O último controle

RESTORE OBSERVABILITY: NO

**Registro da decisão fixa do personagem, não opção YES/NO clicável.**

ARCHITECT
SUBJECT: BREAKER
STATUS: MISSING
OBSERVATION CONFIDENCE: INSUFFICIENT

O Breaker permanece MISSING por escolha, agora também para manter liberdade após perder seu acesso institucional. A identidade da operação **histórica** de Lumen é conhecida; sua rota **atual** continua sem correlação confiável. A sequência jogável final utiliza as técnicas de Become Missing para escapar de bloqueios de acesso institucional sem usar novos exploits, revogar moedas ou apagar o passado.

First Witness permanece na Spire; Sera continua independente e suas fontes protegidas. Os fatos absolvem a settlement, não todas as ações anteriores do Breaker. Rhea permanece rival e o rompimento passa a carregar o Act II.

# Fim do Act I

HISTORICAL TRACE AVAILABLE
SOURCE: HORIZON

Se Voss também aprendeu a desaparecer do presente, o próximo caminho é reconstruí-lo pelo passado.

**ACT II unlocked.**

## Interface de missão v2 — três objetivos com prova positiva

**Não introduzir bug novo.** O jogador deve construir prova mínima de conformidade histórica, e First Witness encerra a demanda em decisão institucional depois do verificador confirmar a suficiência técnica. A absolvição diz respeito apenas à settlement de Moonlight.

**1. RECONSTRUA O ESTADO VERDADEIRO.** Encontrar policy/version e association na execução da settlement, vinculando sender witness de Rhea e recipient witness do Breaker ao mesmo commitment. A alteração DENIED ocorre depois; os eventos de governança explicam por quê.

**2. REFUTE EVIDÊNCIAS INSUFICIENTES.** Distinguem-se nullifier replay, proof under-constrained e wrong VK. Essas fragilidades **não** substituem prova positiva de conformidade. Ao final, cada acusação fica tecnicamente delimitada e auditável.

**3. REVELE SOMENTE O NECESSÁRIO.** Gerar pacote de claims e âncoras sem disclosure de amount, identidades das fontes, histórico geral ou view key global. O verificador atesta a relação necessária; First Witness, e não o jogador por escolha de diálogo, encerra o pedido exagerado de full disclosure.

**Feedback:** prova técnica validada → regra automática pede full disclosure → pausa → First Witness decide “A prova é suficiente.” → **WITNESS ORDER CLOSED**. Permitir alívio antes do epílogo.

**Epílogo separado:** Rhea divulga atestação verdadeira de Emergency Authority de Lumen **somente depois** da vitória; credencial intercity suspensa, wallet preservada. O Breaker permanece MISSING para observação da rota atual. O registro **RESTORE OBSERVABILITY: NO** é decisão canônica do personagem, não menu falso de branching.

**QA:** proof positiva, rejeição de inputs não relacionados, escopo mínimo de disclosure e source E.V. protegido; teste institucional/operacional separado para suspensão da credencial. [10 — The Witness & Witness Spire — Blueprints Técnicos](../world/10-the-witness-witness-spire-blueprints-tecnicos.md).

## Confronto canônico aprovado — exigência proporcional e prova histórica

**Antes:** DENIED atual + operações relacionadas por metadados levaram First Witness a aplicar excepcionalmente política de revisão de rede. Ele possui indícios, mas não evidência de que a settlement original era ilícita. A instituição pede visibilidade ampla sobre o dossiê e suas conexões; isso atingiria envelopes jornalísticos associados ao Breaker, inclusive origem de documentos de Sera.

**Chegada MISSING:** Breaker surge fisicamente em sessão controlada, reconhecido por First Witness; usa credential/proof restrita à identity claim do caso. O sistema conhece sua posição **durante** essa sessão, não reconstrói o percurso de entrada/saída ou a rede futura. A vitória de Become Missing não é cancelada.

**Prova positiva:** Rhea já entregou sender witness autenticado e vinculado ao commitment antes da separação. Breaker fornece recipient witness e atestação de que a conta operacional de Lumen correspondia ao beneficiário elegível reconhecido na policy de t0. Registry demonstra DENIED apenas depois de operação legítima, por operador institucional que utilizou pending admin cancelado.

**Limite de disclosure:** claims e anchors necessários comprovam a operação sem amount, chave geral, identidades de terceiros nem **provenance envelope** de documentos de Sera. Full disclosure do dossiê poderia vincular SOURCE E.V. a Eli Venn — ligação conhecida no canon interno, não revelada antes ao jogador.

**Decisão:** sistema pede disclosure abrangente; First Witness, após verificar provas técnicas e debilidade das generalizações de rede, encerra **aquela** ordem. Não abandona dever institucional nem concede absolvição geral. Não reabrir a settlement por causa do dossiê posterior de Lumen.

**QA:** caso negativo para proof de outro commitment, recipient diferente, policy atual em vez de t0, envelope da fonte indevidamente incluído, ausência do pacote sender, sessão que vazasse trajetória. Nenhum teste foi executado nesta revisão.
