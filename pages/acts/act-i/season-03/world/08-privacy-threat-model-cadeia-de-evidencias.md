---
notion_id: 40c9c563-0425-8163-a9f8-c7ed2abcdf1c
source: https://app.notion.com/p/40c9c56304258163a9f8c7ed2abcdf1c?pvs=204
title: "🔐 08 — Privacy Threat Model & Cadeia de Evidências"
exported_at: 2026-11-07
---

**Documento de produção / Season 3.** Modelo de ameaça e matriz de evidências para as 13 etapas da campanha. Preserva o cânone; hipóteses de fixture, APIs e telas ainda dependem de implementação. Não tratar privacidade como propriedade nativa e automática de toda operação Stellar/Soroban.

# Tese de Moonlight

A pergunta evolui de “quem consegue ver um valor?” para **“quem pode inferir minha identidade e quem tem direito de revelar relações?”**. Privacidade não é invisibilidade universal. O Breaker precisa limitar a informação acessível sem apagar provas legítimas.

# Propriedades que o jogo precisa distinguir

| Propriedade | Protege | Não garante automaticamente |
| --- | --- | --- |
| Confidencialidade de conteúdo | Valor, saldo ou payload quando há protocolo adequado | Identidade do sender, receptor, tempo e grafo transacional |
| Anonimato / unlinkability | Relação entre identidades e ações em modelo adversarial definido | Sigilo de metadados não contemplados no protocolo |
| Integridade de associação | Que uma associação de compliance represente authority/policy corretas no momento | Que policy atual seja retroativamente válida |
| ZK soundness | Que prova aceita satisfaça **o circuito e public inputs vinculados** | Que circuito codifique o claim de negócio esperado |
| Auditoria proporcional | Revelar somente a afirmação e âncoras necessárias | Que exista uma “view key” universal, sempre apropriada ou irrevogável |
| Nullifier uniqueness | Não reutilizar a mesma note em protocolo de gasto | Ocultar automaticamente tempo, sender/receiver ou todos os vínculos |
| Operational MISSING | Modelo observador não reconstrói a trajetória atual com confiança suficiente | Apagar eventos antigos, revogar identidade pública ou impedir todas as formas possíveis de observação |

**Regra técnica:** storage e eventos on-chain são superfícies de observabilidade públicas. Onde a narrativa exige confidencialidade, a fixture deve usar **dados cifrados, commitments, proofs e/ou serviços explicitamente modelados**; não alegar que um require\_auth torna storage ilegível. Uma capability de auditor expirada deve ser verificada no consumer; isso não desfaz plaintext ou keys já divulgados no passado.

# Modelo de adversários — sem onisciência

- **Observador público:** consulta ledger, transações, eventos e dados de infraestrutura expostos.
- **Witness autorizado:** pode acessar informações adicionais somente mediante policy, credential e contextos previstos; a ação de First Witness exige legitimidade processual.
- **Architect:** observa padrões e associações por um modelo probabilístico. MISSING significa confiança insuficiente para seguir a rota atual, não invisibilidade metafísica.
- **Rhea:** detém sender witness e, mais tarde, conhece uma associação institucional histórica compartilhada pelo Breaker em escopo limitado. Não recebe private key geral, nem habilidade de alterar wallet alheia.
- **Jornalista Sera:** protege SOURCE E.V.; disclosure total revela a conexão e colocaria uma pessoa concreta em risco.
- **Serviços institucionais:** podem suspender a credencial intercity emitida por sua autoridade após apuração de Lumen, mas não desligar a wallet Stellar.

# Matriz de observabilidade e continuidade

