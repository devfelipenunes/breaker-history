---
notion_id: 4029c563-0425-810b-9d95-cca9b3630952
source: https://app.notion.com/p/4029c5630425810b9d95cca9b3630952?pvs=204
title: "🎨 09 — Art Bible CANÔNICO | Identidade Visual Aprovada — Baseline Site S1"
exported_at: 2026-11-07
---

**Guia operacional complementar da Season 1:** [10 — Direção de Arte | Meridian S1 — Manual de Produção e Continuidade](10-direcao-de-arte-meridian-s1-manual-de-producao-e-continuidade.md) — especifica direção de câmera, poses, materiais, paleta por Case, fidelidade em edições, qualidade e QA, sem substituir esta baseline canônica.

**BASELINE VISUAL CANÔNICA — APROVADA PELO CRIADOR EM 23/10/2026.** Derivada de **14 artes já publicadas no site** e anexadas pelo criador na conversa: `homepage.webp`, `00.webp` a `12(1).webp`. As imagens existentes são referências positivas de aparência; este documento registra sua leitura e **não substitui nenhuma imagem do site**, nem afirma que os arquivos foram enviados para o Notion/Drive.

# Regra-mestra: consistência por referência, não por improvisação

**BREAKER deve parecer a mesma obra em todas as cenas e Seasons.** As novas artes precisam conservar gramática cinematográfica, silhueta, materiais, luz, iconografia, figurino e desenho consistente dos personagens, sem reproduzir literalmente a mesma arquitetura em todas as cidades. A arte aprovada tem precedência sobre descrição genérica ou prompt recém-escrito. Na dúvida, verificar a referência em vez de reinventar detalhes.

**Fontes desta análise:** as 14 imagens que já estão no site, enviadas diretamente em 23/10/2026. **Originais no Notion:** ainda não anexados aqui; o índice abaixo usa os nomes dos arquivos da conversa e deve receber futuramente links permanentes e/ou upload autorizado de cada arte. As referências de Drive antigas nos documentos de Season continuam válidas, mas não é possível assumir correspondência binária sem conferência.

# 1. Formato, câmera e apresentação

- **Proporção confirmada nas 14 imagens: 8:3 (2,667:1)**. A homepage mede **2048 × 768**; cada arte numerada mede **1600 × 600**. São banners cinematográficos horizontais, **não** imagens 16:9 ou quadradas.
- Preservar a linha do horizonte, arquitetura e sujeito no crop responsivo; preparar **safe area** para desktop e mobile. Não presumir que corte central funciona para toda cena: validar miniatura por miniatura.
- Estabelecimentos de cena com **planos amplos/wide**, eixo profundo, perspectiva arquitetônica imensa, repetição modular, linhas convergentes e sujeito humano em pequena escala. Não transformar os levels em close-ups de personagens.
- Câmera geralmente ao nível de uma plataforma, terraço, corredor, salão ou entrada, com **silhueta em primeiro/segundo plano** e monumento/fonte de poder ao fundo.
- Composição deve guiar o olho à **estrutura-chave do desafio** (Vault, porta, cubo, registro, torre, máquina), não apenas gerar cenário bonito.
- Interiores são quase tão grandiosos quanto exteriores; usar espaço negativo, verticalidade, salões institucionais, blocos suspensos, monumentos e sistemas físicos de dados.
- Realismo cinematográfico de ficção científica: texturas físicas críveis, aço e pedra desgastados, vidro espelhado, microdetalhe industrial, profundidade atmosférica, acabamento de concept art premium. Evitar ilustração cartunesca, anime, low-poly, neon de rua genérico, stock cyberpunk e aparência de jogo mobile casual.

# 1A. Especificação técnica obrigatória — formato, resolução e qualidade

**PRIORIDADE ABSOLUTA: identidade visual e continuidade.** Resolução superior é melhoria técnica, nunca licença para redesenhar Breaker, símbolos, edifícios ou iluminação. Os 14 arquivos do site são referências aprovadas; retoques estéticos (inclusive rostos visíveis em registros) ficam **adiados**, sem bloqueio da direção atual.

## Metadados reais verificados nos arquivos enviados em 23/10/2026

