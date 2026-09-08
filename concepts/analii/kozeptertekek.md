---
tags: [concept]
sources: [01_ea_an_ii_a_b_merged.pdf]
references: ["An II A/B 2. előadás"]
derivation: source
updated: 2026-09-04
---

# Középértéktételek

A három klasszikus középértéktétel — Rolle, Lagrange, Cauchy — és a deriváltak egyenlőségére vonatkozó következménytétel; alkalmazásuk egyenlőtlenségek igazolásában.

## Rolle-féle középértéktétel

**Tétel.** Legyen $a, b \in \mathbb{R}$, $a < b$. Ekkor

$$\left.\begin{aligned} f \in C[a,b] \\ f \in D(a,b) \\ f(a) = f(b) \end{aligned}\right\} \implies \exists\, \xi \in (a, b) : f'(\xi) = 0.$$

**Bizonyítás.** $f \in C[a,b]$ $\implies$ (Weierstrass-tétel) $\exists\, \alpha, \beta \in [a, b]$:
$$f(\alpha) = \min_{[a,b]} f =: m, \qquad f(\beta) = \max_{[a,b]} f =: M.$$

- **1. eset:** $m = M$. Ekkor $f$ állandó $(a, b)$-n, így $\forall x \in (a, b) : f'(x) = 0$, bármely $\xi$ megfelel.

- **2. eset:** $m \neq M$. Mivel $f(a) = f(b)$, legalább az egyik szélső értéket felvevő pont (pl. $\alpha$) $(a, b)$-be esik. Ekkor $\xi := \alpha \in \operatorname{int} \mathcal{D}_f = (a, b)$, és $f$-nek $\xi$-ben lokális minimuma van. Mivel $f \in D\{\xi\}$, az elsőrendű szükséges feltétel alapján $f'(\xi) = 0$. $\blacksquare$

**Geometriai értelmezés.** Ha $f$ folytonos $[a, b]$-n és differenciálható $(a, b)$-n, akkor $f$ grafikonjának van olyan pontja, amelyben az érintő párhuzamos az $x$-tengellyel.

## Lagrange-féle középértéktétel

**Tétel.** Legyen $a, b \in \mathbb{R}$, $a < b$. Ekkor

$$\left.\begin{aligned} f \in C[a,b] \\ f \in D(a,b) \end{aligned}\right\} \implies \exists\, \xi \in (a, b) : f'(\xi) = \frac{f(b) - f(a)}{b - a}.$$

**Bizonyítás.** Az $(a, f(a))$ és $(b, f(b))$ pontokon átmenő szelő egyenlete:
$$y = h_{a,b}(x) = \frac{f(b) - f(a)}{b - a}(x - a) + f(a).$$

Legyen $F(x) := f(x) - h_{a,b}(x)$ ($x \in [a, b]$). Ekkor $F \in C[a,b]$, $F \in D(a, b)$ és
$$F(a) = f(a) - f(a) = 0, \qquad F(b) = f(b) - \left(\frac{f(b)-f(a)}{b-a}(b-a) + f(a)\right) = 0.$$

Tehát $F(a) = F(b)$, és a Rolle-féle tétel szerint $\exists\, \xi \in (a, b)$, amelyre $F'(\xi) = 0$, azaz
$$f'(\xi) - \frac{f(b) - f(a)}{b - a} = 0 \implies f'(\xi) = \frac{f(b) - f(a)}{b - a}. \quad \blacksquare$$

**Geometriai értelmezés.** Ha $f$ folytonos $[a, b]$-n és differenciálható $(a, b)$-n, akkor $f$ grafikonjának van olyan pontja, amelyben a húzott érintő párhuzamos az $(a, f(a))$, $(b, f(b))$ pontokon áthaladó szelővel.

## A deriváltak egyenlőségének tétele

**Tétel.** Legyen $a, b \in \mathbb{R}$, $a < b$ és $f, g \in D(a, b)$. Ekkor

$$1^\circ \quad f' \equiv 0 \text{ $(a,b)$-n} \iff f \equiv \text{állandó $(a,b)$-n.}$$

$$2^\circ \quad f' \equiv g' \text{ $(a,b)$-n} \iff \exists\, c \in \mathbb{R} : f(x) = g(x) + c \quad (x \in (a, b)).$$

