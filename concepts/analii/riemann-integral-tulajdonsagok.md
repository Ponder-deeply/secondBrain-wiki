---
tags: [concept]
sources: [01_ea_an_ii_a_b_merged.pdf]
references: ["An II A/B 8. előadás"]
derivation: source
updated: 2026-09-04
---

# A Riemann-integrál további tulajdonságai

A Riemann-integrál „érzéketlen" a függvény véges halmazon való viselkedésére: véges sok pont megváltoztatása nem befolyásolja az integrálhatóságot, sem az integrál értékét.

## Függvényértékek megváltoztatása véges sok helyen

**Tétel.** T.f.h. $f, g \in K[a,b]$. Ha $f \in R[a,b]$ és az
$$A := \{x \in [a,b] \mid f(x) \neq g(x)\}$$
halmaz **véges**, akkor $g \in R[a,b]$ és
$$\int_a^b g = \int_a^b f.$$

**Bizonyítás** (egy pontban való különbözés esete). Legyen $f \in R[a,b]$, és $f(\alpha) \neq g(\alpha)$ egyetlen $\alpha \in [a,b]$ pontban. Legyen $h := g - f$, azaz
$$h(x) = \begin{cases} 0, & x \in [a,b],\ x \neq \alpha \\ g(\alpha) - f(\alpha), & x = \alpha \end{cases} \quad \text{és} \quad h(\alpha) \neq 0.$$
Elég megmutatni, hogy $h \in R[a,b]$ és $\int_a^b h = 0$ (az integrál additivitásából).

Legyen $\varepsilon > 0$. Legyen $\tau \in \mathcal{F}[a,b]$: $\alpha \in \tau$ és $\|\tau\| < \frac{\varepsilon}{2|h(\alpha)|}$. Ekkor $\alpha$ legfeljebb két részintervallumhoz tartozik.

- Ahol $h \equiv 0$: ott $\sup h = \inf h = 0$.
- A két $\alpha$-t tartalmazó intervallumon: $S(h,\tau) < 2|h(\alpha)| \cdot \frac{\varepsilon}{2|h(\alpha)|} = \varepsilon$.

Másrészt $\forall \tau \in \mathcal{F}[a,b]$ esetén $s(h,\tau) = 0$, tehát $I_*(h) = 0$. Így $h \in R[a,b]$ és $\int_a^b h = 0$. $\blacksquare$

## Kiterjesztés: véges sok pontban értelmezetlen függvények

**Megjegyzés.** Az integrálhatóság fogalma és az integrál értéke kiterjeszthető olyan függvényekre, amelyek az $[a,b]$ intervallum véges sok pontjában nincsenek értelmezve.

Legyen $f$ egy ilyen függvény. Ha $\exists\, g \in R[a,b]$ : $g(x) = f(x)$ legfeljebb véges sok $[a,b]$-beli pont kivételével, akkor azt mondjuk, hogy $f$ **integrálható**, és

$$\int_a^b f := \int_a^b g.$$

Ha ilyen $g$ nem létezik, akkor $f$ **nem integrálható**. Az előző tételből következik, hogy az integrálhatóság ténye és az integrál értéke független a $g$ függvény megválasztásától.

## Kapocs

- [[concepts/analii/riemann-fuggveny]] — a Riemann-függvény mint példa (integrálható, végtelen sok szakadással)
- [[concepts/analii/muvelet-integralhato-fuggvenyekkel]] — algebrai műveletek $R[a,b]$-n
- [[concepts/analii/integral-egyenlotlensegek]] — integrálegyenlőtlenségek
