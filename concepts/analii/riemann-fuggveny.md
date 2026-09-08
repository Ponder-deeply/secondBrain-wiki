---
tags: [concept]
sources: [01_ea_an_ii_a_b_merged.pdf]
references: ["An II A/B 8. előadás"]
derivation: source
updated: 2026-09-04
---

# A Riemann-függvény

A Riemann-függvény egy klasszikus példa: integrálható, de végtelen sok helyen nem folytonos. Megmutatja, hogy az integrálhatóság nem követeli meg a folytonosságot.

## Definíció

$$R(x) := \begin{cases} \frac{1}{q}, & \text{ha } x = \frac{p}{q},\ p \in \mathbb{Z} \setminus \{0\},\ q \in \mathbb{N}^+,\ (p,q) = 1 \\ 1, & \text{ha } x = 0 \\ 0, & \text{ha } x \in \mathbb{R} \setminus \mathbb{Q} \end{cases}$$

## Tulajdonságok

- $R$ periodikus és periódusa 1.
- $\forall a \in \mathbb{R}$ esetén $\lim_{x \to a} R(x) = 0$.
- $R$ minden irracionális helyen folytonos.
- A racionális pontok $R$ megszüntethető szakadási helyei.

## Integrálhatóság

**Tétel.** $R \in R[0,1]$ és $\displaystyle\int_0^1 R(x)\,dx = 0$.

**Bizonyítás.** Tetszőleges $\tau \in \mathcal{F}[0,1]$ felosztás esetén $s(R,\tau) = 0$ (minden intervallumon van irracionális szám), tehát $I_*(R) = 0$.

Azt kell megmutatni, hogy $I^*(R) = 0$, azaz

$$(*)\quad \forall\varepsilon > 0\ \exists\tau \in \mathcal{F}[0,1]:\ S(R,\tau) < \varepsilon.$$

Adott $\varepsilon > 0$-hoz legyen $m \in \mathbb{N}^+$ olyan, hogy $\frac{3}{m} < \varepsilon$. Legyen
$$\tau = \{0 = x_0 < x_1 < \cdots < x_n = 1\} \in \mathcal{F}[0,1],\quad \|\tau\| < \frac{1}{m \cdot N},$$
ahol $N$ az $[0,1]$-beli azon pontok száma, ahol $R(x) > \frac{1}{m}$ (véges sok ilyen van). Ekkor:

- Az $i$ indexek, amelyekre $[x_{i-1}, x_i]$ tartalmaz egy ilyen pontot: legfeljebb $2N$ db. Az ott lévő $M_i(x_i - x_{i-1}) \leq 1 \cdot \frac{1}{m \cdot N}$ tagok összege legfeljebb $2N \cdot \frac{1}{m \cdot N} = \frac{2}{m}$.
- A többi tagra $M_i \leq \frac{1}{m}$, összegük $\leq \frac{1}{m} \cdot 1 = \frac{1}{m}$.

Tehát $S(R,\tau) \leq \frac{2}{m} + \frac{1}{m} = \frac{3}{m} < \varepsilon$. $\blacksquare$

## Kapocs

- [[concepts/analii/riemann-integral-tulajdonsagok]] — az integrál véges sok pont megváltoztatásával szemben érzéketlen
- [[concepts/analii/muvelet-integralhato-fuggvenyekkel]] — műveletek integrálható függvényekkel