| Momento | Superfície exposta / prova | O que a Spire aprende | O que o player consegue demonstrar | Gancho |
| --- | --- | --- | --- | --- |
| Prólogo | Settlement pública com payload confidencial, association atual DENIED | Recipient ligado a operação contestada | Validity da proof e estado de compliance atual são perguntas distintas | Safehouse rastreada sem quebra criptográfica |
| 01 — Public Secret | Credencial em storage público | Local/rota de safehouse | Segredo se extrai do ledger sem autorização privilegiada | Eventos publicam informação indevida |
| 02 — Loud Whisper | Events com dado sensível | Relação/timing de operações | Estado principal pode estar protegido e evento vazar | Profile do Breaker |
| 03 — Someone Else's Face | Registry de identity mutável sem auth adequada | Association set pode ser falsificado | Reprodução de falsificação em fixture; NÃO é necessariamente causa histórica do DENIED | Investigar admin transfer |
| 04 — The Denied | Pending admin não eliminado após cancelamento | Histórico de governança associado ao DENIED | Settlement legítima em t0; cancel em t1; retomada indevida em t2; DENIED em t3 | Midboss Witness |
| BOSS — The Witness | Traces de registro/rota e demanda de disclosure | Região e possível rota atual | Escapar por composição de provas/rotas de disclosure mínimo, sem view key geral | Acusação de nullifier duplicado |
| 05 — Spent Twice | Nullifier repetido em fixture vulnerável | Acusação técnica de double-spend | Repetição no mesmo estado vulnerável não comprova dois gastos atribuíveis ao Breaker | Sender witness Rhea necessário |
| 06 — Proof That Lied | ZK proof aceito para relação under-constrained | Claim acusatório aparentemente validado | Falta de binding do recipient/commitment/claim no circuito | Perseguição via metadados |
| 07 — Glass Trail | Addresses, tempo, correntes visíveis | Rota provável, não identidade absoluta | Construir correlação e apontar hipóteses alternativas; depois reduzir a rota observável | View capability da Spire |
| 08 — Key That Sees | Audit credential expirada aceita pelo consumer | Acesso além da janela autorizada | Invalidar consumer que ignora expiry; reconhecer escopo de key/capability | Verifier registry inconsistente |
| 09 — A Valid Lie | VK de versão/policy errada | Proof matematicamente válido, claim errado | Binding VK/circuit/policy insuficiente; preservar capability de disclosure apesar da vontade de Rhea | MISSING como objetivo |
| 10 — Become Missing | Fluxos de commitments/nullifiers e metadados de rota | Perda de confiança de associação atual | Composição sem reuso, leaks ou associação trivial conforme threat model delimitado | Infiltração Witness Spire |
| Final — Witness Spire | Sender+recipient witnesses + state/policy históricos | Prova legítima do settlement em t0 | Proof positiva válida e mínima; acusação original insuficiente; First Witness encerra ordem | Epílogo separado de Lumen |
| Epílogo — O Sétimo | Atestação histórica assinada por Rhea | Identidade da ação antiga em Lumen, não rota atual | Credencial intercity suspensa; privado ≠ inimputável | Horizon/Galexie, Voss pelo passado |

# Evidência positiva e refutação — não confundir

**Refutar a acusação não basta para provar conformidade.** Cases 05, 06 e 09 demonstram insuficiências em evidências acusatórias ou verificações; o Final precisa ainda compor prova **positiva** de que a settlement foi autorizada/conforme policy no ledger histórico de execução.

O pacote positivo exige:

1. Commitment/transaction identifier da settlement original e policy/version vigentes no ledger da operação.
2. Sender witness de Rhea e recipient witness do Breaker vinculados à **mesma operação** e aos mesmos public inputs.
3. Ancoragem autenticada de estado histórico mostrando que a association válida na execução foi alterada **depois** por autoridade administrativamente cancelada, embora tecnicamente reativada.
4. Claims selecionadas verificadas independentemente — sem revelar amounts, fontes de Sera, grafo completo ou wallets de terceiros.
5. Decisão humana de First Witness de encerrar a demanda automática de full disclosure após receber prova suficiente.

## Relações temporais obrigatórias (sem inventar ordem não definida)

- **T\_settlement**: settlement legítima sob policy/association vigente na sua execução.
- **T\_cancel**: transferência administrativa pendente cancelada institucionalmente, mas o pending state permanece por erro.
- **T\_accept**: antiga entidade aceita o pending indevido e retoma autoridade após o cancelamento.
- **T\_denied**: associação é alterada para DENIED depois da settlement.
- **T\_investigation**: Witness Spire observa proof histórica válida e association atual contestada.

