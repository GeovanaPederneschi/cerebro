---
tags: [cicloai/topico]
materia: Git e Kanban
volta: 1
status: a estudar
---
# V1 · Git: modelo interno (blobs, trees, commits, refs)

[[CicloAI/Matérias/Git e Kanban|Git e Kanban]] · anterior: — · próximo: [[CicloAI/Tópicos/Git e Kanban/V02 - Git - merge x rebase|V2]]

## Resumo

O Git é, por baixo, um **banco de dados de objetos endereçado por conteúdo**: cada objeto é guardado pelo **hash** do seu conteúdo (SHA-1 por padrão; SHA-256 opcional).

**Os 4 tipos de objeto**
- **blob**: o conteúdo de um arquivo (sem nome, sem permissões).
- **tree**: um diretório — lista de nomes apontando para blobs e outras trees, com modos (permissões).
- **commit**: aponta para **uma tree raiz** (o snapshot completo do projeto), para o(s) **commit(s) pai**, e guarda autor, data e mensagem.
- **tag anotada**: aponta para um commit, com mensagem e autor.

**Commit é snapshot, não diff.** O Git economiza espaço porque arquivos iguais têm o mesmo hash e viram o mesmo blob (e depois compacta em *packfiles*).

**Refs**: uma **branch** é só um arquivo com o hash de um commit (`.git/refs/heads/main`). Por isso criar branch é instantâneo. **HEAD** aponta para a branch atual (ou direto para um commit: *detached HEAD*).

**Index (staging area)**: o rascunho da próxima tree; `git add` grava blobs e atualiza o index.

**Consequência importante**: objetos são **imutáveis**. "Alterar" um commit (amend, rebase) cria commits **novos** com hashes novos — os antigos continuam lá até o *garbage collection* (e o `reflog` lembra deles).

## Conceitos-chave

- [[Objetos do Git]] — blob, tree, commit, tag
- [[Endereçamento por conteúdo]]
- [[Branch (Git)]] — ponteiro móvel para um commit
- [[HEAD (Git)]]
- [[Staging area]]

## Exemplo

```bash
git rev-parse HEAD                 # hash do commit atual
git cat-file -t HEAD               # commit
git cat-file -p HEAD               # tree, parent, author, mensagem
git cat-file -p 'HEAD^{tree}'      # lista de blobs e trees
cat .git/HEAD                      # ref: refs/heads/main
cat .git/refs/heads/main           # o hash — uma branch é só isso
git log --graph --oneline --all    # o grafo de commits
```

## Flashcards

#flashcards/git-kanban

Quais são os 4 tipos de objeto do Git?::blob, tree, commit e tag anotada.
O que um blob guarda?::Só o conteúdo do arquivo, sem nome nem permissões.
Um commit guarda um diff?::Não: aponta para uma tree com o snapshot completo, mais pais, autor e mensagem.
O que é uma branch no Git?::Um arquivo/ponteiro com o hash de um commit.
O que é detached HEAD?::HEAD apontando direto para um commit em vez de uma branch.
Por que rebase muda os hashes?::Objetos são imutáveis; o rebase cria commits novos com pais diferentes.
Comando para ver o conteúdo de um objeto::git cat-file -p <hash>.

## Conexões

- Próximo: [[CicloAI/Tópicos/Git e Kanban/V02 - Git - merge x rebase|Merge × rebase]]
- O histórico do Git é um grafo dirigido acíclico: [[CicloAI/Tópicos/Teoria dos Grafos/V10 - DAGs e ordenação topológica|DAGs]]
- Endereçamento por hash também aparece em caches e CDNs: [[CicloAI/Tópicos/AWS/V07 - S3 (classes, políticas, versionamento) e CloudFront|S3 e CloudFront]]

## Para praticar

- Rode os comandos do exemplo num repositório seu e desenhe (papel ou Excalidraw) commit → tree → blobs.
- Crie uma branch e confira que apareceu um arquivo novo em `.git/refs/heads/`.
- Faça um `git commit --amend` e compare o hash antes e depois.

## Fontes

*Pro Git*, cap. 10 — *Git Internals* (git-scm.com/book).

## Minhas anotações
