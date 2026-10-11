---
tags: [cicloai/topico]
materia: Teoria dos Grafos
volta: 1
status: a estudar
---
# V1 · Definições: vértices, arestas, grau, tipos de grafo

[[CicloAI/Matérias/Teoria dos Grafos|Teoria dos Grafos]] · anterior: — · próximo: [[CicloAI/Tópicos/Teoria dos Grafos/V02 - Representações - matriz e lista de adjacência|V2]]

## Resumo

Um **grafo** $G = (V, E)$ é um conjunto de **vértices** (nós) $V$ e de **arestas** $E$ que ligam pares de vértices.

**Tipos**
- **Não dirigido**: a aresta $\{u, v\}$ vale nos dois sentidos (amizade).
- **Dirigido (dígrafo)**: a aresta $(u, v)$ tem sentido (seguir alguém).
- **Ponderado**: cada aresta tem um peso (distância, custo, latência).
- **Simples**: sem laços (aresta de um vértice nele mesmo) e sem arestas múltiplas. **Multigrafo** permite arestas múltiplas; **pseudografo** permite laços.

**Grau** $d(v)$: número de arestas incidentes em $v$ (um laço conta 2). Em dígrafos há **grau de entrada** e **grau de saída**.

**Teorema do aperto de mãos**: $\sum_{v \in V} d(v) = 2|E|$, porque cada aresta soma 1 no grau de cada ponta. Consequência: **o número de vértices de grau ímpar é sempre par**.

**Outros termos**
- **Adjacentes**: vértices ligados por uma aresta.
- **Grafo completo** $K_n$: todos ligados a todos → $\frac{n(n-1)}{2}$ arestas.
- **Grafo regular**: todos os vértices têm o mesmo grau.
- **Subgrafo**: pedaço de um grafo (subconjunto de vértices e arestas).

**Onde aparece**: redes sociais, mapas e rotas, dependências de pacotes (dígrafo acíclico), roteamento de redes, recomendação.

## Conceitos-chave

- [[Grafo]] — vértices + arestas
- [[Grafo dirigido]] × [[Grafo não dirigido]]
- [[Grau de um vértice]]
- [[Teorema do aperto de mãos]]
- [[Grafo completo]]

## Exemplo

Rede: Ana–Bia, Ana–Caio, Bia–Caio, Caio–Davi.
- Graus: Ana 2, Bia 2, Caio 3, Davi 1 → soma 8 = 2 × 4 arestas ✔
- Vértices de grau ímpar: Caio e Davi (2, um número par) ✔
- $K_5$ tem $5 \cdot 4 / 2 = 10$ arestas.

## Flashcards

#flashcards/grafos

Defina grafo::Um par G = (V, E): conjunto de vértices e de arestas que ligam pares de vértices.
Grafo simples::Sem laços e sem arestas múltiplas.
Grau de um vértice::Número de arestas incidentes nele (laço conta 2).
Teorema do aperto de mãos::A soma dos graus é igual a 2 × número de arestas.
Consequência do aperto de mãos::O número de vértices de grau ímpar é sempre par.
Quantas arestas tem Kₙ?::n(n − 1)/2.
Exemplo de grafo dirigido no mundo real::Seguir no Instagram/Twitter, dependências de pacotes, links entre páginas.

## Conexões

- Próximo: [[CicloAI/Tópicos/Teoria dos Grafos/V02 - Representações - matriz e lista de adjacência|Representações]]
- Na prática em banco: [[CicloAI/Tópicos/Banco de Grafos/V01 - Quando usar grafo em vez de relacional|Quando usar banco de grafos]]
- O Git é um grafo dirigido acíclico de commits: [[CicloAI/Tópicos/Git e Kanban/V01 - Git - modelo interno (blobs, trees, commits, refs)|modelo interno do Git]]
- Roteamento na internet usa grafos ponderados: [[CicloAI/Tópicos/Redes/V05 - Roteamento (algoritmos de caminho mínimo na prática)|Roteamento]]

## Para praticar

- Desenhe o grafo de 5 colegas e quem conversa com quem; calcule os graus e confira o teorema.
- É possível um grafo com 5 vértices, todos de grau 3? Por quê? (dica: aperto de mãos)
- Quantas arestas tem $K_{10}$?

## Fontes

*Matemática Discreta e suas Aplicações* (Rosen), cap. 10.1–10.2.

## Minhas anotações
