---
tags: [cicloai/topico]
materia: Revisão do cérebro
volta: 1
status: a estudar
---
# V1 · Criar um MOC (mapa de conteúdo) do ciclo

[[CicloAI/Matérias/Revisão do cérebro|Revisão do cérebro]] · anterior: — · próximo: [[CicloAI/Tópicos/Revisão do cérebro/V02 - Notas atômicas - um conceito = uma nota|V2]]

## Resumo

Um **MOC** (*Map of Content*, termo de Nick Milo no método *Linking Your Thinking*) é uma **nota-índice** que reúne links para outras notas de um tema. Diferente de pastas, que são uma hierarquia rígida, uma mesma nota pode aparecer em **vários MOCs** — do mesmo jeito que um conceito pertence a várias matérias.

**Como montar o MOC do ciclo**
1. Crie a nota `Mapa do Ciclo` na pasta `CicloAI`.
2. Uma seção por matéria, com link para a nota da matéria e para os tópicos já estudados.
3. Uma seção **Conexões entre matérias**, onde você anota as pontes que percebeu (ex.: *Git é um DAG* → Teoria dos Grafos).
4. Uma seção **Dúvidas abertas**.

**Links não resolvidos são sementes**: nas notas de tópico, os conceitos estão como `[[Conceito]]`. Enquanto a nota não existe, o link aparece mais apagado. Quando um conceito ficar claro, clique nele e escreva a nota **com suas palavras** — é assim que o cérebro cresce.

**Graph view**: mostra as notas e os links. Use filtros (`path:CicloAI`, `tag:#cicloai/topico`) e cores por grupo para enxergar as conexões.

**Ritual de fim de volta (30 min)**
- Ler as anotações das sessões da volta.
- Marcar no roteiro o que ficou claro.
- Criar 2–3 notas de conceito.
- Revisar os flashcards do dia.

## Conceitos-chave

- [[MOC (Map of Content)]]
- [[Nota atômica]]
- [[Linking Your Thinking]]
- [[Graph view]]

## Exemplo

```markdown
# Mapa do Ciclo

## Arquitetura de Software
- [[CicloAI/Matérias/Arquitetura de Software|Matéria]]
- V1: [[Características arquiteturais]]

## Conexões entre matérias
- O histórico do Git é um DAG → Teoria dos Grafos
- O C do ACID ≠ o C do CAP

## Dúvidas abertas
- Elasticidade sempre exige serverless?
```

## Flashcards

#flashcards/revisao

O que é um MOC?::Uma nota-índice com links para as notas de um tema; uma nota pode estar em vários MOCs.
Por que MOCs em vez de só pastas?::Pastas forçam uma hierarquia única; MOCs permitem que uma nota pertença a vários temas.
O que fazer com um link [[...]] não resolvido?::Quando o conceito ficar claro, clicar e escrever a nota com suas palavras.
O que é uma nota atômica?::Uma nota sobre uma única ideia, escrita com suas palavras e ligada a outras.

## Conexões

- Próximo: [[CicloAI/Tópicos/Revisão do cérebro/V02 - Notas atômicas - um conceito = uma nota|Notas atômicas]]
- Tópicos desta volta: [[CicloAI/Tópicos/Arquitetura de Software/V01 - Características arquiteturais e como extraí-las dos requisitos|Arquitetura]], [[CicloAI/Tópicos/Cálculo/V01 - Funções - tipos, composição, inversa e gráficos|Cálculo]], [[CicloAI/Tópicos/AWS/V01 - Visão geral - contas, regiões-AZs, free tier e alarme de custos|AWS]], [[CicloAI/Tópicos/Código Limpo/V01 - Nomes significativos|Código Limpo]], [[CicloAI/Tópicos/Teoria dos Grafos/V01 - Definições - vértices, arestas, grau, tipos de grafo|Grafos]], [[CicloAI/Tópicos/SDD e IA no Desenvolvimento/V01 - Panorama - do autocomplete aos agentes; vibe coding x SDD|SDD]], [[CicloAI/Tópicos/ACID, CAP e PACELC/V01 - Transações e ACID|ACID]], [[CicloAI/Tópicos/Git e Kanban/V01 - Git - modelo interno (blobs, trees, commits, refs)|Git]], [[CicloAI/Tópicos/Redes/V01 - Modelos OSI e TCP-IP|Redes]], [[CicloAI/Tópicos/Banco de Grafos/V01 - Quando usar grafo em vez de relacional|Banco de Grafos]]

## Para praticar

- Crie o `Mapa do Ciclo` com as 10 matérias e os tópicos da volta 1.
- Escolha **3 conceitos** que ficaram claros e transforme os links em notas.
- Abra o Graph view filtrando por `path:CicloAI` e tire um print para comparar daqui a 5 voltas.
- Instale o plugin **Spaced Repetition** e faça a primeira revisão dos flashcards.

## Fontes

Nick Milo — *Linking Your Thinking*; documentação do Obsidian (*Graph view*, *Links*); plugin *Spaced Repetition*.

## Minhas anotações
