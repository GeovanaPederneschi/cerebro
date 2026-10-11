---
tags: [cicloai/topico]
materia: Cálculo
volta: 1
status: a estudar
---
# V1 · Funções: tipos, composição, inversa e gráficos

[[CicloAI/Matérias/Cálculo|Cálculo]] · anterior: — · próximo: [[CicloAI/Tópicos/Cálculo/V02 - Exponencial e logaritmo (crescimento e complexidade)|V2]]

## Resumo

Uma **função** $f: A \to B$ associa **cada** elemento do domínio $A$ a **exatamente um** elemento de $B$ (contradomínio). O conjunto dos valores realmente atingidos é a **imagem**. No gráfico, isso é o *teste da reta vertical*: nenhuma reta vertical corta o gráfico duas vezes.

**Tipos mais usados**
- **Afim** $f(x) = ax + b$: reta; $a$ é a inclinação (quanto $y$ muda quando $x$ aumenta 1), $b$ é onde corta o eixo $y$.
- **Quadrática** $f(x) = ax^2 + bx + c$: parábola; vértice em $x = -\frac{b}{2a}$; abre para cima se $a > 0$.
- **Polinomial**, **racional** (com assíntotas), **modular** $|x|$, **exponencial** $a^x$, **logarítmica** $\log_a x$, **trigonométricas**.

**Classificação**
- **Injetora**: valores diferentes de $x$ dão valores diferentes de $y$.
- **Sobrejetora**: a imagem é todo o contradomínio.
- **Bijetora**: as duas → só ela tem **inversa**.

**Composição** $(f \circ g)(x) = f(g(x))$: aplica $g$ primeiro, depois $f$. A ordem importa: em geral $f \circ g \neq g \circ f$. É o mesmo que encadear funções puras em código (`pipe`).

**Inversa** $f^{-1}$: desfaz $f$, ou seja $f^{-1}(f(x)) = x$. O gráfico de $f^{-1}$ é o espelho do de $f$ na reta $y = x$. Para achar: troque $x$ e $y$ e isole $y$.

**Transformações de gráfico**
- $f(x) + k$: sobe $k$; $f(x - h)$: desloca $h$ para a **direita**; $a \cdot f(x)$: estica na vertical; $f(-x)$: espelha no eixo $y$.

## Conceitos-chave

- [[Função (matemática)]] — cada entrada tem exatamente uma saída
- [[Domínio e imagem]]
- [[Composição de funções]] — encadear transformações
- [[Função inversa]] — existe só para funções bijetoras
- [[Função pura]] — o paralelo em programação

## Exemplo

$f(x) = 2x + 1$ e $g(x) = x^2$:
- $(f \circ g)(x) = 2x^2 + 1$
- $(g \circ f)(x) = (2x + 1)^2 = 4x^2 + 4x + 1$ → ordem importa
- Inversa de $f$: $y = 2x + 1 \Rightarrow x = \frac{y - 1}{2} \Rightarrow f^{-1}(x) = \frac{x - 1}{2}$

```ts
const f = (x: number) => 2 * x + 1;
const g = (x: number) => x ** 2;
const compose = <A, B, C>(f: (b: B) => C, g: (a: A) => B) => (x: A) => f(g(x));
compose(f, g)(3); // 19
```

## Flashcards

#flashcards/calculo

O que define uma função?::Cada elemento do domínio tem exatamente uma imagem.
O que significa (f∘g)(x)?::f(g(x)): aplica g primeiro, depois f.
Quando uma função tem inversa?::Quando é bijetora (injetora e sobrejetora).
Como é o gráfico de f⁻¹ em relação ao de f?::Simétrico em relação à reta y = x.
O que f(x − 3) faz com o gráfico de f(x)?::Desloca 3 unidades para a direita.
Em f(x) = ax + b, o que é a?::A inclinação: quanto y varia quando x aumenta 1.
Onde fica o vértice de ax² + bx + c?::Em x = −b/(2a).
Passos para achar a inversa de y = f(x)::Trocar x e y e isolar y.

## Conexões

- Próximo: [[CicloAI/Tópicos/Cálculo/V02 - Exponencial e logaritmo (crescimento e complexidade)|Exponencial e logaritmo]]
- Composição é a base da [[CicloAI/Tópicos/Cálculo/V07 - Regra da cadeia (a base do backpropagation)|regra da cadeia]]
- Funções puras e nomes claros: [[CicloAI/Tópicos/Código Limpo/V02 - Funções - tamanho, um nível de abstração, parâmetros|Funções em código limpo]]

## Para praticar

- Plote no [Desmos](https://www.desmos.com/calculator) $f(x) = x^2$, $f(x - 2)$, $f(x) + 3$ e $-f(x)$ e descreva cada transformação.
- Ache a inversa de $f(x) = \frac{3x - 4}{5}$ e confira compondo $f(f^{-1}(x))$.
- Diga se $f(x) = x^2$ (de ℝ em ℝ) tem inversa. E se o domínio for $x \geq 0$?

## Fontes

Khan Academy — Funções; 3Blue1Brown *Essence of Calculus* (cap. 1); Stewart, cap. 1.

## Minhas anotações
