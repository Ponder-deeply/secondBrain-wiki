---
tags: [concept]
sources: [01_ea_an_ii_a_b_merged.pdf]
references: ["An II A/B 12. előadás"]
derivation: source
updated: 2026-09-04
---

# Improprius integrál

A Riemann-integrál kiterjesztése olyan függvényekre, amelyek értelmezési tartománya nem korlátos, vagy amelyek nem korlátosak az értelmezési tartományon.

## Motiváció

A Riemann-integrál $f \in R[a,b]$ két feltételt ír elő: (a) $[a,b]$ **korlátos és zárt** intervallum, (b) $f$ **korlátos** rajta. Az improprius integrál ezen feltételek lazítása.

Két alapeset:

- **(A) Nem korlátos ÉT:** pl. $\int_1^{+\infty} \frac{1}{x^2}\,dx = 1$ (konvergens), $\int_1^{+\infty} \frac{1}{x}\,dx = +\infty$ (divergens).
- **(B) Nem korlátos integrandus, korlátos ÉT:** pl. $\int_0^1 \frac{1}{\sqrt{x}}\,dx = 2$ (konvergens), $\int_0^1 \frac{1}{x}\,dx = +\infty$ (divergens).

## Értelmezés — nem korlátos intervallum

**Definíció (A).** Legyen $a \in \mathbb{R}$, $f : [a,+\infty) \to \mathbb{R}$ és $f \in R[a,t]$ minden $t > a$-ra. Ha
$$\lim_{t \to +\infty} \int_a^t f(x)\,dx =: I$$
létezik és véges, akkor azt mondjuk, hogy az $\int_a^{+\infty} f$ improprius integrál **konvergens** és értéke $I$. Az integrál **létezik** (vagy $f$ **impropriusan integrálható**), ha konvergens vagy $I = \pm\infty$.

Analóg módon $\int_{-\infty}^a f$. Az $\int_{-\infty}^{+\infty} f$ integrál egy tetszőleges $z$ ponttal hasad:
$$\int_{-\infty}^{+\infty} f := \int_{-\infty}^z f + \int_z^{+\infty} f,$$
ha mindkét tag impropriusan létezik és az összeg értelmezett (a definíció $z$-független).

**Példák:**
- $\int_1^{+\infty} \frac{1}{x^\alpha}\,dx = \frac{1}{\alpha-1}$ ha $\alpha > 1$, $+\infty$ ha $\alpha \leq 1$.
- $\int_{-\infty}^{+\infty} \frac{1}{1+x^2}\,dx = \pi$ (z=0 választással, $\arctan$-nel).

## Értelmezés — nem korlátos integrandus

**Definíció (B).** Legyen $-\infty < a < b < +\infty$, $f : (a,b] \to \mathbb{R}$, $f \in R[t,b]$ minden $t \in (a,b)$-re. Ha
$$\lim_{t \to a+0} \int_t^b f(x)\,dx =: I$$
létezik és véges, $\int_a^b f$ **konvergens**.

Analóg a $b$-ben nem korlátos eset. Mindkét végpontban szinguláris: $z \in (a,b)$ belső ponttal hasad. Belső szinguláris pont ($c \in (a,b)$): hasítás $c$-nél.

**Példák:**
- $\int_0^1 \frac{1}{x^\alpha}\,dx = \frac{1}{1-\alpha}$ ha $\alpha < 1$, $+\infty$ ha $\alpha \geq 1$.
- $\int_{-1}^1 \frac{1}{\sqrt{1-x^2}}\,dx = \pi$ ($\arcsin$-nel).
- $\int_{-\pi/2}^{\pi/2} \tan x\,dx$ **nem létezik** impropriusan ($+\infty - \infty$ alak).
- $\int_0^3 \frac{1}{(x-1)^{2/3}}\,dx = 3 + 3\sqrt[3]{2}$ (belső szingularitás $c=1$-nél).

