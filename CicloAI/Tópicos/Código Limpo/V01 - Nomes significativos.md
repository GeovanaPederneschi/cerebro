---
tags: [cicloai/topico]
materia: Código Limpo
volta: 1
status: a estudar
---
# V1 · Nomes significativos

[[CicloAI/Matérias/Código Limpo|Código Limpo]] · anterior: — · próximo: [[CicloAI/Tópicos/Código Limpo/V02 - Funções - tamanho, um nível de abstração, parâmetros|V2]]

## Resumo

Nomes são a documentação mais lida do código. Um bom nome responde **por que existe, o que faz e como é usado**, sem precisar de comentário.

**Regras práticas**
- **Revele a intenção**: `elapsedTimeInDays` em vez de `d`.
- **Evite desinformação**: não chame de `accountList` algo que não é uma lista; não use nomes quase iguais (`XYZControllerForHandling` × `XYZControllerForStorage`).
- **Distinções com significado**: `data`, `info`, `a1`, `a2`, `ProductData` × `ProductInfo` não dizem nada.
- **Pronunciáveis e buscáveis**: `genymdhms` é impossível de discutir; `7` solto é impossível de buscar → `MAX_RETRIES = 7`.
- **Sem codificações**: nada de notação húngara (`strName`) nem prefixos que o tipo já diz.
- **Classes/tipos = substantivos** (`Invoice`, `StudySession`); **métodos = verbos** (`calculateTotal`, `completeBlock`).
- **Booleanos como pergunta**: `isActive`, `hasPermission`, `canRetry`.
- **Uma palavra por conceito**: escolha `fetch` **ou** `get` **ou** `retrieve` e use em todo o projeto.
- **Use o vocabulário do domínio**: se o negócio fala "apólice", o código fala `Policy`, não `Contract2`.
- **Tamanho proporcional ao escopo**: `i` num loop de 3 linhas é ok; uma variável de módulo precisa de nome completo.

## Conceitos-chave

- [[Nomes significativos]]
- [[Linguagem ubíqua]] — o vocabulário do domínio no código
- [[Números mágicos]] — substituir por constantes nomeadas
- [[Código autoexplicativo]]

## Exemplo

```ts
// antes
function calc(d: number[], t: number) {
  return d.filter((x) => x > t).length;
}

// depois
const MINIMUM_FOCUSED_SESSION_MINUTES = 25;

function countFocusedSessions(sessionDurationsInMinutes: number[]) {
  return sessionDurationsInMinutes.filter(
    (minutes) => minutes >= MINIMUM_FOCUSED_SESSION_MINUTES,
  ).length;
}
```

## Flashcards

#flashcards/codigo-limpo

O que um bom nome deve revelar?::Por que existe, o que faz e como é usado.
Classes e métodos: que classe gramatical usar?::Classes: substantivos. Métodos: verbos.
Como nomear booleanos?::Como pergunta: isActive, hasPermission, canRetry.
O que é 'uma palavra por conceito'?::Usar sempre o mesmo termo para a mesma ideia (ex.: só fetch, nunca misturar com get/retrieve).
Por que evitar números mágicos?::Não comunicam intenção e não são buscáveis; use constantes nomeadas.
Por que ProductData × ProductInfo é ruim?::É uma distinção sem significado: o leitor não sabe a diferença.
Tamanho do nome deve ser proporcional a quê?::Ao tamanho do escopo em que ele vive.

## Conexões

- Próximo: [[CicloAI/Tópicos/Código Limpo/V02 - Funções - tamanho, um nível de abstração, parâmetros|Funções]]
- Usar os termos do negócio é a [[CicloAI/Tópicos/Arquitetura de Software/V07 - DDD estratégico - subdomínios, bounded contexts, context map|linguagem ubíqua do DDD]]
- Nomes claros também ajudam agentes de IA a entender o código: [[CicloAI/Tópicos/SDD e IA no Desenvolvimento/V04 - Regras do projeto para a IA - AGENTS.md, CLAUDE.md, convenções|regras do projeto para IA]]

## Para praticar

- Abra um arquivo do seu trabalho e encontre **5 nomes ruins**. Renomeie (o IDE faz com segurança) e anote antes/depois.
- Procure números mágicos e transforme em constantes.
- Liste os sinônimos que o projeto usa para a mesma coisa (`get/fetch/load`) e escolha um.

## Fontes

*Clean Code*, cap. 2 (Robert C. Martin); *A Philosophy of Software Design*, cap. 14 (Ousterhout).

## Minhas anotações
