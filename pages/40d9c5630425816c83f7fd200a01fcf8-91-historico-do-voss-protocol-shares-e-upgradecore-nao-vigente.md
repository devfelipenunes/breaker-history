---
notion_id: 40d9c563-0425-816c-83f7-fd200a01fcf8
source: https://app.notion.com/p/40d9c5630425816c83f7fd200a01fcf8?pvs=204
title: "🗃️ 91 — Histórico do Voss Protocol | Shares e UpgradeCore (não vigente)"
exported_at: 2026-11-07
---

Here is the result of "fetch" for the Page with URL https://app.notion.com/p/40d9c5630425816c83f7fd200a01fcf8 as of 2026-11-03T15:58:08.484Z:
<page url="https://app.notion.com/p/40d9c5630425816c83f7fd200a01fcf8" icon="🗃️">
<ancestor-path>
<parent-page url="https://app.notion.com/p/40d9c563042581939ffad5f7e19042e3" title="90 — Arquivo Editorial e Estudos | Season 1"/>
<ancestor-2-page url="https://app.notion.com/p/4009c563042581359693d42f09d41062" title="Season 01 — The First Layer"/>
<ancestor-3-page url="https://app.notion.com/p/4019c563042581469a0edc7e30a6eff9" title="ACT I — The World Is Breakable"/>
<ancestor-4-page url="https://app.notion.com/p/4009c563042581a4be0ffd6b2524197c" title="BREAKER — Series Workspace"/>
</ancestor-path>
<properties>
{"title":"91 — Histórico do Voss Protocol \\| Shares e UpgradeCore (não vigente)"}
</properties>
<iconMetadata>{"type":"emoji","emoji":"🗃️"}</iconMetadata>
<content>
<callout icon="🗃️" color="yellow_bg">
<b>ARQUIVO DE PESQUISA — NÃO VIGENTE.</b> Esta é a cópia integral das propostas antigas de Voss Protocol, incluindo shares guardadas nos Cases e UpgradeCore. Foi separada da especificação ativa para reduzir ambiguidades e manter rastreabilidade. Para roteiro e gameplay atuais, consulte <mention url="https://app.notion.com/p/40d9c563042581bf886cfc339d730fd1" /> e <mention url="https://app.notion.com/p/4039c56304258137ae19e8787acc1d1f" />. Esta página não é prova de implementação.
</callout>

# HISTÓRICO — Modelo anterior de shares armazenadas nos Cases (NÃO VIGENTE)

Warehouse <b>17</b>, Forgotten Floor <b>24</b> e Sector <b>13</b> não formam a senha numérica <code>172413</code>. Os números são <b>endereços narrativos</b> de três vestígios diferentes, preparados por Voss como forma de recuperar material de diagnóstico. O jogador os encontra em momentos separados da Season; só na Spire compreende que constituem três partes de um mesmo protocolo.

O payoff não é apenas uma frase escondida. O jogador precisa <b>reconstruir uma chave de 256 bits, satisfazer um commitment em Soroban, conferir um manifesto histórico assinado e usar o material recuperado como entrada da cadeia técnica do Final Boss</b>.

## Regra editorial

- O enigma é obrigatório para a conclusão técnica do Final Boss, mas é <b>dedução e coleta de evidências</b>, não a introdução de uma quarta vulnerabilidade.
- O destino da história permanece único: <code>QUALIFIED / PROVISIONAL</code>. Não há menus de moral, endings alternativos ou decisão de aceitar o Architect.
- O manifesto é anterior à investigação atual; Voss não conhecia o futuro Breaker e não assinou uma autorização irrestrita para ele.
- Uma assinatura de Voss prova, no limite, a autenticidade de um texto sob uma chave pública ancorada. <b>Ela NÃO autoriza atualizar o ArchitectCore</b>. A escalada posterior depende de bugs reais, não de um “master key” deixado por Voss.
- O Observer independente continua atribuindo o status final após validar os estados e a chain of evidence. O contrato vulnerável do Core não determina a própria qualificação.