**Jelölésegyezés:** ha $f \in R[a,b]$, a Riemann- és improprius integrál megegyezik — utóbbi az előbbi kiterjesztése.

## Alapvető tételek

A Riemann-integrál alaptulajdonságai (linearitás, monotonitás, $[a,c] + [c,b]$ additivitás) változatlanul érvényesek konvergens improprius integrálokra.

**Linearitás.** $\int_a^b f$ és $\int_a^b g$ konvergens $\Rightarrow$ $\int_a^b (\lambda_1 f + \lambda_2 g) = \lambda_1 \int_a^b f + \lambda_2 \int_a^b g$.

**Összehasonlító kritériumok.** Legyen $0 \leq f \leq g$ az $(a,b)$-n.
- **Majoráns:** $\int_a^b g$ konvergens $\Rightarrow$ $\int_a^b f$ is konvergens.
- **Minoráns:** $\int_a^b f$ divergens $\Rightarrow$ $\int_a^b g$ is divergens.

**Példa:** $\int_0^{+\infty} e^{-x^2}\,dx$ konvergens, mert $e^{-x^2} \leq e^{-x}$ az $[1,+\infty)$-en és $\int_1^{+\infty} e^{-x}\,dx = 1/e$. Primitívje nem elemi — értéke $\sqrt{\pi}/2$ (később bizonyítjuk).

**Abszolút konvergencia.** $\int_a^b f$ **abszolút konvergens**, ha $\int_a^b |f|$ konvergens. Akkor $\int_a^b f$ is konvergens, és $\left|\int_a^b f\right| \leq \int_a^b |f|$. Megfordítás nem igaz: pl. $\int_1^{+\infty} \frac{\sin x}{x}\,dx$ konvergens, de nem abszolút.

**Newton–Leibniz kiterjesztett.** Ha $f \in R[u,v]$ minden $a<u<v<b$-re és $F$ az $f$ primitív függvénye $(a,b)$-n, akkor $\int_a^b f$ akkor és csak akkor konvergens, ha $\lim_{a+0} F$ és $\lim_{b-0} F$ véges határértékek léteznek, és
$$\int_a^b f = \lim_{b-0} F - \lim_{a+0} F =: [F(x)]_a^b.$$

## Végtelen sorokra integrálkritérium

**Tétel.** Legyen $f : [0,+\infty) \to \mathbb{R}$, $f \searrow$ (monoton csökkenő) és $f \geq 0$. Legyen $a_k := f(k)$. Ekkor
$$\sum_{k=0}^\infty a_k \text{ konvergens} \iff \int_0^{+\infty} f(x)\,dx \text{ konvergens.}$$

Általánosan tetszőleges $M \in \mathbb{Z}$ alsó határral. **Bizonyítás-vázlat:** $f \searrow$ miatt $\int_{k-1}^k f \leq a_{k-1}$ és $a_k \leq \int_k^{k+1} f$ — a részletösszegek és az integrál egymást kétoldalúan közrefogják.

**Példa.** A **hiperharmonikus sor** $\sum_{n=1}^\infty \frac{1}{n^\alpha}$ akkor és csak akkor konvergens, ha $\alpha > 1$ — közvetlen következmény $\int_1^{+\infty} \frac{1}{x^\alpha}\,dx$ konvergenciájából.

## Kapocs

- [[concepts/analii/newton-leibniz-tetel]] — az alaptétel; improprius esetre kiterjesztve
- [[concepts/analii/primitiv-fuggveny]] — Liouville: $e^{-x^2}$-nek nincs elemi primitívje, de improprius integrálja létezik
- [[concepts/analii/hatarozott-integral-ertelmezese]] — Riemann-integrál, amelynek kiterjesztése az improprius
- [[concepts/analii/sikido-terulete]] — nem korlátos síkidom területe ($T(A) = \int_{-\infty}^{+\infty} \frac{1}{1+x^2} = \pi$)
- [[concepts/analii/banach-fixponttetel]] — a 13. ea. témája, jellegében különálló
