---
tags: [concept]
sources: [01_ea_an_ii_a_b_merged.pdf]
references: ["An II A/B 9. előadás"]
derivation: source
updated: 2026-09-04
---

# Folytonos függvények integrálhatósága

A folytonosság erősebb tulajdonság az integrálhatóságnál: minden $[a,b]$-n folytonos függvény Riemann-integrálható.

## Főtétel

**Tétel.** Ha $f$ függvény **folytonos** az $[a,b]$ intervallumon, akkor **integrálható** $[a,b]$-n:
$$C[a,b] \subset R[a,b].$$

**Bizonyítás.** Megmutatjuk, hogy $\forall f \in C[a,b]$ függvényre teljesül:
$$\forall \varepsilon > 0\ \exists \tau \in \mathcal{F}[a,b]: \Omega(f,\tau) < \varepsilon.$$

Mivel $-\infty < a < b < +\infty$ és $f \in C[a,b]$, a **Heine-tétel** alapján $f$ egyenletesen folytonos $[a,b]$-n. Tehát $\exists \delta > 0$:

$$\forall x, y \in [a,b],\ |x-y| < \delta \Rightarrow |f(x)-f(y)| < \frac{\varepsilon}{b-a}.$$

Legyen $\tau \in \mathcal{F}[a,b]$ egy olyan felosztás, amelyre $\|\tau\| < \delta$. Ekkor minden $i$-re és $x, y \in [x_{i-1}, x_i]$-re $|x-y| < \delta$, ezért $|f(x)-f(y)| < \frac{\varepsilon}{b-a}$, amiből:

$$M_i - m_i = \sup_{[x_{i-1},x_i]} f - \inf_{[x_{i-1},x_i]} f \leq \frac{\varepsilon}{b-a}.$$

Tehát:
$$\Omega(f,\tau) = \sum_{i=1}^n (M_i - m_i)(x_i - x_{i-1}) \leq \frac{\varepsilon}{b-a} \cdot \sum_{i=1}^n (x_i - x_{i-1}) = \frac{\varepsilon}{b-a} \cdot (b-a) = \varepsilon. \qquad \blacksquare$$

## Összefoglalás

$$C[a,b] \subset R[a,b], \qquad \text{és a befoglalás valódi.}$$

(A Riemann-függvény $R \in R[a,b]$, de $R \notin C[a,b]$.)

## Kapocs

- [[concepts/analii/egyenletes-folytonossag]] — Heine-tétel: $f \in C[a,b] \Rightarrow f$ egyenletesen folytonos
- [[concepts/analii/integralhato-fuggvenyek]] — Darboux-kritérium (szükséges és elégséges)
- [[concepts/analii/monoton-fuggvenyek-integralhatasaga]] — monoton $\Rightarrow$ integrálható (más bizonyítás)
- [[concepts/analii/riemann-fuggveny]] — ellenpélda: $R \in R[0,1]$, de $R \notin C[0,1]$