- **Quantidade:** 14 imagens.
- **Homepage (**`homepage.webp`**): 2048 × 768 px**, proporção **8:3**, arquivo de **249.804 bytes (\~250 kB)**.
- **13 cenas (**`00.webp`** até **`12(1).webp`**): cada uma 1600 × 600 px**, proporção **8:3**; tamanhos individuais de **128.700 a 210.132 bytes (\~129–210 kB)**.
- **Formato atual:** **WebP**, imagens abertas em modo **RGB**, **sem transparência/alpha**. As versões fornecidas são assets finais de site, não arquivos de trabalho em camadas.
- **Qualidade do encoder WebP original:** **não identificável com certeza pelos metadados disponíveis**. Não afirmar “quality 90” nem “lossless” sem fonte. Peso do arquivo não mede sozinho qualidade visual nem resolução nativa de geração.
- **PPI/DPI:** não determina a nitidez no navegador; priorizar **pixels, detalhes efetivos, contraste, composição e compressão**, não um número arbitrário de DPI.

## Padrão para os próximos banners

| Propriedade | Regra |
| --- | --- |
| Aspect ratio | **8:3 obrigatório** para banners de homepage, cenas de levels e bosses, até pedido expresso de outro layout |
| Referência de publicação | **1600×600** para cenas; **2048×768** para homepage — dimensões **atuais comprovadas**, não limite máximo |
| Master recomendado para futuras artes premium | **4096×1536 px**, 8:3, **meta de entrega/processamento** — não promessa de geração nativa em 4K |
| Master alternativo | **3200×1200 px** (2× banner de nível) quando a cena ou pipeline não comportar 4096×1536 |
| Master de preservação | **PNG sem perdas** ou arquivo-fonte/edição em máxima fidelidade disponível, preservando composição e origem |
| Exportação para site | **WebP** otimizado, 8:3, em versões responsivas; testar visualmente legibilidade e o peso do arquivo |
| Compressão de exportação | Testar qualidade WebP em faixa **85–92 como ponto de partida**, ajustar após comparação; não afirmar que esse era o valor das imagens originais |
| Espaço de cor | **sRGB** no arquivo web para aparência estável entre navegadores; preservar RGB e sem alpha se não houver necessidade de transparência |
| Controle de identidade | Sempre comparar lado a lado com os arquivos já publicados; **não aceitar melhora de pixels com mudança de personagem, emblema ou cidade** |

**Importante:** resolução master de 4096×1536 é um **alvo de pós-processamento/exportação**, não alegação de que o modelo produz naturalmente exatamente essa saída. Dependendo das resoluções nativas do gerador, criar na melhor qualidade disponível, fazer composição/crop consciente para 8:3, e **upscale de alta qualidade** para o master. Upscaling aumenta dimensões e pode melhorar apresentação percebida, mas **não recupera informação real perdida** nem garante novos microdetalhes corretos.

## Qualidade visual que deve ser preservada ou melhorada

1. **Detalhe arquitetônico:** vigas, painéis, grades, textura de metal, janelas e plataformas com perspectiva consistente; nenhum efeito de “derretimento” de estruturas.
2. **Fidelidade do protagonista:** silhueta do casaco, cabelo curto, escala e postura idênticos às referências; nunca “embelezar” inventando outra pessoa.
3. **Luz realista:** contraste alto sem pretos totalmente esmagados, pontos de luz com direção e reflexos coerentes; preservar luz dourada/âmbar e azul técnico.
4. **Profundidade cinematográfica:** névoa com gradação, horizonte, primeiro/meio/último plano e sem nitidez artificial de oversharpen.
5. **Detalhe local:** portas, números, emblema e monitores da cena corretos. Se um número ou palavra for essencial, preferir overlay vetorial/HTML supervisionado.
6. **Qualidade de entrega:** sem artifacts de compressão visíveis, banding de céu/fumaça, halos de upscale, textura plastificada ou serrilhado de fios/linhas.
7. **Teste responsivo:** crop 8:3 em desktop e visualização mobile — sujeito e landmark precisam continuar inteligíveis.

## Workflow aprovado para elevar qualidade sem perder identidade

**Passo 1:** partir de **referência aprovada do site** + ficha do Case + símbolos/personagens canônicos; não começar de “cyberpunk cinematic” genérico.

**Passo 2:** produzir arte com **máxima fidelidade nativa disponível no gerador** e composição pensada para 8:3. Caso a geração nativa use outro aspect ratio, fazer expansão/recomposição controlada, evitando cortar o foco visual.

