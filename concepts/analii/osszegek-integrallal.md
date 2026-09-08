---
tags: [concept]
sources: [01_ea_an_ii_a_b_merged.pdf]
references: ["An II A/B 11. előadás"]
derivation: source
updated: 2026-09-04
---

# Összegek határértéke integrállal

A határozott integrál segítségével bizonyos összegek határértékét könnyen kiszámíthatjuk: az $\frac{1}{n}\sum_{k=1}^n f\!\left(\frac{k}{n}\right)$ alakú összegek $\int_0^1 f(x)\,dx$-hez tartanak. Ez az eszköz lehetővé teszi hatványösszegek aszimptotikájának, ill. a harmonikus sor logaritmikus növekedésének pontos leírását (Euler-állandó).

## Alaptétel

**Tétel.** Ha $f \in R[a, b]$, akkor

$$\lim_{n \to +\infty} \frac{1}{n} \cdot \sum_{k=1}^{n} f\!\left(\frac{k}{n}\right) = \int_0^1 f(x)\; dx.$$

**Bizonyítás.** Legyen $n \in \mathbb{N}^+$, $\tau_n := \left\{\frac{k}{n} \mid k = 0, 1, \ldots, n\right\} \in \mathcal{F}[0, 1]$ és $\xi_n := \left(\frac{1}{n}, \frac{2}{n}, \ldots, \frac{n}{n}\right)$. Ekkor minden $n \in \mathbb{N}^+$-re

$$\sigma(f, \tau_n, \xi_n) = \frac{1}{n} \cdot \sum_{k=1}^{n} f\!\left(\frac{k}{n}\right).$$

Mivel $\|\tau_n\| = \frac{1}{n} \to 0$, ha $n \to +\infty$, ezért a Riemann-kritérium alapján

$$\lim_{n \to +\infty} \frac{1}{n} \sum_{k=1}^{n} f\!\left(\frac{k}{n}\right) = \int_0^1 f(x)\; dx. \qquad \blacksquare$$

## Alkalmazás: $n^\alpha$ aszimptotika

**Példa.** Legyen $\alpha > 0$. Számítsuk ki a

$$\lim_{n \to +\infty} \frac{1^\alpha + 2^\alpha + \cdots + n^\alpha}{n^{\alpha+1}}$$

határértéket.

**Megoldás.** Legyen $f(x) := x^\alpha$ ($x \in [0, 1]$). Ekkor $f \in R[0, 1]$, és

$$\int_0^1 f(x)\; dx = \int_0^1 x^\alpha\; dx = \left[\frac{x^{\alpha+1}}{\alpha+1}\right]_0^1 = \frac{1}{\alpha+1}.$$

Másrészt

$$\frac{1^\alpha + 2^\alpha + \cdots + n^\alpha}{n^{\alpha+1}} = \frac{1}{n} \cdot \left(\left(\frac{1}{n}\right)^\alpha + \left(\frac{2}{n}\right)^\alpha + \cdots + \left(\frac{n}{n}\right)^\alpha\right) = \frac{1}{n} \sum_{k=1}^n f\!\left(\frac{k}{n}\right).$$

Az alaptétel szerint tehát

$$\lim_{n \to +\infty} \frac{1^\alpha + 2^\alpha + \cdots + n^\alpha}{n^{\alpha+1}} = \frac{1}{\alpha+1}. \qquad \blacksquare$$

**Következmény (aszimptotika).** Ebből következik, hogy

$$1^\alpha + 2^\alpha + \cdots + n^\alpha \sim \frac{1}{\alpha+1} n^{\alpha+1} \qquad (n \to +\infty),$$

vagyis az összeg $n^{\alpha+1}$ **nagyságrendű**.

**Megjegyzés.** $\alpha = 1, 2, 3$ esetén zárt alak is ismert ($\frac{n(n+1)}{2}$, $\frac{n(n+1)(2n+1)}{6}$, $\left(\frac{n(n+1)}{2}\right)^2$). Más $\alpha$-kra (pl. $\alpha = \frac{1}{2}$) zárt alak nincs, mégis megkapjuk a nagyságrend pontos leírását.

