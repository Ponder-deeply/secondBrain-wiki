---
tags: [concept]
sources: [01_ea_an_ii_a_b_merged.pdf]
references: ["An II A/B 7. előadás"]
derivation: source
updated: 2026-09-04
---

# Integrálható függvények — ekvivalens jellemzések

Az integrálhatóság $I_*(f) = I^*(f)$ definíciója helyett három ekvivalens, praktikusabb kritérium áll rendelkezésre.

## Oszcillációs összeg

$$\Omega(f,\tau) := S(f,\tau) - s(f,\tau) = \sum_{i=1}^n (M_i - m_i)(x_i - x_{i-1}).$$

Ez méri, mennyire „ingadozik" $f$ az egyes részintervallumokon. Minél kisebb $\Omega$, annál pontosabb a közelítés.

## Darboux-kritérium

**Tétel.** $f \in R[a,b]$ $\iff$ $\forall \varepsilon > 0\ \exists \tau \in \mathcal{F}[a,b]: \Omega(f,\tau) < \varepsilon$.

**Bizonyítás.** ($\Rightarrow$) Ha $f \in R[a,b]$, akkor $I_*(f) = I^*(f) =: I$. Adott $\varepsilon > 0$-hoz léteznek $\tau_1, \tau_2$ felosztások, melyekre $I - s(f,\tau_1) < \varepsilon/2$ és $S(f,\tau_2) - I < \varepsilon/2$. Legyen $\tau = \tau_1 \cup \tau_2$. Ekkor:
$$\Omega(f,\tau) = S(f,\tau) - s(f,\tau) \leq S(f,\tau_2) - s(f,\tau_1) < \varepsilon.$$

($\Leftarrow$) Ha $\forall \varepsilon > 0\ \exists \tau: \Omega(f,\tau) < \varepsilon$, akkor
$$0 \leq I^*(f) - I_*(f) \leq S(f,\tau) - s(f,\tau) = \Omega(f,\tau) < \varepsilon,$$
tehát $I^*(f) = I_*(f)$, azaz $f \in R[a,b]$. $\blacksquare$

## Sorozatos kritérium

$f \in R[a,b]$ és $\int_a^b f = I$ $\iff$ $\exists (\tau_n)$ felosztássorozat: $s(f,\tau_n) \to I$ és $S(f,\tau_n) \to I$.

## Riemann-féle közelítő összeg

Legyen $\tau \in \mathcal{F}[a,b]$ és $\xi_i \in [x_{i-1}, x_i]$ ($i = 1,\ldots,n$) tetszőleges közbülső pontok. A

$$\sigma(f,\tau,\xi) := \sum_{i=1}^n f(\xi_i)(x_i - x_{i-1})$$

összeget **Riemann-féle közelítő összegnek** nevezzük.

**Riemann-kritérium.** $f \in R[a,b]$ és $\int_a^b f = I$ $\iff$ $\forall \varepsilon > 0\ \exists \delta > 0$: ha $\|\tau\| < \delta$, akkor $|\sigma(f,\tau,\xi) - I| < \varepsilon$ minden $\xi$ választásra.

## Ellenpéldák és példák

**Dirichlet-függvény** (nem integrálható):
$$D(x) = \begin{cases} 1, & x \in \mathbb{Q} \\ 0, & x \notin \mathbb{Q} \end{cases}$$
Minden felosztáshoz $s(D,\tau) = 0$ és $S(D,\tau) = 1$, tehát $I_*(D) = 0 \neq 1 = I^*(D)$, így $D \notin R[0,1]$.

**Geometriai felosztás** ($\int_1^2 \frac{1}{x^2}\,dx = \frac{1}{2}$): $x_k = q^k$ ($q = 2^{1/n}$) felosztással igazolható.

## Kapocs

- [[concepts/analii/hatarozott-integral-ertelmezese]] — definíció, Darboux-integrál, finomítási tétel
- [[concepts/analii/riemann-fuggveny]] — Riemann-függvény: integrálható, de végtelen sok szakadással
- [[concepts/analii/monoton-fuggvenyek-integralhatasaga]] — monoton $\Rightarrow$ integrálható
- [[concepts/analii/folytonos-fuggvenyek-integralhatasaga]] — folytonos $\Rightarrow$ integrálható