**Passo 3:** comparar o resultado em tela cheia com os originais e validar primeiro **identidade**, depois **qualidade de imagem**. Se o aspecto visual mudou, reprovar mesmo em resolução maior.

**Passo 4:** ampliar a resolução do master se necessário (ideal 4096×1536, sem prometer detalhe nativo), verificar artefatos, preservar original e exportar versões WebP otimizadas no tamanho adequado ao site.

**Passo 5:** registrar nome, Season, Case, dimensões reais, formato, tamanho de arquivo, versão, referência-base, revisão visual e aprovação.

**Escopo atual:** especificação documental. Nenhuma imagem regenerada, aumentada, substituída ou publicada por esta atualização.

# 2. Luz, cor e material — evidência das imagens

**Paleta-base extraída por amostragem aproximada de pixels do conjunto**, para orientar prompts; **não** é uma especificação exata de cor de marca:

- Escuros predominantes: **#090707**, **#18181C**, **#293039**.
- Sombras e aço azulados: **#3E4C5E**, **#5B6D86**, acento frio **#7E9EBF**.
- Bronze/ferro aquecido: **#3D1F17**, **#6B3D2F**, âmbar suave **#9D6B5A** e luz **#DBA985**.
- **Luzes de função:** dourado/âmbar = autoridade, energia, prestígio e infraestrutura ativa; azul/ciano = análise, dados, mecanismos de observação; vermelho = alerta, dano, acesso interditado e risco (concentrado em Sector 13 e anomalias).
- Alto contraste entre o breu arquitetônico e pequenos recortes luminosos; não aplicar brilho uniforme à imagem inteira.
- Névoa volumétrica, luz rasante, amanhecer/pôr do sol e reflexos molhados dão profundidade. Chuva e poças são **recorrências**, não obrigações em toda cena; há exteriores secos/sunset e salões internos diferentes.
- Mesma família física: grafite, aço escovado, bronze, painéis escuros, pedra polida, vidro técnico, telões holográficos **subordinados ao ambiente**. Nada de ambientes constituídos apenas por UI flutuando no vazio.

# 3. Identidade visual invariável

## Breaker

- Homem visto predominantemente **de costas, em três-quartos afastado ou como silhueta**; rosto e características faciais não devem ficar legíveis.
- **Cabelo preto, curto e compacto**, laterais e nuca aparadas; nunca comprido ou volumoso além do modelo existente.
- **Sobretudo/casaco comprido escuro**, calça escura e calçado robusto. Silhueta reconhecível: gola estruturada, ombros contidos, proporção humana realista, sem armadura volumosa, capa heroica de fantasia ou troca aleatória de vestuário.
- Escala intencionalmente pequena diante da infraestrutura: o mundo parece maior do que ele. Evitar poses publicitárias de super-herói, retratos frontais, olhos luminosos genéricos ou close-up de rosto.
- Em cenas investigativas a sua atitude é **observadora, cautelosa, solitária e ativa**, não um guerreiro mágico brandindo arma.

## Demais personagens

- Rostos de Rhea, Mara, Voss, Witnesses e demais figuras centrais **ocultos em artes novas**: de costas, contra luz, perfis no escuro, capacete/visor opaco, projeção abstrata ou obstrução. Não deformar rostos para criar mistério; esconder por direção de câmera.
- Manter figurino, anatomia, cortes de cabelo, estatura relativa e símbolos estáveis a partir das referências aprovadas quando disponíveis; **não inventar modelo facial canônico** a partir dos retratos existentes.
- Witnesses têm presença institucional: silhuetas limpas, frias e controladas; não transformá-los em tropa militar comum.
- Para Rhea × Breaker, preservar oposição de posições e a proximidade gradual de Season 3 sem revelar o epílogo nas capas de marketing.

## Iconografia/linguagem do mundo

- O **emblema geométrico dourado** de Meridian, próximo de círculo/rosa-dos-ventos com eixo central, aparece em arquitetura, arquivo, Vault, logística e espaço institucional. É marca recorrente: **reusar o desenho oficial de referência**, não inventar variações do símbolo ou confundi-lo com logotipo Stellar.
- **Anéis concêntricos / halos de luz** em torno de torres e máquinas sugerem autoridade sistêmica e observação. Preservar gramática de anel, não colocá-lo literalmente em todos os lugares.
- **Monólitos, cubos técnicos suspensos, arquivos modulares, cabos e passarelas** representam a infraestrutura programável incorporada fisicamente à cidade.
- **Números funcionais** (13, 17, 24), diretórios e terminais são elementos de sinalização da ficção, não branding em cima da arte.
- Em **capas e key art** não inserir título, slogan nem texto decorativo; tipografia e CTAs devem viver na interface. Em cenas com **tela diegética** (Vault, logs, arquivo), textos só quando inevitáveis, revisados manualmente por legibilidade, ortografia e coerência do canon.