# Design de experiência — antecipação por três Cases

## HISTÓRICO — Case 03 / SHARE A (substituído por rodapé de arquivo)

Na custódia técnica temporária da Ghost Key surge um objeto de evidência chamado <code>W17 / DIAGNOSTIC TRACE</code>. O Breaker preserva o objeto integralmente no dossiê já existente, sem atribuir ao item uma nova função de abrir portas. O conteúdo decodificado guarda um <code>share_a: bytes32</code> e um <code>evidence_id</code>. A interface mostra uma etiqueta de arquivo comum, não uma indicação “1 de 3”. A contestação de propriedade, o dano humano e a custódia da Ghost Key continuam sendo o centro da fase.

## HISTÓRICO — Case 04 / SHARE B (substituído por rodapé de arquivo)

O registro recuperável em <code>Persistent</code> de Floor 24 contém uma referência de diagnóstico <code>F24 / ARCHIVED ENTRY</code>. Depois da restauração legítima via footprint, o jogador pode inspecionar <code>share_b: bytes32</code> em uma entrada técnica. Não ler dado arquivado no contrato antes de restaurar o estado; não confundir TTL com material apagado irreversivelmente. A pista é observável, mas não necessária para vencer o Case isoladamente.

## HISTÓRICO — Case 07 / SHARE C (substituído por rodapé de arquivo)

O snapshot histórico do <b>indexador externo</b>, exposto pela recuperação degradada após o exploit de resource exhaustion, inclui o item <code>S13 / RECOVERY SNAPSHOT</code> com <code>share_c: bytes32</code>. Não fingir que storage Soroban on-chain pode ser ocultado de leituras públicas. O índice externo e seus critérios de acesso já fazem parte do cânone do Case 07. Não criar nova falha obrigatória nem exposição de dados de identidade.

## Justiça investigativa

Os registros narrativos dos níveis 03 (Warehouse 17), 04 (The Forgotten Floor) e 08 (Sector 13) carregam o mesmo rodapé diegético: <code>ARCHIVE: LEGACY / RETENTION: OPEN</code>. O manifesto no nível 11 repete esse rodapé. Os registros permanecem nos casos em que foram encontrados; o jogador pode reabrir os níveis já concluídos e consultar Arquivos. Eles fornecem contexto para a descoberta, não os bytes criptográficos.

A tela inicial do final não lista as três localizações, não conta referências e não explica XOR. O jogador percebe a relação comparando arquivos antigos com o manifesto. Dicas opcionais avançam da observação das imagens e registros à comparação de campos; somente a última explicita a combinação byte a byte com XOR. O compromisso confirma a reconstrução para a instância, rede e carteira atuais.

# Núcleo criptográfico

## Reconstrução 3 de 3

No provisionamento de cada instância de desafio:

- Gerar <code>key K</code> aleatória de <b>32 bytes</b> e independentes <code>share_a</code> e <code>share_b</code>, também aleatórios e de 32 bytes.
- Calcular <code>share_c = K XOR share_a XOR share_b</code>.
- Na solução, reconstruir <code>K = share_a XOR share_b XOR share_c</code>.
- Se faltar ao menos uma share uniforme independente, as demais não revelam K; cada share deve ter 256 bits e não pode ser um número pequeno transformado em hash.
- Para fins de gameplay, o solver recupera as três shares; não chamar isso de Shamir, limiar 2-de-3, multisig ou ZK.

O rótulo <code>17/24/13</code> é localizador e ordem editorial, <b>não material de entropia</b>. Fazer <code>SHA256("172413")</code> seria trivialmente reversível por brute force e não satisfaz a proposta.

## Commitment de instância

Definir bytes canônicos e separados por domínio:

<code>commitment = SHA256(encode("BREAKER:VOSS:EVIDENCE:v1", network_id, instance_id, key32))</code>

