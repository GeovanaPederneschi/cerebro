---
tags: [cicloai/topico]
materia: AWS
volta: 1
status: a estudar
---
# V1 · Visão geral: contas, regiões/AZs, free tier e alarme de custos

[[CicloAI/Matérias/AWS|AWS]] · anterior: — · próximo: [[CicloAI/Tópicos/AWS/V02 - IAM - usuários, roles, policies, menor privilégio|V2]]

## Resumo

**Infraestrutura global**
- **Região**: área geográfica com vários data centers (ex.: `sa-east-1` São Paulo, `us-east-1` N. Virgínia).
- **Availability Zone (AZ)**: um ou mais data centers **isolados** (energia, rede, refrigeração próprios) dentro da região, ligados entre si com baixa latência. A maioria das regiões tem 3 ou mais.
- **Edge locations**: pontos de presença usados por CloudFront e Route 53 para ficar perto do usuário.

**Regra de ouro**: alta disponibilidade = espalhar entre **AZs**; recuperação de desastre = entre **regiões**.

**Serviços globais × regionais**: IAM, Route 53 e CloudFront são globais; EC2, RDS, Lambda, VPC são regionais. Buckets S3 ficam numa região, mas o **nome** é único no mundo.

**Como escolher a região**: latência para os usuários, legislação/conformidade (LGPD, dados no país), preço (São Paulo costuma ser mais cara que N. Virgínia) e disponibilidade do serviço (novidades chegam antes em `us-east-1`).

**Conta e segurança inicial**
- A **conta root** (e-mail do cadastro) tem poder total: ative **MFA** e não use no dia a dia.
- Crie um usuário administrativo (via **IAM Identity Center** ou IAM) para trabalhar.

**Custos**
- O free tier mudou em 2025: contas novas passaram a receber créditos e um período de plano gratuito — confira as regras atuais na página oficial antes de subir recursos.
- Crie um **AWS Budget** com alerta por e-mail logo no primeiro dia. Use o **Cost Explorer** para ver para onde vai o dinheiro.

**Modelo de responsabilidade compartilhada**: a AWS cuida da segurança **da** nuvem (hardware, data centers, hipervisor); você cuida da segurança **na** nuvem (dados, IAM, configuração de rede, sistema operacional das EC2).

## Conceitos-chave

- [[Região AWS]] e [[Availability Zone]]
- [[Alta disponibilidade]] × [[Recuperação de desastre]]
- [[Modelo de responsabilidade compartilhada]]
- [[Conta root AWS]] — MFA e não usar no dia a dia
- [[AWS Budgets]] — alertas de custo

## Flashcards

#flashcards/aws

Região × Availability Zone::Região é uma área geográfica; AZ é um conjunto isolado de data centers dentro da região.
Como obter alta disponibilidade na AWS?::Distribuindo recursos em múltiplas AZs da mesma região.
Como fazer recuperação de desastre na AWS?::Replicando para outra região.
Cite 3 serviços globais da AWS::IAM, Route 53 e CloudFront.
4 critérios para escolher a região::Latência, conformidade/legislação, preço e disponibilidade do serviço.
Primeiros cuidados com a conta root::Ativar MFA, não usar no dia a dia e criar um usuário administrativo separado.
Responsabilidade compartilhada: o que é do cliente?::Segurança NA nuvem: dados, IAM, configurações de rede e SO das instâncias.
Ferramenta para receber alerta de gastos::AWS Budgets.

## Conexões

- Próximo: [[CicloAI/Tópicos/AWS/V02 - IAM - usuários, roles, policies, menor privilégio|IAM]]
- Disponibilidade como característica: [[CicloAI/Tópicos/Arquitetura de Software/V01 - Características arquiteturais e como extraí-las dos requisitos|Características arquiteturais]]
- Latência entre regiões tem a ver com [[CicloAI/Tópicos/Redes/V01 - Modelos OSI e TCP-IP|camadas de rede]] e com o [[CicloAI/Tópicos/ACID, CAP e PACELC/V09 - PACELC - latência x consistência sem partição|PACELC]]

## Para praticar

- Crie a conta (ou entre na sua), ative **MFA no root** e crie um usuário administrativo.
- Crie um **Budget de US$ 5** com alerta por e-mail.
- No console, troque de região e veja que os recursos de EC2 mudam, mas os do IAM não.

## Fontes

AWS — *Global Infrastructure*; AWS Skill Builder — *Cloud Practitioner Essentials*; página oficial do AWS Free Tier.

## Minhas anotações
