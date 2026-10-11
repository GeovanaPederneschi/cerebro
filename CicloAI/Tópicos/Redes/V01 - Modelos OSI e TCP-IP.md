---
tags: [cicloai/topico]
materia: Redes
volta: 1
status: a estudar
---
# V1 · Modelos OSI e TCP/IP

[[CicloAI/Matérias/Redes|Redes]] · anterior: — · próximo: [[CicloAI/Tópicos/Redes/V02 - Enlace - Ethernet, MAC, switches e ARP|V2]]

## Resumo

Redes são organizadas em **camadas**: cada uma resolve um problema e oferece um serviço para a de cima.

**Modelo OSI (7 camadas, referência teórica)**
7. Aplicação · 6. Apresentação · 5. Sessão · 4. Transporte · 3. Rede · 2. Enlace · 1. Física
*(mnemônico de baixo para cima: "**F**ui **E**m **R**ede **T**omar **S**orvete **A**o **A**noitecer")*

**Modelo TCP/IP (o que a internet usa)**
- **Aplicação**: HTTP, DNS, TLS, SMTP, SSH (junta as camadas 5–7 do OSI).
- **Transporte**: TCP (confiável, ordenado) e UDP (rápido, sem garantias). Usa **portas**.
- **Internet**: IP — endereçamento e roteamento entre redes.
- **Enlace / acesso à rede**: Ethernet, Wi-Fi, endereços MAC.

**Encapsulamento**: ao descer, cada camada põe seu cabeçalho:
dados → **segmento** (TCP) → **pacote** (IP) → **quadro** (Ethernet) → **bits**. Ao subir, cada camada retira o seu.

**Dispositivos por camada**: switch (camada 2, MAC), roteador (camada 3, IP), load balancer **L4** (olha IP/porta) × **L7** (olha HTTP: rota, cabeçalhos).

**Por que importa no dia a dia**: para debugar ("é DNS? é TLS? é a porta?"), escolher load balancer (na AWS, ALB é L7 e NLB é L4) e entender latência.

## Conceitos-chave

- [[Modelo OSI]]
- [[Modelo TCP-IP]]
- [[Encapsulamento (redes)]]
- [[TCP]] × [[UDP]]
- [[Load balancer L4 x L7]]

## Exemplo

Ao abrir `https://exemplo.com`:
1. **DNS** (aplicação) descobre o IP.
2. **TCP** (transporte) abre conexão na porta 443.
3. **TLS** cifra o canal.
4. **HTTP** envia `GET /`.
5. Cada mensagem desce: segmento TCP → pacote IP → quadro Wi-Fi/Ethernet → sinal.

## Flashcards

#flashcards/redes

As 7 camadas do OSI, de baixo para cima::Física, Enlace, Rede, Transporte, Sessão, Apresentação, Aplicação.
As 4 camadas do TCP/IP::Enlace (acesso à rede), Internet, Transporte, Aplicação.
Nome da unidade de dados em cada camada::Transporte: segmento; Rede: pacote; Enlace: quadro; Física: bits.
Em que camada trabalha um switch? E um roteador?::Switch: camada 2 (MAC). Roteador: camada 3 (IP).
Load balancer L4 × L7::L4 decide por IP/porta; L7 entende HTTP (rotas, cabeçalhos, cookies).
TCP × UDP em uma frase::TCP: confiável e ordenado, com conexão. UDP: sem conexão e sem garantias, menor latência.
O que é encapsulamento?::Cada camada adiciona seu cabeçalho ao descer a pilha e o remove ao subir.

## Conexões

- Próximo: [[CicloAI/Tópicos/Redes/V02 - Enlace - Ethernet, MAC, switches e ARP|Enlace]]
- Na AWS: [[CicloAI/Tópicos/AWS/V06 - Load balancers (ALB x NLB)|ALB × NLB]]
- Arquitetura em camadas também aparece no software: [[CicloAI/Tópicos/Arquitetura de Software/V05 - Camadas e monolito modular - fronteiras e regras de dependência|Camadas e monolito modular]]

## Para praticar

- Rode `curl -v https://example.com` e identifique, na saída, o DNS, a conexão TCP, o handshake TLS e a requisição HTTP.
- Abra o Wireshark (ou as DevTools → Network) e veja uma requisição: quais camadas você consegue enxergar?

## Fontes

*Redes de Computadores e a Internet* (Kurose & Ross), cap. 1.5; *High Performance Browser Networking*, cap. 1.

## Minhas anotações