O <code>network_id</code> e <code>instance_id</code> são fornecidos pela configuração legítima do challenge/verificador, jamais escolhidos pelo caller da transação de unlock. O commitment é calculado no provisionamento e armazenado no EvidenceGate; a assinatura histórica de Voss <b>não</b> precisa vincular-se ao ID futuro do jogador. Serialização canônica com tamanho explícito para evitar concatenação ambígua.

## Modelo do EvidenceGate

Funções planejadas, sujeitas a checagem e implementação com a versão vigente do SDK:

```rs
// Pseudocódigo de interface, não código Soroban compilado.
unlock_evidence(player: Address, key: BytesN<32>) {
    player.require_auth();
    assert_eq!(player, challenge_instance.owner);
    assert_eq!(sha256(canonical_domain_payload(instance, key)), commitment);

    evidence_unlocked[player] = true;
    emit("EvidenceUnlocked", player, instance.id);
}

verify_voss_manifest(player: Address, manifest: Bytes, signature: BytesN<64>) {
    player.require_auth();
    assert!(evidence_unlocked[player]);
    assert_eq!(sha256(manifest), expected_manifest_hash);
    assert!(verify_ed25519(pinned_voss_public_key, manifest, signature));

    manifest_verified[player] = true;
    emit("ManifestVerified", player, historical_record_id);
}
```

<code>expected_manifest_hash</code> e <code>pinned_voss_public_key</code> devem derivar de dados de configuração ancorados/históricos que o jogador possa auditar; não são argumentos controlados pelo atacante. O contrato não concede privilégios administrativos. O player pode gerar a transação para demonstrar conhecimento da chave e origem do manifesto, mas não pode transformar <code>manifest_verified</code> em autorização genérica de upgrade.

A identidade documental de Voss deve ser sustentada por mais de um registro prévio do mundo; a matemática sozinha comprova assinatura por aquela chave, não identidade civil.

## Sigilo e arquitetura honesta

A rede Stellar/Soroban é pública: calldata, storage e eventos podem ser inspecionados. Revelar K em <code>unlock_evidence</code> expõe K publicamente, portanto esta mecânica é <b>prova de obtenção de evidência e progressão por instância, não confidencialidade persistente</b>. Evitar alegar que uma função <code>require_auth()</code> oculta informação on-chain.

- A e B podem ter representações auditáveis em artefatos públicos já existentes, mas C deve ser obtida pelo arquivo externo de Sector 13 na experiência inicial; jamais publicar todas as shares em texto claro nos mesmos dados que todo jogador consulta no início.
- Para multiplayer/competição, gerar K, shares, commitment e owner binding <b>por instância</b>. Após uma solução pública, o segredo daquela instância deixa de ser segredo; a transação não deve servir para ganhar pontos/autorizações em outra instância.
- Se for desejável manter privado o manifesto antes do final, publicá-lo apenas cifrado e permitir decriptação local com chave derivada de K (e nonce/AEAD corretos); isso é uma extensão opcional e necessita modelo de ameaça. A especificação aprovada <b>não depende</b> de confidencialidade contínua nem de serviço de decriptação arbitrário.
- Não tratar hash como encoding reversível, assinatura como autorização, nem hashlock como ZK.

# Manifesto histórico de Voss — autenticidade não é autoridade

Um registro anterior ao Vault foi assinado por Voss e referenciado pela operação programada que o Final Boss já possuía. Campos de referência:

```txt
VOSS DIAGNOSTIC MANIFEST (v1)
historical_record_id
timestamp_historical
operation: diagnose_core
target: ControlNode
diagnostic_reference
evidence_root_or_digest
historical_nonce
voss_signature (Ed25519)
```

O texto exato assinado deve incluir domain separation, identificação de rede e target histórico. O <code>manifest_hash</code> é fixo, não editável pelo caller. O jogador cruza o timestamp do manifesto com os registros de Voss anteriores ao incidente do Vault, mas não aprende os termos de sua decisão <code>REFUSED</code>.