# 4. Inventário das 14 referências aprovadas no site

Nome de arquivo = identificador de busca no material enviado. Títulos de cena abaixo são **descrições visuais**, não atribuição automática de nome de Case quando a foto não comprova a localização.

| Arquivo | Evidência visual e papel | Elementos a preservar | Atenção/QA |
| --- | --- | --- | --- |
| **homepage.webp** | Panorama monumental da cidade, ao entardecer, torre-eixo central com anel, pontes, mar/névoa e montanhas. | Silhueta skyline, escala, anel, contra-luz laranja no horizonte, recortes institucionais. | **Master de atmosfera para Meridian**; não tornar cada cidade futura idêntica. |
| **00.webp** | Investigação do cofre em ambiente interno: painel de grande escala com transferência **2.400.000 → 0**, monitoramento e frente vermelha. | Mistério da transação, arquitetura técnica e contraste vermelho de anomalia. | UI/valores devem ser auditados manualmente; sinalização diegética, não pista técnica falsa. |
| **01.webp** | Hall institucional do Vault com emblema de Meridian, painéis de validação e Breaker de costas. | Pedra/metal, autoridade organizada, a impressão de que todas as verificações passaram. | Evitar afirmar que uma UI implica autorização legítima. |
| **02.webp** | Memorial/galeria urbana com retratos em totens, Breaker observando registros. | Evidência social, escala institucional e tom fúnebre, retratos como objetos de arquivo. | **Revisão futura possível:** rostos nos totens visíveis; para imagens novas, ocultar, abstrair ou obscurecer. |
| **03.webp** | Grande espaço logístico com contêineres, marca e **Warehouse 17**, iluminação quente e infraestrutura elevada. | Função do local legível, emblemas, logística cotidiana, sensação material dos Cases. | Manter código e simbologia sem texto gerado incorreto. |
| **04.webp** | Porta monumental **24**, corredores verticalizados, luminárias vermelhas, múltiplos níveis e passarelas. | Descoberta do andar oculto: hierarquia de escala, concreto, iluminação de acesso perigoso. | Não exagerar até virar cenário fantástico sem função. |
| **05.webp** | Salão com gigantesca figura encapuzada/monumental e halo luminoso, personagens pequenos. | Mistério do Custodian, reverência institucional, simetria opressiva. | Não cristalizar a figura como entidade humana sobrenatural; compatibilizar com boss como sistema composto. |
| **06.webp** | Sala investigativa quente com papéis e holoarquivos sobre **Aren Voss**; Breaker em primeiro plano. | Contraste de investigação íntima dentro do universo monumental; vestígios, documentos e luz prática. | **Exceção a revisar depois:** rosto de Voss muito identificável e texto de telão; não usar como face-sheet obrigatório. |
| **07.webp** | Exterior de grande instalação técnica **13**, névoa e iluminação azul, passarelas e trânsito industrial. | Função de infraestrutura e escala urbana, variação fria do padrão de Meridian. | Preservar a distinção exterior de instalação vs interior de arquivo. |
| **08.webp** | Grande interior **13** em luz vermelha, telões com rostos/registros e figuras distribuídas. | Escalada de perigo, fechamento institucional, vermelho de emergência reservado. | Retratos frontais visíveis contradizem a regra nova de rostos ocultos; reavaliar numa revisão visual posterior. |
| **09.webp** | Sala circular de arquivo/observação com **orbe azul** holográfico, painéis e Breaker minúsculo. | Simetria, profundidade circular, holograma como objeto focal, luz fria e leitura de sistema. | Não transformar toda infraestrutura em esfera decorativa. |
| **10.webp** | Plataforma/terraço alto, trem/cápsula suspensa com emblema, torres e pôr do sol dourado. | Mobilidade vertical como infraestrutura; linhas suspensas e camada superior da cidade. | Preservar sentido de escala e plausibilidade operacional do transporte. |
| **11.webp** | Cúbico monumental flutuante em galeria escura com dados azulados e observadores. | Geometria de sistema, blocos físicos, blue/cold tech, silêncio e suspense. | Cubos devem sugerir infraestrutura, não feitiçaria. |
| **12(1).webp** | Figura humana isolada diante de eixo colossal e anéis dourados; módulos/cubos orbitais. | Clímax visual, luz dourada radial, massividade, figura minúscula e simetria. | Evitar antropomorfizar literalmente o Architect como um deus físico único; cena funciona como metáfora espacial. |