**Bizonyítás.**
- $1^\circ$ ($\Rightarrow$): A Lagrange-tétel következménye. Ha $x_1, x_2 \in (a, b)$, $x_1 < x_2$, akkor $f \in C[x_1, x_2]$, $f \in D(x_1, x_2)$, ezért $\exists\, \xi \in (x_1, x_2)$: $\dfrac{f(x_2) - f(x_1)}{x_2 - x_1} = f'(\xi) = 0$, tehát $f(x_1) = f(x_2)$.
- $2^\circ$: Alkalmazzuk az $1^\circ$ állítást az $F := f - g$ függvényre. $\blacksquare$

## Cauchy-féle középértéktétel

**Tétel.** Legyen $a, b \in \mathbb{R}$, $a < b$. Ekkor

$$\left.\begin{aligned} f, g \in C[a,b] \\ f, g \in D(a,b) \\ \forall x \in (a,b): g'(x) \neq 0 \end{aligned}\right\} \implies \exists\, \xi \in (a, b) : \frac{f'(\xi)}{g'(\xi)} = \frac{f(b) - f(a)}{g(b) - g(a)}.$$

**Bizonyítás.** A $g'(x) \neq 0$ feltételből a Rolle-tétellel következik, hogy $g(a) \neq g(b)$. Legyen
$$F(x) := f(x) - f(a) - \frac{f(b) - f(a)}{g(b) - g(a)}\bigl(g(x) - g(a)\bigr) \quad (x \in [a, b]).$$

Ekkor $F \in C[a,b]$, $F \in D(a,b)$, $F(a) = F(b) = 0$. A Rolle-tétel szerint $\exists\, \xi \in (a, b)$, amelyre $F'(\xi) = 0$:
$$0 = F'(\xi) = f'(\xi) - \frac{f(b) - f(a)}{g(b) - g(a)}\cdot g'(\xi) \implies \frac{f'(\xi)}{g'(\xi)} = \frac{f(b) - f(a)}{g(b) - g(a)}. \quad \blacksquare$$

## Alkalmazás: egyenlőtlenségek bizonyítása

**Példa.** Igazoljuk az $x - \dfrac{x^2}{2} < \ln(1+x) < x$ ($x > 0$) egyenlőtlenséget.

**$\ln(1+x) < x$ igazolása.** Legyen $x > 0$ tetszőleges, $a := 1$, $b := x+1$, $f := \ln$. Ekkor $f \in C[a,b]$, $f \in D(a,b)$, és a Lagrange-tétel szerint $\exists\, 1 < \xi < x+1$:
$$f'(\xi) = \frac{\ln(x+1) - \ln 1}{x+1 - 1} = \frac{\ln(x+1)}{x}, \qquad f'(\xi) = \frac{1}{\xi} < 1,$$
ezért $\dfrac{\ln(x+1)}{x} < 1$, azaz $\ln(1+x) < x$.

**$x - \frac{x^2}{2} < \ln(1+x)$ igazolása.** Alkalmazzuk az előző módszert az $f(t) := \ln t + \dfrac{(t-1)^2}{2}$ ($t > 0$) függvényre. Ekkor $\exists\, 1 < \xi < x+1$:
$$f'(\xi) = \frac{f(x+1) - f(1)}{(x+1) - 1} = \frac{\ln(x+1) + \frac{x^2}{2}}{x}.$$
Mivel $f'(t) = \dfrac{1}{t} + t - 1 > 1$ ($t > 1$), ezért $f'(\xi) > 1$, amiből $\ln(x+1) + \dfrac{x^2}{2} > x$, vagyis $x - \dfrac{x^2}{2} < \ln(1+x)$. $\blacksquare$

## Kapocs

- [[concepts/analii/lokalis-szelsertekek]] — Fermat-féle feltétel: a Rolle-tétel bizonyítása erre épít
- [[concepts/analii/monotonitas]] — a Lagrange-tétel közvetlen következménye a monotonitás és derivált kapcsolatáról szóló tétel
- [[concepts/analii/lhospital-szabalyok]] — L'Hospital-szabályok bizonyítása a Cauchy-féle középértéktételre épül
- [[concepts/analii/taylor-formula-maradektag]] — a Lagrange-maradéktag a Cauchy-középértéktétellel igazolható
- [[concepts/analii/primitiv-fuggveny]] — a deriváltak egyenlőségének tétele az integrálfüggvény egyediségének alapja
