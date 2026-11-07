---
notion_id: 40c9c563-0425-81ac-9e64-cd78769471df
source: https://app.notion.com/p/40c9c563042581ac9e64cd78769471df?pvs=204
title: "🛠️ 11 — Production Tracker & QA — Season 3"
exported_at: 2026-11-07
---

Here is the result of "fetch" for the Page with URL https://app.notion.com/p/40c9c563042581ac9e64cd78769471df as of 2026-11-03T00:08:24.024Z:
<page url="https://app.notion.com/p/40c9c563042581ac9e64cd78769471df" icon="🛠️">
<ancestor-path>
<parent-page url="https://app.notion.com/p/4019c56304258179bfa0fc93d15ac390" title="Season 03 — Shadows of Privacy — Moonlight"/>
<ancestor-2-page url="https://app.notion.com/p/4019c563042581469a0edc7e30a6eff9" title="ACT I — The World Is Breakable"/>
<ancestor-3-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
<properties>
{"title":"11 — Production Tracker & QA — Season 3"}
</properties>
<iconMetadata>{"type":"emoji","emoji":"🛠️"}</iconMetadata>
<content>
<callout icon="🛠️" color="yellow_bg">
<b>Tracker de documentação, implementação e QA — Season 3.</b> Fases descritas no Notion, sem comprovação de deploy, contratos, ZK circuit/verifier, frontend ou quantidade de slides. Status “NÃO VERIFICADO” <b>não significa</b> não implementado. Evitar marcar como concluído sem execução reproduzível.
</callout>

# Estado editorial inicial

- Prologue, Cases 01–10, Witness e Witness Spire: cânone existente preservado.
- Matriz de evidências, threat model, roteiro de slides e blueprints: especificações de produção desta revisão; ainda requerem adaptação a implementações reais.
- Privacy/ZK não devem ser declarados seguros com base em um texto de design. O scope de cada propriedade precisa ser comprovado no código e no protocolo.

# Inventário de fases

| Fase | Natureza predominante | Risco central | Evidência de produção |
| --- | --- | --- | --- |
| 00 — Valid Transfer | Narrativa | Confundir proof válida de settlement com associação atual | Frontend não verificado |
| 01 — Public Secret | BUG | Secret on-chain dito “privado” | Fixture e QA não verificados |
| 02 — Loud Whisper | BUG | Event leak confundido com storage leak | Fixture e QA não verificados |
| 03 — Someone Else's Face | BUG | Replay genérico confundido com causa histórica | Fixture e QA não verificados |
| 04 — The Denied | BUG | Timeline admin/policy incoerente | Fixture e QA não verificados |
| Boss — The Witness | COMPOSIÇÃO | Vitória de fuga sem objetivo verificável | Fixture e QA não verificados |
| 05 — Spent Twice | INVARIANT FAILURE | Reutilização do nullifier erroneamente prova culpa | Pool e QA não verificados |
| 06 — Proof That Lied | ZK SOUNDNESS | Proof válida interpretada como claim verdadeira | Circuit/verifier não verificados |
| 07 — Glass Trail | THREAT MODEL | Confidentiality confundida com anonymity | Fixture/trace não verificados |
| 08 — Key That Sees | BUG + GOVERNANCE | “View key universal” inexistente / expiry | Capability e QA não verificados |
| 09 — A Valid Lie | VERIFIER REGISTRY | Repetir falha do circuito de Case 06 | VK binding e QA não verificados |
| 10 — Become Missing | CORRECT COMPOSITION | Anonimato absoluto prometido sem threat model | Modelo e QA não verificados |
| Final — Witness Spire | COMPOSIÇÃO | Refutação tratada como absolvição; disclosure excessivo | Prover e QA não verificados |

# Prioridades

<b>P0 — Consistência e verificação formal</b>

- Fixar prova histórica de settlement, binding sender/recipient, policy na execução e alteração DENIED posterior.
- Diferenciar Case 03 (reprodução de perfil forjado) de Case 04 (causa histórica do DENIED).
- Definir verificador objetivo para Boss Witness e Final Spire.
- Diferenciar Case 06 under-constrained de Case 09 wrong VK/policy registry.
- Definir privilégio e expiração da auditor capability no Case 08 sem alegar segredo do ledger.
- Especificar MISSING no modelo de observação e scope da privacidade.
- Garantir que o epílogo permaneça um segundo procedimento, com perda institucional não financeira.

<b>P1 — Experiência e narrativa</b>