**Nota:** Numeração dos arquivos é a do pacote enviado; confirmar associações finais com os IDs reais de level/arte no site antes de renomear assets ou automatizar geração por Case.

# 5. Variação permitida — mesma obra, cidades distintas

**São invariantes globais:** composição cinematográfica 8:3 para banners, escala monumental, materiais físicos críveis, rosto oculto, figurino/silhueta do Breaker, sistema de símbolos consistente, rigor da luz, sensação de arquitetura que exerce poder, continuidade de personagens.

**Variáveis por cidade:**

- **Meridian (S1):** verticalidade de torres e plataformas, aço negro, bronze dourado, frio industrial e alarmes vermelhos contextuais. A coleção de 14 imagens é a referência visual **direta** dessa cidade.
- **Lumen (S2):** manter a qualidade cinematográfica e silhuetas, mas privilegiar geografia **horizontal/aquática**, grandes espaços ricos, sol e ouro/ivory; crise altera visualmente a cidade. Não apenas recolorir Meridian para dourado.
- **Moonlight (S3):** espelhos, vidro negro, transparência parcial, água escura, prata/azul/violeta discreto e espaços negativos; a imagem comunica observabilidade incompleta. Não copiar o anel/torre central de Meridian como único landmark.
- **Seasons 4–7:** manter gramática visual, mas seguir geografia, economia, silhueta e materiais próprios de cada cidade conforme o [07 — Atlas Visual & Worldbuilding (estudo)](07-atlas-visual-worldbuilding-estudo.md). O Atlas continua **estudo**, não passa a canon só por ser referenciado.

# 6. Brief reutilizável para gerar nova arte

> **BREAKER \| \[Season / cidade / Case / objetivo narrativo\].** Arte cinematográfica realista premium, continuidade estrita com as 14 imagens-base aprovadas. Banner **8:3**; composição de grande-angular com profundidade de múltiplos planos e um foco arquitetônico narrativo. Materiais plausíveis, superfícies molhadas/reflexivas quando houver razão ambiental, atmosfera volumétrica sutil, contraste de sombra grafite/azul com luz âmbar/dourada de infraestrutura; cor de alerta somente em momentos narrativamente previstos. Breaker sempre com sobretudo escuro, cabelo preto curto e compacto, laterais aparadas, de costas/três-quartos sem rosto visível, escala humana pequena. Manter emblemas e silhuetas oficiais de referência; local específico deve estar funcionalmente reconhecível. Sem texto sobreposto, logos inventados, rostos expostos, fantasias de armadura, skyline genérico ou mudança de proporção. Para outra cidade, substituir paleta/geografia pela ficha da Season, **nunca** a gramática cinematográfica.

**Campos obrigatórios do briefing antes da geração:** ID do Case e spoiler level; função da cena (pré/post, ambiente, pista, boss, capa); referência visual **principal** pelo arquivo; referência de personagem/símbolo; landmark; posição da câmera; cor primária/secundária; elementos que não podem aparecer; corte desktop/mobile.

# 7. Checklist rígido de qualidade de novas imagens

- [ ] Usa o banner **8:3** e resiste ao recorte mobile sem perder personagem, landmark ou pista.
- [ ] É reconhecível como BREAKER em miniatura, sem depender de título ou legenda.
- [ ] Preserva Breaker (casaco, silhueta, cabelo **curto** e rosto **oculto**) e aparência do elenco.
- [ ] Reutiliza corretamente o **mesmo** emblema quando for Meridian — não redesenha sua geometria.
- [ ] Mantém luz física e volumetria críveis, sem luz fluorescente difusa generalizada.
- [ ] Tem arquitetura funcional e narrativamente pertinente ao Case.
- [ ] Diferencia a cidade pelo desenho urbano, não só pela cor.
- [ ] Não antecipa spoilers (Voss, Architect, Registry, soluções de exploit, revelação de Rhea etc.).
- [ ] Não contém rosto nítido de personagens canônicos nem variações faciais geradas.
- [ ] Não contém escrita decorativa sobreposta. Telas diegéticas, quando existirem, são revisadas manualmente.
- [ ] Não inventa marcas, identidades, armas, QR codes, carteiras, transferências ou resultados falsos.
- [ ] Foi comparada lado a lado com uma imagem-base aprovada e teve desvios justificados.
- [ ] Tem identificação de **versão**, arquivo final, relação com Case, status e quem aprovou.

