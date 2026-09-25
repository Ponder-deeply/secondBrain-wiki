---
tags: [concept, dimatii/polinomok]
sources: [DimatIIEa05.pdf, DimatIIEa06.pdf]
derivation: source
updated: 2026-09-08
---

# Gyök multiplicitása

Egy gyök multiplicitása az a legnagyobb kitevő, amellyel a gyöktényező még kiemelhető; a derivált a multiplicitást — a karakterisztika által megengedett mértékben — pontosan eggyel csökkenti.

## Tartalom

### Definíció

Legyen $R$ egységelemes integritási tartomány, $0 \neq f \in R[x]$ és $n \in \mathbb{N}^+$. Azt mondjuk, hogy $c \in R$ az $f$ egy **$n$-szeres gyöke**, ha

$$(x-c)^n \mid f, \qquad (x-c)^{n+1} \nmid f.$$

Ekkor $c$ **multiplicitása** $n$.

**Megjegyzés.** A definíció azzal ekvivalens, hogy $f(x) = (x-c)^ng(x)$, ahol $c$ **nem** gyöke $g$-nek.

### A derivált és a multiplicitás

**Tétel.** Legyen $R$ egységelemes integritási tartomány, $f \in R[x]$, $n \in \mathbb{N}^+$, és legyen $c \in R$ az $f$ egy $n$-szeres gyöke. Ekkor $c$ az $f'$-nek legalább $(n-1)$-szeres gyöke, és ha $\mathrm{char}(R) \nmid n$, akkor **pontosan** $(n-1)$-szeres gyöke.

*Bizonyítás.* Legyen $f(x) = (x-c)^ng(x)$, ahol $c$ nem gyöke $g$-nek. A szorzatszabállyal

$$f'(x) = n(x-c)^{n-1}g(x) + (x-c)^ng'(x) = (x-c)^{n-1}\big(ng(x) + (x-c)g'(x)\big).$$

Tehát $c$ valóban legalább $(n-1)$-szeres gyöke $f'$-nek. Pontosan $(n-1)$-szeres akkor lesz, ha $c$ nem gyöke a zárójeles tényezőnek:

$$ng(c) + (c-c)g'(c) = ng(c) + 0\cdot g'(c) = ng(c).$$

Ez pedig teljesül, ha $\mathrm{char}(R) \nmid n$, hiszen ekkor $g(c) \neq 0$ miatt $ng(c) \neq 0$. $\square$

### Ellenpélda: amikor a karakterisztika osztja a multiplicitást

Legyen $f(x) = x^4 - x \in \mathbb{Z}_3[x]$. Ekkor $1$ a $3$-szoros gyöke $f$-nek, mert

$$f(x) = x(x^3-1) \overset{\mathbb{Z}_3}{=} x(x^3 - 3x^2 + 3x - 1) = x(x-1)^3.$$

A derivált viszont

$$f'(x) = 4x^3 - 1 \overset{\mathbb{Z}_3}{=} x^3 - 3x^2 + 3x - 1 = (x-1)^3,$$

tehát $1$ **továbbra is** $3$-szoros gyöke $f'$-nek: a multiplicitás nem csökkent, mert $\mathrm{char}(\mathbb{Z}_3) = 3 \mid 3$.

## Kapocs

- [[concepts/dimatii/gyoktenyezo-es-gyokok-szama]] — az egyszeres gyök és a gyöktényező kiemelése
- [[concepts/dimatii/polinom-algebrai-derivaltja]] — a tétel eszköze
- [[concepts/dimatii/polinomok-maradekos-osztasa]] — a gyöktényező-hatványok kiemelésének technikai alapja
