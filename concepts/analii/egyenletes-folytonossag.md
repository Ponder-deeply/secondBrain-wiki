---
tags: [concept]
sources: [01_ea_an_ii_a_b_merged.pdf]
references: ["An II A/B 9. előadás"]
derivation: source
updated: 2026-09-04
---

# Egyenletes folytonosság

Az egyenletes folytonosság erősebb a pontbeli folytonosságnál: a $\delta > 0$ csak $\varepsilon$-tól függ, az $a$ ponttól nem. Kompakt intervallumon a kettő ekvivalens (Heine-tétel).

## Pontbeli vs. egyenletes folytonosság

**Pontbeli folytonosság** ($f \in C\{a\}$):
$$\forall \varepsilon > 0\ \exists \delta > 0:\ \forall x \in H,\ |x-a| < \delta \Rightarrow |f(x)-f(a)| < \varepsilon.$$
(A $\delta$ függ $a$-tól és $\varepsilon$-tól.)

**Egyenletes folytonosság** ($f$ egyenletesen folytonos $H$-n):

**Definíció.** Az $f \in \mathbb{R} \to \mathbb{R}$ függvény **egyenletesen folytonos** a $H \subset \mathcal{D}_f$ halmazon, ha
$$\forall \varepsilon > 0\ \exists \delta > 0:\ \forall x, y \in H,\ |x-y| < \delta \Rightarrow |f(x)-f(y)| < \varepsilon.$$
(A $\delta$ csak $\varepsilon$-tól függ, $a$-tól nem.)

**Szemléletes megfogalmazás:** $f$ egyenletesen folytonos $H$-n, ha „$H$ tetszőlegesen közel eső pontjaiban a függvényértékek is tetszőlegesen közel vannak egymáshoz."

**Tétel.** Egyenletesen folytonos $\Rightarrow$ folytonos.

**Bizonyítás.** Legyen $a \in H$ és $\varepsilon > 0$ tetszőleges. Az egyenletes folytonosság definíciójából $\exists \delta > 0$ (csak $\varepsilon$-tól függő): $\forall x, y \in H, |x-y| < \delta \Rightarrow |f(x)-f(y)| < \varepsilon$. Ezt $y = a$-ra alkalmazva: $|x-a| < \delta$ esetén $|f(x)-f(a)| < \varepsilon$. Ez éppen $f \in C\{a\}$. $\blacksquare$

## Példák

**1. példa.** $f(x) = x^2$ ($x \in (0,1)$): egyenletesen folytonos.
$$|f(x)-f(a)| = |x^2-a^2| = |(x-a)(x+a)| \leq 2|x-a| < \varepsilon,$$
ha $|x-a| < \delta = \varepsilon/2$. Ez $a$-tól független.

**2. példa.** $f(x) = \frac{1}{x}$ ($x \in (0,1)$): **nem** egyenletesen folytonos.
$$\delta_1 = \frac{\varepsilon}{1+a\varepsilon} \cdot a^2, \quad \delta_2 = \frac{\varepsilon}{1-a\varepsilon} \cdot a^2,$$
ezért $\delta \to 0$, ha $a \to 0$ — nem létezik $a$-tól független $\delta$.

**3. példa.** $f(x) = x^2$:
- (a) $[0,1]$-en: egyenletesen folytonos ($\delta = \varepsilon/2$ működik).
- (b) $[1,+\infty)$-en: **nem** egyenletesen folytonos. ($x = n + \frac{1}{n}$, $y = n$: $|x-y| = \frac{1}{n} \to 0$, de $|f(x)-f(y)| = 2 + \frac{1}{n^2} > 2$.)

**4. példa.** $f(x) = \frac{1}{x}$ ($x > 0$):
- (a) $[1,+\infty)$-en: egyenletesen folytonos ($|f(x)-f(y)| = \frac{|x-y|}{|xy|} \leq |x-y| < \varepsilon$ ha $\delta = \varepsilon$).
- (b) $(0,1)$-en: **nem** egyenletesen folytonos. ($x = \frac{1}{n}$, $y = \frac{1}{n+1}$: $|x-y| \to 0$, de $|f(x)-f(y)| = 1$.)

**Következtetés** (3(b) és 4(b) alapján): a folytonosság $\Rightarrow$ egyenletes folytonosság fordítás **nem igaz** általánosan.

## Heine-tétel

**Heine-tétel.** Ha $-\infty < a < b < +\infty$ és $f \in C[a,b]$, akkor $f$ **egyenletesen folytonos** $[a,b]$-n.

**Bizonyítás** (indirekt). T.f.h. $f$ nem egyenletesen folytonos $[a,b]$-n. Ekkor:
$$\exists \varepsilon > 0,\ \forall \delta > 0\text{-hoz}:\ \exists x, y \in [a,b],\ |x-y| < \delta\ \text{ és }\ |f(x)-f(y)| \geq \varepsilon.$$

$\delta := \frac{1}{n}$ ($n \in \mathbb{N}^+$) választással: $\exists x_n, y_n \in [a,b]$:
$$|x_n - y_n| < \frac{1}{n} \quad \text{és} \quad |f(x_n) - f(y_n)| \geq \varepsilon. \quad (*)$$

Az $(x_n)$ sorozat korlátos, ezért $\exists (x_{n_k})$ konvergens részsorozat, amelynek határértéke $\alpha \in [a,b]$.

Ekkor $y_{n_k} = (y_{n_k} - x_{n_k}) + x_{n_k} \to 0 + \alpha = \alpha$.

Mivel $f \in C[a,b]$, ezért $f \in C\{\alpha\}$, tehát $f(x_{n_k}) \to f(\alpha)$ és $f(y_{n_k}) \to f(\alpha)$, így:
$$\lim_{n_k \to +\infty} (f(x_{n_k}) - f(y_{n_k})) = 0.$$
Ez ellentmond $(*)$-nak. $\blacksquare$

## Kapocs

- [[concepts/analii/folytonossag-es-derivalt]] — pontbeli folytonosság
- [[concepts/analii/folytonos-fuggvenyek-integralhatasaga]] — Heine-tétel alkalmazása: $f \in C[a,b] \Rightarrow f \in R[a,b]$
