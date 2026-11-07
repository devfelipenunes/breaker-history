---
notion_id: 4019c563-0425-81b2-93a8-c3025d77c3d6
source: https://app.notion.com/p/4019c563042581b293a8c3025d77c3d6?pvs=204
title: "🌫️ 10 — Become Missing"
exported_at: 2026-11-07
---

**Sem vulnerabilidade nova. Challenge de composição correta de privacy.**

# História

O Breaker já possui evidência suficiente para confrontar a Witness Spire.

O problema é chegar até ela sem ser interceptado.

Rhea não pode fazer isso por ele.

A própria presença dela aumentaria a correlação.

Pela primeira vez desde que começaram a cooperar, separar-se é parte da solução. A confiança é sincera e separar-se custa aos dois. Quando Rhea diz que talvez nunca consiga encontrá-lo, não está mentindo: **a decisão de entregar a atribuição de Lumen ainda não aconteceu**.

Rhea:

> **“Se você desaparecer agora, eu não vou conseguir encontrar você.”**

Breaker:

> **“Esse é o objetivo.”**

# Missão

> **TORNE-SE MISSING.**

Não apagar a wallet.

Não morrer.

Não mentir.

Reduzir correlação até Architect e Witnesses deixarem de reconstruir sua trajetória com confiança.

# Conceitos

- commitments;
- nullifiers;
- privacy pool transfers;
- unlinkability;
- timing discipline;
- selective disclosure;
- redução de metadata pública.

# Condição de vitória

Completar uma rota privada sem:

- reutilizar nullifier;
- vazar secret em storage/event;
- criar associação trivial por timing;
- entregar view authority;
- revelar dados além do necessário.

# Resultado

ARCHITECT
SUBJECT: BREAKER
OBSERVATION CONFIDENCE: 81%
54%
19%
...

SIGNAL LOST

STATUS: MISSING

# Significado

Neste ponto, MISSING é operacional.

O sistema perdeu a trajetória do Breaker.

Isso permite a infiltração final.

# Resultado narrativo

O jogador conquista algo que Voss talvez já soubesse fazer:

existir sem permanecer observável.

Unlock:

**FINAL BOSS — THE WITNESS SPIRE**

## Loop jogável v2 — composição de privacidade sob ameaça delimitada

**MISSING é um resultado do modelo de observação dos Witnesses/Architect, não anonimato perfeito.** Definir fontes que o adversário vê e um critério determinístico de correlação na fixture. O jogador não apaga transações antigas, nem deixa de existir.

**Investigar:** grafo de metadados até então observado, commitments, nullifiers gastos, eventos, horários e endpoints de origem. Rhea não pode acompanhar a última rota sem aumentar correlação.

**Executar:** completar sequência de ações de privacy na instância de teste sem reutilizar nullifier, revelar segredo em storage/event, fornecer view capability ampla, produzir vínculo trivial entre entradas e saídas ou abrir associações desnecessárias. O challenge combina conhecimentos já adquiridos, sem nova categoria de bug.

**Verifier:** checks de nullifier único, informações expostas nos eventos, binding correto e risco de correlação segundo threat model. Uma métrica determinística de **observability confidence** cai até limite de insuficiência — o número é **modelo ficcional** e não probabilidade comprovada de anonimato de qualquer protocolo real.

**Consequência:** Breaker chega à Spire operacionalmente MISSING; isso não encerra a investigação nem revela o vínculo histórico de Lumen.

**Rhea:** separação é necessária e custosa, sem premeditação de traição. Ela acredita que talvez não consiga encontrá-lo novamente.

**Diferencial:** composição **correta** das primitivas, não mais um exploit.

## Ajuste canônico aprovado — separação, prova e presença controlada

Antes de iniciar a rota MISSING, o Breaker **já recebeu** o pacote sender witness autenticado de Rhea, vinculado ao commitment da devolução de garantia, no encerramento do Case 09. A separação é real: nenhuma chamada posterior a ela será necessária para concluir a prova.

**O que MISSING significa:** o observador perde capacidade de reconstruir a trajetória atual em escala de cidade; não apaga memória, associações históricas ou a capacidade de First Witness reconhecer o sujeito diante de si. Breaker poderá comparecer a uma sessão delimitada da Spire, autenticar a identidade **processual** com credential/proof de escopo estreito e, ainda assim, não entregar rota de entrada e saída.

**Feedback:** `WITNESS PACKAGE: AVAILABLE` / `OBSERVATION: INSUFFICIENT` / `PROCESS CLAIM: AUTHENTICATABLE`. O breach report explica que estar presente durante sessão não implica tracking contínuo. Não existe invisibilidade perfeita.