**Ordem comprovada:** T\_cancel \< T\_accept, T\_settlement \< T\_denied, T\_accept \< T\_denied, T\_denied \< T\_investigation. A ordem relativa entre **T\_cancel** e **T\_settlement** não está fixa no cânone; escolher quando desenhar as fixtures, preservando a policy válida na execução. Não inventar block heights antes de implementar testes.

# Confiança Rhea × Breaker — prova por ações

- **Case 05:** troca mínima e necessária de sender/recipient material, sem confiança geral.
- **Case 06:** Rhea entrega voluntariamente material autenticado que poderia reter; Breaker não usa o bug para destruir toda a verificação.
- **Case 07:** ela protege a rota atual; ele compartilha em escopo limitado vínculo histórico de Lumen, com aviso claro de risco. Rhea **não decidiu** divulgá-lo.
- **Case 08:** Rhea se expõe à revisão institucional; Breaker protege a origem dela.
- **Case 09:** Rhea quer destruir capability; Breaker impede e ela respeita, genuinamente.
- **Case 10:** separação estratégica; confiança existe, e a incerteza de reencontro é sincera.
- **Final:** os dois concluem a prova mínima; Moonlight CASE CLOSED.
- **Epílogo:** somente depois surge pedido separado de Lumen; Rhea decide unilateralmente atribuir conta operacional ao Breaker. Sem hacking de wallet nem traição premeditada.

# QA de privacidade e causalidade

- [ ] Cada revelação nasce de dados que o adversário daquele momento poderia observar.
- [ ] Metadados não desaparecem só porque amounts estão confidenciais.
- [ ] Proof válida para um circuito falso não é claim comercial verdadeiro.
- [ ] MISSING é score insuficiente de observação atual; não apaga Lumen histórica.
- [ ] Um usuário consegue explicar o mínimo revelado versus informação preservada no Final.
- [ ] A fonte E.V. não é identificada cedo, salvo em material interno marcado spoiler.
- [ ] A decisão institucional e a ruptura com Rhea ocorrem somente após conclusão real da Witness Spire.

# Integração da aprovação canônica — modelo de ameaça e cadeia de prova

| Superfície | Prova/ação agora definida | Limite obrigatório |
| --- | --- | --- |
| Devolução Cascade | Rhea envia parcela de garantia operacional devida ao Breaker sob policy t0 | Confidential amount não implica ocultar todos metadados |
| Reclassificação | Operador de compliance usa pending admin formalmente cancelado e reclassifica depois | Sem retroatividade, sem conspirador novo |
| Investigação de rede | DENIED + múltiplas operações correlacionadas acionam policy excepcional de full disclosure | Grafo de risco não prova culpa |
| Vínculo de beneficiário | Conta Lumen e credencial intercity aparentemente divergentes são ligadas por atestação limitada com Rhea | Consentimento contextual não autoriza denúncia externa |
| Handoff do witness | Rhea entrega pacote antes de Case10 | Sem private key nem canal posterior que reidentifique rota |
| Sessão final | Breaker se apresenta fisicamente com autenticação processual restrita | MISSING significa não rastreabilidade contínua, não invisibilidade instantânea |
| Sera / SOURCE E.V. | Documentos contêm conteúdo útil e envelope de provenance com metadados da fonte | Full disclosure do dossiê exporia envelope; prova mínima o exclui |

**Cronologia de controle:** T\_settlement \< T\_DENIED; T\_cancel \< T\_accept \< T\_DENIED; não inventar ordem não estabelecida entre T\_cancel e T\_settlement. Após case CLOSED, processo Lumen recebe atestação de Rhea e afeta somente credencial institucional intercity.

**Aceitação:** o Final deve demonstrar positivamente titularidade/eligibilidade de recipient da garantia em t0 e não apenas refutar inferência acusatória. Mostrar exatamente quais public inputs, hashes e credenciais permitem isso.