O manifesto <b>não</b> contém <code>grant_admin</code>, <code>upgrade</code> ou privilégio sobre o Architect. Isso mantém o dilema dramático: o Breaker recupera uma instrução autêntica de diagnóstico e é ele próprio quem usa falhas de autorização para transformá-la em controle do Core.

# Integração exata ao Final Boss atual — fonte: decisão 71 e código

```txt
Níveis concluídos 03/04/08
  └─ registros de arquivo com rodapé recorrente
        └─ jogador reconhece a origem comum
              └─ instância 11: campos públicos do contexto → commitment
                    └─ manifesto Ed25519 histórico
                          └─ rejeição autenticada do Decoder registrada como VossProof
                                └─ instância 12: nova prova de contexto e assinatura
                                      └─ Timelock: DiagnoseCore → OpenForensicSession(player)
                                            └─ execução única → validador independente
                                                  └─ QUALIFIED / PROVISIONAL
```

- Os registros dos níveis antigos são pistas narrativas; o código on-chain deriva as shares públicas do contexto e do índice da instância atual. Elas não são segredos nem bytes armazenados nos casos anteriores.
- O nível 11 preserva o erro do Decoder como parte do exploit. O nível 12 repete a prova contextual em uma instância nova, respeita o timelock e consome o payload uma vez.
- A assinatura fixa autentica o comando histórico de Voss. Ela não concede autoridade nem permite substituir WASM.
- O Observer/validador independente decide a conclusão a partir do estado da instância. A apresentação das pistas não altera os contratos nem o resultado on-chain.

# Roteiro in-game — camada de descoberta (revisão 2026-11-02)

1. <b>Primeiro contato:</b> o manifesto assinado mostra a operação histórica e o rodapé <code>ARCHIVE: LEGACY / RETENTION: OPEN</code>. Não lista locais, quantidade de pistas ou método.
2. <b>Reconhecimento:</b> o jogador pode voltar aos níveis concluídos e reler os registros de Arquivos. A repetição do rodapé liga documentos de procedências diferentes; os números nas imagens funcionam como endereços narrativos.
3. <b>Investigação técnica:</b> o ABI e a instância pública expõem três campos associados ao contexto atual. A reconstrução é uma dedução técnica do jogador, não um tutorial na interface. Os campos antigos não são as shares nem precisam ser copiados para a nova instância.
4. <b>Confirmação:</b> a carteira dona submete a reconstrução; o commitment confirma o contexto da instância. A assinatura Ed25519 prova a autenticidade do manifesto histórico, não autoriza ações fora de <code>diagnose_core</code>.
5. <b>Rewrite:</b> o Decoder retorna uma rejeição específica, mas o nível 11 a registra incorretamente como <code>VossProof</code>. A falha demonstrada é o tratamento do resultado.
6. <b>The Architect:</b> com uma instância nova, a operação amadurece após o timelock. O jogador troca o payload <code>DiagnoseCore</code> por <code>OpenForensicSession(player)</code>; a validação independente confirma a operação executada. Não há upgrade de WASM.

O canal privado de Mara termina em Rewrite. O mistério <code>REFUSED</code> continua reservado ao payoff posterior; o protocolo abre um registro diagnóstico, não um expositor de spoilers.

# Testes e critérios de aceite