- Diferenciar loops jogáveis de Case 01/storage, 02/events, 03/profile e 04/governance.
- Entre Cases 05–09 construir confiança por atos demonstráveis de reciprocidade, não diálogo explicativo.
- Provar que cada pista dos Witnesses tem fonte rastreável, e que SOURCE E.V. é identificada só no clímax.
- Adaptar os beats de slides a componentes existentes, mantendo imagem cinematográfica e Breach Report separado.

<b>P2 — Polimento</b>

- Estados visuais progressivos do Veil, Glass District, Pool, Blind Quarter e Spire.
- Efeitos de rastreio e degradação de observation confidence, sem confundir grau de confiança da inferência com probabilidade matemática garantida.
- Pequena sequência pós-epílogo que reusa Become Missing, sem nova vulnerabilidade.

# Checklist por fase

- [ ] Classificação da fase como BUG / INVARIANT / THREAT MODEL / CORRECT COMPOSITION clara.
- [ ] Objetivo em linguagem narrativa e atividade técnica distinta da anterior.
- [ ] Caso vulnerável e secure mirror/defesa, quando aplicáveis.
- [ ] Public inputs, commitments e event/ledger sources explicitamente definidos.
- [ ] Teste positivo de vitória e negativo/false positive.
- [ ] Estado inicial/reset determinístico e replay isolado (nenhum ativo real).
- [ ] Verifier independente de UI e de contratos que o player possa substituir.
- [ ] Evidência armazenada no Evidence Locker com origem, escopo e data.
- [ ] Gancho para próximo Case sem adivinhar relações.
- [ ] Slides não ensinam bug antes de o jogador explorá-lo.
- [ ] Breach Report explica alcance/limite da propriedade de privacidade e mitigação quando aplicável.
- [ ] Consentimento e disclosure não viram escolhas falsas com finais distintos.
- [ ] Backend/frontend testados no stack Soroban/ZK de versões fixadas.

# Registro a preencher após acesso ao repositório

<b>Case ID; owner; branch/commit; Soroban SDK/runtime; stack ZK (circuit + proving/verifying system); testnet/local fixture; proved public inputs; secure mirror; exploit trace; verificador; screenshots/slides; playtest; blockers; status.</b>

# Estratégia de playtest

1. <b>Prologue–Case 04–Witness:</b> testar se o jogador entende por que informações públicas comprometem privacidade e por que a associação atual não basta para julgar o passado.
2. <b>Cases 05–06:</b> separar nullifier replay de under-constrained circuit; perguntar se proof válida garante claim verdadeira.
3. <b>Cases 07–09:</b> observar interpretação de metadados, limite de auditoria e associação de VK/policy.
4. <b>Case 10 + Final:</b> testar se o jogador alcança MISSING no threat model, constrói prova positiva e consegue divulgar apenas claims necessárias.
5. <b>Epílogo:</b> perguntar o que Rhea revelou, para qual processo, quando decidiu e o que foi efetivamente suspenso.

# Referências

- <mention url="https://app.notion.com/p/4019c56304258120bb15ce9d8ce99725" />
- <mention url="https://app.notion.com/p/40c9c56304258163a9f8c7ed2abcdf1c" />
- <mention url="https://app.notion.com/p/40c9c563042581cbb4f2c2c801ec0ea5" />
- <mention url="https://app.notion.com/p/4029c56304258153a677d79433eb2a70" />

# QA P0 de causalidade e privacidade — decisões aprovadas

- [ ] Prologue demonstra receipt de devolução da garantia, DENIED posterior e motivo de protocolo excepcional de rede; não afirma culpa pela mera correlação.
- [ ] Case 01: Sera apresenta extrato administrativo redigido, fonte E.V. protegida e envelope de proveniência não público; não entrega exploit.
- [ ] Case 04: três fontes independentes — documento Sera, evento CANCELLED/PENDING, aceitação do operador + DENIED pós-execução.
- [ ] Case 07: mismatch de identificadores de beneficiário exige atestação limitada compartilhada com Rhea, com propósito declarado e risco sinalizado.
- [ ] Case 09/10: sender witness entregue autenticado antes da separação; não requer reencontro.
- [ ] Final: Breaker aparece à Spire fisicamente, com credential de caso restrita; First Witness o identifica na sessão sem conseguir rastrear entrada/saída continuamente.
- [ ] A prova de settlement usa policy histórica e atestação beneficiário; full disclosure alcançaria envelope jornalístico associado ao dossiê, mas prova mínima exclui origem E.V.
- [ ] Epílogo: atestação voluntária de Rhea refere-se <b>apenas</b> à investigação independente de Lumen após encerramento de Moonlight; somente credencial institucional intercity é suspensa.
- [ ] Stack ZK, threat model, views e modelos de observação testados antes de declarar segurança ou certeza do resultado.
</content>
</page>

