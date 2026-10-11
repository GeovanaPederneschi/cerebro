---
tags: [cicloai/topico]
materia: ACID, CAP e PACELC
volta: 1
status: a estudar
---
# V1 · Transações e ACID

[[CicloAI/Matérias/ACID, CAP e PACELC|ACID, CAP e PACELC]] · anterior: — · próximo: [[CicloAI/Tópicos/ACID, CAP e PACELC/V02 - Níveis de isolamento e anomalias (dirty read, non-repeatable, phantom)|V2]]

## Resumo

Uma **transação** agrupa várias leituras e escritas numa **unidade lógica**: ou tudo acontece, ou nada acontece. O banco cuida dos casos difíceis (queda no meio, concorrência) para a aplicação não ter que cuidar.

**ACID**
- **A — Atomicidade**: tudo ou nada. Se algo falha no meio, a transação é **abortada** e as escritas anteriores são desfeitas (*rollback*). Kleppmann sugere pensar como "abortabilidade".
- **C — Consistência**: as **invariantes da aplicação** continuam verdadeiras (ex.: a soma dos saldos não muda numa transferência). É, em boa parte, responsabilidade da **aplicação**; o banco ajuda com *constraints* (chave estrangeira, `CHECK`, `UNIQUE`).
- **I — Isolamento**: transações concorrentes não atrapalham umas às outras. O ideal é a **serializabilidade** (como se rodassem uma de cada vez), mas na prática os bancos usam níveis mais fracos por desempenho.
- **D — Durabilidade**: depois do *commit*, o dado não se perde, mesmo com queda — graças ao *write-ahead log* (WAL), ao `fsync` e à replicação.

⚠️ O **C do ACID não é o C do CAP**. No ACID é sobre invariantes; no CAP é sobre todos verem o dado mais recente (linearizabilidade).

**Atenção a retries**: se uma transação aborta e a aplicação tenta de novo, a operação precisa ser **idempotente** — senão, se o commit funcionou mas a resposta se perdeu, você executa duas vezes.

## Conceitos-chave

- [[Transação]]
- [[ACID]]
- [[Rollback]]
- [[Invariante]] — regra que precisa continuar verdadeira
- [[Write-ahead log]]
- [[Idempotência]]

## Exemplo

```sql
BEGIN;
UPDATE contas SET saldo = saldo - 100 WHERE id = 1;
UPDATE contas SET saldo = saldo + 100 WHERE id = 2;
-- se qualquer comando falhar: ROLLBACK (atomicidade)
COMMIT; -- depois daqui, o dado sobrevive a uma queda (durabilidade)
```
Invariante (consistência): `saldo >= 0` garantido por `CHECK (saldo >= 0)`.

## Flashcards

#flashcards/acid-cap

O que é uma transação?::Um grupo de operações tratado como uma unidade: tudo acontece ou nada acontece.
Atomicidade (ACID)::Tudo ou nada: em caso de falha, a transação é abortada e as escritas são desfeitas.
Consistência (ACID)::As invariantes da aplicação continuam válidas; é em boa parte responsabilidade da aplicação.
Isolamento (ACID)::Transações concorrentes não interferem entre si; o ideal é a serializabilidade.
Durabilidade (ACID)::Após o commit o dado não se perde, mesmo com falhas (WAL, fsync, replicação).
O C do ACID é o mesmo do CAP?::Não. ACID: invariantes da aplicação. CAP: linearizabilidade (todos veem o dado mais recente).
Por que retries de transação exigem cuidado?::O commit pode ter funcionado e só a resposta se perdido; sem idempotência, a operação roda duas vezes.

## Conexões

- Próximo: [[CicloAI/Tópicos/ACID, CAP e PACELC/V02 - Níveis de isolamento e anomalias (dirty read, non-repeatable, phantom)|Níveis de isolamento]]
- Idempotência volta em [[CicloAI/Tópicos/Arquitetura de Software/V11 - Sagas (orquestração x coreografia), outbox e idempotência|Sagas, outbox e idempotência]]
- RDS × DynamoDB e suas garantias: [[CicloAI/Tópicos/AWS/V08 - RDS e Aurora|RDS e Aurora]]

## Para praticar

- Num Postgres local (ou no [db-fiddle](https://www.db-fiddle.com)), crie a tabela `contas` com `CHECK (saldo >= 0)` e faça uma transferência que viole a regra. Observe o rollback.
- Abra duas sessões e faça `BEGIN` nas duas, atualizando a mesma linha: o que acontece com a segunda?

## Fontes

*Designing Data-Intensive Applications*, cap. 7 (Kleppmann); documentação do PostgreSQL — *Transactions*.

## Minhas anotações