- [ ] A, B, C são recuperáveis por ações documentadas nos Cases correspondentes e continuam disponíveis no Evidence Locker após concluídos.
- [ ] As três shares corretas reconstruem K; qualquer share alterada falha. Números <code>172413</code> e derivadas triviais falham.
- [ ] Hash de compromisso combina rede, instância, domínio e bytes canônicos. Não aceitar compromisso ou public key enviados pelo usuário.
- [ ] Falha sem assinatura da carteira do jogador/owner incorreto; falha de replay em outra instância.
- [ ] Manifesto adulterado, assinatura inválida, chave pública substituída, target/ação diferente ou replay entre domínios falham.
- [ ] O manifesto original <code>diagnose_core</code> não concede diretamente admin, upgrade ou status.
- [ ] EvidenceGate validado + Decoder não explorado <b>não</b> produz <code>VOSS_PROOF</code>; a cadeia técnica continua necessária.
- [ ] O Wasm falso que retorna <code>QUALIFIED</code> sozinho não altera o status do Observer.
- [ ] Testes do contrato vulnerável e de sua versão corrigida, além do verificador independente e reset determinístico por instância.
- [ ] Auditoria de visibilidade dos dados na rede pública, sem claims enganosas de sigilo.
- [ ] Narrativa e conclusões idênticas com pistas descobertas cedo/tarde e com soluções técnicas alternativas permitidas.
- [ ] Teste de usabilidade sem walkthrough: o jogador entende a relação entre os números, o manifesto e a autorização sem tentativa-e-erro cega.

# Dependências e implementação — pendente

1. Gerador determinístico de fixture/instância com CSPRNG, K de 32 bytes, shares XOR e commitment.
2. Distribuir os artefatos W17/F24/S13 pelos ambientes atuais e registrar seus identificadores.
3. Definir política de owner, interfaces, digest e serialização do EvidenceGate compatíveis com SDK Soroban usado.
4. Public key histórica de Voss: ancoragem canônica, conteúdo exato do manifesto, assinatura e fixtures.
5. Integrar pré-condições ao ArchiveNode, entrada no Decoder, eventos e checagem do Observer.
6. Adicionar Evidence Locker e UI de recomposição/prova no BREAKER OS.
7. Implementar e executar testes negativos, replay entre instâncias e solve end-to-end.
8. Adaptar as cenas da novelização e da narrativa da Season após validação de ritmo, sem substituir o arco moral.

<b>Status real:</b> decisão de game design registrada; pseudocódigo e contratos <b>não implementados nem testados</b>. Chaves, hashes, assinaturas e artefatos finais ainda precisam ser gerados pela implementação.

# Referências de continuidade

- <mention url="https://app.notion.com/p/4009c5630425815581b2df01797d5365" />
- <mention url="https://app.notion.com/p/4009c5630425813cb1f3e2515b9de879" />
- <mention url="https://app.notion.com/p/4009c5630425815084b7dd82afc14074" />
- <mention url="https://app.notion.com/p/4009c56304258134a525e38dc0eba08b" />
- <mention url="https://app.notion.com/p/4019c56304258181a4e2ef561d8954a2" />
- <mention url="https://app.notion.com/p/4029c563042581d298eeddf85aac2d69" /> (estudo anterior, não canônico).

# Pesquisa — tornar a conexão entre os fragmentos discreta, mas justa

<b>Estado:</b> estudo editorial histórico de 2026-11-02. A decisão já foi incorporada à Final Narrative v1.4: rodapés recorrentes W17/F24/S13, prova contextual pública por instância, manifesto histórico autenticado, falha Decoder→VossProof e sessão forense no timelock. Este estudo não é aprovação pendente nem orientação para voltar ao modelo de shares secretas.

## Veredito

A intenção é boa: o jogador deve perceber por conta própria que pistas de casos antigos pertencem ao desafio final. Hoje, porém, o documento entrega essa intenção cedo demais. Rótulos como <code>SHARE A/B/C</code>, a indicação explícita de “3 references unresolved” e a descrição passo a passo da recomposição transformam a descoberta em execução de instrução.

A meta recomendada é <b>ocultar a categoria e a relação, não ocultar as evidências necessárias</b>. A solução deve parecer surpreendente antes da descoberta e inevitável depois que o jogador a entende.

## O que a pesquisa sustenta

