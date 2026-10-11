---
tags: [cicloai/topico]
materia: Arquitetura de Software
volta: 1
status: a estudar
---
# V1 · Características arquiteturais e como extraí-las dos requisitos

[[CicloAI/Matérias/Arquitetura de Software|Arquitetura de Software]] · anterior: — · próximo: [[CicloAI/Tópicos/Arquitetura de Software/V02 - Trade-offs, fitness functions e ADRs (registrar decisões)|V2]]

## Resumo

**Características arquiteturais** (também chamadas de atributos de qualidade, requisitos não funcionais ou "-ilities") são os critérios de sucesso do sistema que **não** dizem respeito ao domínio do negócio: escalabilidade, disponibilidade, desempenho, segurança, manutenibilidade, testabilidade, implantabilidade, observabilidade.

Segundo Richards & Ford, algo é uma característica arquitetural quando atende a três critérios:
1. **Não é do domínio** — não é uma regra de negócio ("calcular frete"), é uma qualidade ("calcular frete em < 200 ms").
2. **Influencia a estrutura** — exige uma decisão de arquitetura (cache, réplicas, filas, separação de serviços).
3. **É crítica** para o sucesso do sistema.

Elas podem ser **explícitas** (estão nos requisitos) ou **implícitas** (ninguém pede, mas todos esperam: segurança, disponibilidade, usabilidade).

**Extrair dos requisitos** é traduzir a linguagem do negócio:
- "Precisamos lançar antes da Black Friday" → *time-to-market* → agilidade, testabilidade, implantabilidade.
- "No dia do evento o acesso explode" → **elasticidade** (picos), não só escalabilidade.
- "Guardamos dados de cartão" → segurança, conformidade (PCI, LGPD).
- "Vamos expandir para outros países" → escalabilidade, localização, latência.

**Priorize poucas (≈3).** Cada característica tem custo e conflita com outras (ex.: segurança × desempenho, consistência × disponibilidade). Tentar maximizar todas gera um design genérico e complexo. A meta é a "arquitetura menos pior" para o contexto.

**Quantifique.** "Rápido" e "sempre no ar" não são testáveis. Transforme em números: *p95 < 200 ms com 500 req/s*, *disponibilidade de 99,9% ao mês* (≈ 43 min de indisponibilidade).

## Conceitos-chave

- [[Características arquiteturais]] — qualidades não funcionais que moldam a estrutura
- [[Escalabilidade]] × [[Elasticidade]] — crescimento contínuo × picos repentinos
- [[Disponibilidade]] — % do tempo em que o sistema atende; base dos SLOs
- [[Requisitos não funcionais]] — explícitos e implícitos
- [[Trade-off]] — toda escolha de qualidade custa outra

## Exemplo

| Frase do negócio | Característica | Como medir |
|---|---|---|
| "Não pode cair no fechamento do mês" | Disponibilidade | 99,95% no período de fechamento |
| "Lançamos uma feature por semana" | Implantabilidade, testabilidade | Deploy diário com < 15 min de pipeline |
| "Campanhas de TV geram picos" | Elasticidade | Suportar 10× a carga média em 5 min |

## Flashcards

#flashcards/arquitetura

O que é uma característica arquitetural?::Um critério de sucesso não ligado ao domínio, que influencia a estrutura do sistema e é crítico (ex.: escalabilidade, disponibilidade).
Escalabilidade × elasticidade::Escalabilidade: suportar crescimento contínuo da carga. Elasticidade: suportar picos repentinos e encolher depois.
O que são características implícitas?::As que ninguém escreve nos requisitos mas todos esperam, como segurança e disponibilidade.
Por que priorizar só umas 3 características?::Cada uma tem custo e conflita com outras; maximizar todas gera um design genérico e complexo.
99,9% de disponibilidade permite quanto tempo fora do ar por mês?::Cerca de 43 minutos.
Como tornar 'o sistema precisa ser rápido' um requisito útil?::Quantificando: ex. p95 de latência < 200 ms na rota X com N req/s.
'Precisamos lançar antes do concorrente' indica qual característica?::Time-to-market: agilidade, testabilidade e implantabilidade.

## Conexões

- Próximo passo natural: [[CicloAI/Tópicos/Arquitetura de Software/V02 - Trade-offs, fitness functions e ADRs (registrar decisões)|Trade-offs, fitness functions e ADRs]]
- Medir disponibilidade com SLOs: [[CicloAI/Tópicos/Arquitetura de Software/V14 - Escalabilidade, cache, observabilidade-SLOs; migração com strangler fig|Escalabilidade e observabilidade]]
- A AWS organiza essas qualidades nos pilares do [[CicloAI/Tópicos/AWS/V15 - Well-Architected + projeto - deploy de uma API serverless completa|Well-Architected Framework]]
- Consistência × disponibilidade é o coração do [[CicloAI/Tópicos/ACID, CAP e PACELC/V08 - Teorema CAP (e o que ele NÃO diz)|Teorema CAP]]

## Para praticar

- Pegue o sistema em que você trabalha e liste as **3 características mais importantes**, justificando cada uma com uma frase do negócio.
- Para cada uma, escreva **como mediria** (número + condição).
- Anote 1 característica implícita que o time nunca discutiu.

## Fontes

*Fundamentals of Software Architecture*, cap. 4–5 (Richards & Ford); ISO/IEC 25010 (modelo de qualidade).

## Minhas anotações
