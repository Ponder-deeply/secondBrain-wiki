---
tags: [concept]
sources: [01_ea_an_ii_a_b_merged.pdf]
references: ["An II A/B 11. előadás"]
derivation: source
updated: 2026-09-04
---

# Ívhossz

Egy síkbeli függvénygrafikon hosszát az ívhossz fogalmával mérjük: rektifikálható grafikonokra ez egyenlő az összes lehetséges beírt töröttvonal hosszainak szuprémumával, $C^1$ függvények esetén pedig kiszámítható egy határozott integrállal.

## A grafikon mint síkbeli halmaz

Legyen $a, b \in \mathbb{R}$, $a < b$ és $f : [a, b] \to \mathbb{R}$. Az

$$\Gamma_f := \bigl\{(x, f(x)) \mid x \in [a, b]\bigr\}$$

síkbeli halmazt az $f$ **grafikonjának** nevezzük.

## Beírt töröttvonal

Tetszőleges $\tau = \{a = x_0 < x_1 < \cdots < x_n = b\} \in \mathcal{F}[a, b]$ felosztás esetén tekintsük az

$$(x_0, f(x_0)),\; (x_1, f(x_1)),\; \ldots,\; (x_n, f(x_n))$$

pontokat összekötő szakaszokat; ezt nevezzük az $f$ függvénygrafikon $\tau$ felosztáshoz tartozó **beírt töröttvonalának**. Ennek hossza

$$\ell_f(\tau) = \sum_{i=1}^{n} \sqrt{(x_i - x_{i-1})^2 + \bigl(f(x_i) - f(x_{i-1})\bigr)^2}.$$

## Rektifikálhatóság és ívhossz

**Definíció.** Legyen $a, b \in \mathbb{R}$, $a < b$ és $f : [a, b] \to \mathbb{R}$. Azt mondjuk, hogy a $\Gamma_f$ függvénygrafikon **rektifikálható**, ha

$$\ell(\Gamma_f) := \sup\bigl\{\ell_f(\tau) \mid \tau \in \mathcal{F}[a, b]\bigr\} < +\infty.$$

Ebben az esetben $\ell(\Gamma_f)$ az $f$ függvénygrafikon **ívhossza**.

**Jelölés:** $f \in C^1[a, b]$ jelenti, hogy $f$ folytonosan differenciálható $[a, b]$-n, vagyis $f \in D[a, b]$ és $f' \in C[a, b]$ (a végpontokban elegendő az egyoldali derivált létezése).

## Az ívhossz-tétel ($C^1$ eset)

**Tétel.** Legyen $a, b \in \mathbb{R}$, $a < b$, és tegyük fel, hogy $f : [a, b] \to \mathbb{R}$ függvény **folytonosan deriválható** (azaz $f \in C^1[a, b]$). Ekkor $\Gamma_f$ rektifikálható, és az ívhossza

$$(\ast) \qquad \ell(\Gamma_f) = \int_a^b \sqrt{1 + \bigl[f'(x)\bigr]^2}\; dx < +\infty.$$

### Bizonyítás vázlata

**(i) Rektifikálhatóság ($\ell(\Gamma_f) < +\infty$).**
Legyen $\tau \in \mathcal{F}[a, b]$ tetszőleges. A Lagrange-féle középértéktétel szerint minden $i$-re van $\xi_i \in (x_{i-1}, x_i)$ amelyre $f(x_i) - f(x_{i-1}) = f'(\xi_i)(x_i - x_{i-1})$, ezért

$$\ell_i = (x_i - x_{i-1})\sqrt{1 + [f'(\xi_i)]^2}.$$

Legyen $g(x) := \sqrt{1 + [f'(x)]^2}$. Mivel $g$ folytonos, ezért korlátos: $\exists M : |g| \leq M$. Így

$$\ell_f(\tau) = \sum_{i=1}^n \ell_i \leq M \cdot (b - a),$$

tehát $\ell(\Gamma_f) \leq M \cdot (b-a) < +\infty$.

**(ii) A $(\ast)$ képlet igazolása.**

Az $\ell_f(\tau)$ összeg a $g(x) = \sqrt{1+[f'(x)]^2}$ folytonos függvény $\tau$ felosztáshoz és $(\xi_i)$ közbülső értékekhez tartozó Riemann-féle közelítő összege, tehát $s(g, \tau) \leq \ell_f(\tau) \leq S(g, \tau)$.

Mivel $g \in R[a, b]$, ezért minden $\varepsilon > 0$-ra létezik $\tau_1$ felosztás, amelyre $\ell(\Gamma_f) - \varepsilon < \ell_f(\tau_1)$, és létezik $\tau_2$ amelyre $S(g, \tau_2) < \int_a^b g + \varepsilon$. A $\tau := \tau_1 \cup \tau_2$ finomításra

$$\ell(\Gamma_f) - \varepsilon < \ell_f(\tau) \leq S(g, \tau) \leq \int_a^b g + \varepsilon.$$

Másrészt $\int_a^b g - \varepsilon < s(g, \tau_2) \leq \ell_f(\tau_2) \leq \ell(\Gamma_f)$. Mivel ez minden $\varepsilon > 0$-ra teljesül, ezért $\ell(\Gamma_f) = \int_a^b g\; dx$. $\blacksquare$

## Példa: a kör kerülete

Az $R$ sugarú kör negyedének ívhossza az $f(x) = \sqrt{R^2 - x^2}$ ($|x| \leq R/\sqrt{2}$) függvénnyel számítható:

$$f'(x) = \frac{1}{2\sqrt{R^2 - x^2}} \cdot (-2x) = \frac{-x}{\sqrt{R^2 - x^2}},$$

ezért

$$1 + [f'(x)]^2 = 1 + \frac{x^2}{R^2 - x^2} = \frac{R^2}{R^2 - x^2} = \frac{1}{1 - (x/R)^2}.$$

Az $[-R/\sqrt{2},\, R/\sqrt{2}]$ intervallumon mért ívhossz:

$$\ell(\Gamma) = \int_{-R/\sqrt{2}}^{R/\sqrt{2}} \frac{1}{\sqrt{1-(x/R)^2}}\,dx = \left[R \arcsin\frac{x}{R}\right]_{-R/\sqrt{2}}^{R/\sqrt{2}} = R\!\left(\frac{\pi}{4} - \left(-\frac{\pi}{4}\right)\right) = R \cdot \frac{\pi}{2}.$$

Az $R$ sugarú kör kerülete tehát $4 \cdot R \cdot \frac{\pi}{2} = 2R\pi$.

**Megjegyzés.** Ez egyben igazolja, hogy az így definiált $\pi$ szám valóban megegyezik a közép-iskolában bevezetett $\pi$-vel. A $g(x) := \sqrt{R^2 - x^2}$ ($|x| \leq R$) teljes félkörre a tétel közvetlenül **nem** alkalmazható, mert $g \notin C^1[-R, R]$ (a végpontokban a derivált végtelen).

## Kapocs

- [[concepts/analii/sikido-terulete]] — síkidom területe; szintén görbe alatti terület integrállal
- [[concepts/analii/hatarozott-integral-ertelmezese]] — Riemann-integrál definíciója, amelyre az ívhossz-tétel épül
- [[concepts/analii/forgastest-felszine]] — forgástest felszínének képlete az ívhossz-képletre épül
- [[concepts/analii/newton-leibniz-tetel]] — a Newton–Leibniz-tétel segítségével számítjuk ki az integrált
- [[concepts/analii/kozeptertekek]] — a Lagrange-féle középértéktétel kulcslépés a bizonyításban
