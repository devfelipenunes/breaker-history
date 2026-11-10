---
notion_id: 4019c563-0425-817d-8adc-c534f531c010
source: https://app.notion.com/p/4019c5630425817d8adcc534f531c010?pvs=204
title: "🛠️ 03 — Plano de Produção do Act I"
exported_at: 2026-11-07
---

# Definition of Done — Every Case

Um Case só está pronto para entrar no jogo quando possui **todas** as camadas abaixo.

# 1. Narrative Layer

## Before

- local da cena;
- evidência inicial;
- motivo para o Breaker se importar;
- objetivo em linguagem narrativa;
- nenhum nome de vulnerabilidade.

## During

- contratos e estado acessíveis;
- terminal commands necessários;
- pistas reativas;
- hints graduais opcionais;
- mundo reage às tentativas relevantes.

## Breach

- exploit/solution altera o estado;
- feedback visual/terminal imediato;
- consequência narrativa clara.

## After

- revelação;
- nova pista;
- próximo Case;
- postmortem técnico.

# 2. Technical Layer

Cada Case precisa de:

- vulnerable contract fixture;
- secure mirror ou remediation patch;
- deterministic test scenario;
- exploit test que prova a condição de vitória;
- negative tests;
- clear invariant;
- deploy script/local setup;
- reset/replay support.

# 3. Educational Layer

Postmortem deve responder:

1. **What did the contract/system believe?**
2. **Why was that belief wrong?**
3. **What invariant failed?**
4. **How was it exploited?**
5. **How should it be fixed?**
6. **Where does this class appear in real systems?**

# 4. Game Layer

Todo Case deve entregar pelo menos um:

- clue;
- identity;
- access path;
- story item;
- recording;
- location;
- character revelation;
- state change;
- moral complication.

Nunca criar challenge só porque a vulnerabilidade é interessante.

# 5. Difficulty Curve

## Season 1

**Read the contract.**

O jogador aprende primitives de Soroban/security.

## Season 2

**Read the system.**

O jogador precisa compreender dependências econômicas.

## Season 3

**Read the threat model.**

O jogador precisa distinguir bug, proof, observability e privacy property.

# 6. Boss Rule

Mid-Boss e Final Boss:

- não apresentam vulnerability label;
- preferencialmente não introduzem vulnerability nova;
- combinam conhecimento anterior;
- exigem investigação, não brute force;
- produzem payoff narrativo maior que qualquer Case isolado.

# 7. Security Validation

Antes de marcar uma vulnerability como canonical:

- verificar comportamento atual do Soroban runtime;
- validar contra Stellar docs;
- reproduzir em fixture local;
- evitar copiar threat model EVM incompatível;
- registrar fonte técnica;
- manter data/version context quando o comportamento depender do runtime.

# 8. Act I Implementation Order

## Phase A — Vertical Slice

Implementar primeiro:

1. S1 Case 01 — No Forced Entry;
2. S2 Case 01 — Stale Truth;
3. S3 Case 01 — The Public Secret.

Objetivo: provar que o mesmo Breaker Terminal suporta três fantasias diferentes.

## Phase B — First Four

Completar Cases 01–04 de cada Season.

## Phase C — Mid-Bosses

Custodian, Liquidator, Witness.

## Phase D — Late Cases

Cases 05–10.

## Phase E — Finals

Architect, Cascade, Witness Spire.

# 9. Act I Quality Gate

O Act I só está narrativamente fechado quando:

- S1 explica por que o jogador vira Breaker;
- S2 explica por que Rhea aceitou;
- S3 demonstra o custo de ser observável;
- Voss continua misterioso, mas sua recusa ganha significado;
- Architect permanece moralmente ambíguo;
- o jogador termina MISSING;
- Horizon/Galexie é a única continuação natural da busca.

# Evidências, produção e verificação do epílogo "O Sétimo"

- Especificar a credencial intercity ficcional, seus emissores, privilégio de trânsito/serviços, escopo geográfico, processo de suspensão e possibilidade de revisão. **Não** confundir com credenciais da Authority revogadas em S1, status do Architect ou conta Stellar.
- Criar evidência do processo A (settlement Moonlight válida), processo B (Emergency Authority Lumen), atestação de Rhea, registro de recebimento e decisão de suspensão, com timestamps compatíveis e domínio de assinatura explícito.
- Provar que a revelação de Rhea não usa uma assinatura contextual como autorização do Breaker; a divulgação é uma escolha de privacidade e a sanção depende de decisão institucional separada.
- Foreshadowing: auditoria pós-Lumen e associação intercity antes da Season 3; cooperação e compartilhamento com escopo nos Cases 05–08; tentativa de Rhea de propor prova não nominativa na conclusão. Nenhum indício deve tornar a premeditação canônica.
- Final: verificar que o Case de Moonlight fecha corretamente; depois mostrar a notificação independente, perda visível de acesso e evasão com habilidades de Become Missing. Não introduzir exploit novo, falso veredicto penal ou wipe de wallet.
- Testar leitura crítica: o público consegue explicar por que Rhea escolheu, o que mais poderia ter feito, qual consentimento violou e por que a confiança anterior era genuína.

# 10. Source Baseline

Primary:

- Stellar developer documentation;
- Soroban Guard vulnerable/secure fixtures;
- OpenZeppelin Stellar contracts;
- Nethermind Stellar Private Payments.

Secondary:

- reproducible security research;
- audits with concrete PoCs;
- ZK circuit security references.

Never use a vulnerability only because a blog post names it. It must be reproducible and fit the game.

# Revised Act I Narrative Gates

Antes de considerar qualquer Season do Act I pronta para produção, validar:

