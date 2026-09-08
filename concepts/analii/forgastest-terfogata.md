---
tags: [concept]
sources: [01_ea_an_ii_a_b_merged.pdf]
references: ["An II A/B 11. előadás"]
derivation: source
updated: 2026-09-04
---

# Forgástest térfogata

Egy $f \geq 0$ függvény grafikonjának $x$ tengely körüli megforgatásával adódó forgástest térfogatát a $\pi \int_a^b f^2$ integrállal számítjuk.

## A forgástest definíciója

Legyen $f \in R[a, b]$, és t.f.h. $f \geq 0$ az $[a, b]$ intervallumon. Az $f$ grafikonjának $x$ tengely körüli megforgatásával adódó

$$H_f := \bigl\{(x, y, z) \in \mathbb{R}^3 \mid a \leq x \leq b,\; y^2 + z^2 \leq f^2(x),\; y, z \in \mathbb{R}\bigr\}$$

halmazt az $f$ által meghatározott **forgástestnek** nevezzük.

## A térfogat definíciója

A területhez és az ívhosszhoz hasonlóan a forgástestet beírt és körülírt hengerekkel közelítjük. Tetszőleges $\tau = \{a = x_0 < x_1 < \cdots < x_n = b\} \in \mathcal{F}[a, b]$ felosztáshoz legyenek

$$m_i := \inf_{x \in [x_{i-1}, x_i]} f(x), \qquad M_i := \sup_{x \in [x_{i-1}, x_i]} f(x),$$

és

$$h_i := \{(x, y, z) \in \mathbb{R}^3 \mid x_i \leq x \leq x_{i+1},\; y^2 + z^2 \leq m_i^2\},$$
$$H_i := \{(x, y, z) \in \mathbb{R}^3 \mid x_i \leq x \leq x_{i+1},\; y^2 + z^2 \leq M_i^2\}.$$

Ekkor $\bigcup_{i=1}^n h_i \subset H_f \subset \bigcup_{i=1}^n H_i$, és a forgó hengerek térfogatainak összege:

$$\sum_{i=1}^n \pi m_i^2 \cdot (x_i - x_{i-1}) = s(\pi f^2, \tau), \qquad \sum_{i=1}^n \pi M_i^2 \cdot (x_i - x_{i-1}) = S(\pi f^2, \tau).$$

Mivel $\pi f^2 \in R[a, b]$, ezért $\int_a^b \pi f^2$ az egyetlen szám, amely minden $\tau$ esetén $s(\pi f^2, \tau)$ és $S(\pi f^2, \tau)$ közé esik. Ezért a $H_f$ forgástest ($V(H_f)$-fel jelölt) **térfogatát** így értelmezzük:

$$V(H_f) := \pi \int_a^b f^2(x)\; dx.$$

**Definíció (tömör összefoglalás).** Legyen $0 \leq f \in R[a, b]$. Ekkor az $f$ grafikonjának az $x$ tengely körüli megforgatásával adódó $\mathcal{A}_f$ forgástestnek van térfogata, és az egyenlő a

$$\pi \int_a^b f^2(x)\; dx$$

integrállal.

## Példa: a gömb térfogata

Az $(0, 0, 0)$ középpontú $R$ sugarú gömb az $f(x) := \sqrt{R^2 - x^2}$ ($x \in [-R, R]$) függvény grafikonjának az $x$ tengely körüli megforgatásával adódó térrész. E gömb térfogata:

$$\pi \int_{-R}^{R} (R^2 - x^2)\; dx = \pi \left[R^2 x - \frac{x^3}{3}\right]_{-R}^{R} = \pi \cdot \frac{2R^3 \cdot 2}{3} \cdot \frac{1}{1} = \frac{4R^3\pi}{3}. \qquad \blacksquare$$

Részletesen:

$$\pi \left[\left(R^3 - \frac{R^3}{3}\right) - \left(-R^3 + \frac{R^3}{3}\right)\right] = \pi \cdot 2\left(R^3 - \frac{R^3}{3}\right) = \pi \cdot 2 \cdot \frac{2R^3}{3} = \frac{4R^3\pi}{3}.$$

## Kapocs

- [[concepts/analii/forgastest-felszine]] — a forgástest felszínének kiszámítása; analóg, de bonyolultabb konstrukció
- [[concepts/analii/sikido-terulete]] — síkidom területe mint egydimenziós analóg
- [[concepts/analii/ivhossz]] — ívhossz; a forgástest-problémánál hasonló gondolatmenetet alkalmazunk
- [[concepts/analii/hatarozott-integral-ertelmezese]] — az alsó/felső közelítő összeg és a Riemann-integrál definíciója
- [[concepts/analii/newton-leibniz-tetel]] — az integrál kiszámításának eszköze