## Alkalmazás: a harmonikus sor becslése és az Euler-állandó

A harmonikus sor divergens: $\sum_{n=1}^{+\infty} \frac{1}{n} = +\infty$, azaz a részletösszegek $H_n := 1 + \frac{1}{2} + \frac{1}{3} + \cdots + \frac{1}{n} \to +\infty$.

### Logaritmikus becslés

**Állítás.**

$$\ln n < H_n < \ln n + 1 \qquad (2 \leq n \in \mathbb{N}).$$

**Bizonyítás.**

Legyen $f(x) := \frac{1}{x}$ ($x \geq 1$), ekkor $f \downarrow$ az $[1, +\infty)$-en, ezért $f(x) < f(k) = \frac{1}{k}$ ha $x \in (k, k+1)$.

*Alsó becslés:* $f(x) < \frac{1}{k}$ minden $x \in (k, k+1)$-re ($k = 1, 2, \ldots, n$), ezért

$$\frac{1}{k} > \int_k^{k+1} \frac{1}{x}\; dx,$$

összegzés után $H_n > \int_1^{n+1} \frac{1}{x}\; dx = \ln(n+1) > \ln n$. $\checkmark$

*Felső becslés:* Mivel $f \downarrow$, ezért $\frac{1}{k+1} = f(k+1) < f(x)$ minden $x \in (k, k+1)$-re, tehát

$$\frac{1}{k+1} < \int_k^{k+1} \frac{1}{x}\; dx.$$

Összegezve $k = 1, \ldots, n-1$-re:

$$\frac{1}{2} + \frac{1}{3} + \cdots + \frac{1}{n} < \int_1^n \frac{1}{x}\; dx = \ln n,$$

ezért $H_n = 1 + \frac{1}{2} + \cdots + \frac{1}{n} < 1 + \ln n$. $\checkmark$ $\blacksquare$

### Az Euler-állandó

A becslésekből könnyen látható, hogy

$$0 < 1 + \frac{1}{2} + \frac{1}{3} + \cdots + \frac{1}{n} - \ln n \qquad (2 \leq n \in \mathbb{N}).$$

Megmutatható, hogy a $\left(\sum_{k=1}^n \frac{1}{k} - \ln n\right)$ sorozat **monoton csökkenő** és alulról korlátos, tehát konvergál. A határértéke az ún. **Euler-állandó** (más néven Euler–Mascheroni-állandó):

$$\gamma := \lim_{n \to +\infty} \left(\sum_{k=1}^n \frac{1}{k} - \ln n\right) \approx 0{,}577\ldots$$

(Régóta megoldatlan probléma, hogy $\gamma$ racionális-e vagy sem.)

A fentiek alapján

$$H_n = 1 + \frac{1}{2} + \frac{1}{3} + \cdots + \frac{1}{n} = \ln n + \gamma + \varepsilon_n \qquad (2 \leq n \in \mathbb{N}),$$

ahol $\varepsilon_n \searrow 0$, ha $n \to +\infty$. Más szóval:

$$1 + \frac{1}{2} + \frac{1}{3} + \cdots + \frac{1}{n} \sim \ln n \qquad (n \to +\infty).$$

## Kapocs

- [[concepts/analii/hatarozott-integral-ertelmezese]] — Riemann-féle közelítő összeg definíciója, amelyre az alaptétel épül
- [[concepts/analii/integralhato-fuggvenyek]] — Riemann-kritérium: $\|\tau\| \to 0 \Rightarrow \sigma \to \int f$
- [[concepts/analii/monoton-fuggvenyek-integralhatasaga]] — $\frac{1}{x}$ monoton csökkenő, ezért integrálható; a becslés alapja
- [[concepts/analii/newton-leibniz-tetel]] — az integrál kiszámítása: $\int_1^n \frac{1}{x}\,dx = \ln n$
- [[concepts/analii/alapintegralok]] — $\int x^\alpha\,dx$ és $\int \frac{1}{x}\,dx$ alapintegrálok