- Season 1 termina com o jogador **QUALIFIED / PROVISIONAL**, não ACCEPTED.
- A motivação para ir a Lumen é encontrar uma Breaker ACCEPTED e entender por que ela aceitou o que Voss recusou.
- Season 2 nunca pode sugerir que um único bug explica Lumen.
- Rhea precisa tomar pelo menos uma decisão que funcione sistemicamente e cause perda real a terceiros.
- Ilyan Marr e Nia Kade devem aparecer como consequências humanas do colapso, não como quest dispensers.
- Mara continua presente no Act I, mas sem recuperar autoridade institucional em Season 2.
- Acceptance do jogador acontece apenas depois da intervenção consciente em The Cascade.
- Season 3 deve usar a lógica moral de Lumen contra o jogador: exceptional circumstances do not automatically legitimize unlimited access.
- O First Witness age de boa-fé e possui arco próprio: certainty → persistence → doubt → choice.
- Sera Quill e Eli Venn dão peso humano ao custo de full disclosure.
- Case 10 torna o Breaker operacionalmente MISSING para alcançar a Witness Spire.
- O Final Boss limpa o nome do jogador por claim-only disclosure.
- Depois da absolvição, Rhea toma **uma decisão tardia que rompe uma confiança real**: entrega uma atestação individual sobre a intervenção do Breaker em Lumen, separada da settlement de Moonlight, desencadeando suspensão de sua credencial institucional intercity até revisão. O Breaker escolhe não restaurar observabilidade e permanece MISSING. A atestação não condena automaticamente, não compromete wallet Stellar nem desfaz a prova final.
- Mara e First Witness devem formar um espelho institucional: Mara abre acesso que deveria estar fechado; First Witness fecha disclosure que deveria ser aberto pelo procedimento.
- Act I deve terminar com a progressão temática: **BREAK TO KNOW → BREAK TO SAVE → KNOW WHEN NOT TO BREAK.**

# Gates de personagem — versão canônica

Antes de aprovar qualquer roteiro:

- Rhea deve permanecer inimiga durante toda a Season 2.
- O reveal de Lumen muda a interpretação da Rhea, não transforma a relação em amizade.
- The Cascade permite cooperação tática, mas termina com rivalidade ativa.
- Season 3 só pode iniciar cooperação Breaker × Rhea quando a prova exigir sender witness + recipient witness.
- A cooperação de Moonlight precisa produzir confiança **verdadeira demonstrada em jogo** (Cases 06, 07, 08 e 09), não reconciliação ideológica. Rhea não começa a Season planejando trair o Breaker. A traição ocorre só depois da vitória e de uma decisão nova, própria, sobre o escopo de uma investigação de Lumen.
- Rhea deve querer destruir uma capability de disclosure e ser impedida pelo Breaker; **ela respeita esse limite** e não destrói a capability. O episódio não cancela a posterior traição, que usa informação verdadeira, não um exploit ou ordem do Architect.
- Sera Quill deve aparecer visualmente/textualmente desde Season 1 através da Network Wire.
- Em Season 2, uma publicação correta de Sera precisa produzir consequência de mercado.
- Em Season 3, o jogador deve reconhecer o nome de Sera antes de conhecer a pessoa.
- Mara precisa recusar uma restauração de acesso oferecida pelo Breaker em Lumen.
- Ilyan precisa agir no Final de Lumen; não pode existir apenas como vítima.
- Nia permanece âncora humana, sem virar protagonista.
- Eli Venn deve existir inicialmente apenas como SOURCE: E.V.
- First Witness precisa ter motivo anterior para confiar em selective disclosure.
- A recusa de Voss deve ser tratada como decisão com custo, não como superioridade moral.
- Status do Architect são classificações do sistema, não verdades absolutas sobre o personagem.
- Falas de personagens devem ser escritas em português nos documentos canônicos.

# Nova baseline narrativa — 12 decisões aprovadas (2026-11-02)

**Aprovação editorial ≠ implementação comprovada.** As 12 lacunas de causalidade foram incorporadas ao cânone, mas não há evidência nesta revisão de testes de contrato, fixture, prova ZK ou gameplay. Não marcar as tarefas como concluídas por terem texto no Notion.

**P0 — S1:** evidências de três relatórios históricos de Voss; classificação do Oracle falha em prever a decisão canônica de parar inserts no Sector 13; Mara assina recibo depois de CASE CLOSED com credential/hash atribuíveis.

**P0 — S2:** simulação Liquidator usando mesma seed com/sem intervenção de Rhea em 2 controles (filtro de preço inadequado + limite de lote); relatório de risco parcial acessível e justificação racional do bloqueio. Garantia operacional real na Cascade; ownership, custódia, autorização específica de Rhea como settlement sender, retorno ao beneficiário e motivo da rota confidencial de Moonlight.

**P0 — S3:** policy de investigação excepcional acionada por DENIED+grafo; operador de compliance aceita pending admin revogado; prova histórica de beneficiário entre duas identidades aparentes; sender witness entregue antes da separação; sessão limitada com MISSING preservado; envelope redigido da fonte de Sera e prova mínima.

**Testes de aceitação narrativa:** (1) player explica por que Breaker bloqueou Rhea; (2) por que a devolução era legítima e precisava de Moonlight; (3) por que Breaker confiou a atestação a Rhea; (4) por que First Witness pediu tudo e reconheceu excesso; (5) por que entregar uma atribuição verdadeira em Lumen rompe confiança sem desfazer vitória Moonlight.

**Fonte de verdade:** [00 — História Canônica do Act I](00-historia-canonica-do-act-i.md); [07 — Escolhas de Acontecimentos | Writers' Room Act I](../../../../databases/act-i-story-decisions.txt).

[ARQUIVO — Storyboards S1 (51 fichas) \| material de produção pausado](../season-01/production/archive/storyboards-s1-paused.md)
