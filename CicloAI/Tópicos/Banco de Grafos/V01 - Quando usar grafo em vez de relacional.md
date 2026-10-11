---
tags: [cicloai/topico]
materia: Banco de Grafos
volta: 1
status: a estudar
---
# V1 · Quando usar grafo em vez de relacional

[[CicloAI/Matérias/Banco de Grafos|Banco de Grafos]] · anterior: — · próximo: [[CicloAI/Tópicos/Banco de Grafos/V02 - Property graph - nós, relacionamentos, propriedades e labels|V2]]

## Resumo

Bancos relacionais são ótimos para dados tabulares, agregações e relatórios. Mas consultas que **seguem relacionamentos em profundidade** (amigos de amigos de amigos, caminhos, cadeias de dependência) viram muitos `JOIN`s — e o custo cresce com a profundidade **e** com o tamanho das tabelas.

Em um **banco de grafos**, relacionamentos são **cidadãos de primeira classe**: são gravados fisicamente ligando os nós. No Neo4j isso se chama *index-free adjacency*: percorrer uma relação é seguir um ponteiro, então o custo é proporcional ao **pedaço do grafo que você visita**, não ao total de dados.

**Quando brilha**
- Redes sociais e recomendação ("quem comprou X também comprou Y").
- Detecção de fraude (anéis de contas que compartilham telefone, endereço, cartão).
- Gestão de identidade e permissões (quem tem acesso a quê, por herança).
- Grafos de conhecimento e GraphRAG para IA.
- Dependências de infraestrutura e análise de impacto.

**Quando NÃO usar**
- Relatórios e agregações sobre todos os registros.
- Dados tabulares simples, sem relacionamentos importantes.
- Altíssimo volume de escrita de eventos independentes.

**Dois modelos**: *property graph* (Neo4j, Amazon Neptune, Memgraph) — nós e relações com propriedades; e *RDF / triplestore* (sujeito–predicado–objeto, SPARQL) — mais usado em web semântica.

## Conceitos-chave

- [[Banco de grafos]]
- [[Index-free adjacency]]
- [[Property graph]] × [[RDF]]
- [[Neo4j]] e [[Cypher]]
- [[Grafo de conhecimento]]

## Exemplo

"Amigos de amigos da Ana":

```sql
SELECT DISTINCT f2.amigo_id
FROM amizades f1
JOIN amizades f2 ON f2.pessoa_id = f1.amigo_id
WHERE f1.pessoa_id = 1 AND f2.amigo_id <> 1;
```

```cypher
MATCH (ana:Pessoa {nome: 'Ana'})-[:AMIGO*2]-(fof:Pessoa)
WHERE fof <> ana
RETURN DISTINCT fof.nome
```
Para 3, 4, 5 níveis: no SQL, mais um `JOIN` por nível; no Cypher, só muda `*2` para `*3..5`.

## Flashcards

#flashcards/banco-de-grafos

Quando um banco de grafos supera o relacional?::Em consultas que percorrem relacionamentos em profundidade (caminhos, amigos de amigos, fraude).
O que é index-free adjacency?::Cada nó guarda ponteiros diretos para seus vizinhos; percorrer uma relação não exige busca em índice.
O custo de uma travessia em grafo depende de quê?::Do tamanho do subgrafo visitado, não do total de dados.
Cite 3 casos de uso de banco de grafos::Recomendação, detecção de fraude, permissões/identidade (também: grafos de conhecimento).
Quando NÃO usar banco de grafos?::Para relatórios e agregações em massa ou dados tabulares sem relações importantes.
Property graph × RDF::Property graph: nós e relações com propriedades (Neo4j). RDF: triplas sujeito–predicado–objeto (SPARQL).

## Conexões

- Próximo: [[CicloAI/Tópicos/Banco de Grafos/V02 - Property graph - nós, relacionamentos, propriedades e labels|Property graph]]
- A teoria por trás: [[CicloAI/Tópicos/Teoria dos Grafos/V01 - Definições - vértices, arestas, grau, tipos de grafo|Definições de grafos]]
- Grafos + IA: [[CicloAI/Tópicos/Banco de Grafos/V14 - Grafos + IA - knowledge graphs e GraphRAG|GraphRAG]]
- Garantias do Neo4j em CAP: [[CicloAI/Tópicos/ACID, CAP e PACELC/V15 - Classificar bancos reais (Postgres, DynamoDB, Cassandra, MongoDB, Neo4j)|Classificar bancos reais]]

## Para praticar

- Pense em 3 consultas do seu trabalho que usam muitos `JOIN`s encadeados. Alguma seria mais natural como grafo?
- Desenhe (nós e setas) o modelo de um caso de fraude: Cliente, Cartão, Telefone, Endereço.

## Fontes

*Graph Databases* (Robinson, Webber & Eifrem, O'Reilly — gratuito no site da Neo4j), cap. 1–2; GraphAcademy *Neo4j Fundamentals*.

## Minhas anotações
