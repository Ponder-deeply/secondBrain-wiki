---
tags: [concept]
sources: [01_ea_an_ii_a_b_merged.pdf]
references: ["An II A/B 11. előadás"]
derivation: source
updated: 2026-09-04
---

# Forgástest felszíne

Egy $0 \leq f \in C^1[a, b]$ függvény grafikonjának $x$ tengely körüli megforgatásával adódó forgásfelület felszíne egyenlő a $2\pi \int_a^b f(x) \sqrt{1 + [f'(x)]^2}\, dx$ integrállal.

## A forgásfelület

Legyen $f \geq 0$ függvény az $[a, b]$ intervallumon. Jelöljük $\mathcal{A}_f$-fel az $f$ grafikonjának az $x$ tengely körüli megforgatásával adódó **forgásfelületet**:

$$\mathcal{A}_f := \bigl\{(x, y, z) \in \mathbb{R}^3 \mid a \leq x \leq b,\; y^2 + z^2 = f^2(x),\; y, z \in \mathbb{R}\bigr\}.$$

**Megjegyzés a definícióról.** A felszín problémája (még forgásfelület esetén is) jóval bonyolultabb, mint a terület vagy a térfogat problémája. Naiv közelítésként adódna, hogy az $\mathcal{A}_f$ felszínét az $f$ grafikonjába beírt töröttvonalak megforgatásával kapott halmazok (csonkakúp-palástok) felszíneinek szuprémumával közelítsük — ez azonban **hibás**: a szuprémum nem adja vissza az intuitívan helyes értéket (például $|x|$ függvénynél $[-1, 1]$-en a naiv szuprémum $4\pi > 2\sqrt{2}\pi$, az integrálképlet szerinti értékkel szemben).

Ezért a felszínt a végeredményként kapott integrállal **definiáljuk**.

## A felszín képlete

**Definíció.** Legyen $-\infty < a < b < +\infty$, és t.f.h. $0 \leq f \in C^1[a, b]$. Ekkor az $f$ grafikonjának az $x$ tengely körüli megforgatásával adódó $\mathcal{A}_f$ forgásfelületnek van felszíne, és értéke

$$T(\mathcal{A}_f) = 2\pi \int_a^b f(x) \cdot \sqrt{1 + \bigl[f'(x)\bigr]^2}\; dx.$$

**Motiváció.** A képlet szerkezetét beláthatjuk úgy, hogy egy $[x_{i-1}, x_i]$ kis intervallumon $f$ közel állandó ($\approx f(\xi_i)$), és az ívdarab hossza $\approx \sqrt{1 + [f'(\xi_i)]^2} \cdot (x_i - x_{i-1})$. A megforgatással kapott csonkakúp palástjának felszíne $\approx 2\pi f(\xi_i) \cdot \ell_i$, ami az integrál Riemann-közelítő összegébe illeszkedik.

## Példa: a gömb felszíne

Az origó középpontú $R$ sugarú gömbfelületet az $f_r(x) = \sqrt{R^2 - x^2}$ ($x \in [-r, r]$) függvény grafikonjának $x$ tengely körüli megforgatásával kapjuk, ahol $0 < r < R$. Számítsuk ki az $[-r, r]$ darab felszínét:

$$f_r'(x) = \frac{-x}{\sqrt{R^2 - x^2}}, \qquad 1 + \bigl[f_r'(x)\bigr]^2 = 1 + \frac{x^2}{R^2 - x^2} = \frac{R^2}{R^2 - x^2}.$$

Tehát

$$F_r := 2\pi \int_{-r}^{r} \sqrt{R^2 - x^2} \cdot \frac{R}{\sqrt{R^2 - x^2}}\; dx = 2\pi R \int_{-r}^{r} 1\; dx = 4Rr\pi.$$

A szemléletes alap alapján könnyen elfogadható, hogy $r \to R$ esetén $\mathcal{A}_r \to \mathcal{A}_R$, ahol $\mathcal{A}_R$ az $R$ sugarú gömb felülete. Ugyanakkor

$$\lim_{r \to R} F_r = \lim_{r \to R} 4Rr\pi = 4R^2\pi,$$

ami valóban nem más, mint az $R$ sugarú gömb felszíne. $\blacksquare$

**Összefoglalás:** Az $R$ sugarú gömb felszíne $4R^2\pi$.

## Kapocs

- [[concepts/analii/ivhossz]] — az ívhossz-képlet $\sqrt{1+[f']^2}$ tagja a felszín-képletben is megjelenik
- [[concepts/analii/forgastest-terfogata]] — a forgástest térfogata analóg szerkezetű definícióval
- [[concepts/analii/sikido-terulete]] — síkidom területe mint egydimenziós analóg
- [[concepts/analii/newton-leibniz-tetel]] — az integrál kiszámításának eszköze
