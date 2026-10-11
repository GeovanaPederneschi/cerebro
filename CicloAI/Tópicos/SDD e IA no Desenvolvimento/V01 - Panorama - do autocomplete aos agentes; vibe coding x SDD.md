---
tags: [cicloai/topico]
materia: SDD e IA no Desenvolvimento
volta: 1
status: a estudar
---
# V1 · Panorama: do autocomplete aos agentes; vibe coding x SDD

[[CicloAI/Matérias/SDD e IA no Desenvolvimento|SDD e IA no Desenvolvimento]] · anterior: — · próximo: [[CicloAI/Tópicos/SDD e IA no Desenvolvimento/V02 - O que é SDD - fluxo specify - plan - tasks - implement|V2]]

## Resumo

**Como chegamos aqui**
1. **Autocomplete** (Copilot, 2021): completa linhas e funções.
2. **Chat** (2022–23): você pergunta, copia e cola.
3. **Agentes** (2024–26): leem o repositório, rodam comandos, editam vários arquivos, executam testes e abrem PRs (Claude Code, Cursor Agent, Copilot Agent, Codex).

**Vibe coding** (termo popularizado por Andrej Karpathy em 2025): descrever vagamente o que quer e aceitar o que a IA gera, sem olhar muito. Bom para protótipos e scripts descartáveis. Ruim para software mantido: as decisões ficam implícitas, o código fica inconsistente e ninguém sabe *por que* algo foi feito.

**Spec-Driven Development (SDD)** inverte a lógica: a **especificação** (o quê e o porquê) vira o artefato principal, versionado junto com o código. Fluxo típico:
1. **Specify** — requisitos, usuários, critérios de aceitação (sem falar de tecnologia).
2. **Plan** — plano técnico: arquitetura, stack, modelos de dados, trade-offs.
3. **Tasks** — lista de tarefas pequenas e verificáveis.
4. **Implement** — o agente executa as tarefas; testes conferem contra a spec.

Em cada passagem há um **ponto de revisão humana**. O papel da dev muda: menos digitar, mais **especificar, decidir e revisar**.

**Riscos que continuam existindo**: aceitar código sem entender, APIs "alucinadas", falhas de segurança, perda do domínio do próprio código, custo de tokens.

## Conceitos-chave

- [[Spec-Driven Development]]
- [[Vibe coding]]
- [[Agente de código]] — IA que age no repositório (lê, executa, edita)
- [[Especificação]] como fonte da verdade
- [[Human-in-the-loop]] — revisão humana nos pontos de decisão

## Exemplo

| | Vibe coding | SDD |
|---|---|---|
| Entrada | "faz um login aí" | Spec com fluxos, regras e critérios de aceitação |
| Decisões | Implícitas, dentro do código | Explícitas, no plano |
| Revisão | No fim (se houver) | A cada etapa |
| Bom para | Protótipo, script | Produto mantido por um time |

## Flashcards

#flashcards/sdd

O que é Spec-Driven Development?::Desenvolver a partir de uma especificação versionada que é a fonte da verdade; plano, tarefas e código derivam dela.
As 4 etapas típicas do SDD::Specify → Plan → Tasks → Implement.
O que é vibe coding?::Descrever vagamente e aceitar o código gerado pela IA sem revisar a fundo.
Quando vibe coding é aceitável?::Em protótipos e scripts descartáveis.
O que a etapa Specify NÃO deve conter?::Decisões de tecnologia; ela fala do quê e do porquê, não do como.
Diferença entre chat e agente de código::O agente age no ambiente: lê o repo, roda comandos, edita arquivos e testa; o chat só responde.
Como muda o papel da dev com SDD?::Menos digitar código, mais especificar, decidir e revisar.

## Conexões

- Próximo: [[CicloAI/Tópicos/SDD e IA no Desenvolvimento/V02 - O que é SDD - fluxo specify - plan - tasks - implement|O fluxo do SDD]]
- Specs e ADRs registram decisões: [[CicloAI/Tópicos/Arquitetura de Software/V02 - Trade-offs, fitness functions e ADRs (registrar decisões)|Trade-offs e ADRs]]
- Código gerado ainda precisa ser legível: [[CicloAI/Tópicos/Código Limpo/V01 - Nomes significativos|Nomes significativos]]

## Para praticar

- Escolha uma feature pequena do seu trabalho e escreva **duas versões de pedido para a IA**: uma "vibe" (1 frase) e uma spec curta (objetivo, regras, 3 critérios de aceitação). Compare os resultados.
- Anote: em que tipo de tarefa você hoje faz vibe coding sem perceber?

## Fontes

Repositório *github/spec-kit* (README e spec-driven.md); documentação do Kiro; documentação do Claude Code.

## Minhas anotações