**Bloqueio:** reprovar ou revisar se falhar em personagem, símbolo, spoiler, coerência de mundo ou origem técnica da cena. Cor e acabamento isolados não compensam erro de continuidade.

# 8. Observações e backlog — sem alterar nenhuma arte atual

1. **Fisionomias em arquivos** (`02.webp`, `06.webp`, `08.webp`) confrontam a regra global mais recente de ocultar rostos. Isto é uma **dívida de consistência para revisão futura**; não apagar nem redesenhar sem decisão específica. É possível conservar o conteúdo diegético enquanto se abstrai/oculta a fisionomia.
2. **Texto gerado em UI diegética:** conferir grafia, números, nomes, datas, hierarquia, sentido da autorização; se for essencial ao puzzle, priorizar tipografia real em camada de UI/HTML sobre imagem gerada.
3. **Emblema Meridian:** selecionar um arquivo-mestre vetorial posteriormente; este estudo não fornece geometria vetorial exata nem deve induzir a IA a inventá-la.
4. **Personagem-modelo:** extrair sheet técnico de silhueta, cabelo e roupa a partir do conjunto; **não** definir um rosto único a partir de cenas que foram mantidas ocultas.
5. **Arquivos base:** armazenar posteriormente os 14 originais com link permanente, hash, legenda e aprovação num repositório de artes; até então, este documento referencia os nomes de arquivo enviados e não constitui upload dos binários.
6. **Capas S2/S3:** manter suas referências próprias já aprovadas no Drive; este padrão é um **elo de qualidade cinematográfica**, não substitui de forma automática seus conceitos visuais.

# 9. Hierarquia de decisão

1. Arte concreta **aprovada e utilizada** no site.
2. Este **Art Bible canônico** para invariantes, padrão técnico e QA.
3. Referências canônicas específicas de personagens e Seasons.
4. Atlas Visual de mundo (**estudo/proposta**, apenas para ideias não conflitantes).
5. Prompt novo ou referência externa (nunca sobrepor automaticamente às anteriores).

**Regra editorial:** arte nova só passa a ser referência após revisão/aprovação. Uma imagem gerada não redefine o personagem nem a cidade por mera semelhança de estilo.

# 10. Easter Eggs — nova checagem de arte e mapa (propostas)

Ao revisar qualquer banner da Season 1 ou o mapa de Meridian, consultar [17 — Easter Eggs | Season 1 — Mapa, Arte & Stellar DNA](../../databases/season-01-reference-catalog.txt). Estes itens são **opcionais e não canônicos** até revisão explícita e não têm autorização para alterar as 14 imagens-base.

- Toda proposta precisa de **asset de referência**, **posição na composição** (primeiro plano/fundo/placa/UI), **suporte**, **fonte da referência Stellar**, **risco de spoiler** e **estado**.
- Em banners 8:3, pequenos detalhes podem ser ambientais; em mobile devem poder desaparecer sem prejudicar a narrativa ou legibilidade. Nunca sobrepor logo oficial de Meridian, rosto, prova, evento, data crítica ou imagem do hack.
- Preferir overlays diegéticos com tipografia controlada quando uma referência contiver letras, datas ou números, em vez de regenerar todo o banner.
- Imagens existentes não estão modificadas. Nenhum easter egg pode parecer flag obrigatória, solução de exploit, pista exclusiva do Voss Protocol ou indicativo de parceria real.
- Para mapa fictício, só cadastrar um ponto se fizer sentido na geografia atual; posição narrativa não é geolocalização do mundo real.
- Checklist extra de aprovação: verificar marca/licença, contraste e corte mobile, false affordances (ícones que parecem clicáveis sem ação), lore, spoilers, custo de execução e teste no runtime.