- A palestra [Puzzle Writing: Best Practices, de Clara Fernández-Vara (GDC)](https://www.gdcvault.com/play/1013851/puzzle-writing-best) descreve o puzzle como um acordo: o jogo fornece informação suficiente, mantém o desafio e integra a solução ao mundo e à história.
- A tese de doutorado [Effective player guidance in logic puzzles, de Alice Lynch (University of St Andrews, 2024)](https://research-repository.st-andrews.ac.uk/handle/10023/29069?show=full) estudou formas de ajuda que orientam o jogador a deduzir passos mais fáceis em vez de completar a resposta por ele. Os estudos reportados encontraram melhor experiência e menor sensação de “cola” com esse tipo de assistência.
- O estudo de [Wauck e Fu sobre sistemas de dicas (IUI/ACM, 2017)](https://doi.org/10.1145/3025171.3025224) encontrou preferência dos participantes por receber menos dicas do que em algumas condições automáticas. Isso favorece pistas graduais e sob demanda, em vez de avisos frequentes que anunciam a solução.
- O artigo de referência de design [Cluing & Fairness](https://pvliesdonk.github.io/gamebook/content/articles/puzzles-clues-information/cluing-and-fairness.html) distingue indireção de obscuridade: a inferência pode ser difícil, mas cada passo precisa fazer sentido depois de descoberto. Também alerta contra depender de uma única pista crítica que o jogador pode ignorar.

## Aplicação ao final de BREAKER

1. <b>Os números nas imagens funcionam como endereços, não como código.</b> W17, F24 e S13 podem levar o jogador a arquivos ou locais já visitados. Evitar somá-los, concatená-los ou apresentar os valores como senha.
2. <b>Remover os rótulos didáticos.</b> Não chamar os dados coletados de “share”, não numerar os fragmentos como primeiro/segundo/terceiro e não nomear a operação criptográfica na interface.
3. <b>Dar unidade por uma assinatura de contexto.</b> Os três registros podem compartilhar, sem explicação, um detalhe documental recorrente — por exemplo, o mesmo padrão de origem, campo de diagnóstico ou convenção de arquivo. Separadamente, cada registro continua plausível dentro do caso em que aparece.
4. <b>Não anunciar a quantidade de pistas.</b> O registro final pode indicar que uma referência histórica está incompleta, sem dizer quantos itens faltam nem listar os três locais. O manifesto deve confirmar a descoberta quando o jogador trouxer a reconstrução, não ensinar a procurar “três shares”.
5. <b>Preservar acesso retroativo.</b> Depois de vencer um caso, os registros relevantes precisam continuar consultáveis no Evidence Locker. Uma pista discreta não pode virar uma pista perdível.
6. <b>Usar dicas progressivas e opcionais.</b> Se necessário, a primeira dica chama atenção para os números como referências; a seguinte pede comparação de proveniência entre registros; a última aponta para a operação entre campos. Cada dica deve orientar uma inferência, sem entregar bytes ou resposta final.
7. <b>Fazer o contrato confirmar, não explicar.</b> O commitment e a assinatura atestam que a recomposição e o manifesto correspondem aos dados esperados. Eles não devem substituir a descoberta narrativa nem alegar sigilo de valores publicados na rede.

## Como saber se ficou bom

Fazer um teste cego com pessoas que conheçam o público-alvo do jogo, mas não esta solução. Observar se encontram os registros antigos, se formulam hipóteses próprias, quais hipóteses falsas parecem razoáveis, quando pedem dica e se reconhecem o padrão retrospectivamente após a confirmação. Se ninguém percebe a relação, melhorar a recorrência/contexto das pistas; se todos apontam a resposta imediatamente, reduzir os rótulos e anúncios explícitos. Não avaliar só se conseguem enviar a transação: o objetivo é que entendam por que aqueles registros se conectam.

<b>Recomendação editorial:</b> manter a criptografia e o vínculo técnico ao desafio final, mas revisar a camada apresentada ao jogador para trocar instruções explícitas por pistas diegéticas recorrentes. Os números das imagens podem ser o primeiro fio; a evidência documental faz a conexão; o contrato dá a confirmação.
</content>
</page>

