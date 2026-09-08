---
tags: [concept]
sources: [01_ea_an_ii_a_b_merged.pdf]
references: ["An II A/B 8. előadás"]
derivation: source
updated: 2026-09-04
---

# Műveletek integrálható függvényekkel

Integrálható függvényeken végzett algebrai műveletek megőrzik az integrálhatóságot, és az integrál lineárisan viselkedik.

## Tétel

T.f.h. $f, g \in R[a,b]$ és $\lambda \in \mathbb{R}$. Ekkor:

**1°** $\lambda \cdot f \in R[a,b]$ és $\displaystyle\int_a^b (\lambda \cdot f) = \lambda \cdot \int_a^b f$

**2°** $f + g \in R[a,b]$ és $\displaystyle\int_a^b (f+g) = \int_a^b f + \int_a^b g$

**3°** $f \cdot g \in R[a,b]$

**4°** Ha $|g(x)| \geq m > 0$ ($\forall x \in [a,b]$), akkor $\dfrac{f}{g} \in R[a,b]$

## Bizonyítás

**1°** $\lambda \geq 0$ esetén $s(\lambda f, \tau) = \lambda \cdot s(f,\tau)$ és $S(\lambda f, \tau) = \lambda \cdot S(f,\tau)$. Ha $\lambda < 0$, akkor $s(\lambda f, \tau) = \lambda \cdot S(f,\tau)$ és $S(\lambda f, \tau) = \lambda \cdot s(f,\tau)$.

**2°** Legyen $\tau = \{x_0 = a < x_1 < \cdots < x_n = b\} \in \mathcal{F}[a,b]$, és legyenek
$$f_i = \inf_{[x_{i-1},x_i]} f,\quad F_i = \sup_{[x_{i-1},x_i]} f,\quad g_i = \inf_{[x_{i-1},x_i]} g,\quad G_i = \sup_{[x_{i-1},x_i]} g.$$
Mivel $f_i + g_i \leq f(x) + g(x) \leq F_i + G_i$, ezért
$$f_i + g_i \leq \inf_{[x_{i-1},x_i]}(f+g) \leq \sup_{[x_{i-1},x_i]}(f+g) \leq F_i + G_i,$$
amiből $(x_i - x_{i-1})$-gyel szorozva és összegezve:
$$s(f,\tau) + s(g,\tau) \leq s(f+g,\tau) \leq S(f+g,\tau) \leq S(f,\tau) + S(g,\tau).$$
Ebből $\tau_1, \tau_2 \in \mathcal{F}[a,b]$ és $\tau = \tau_1 \cup \tau_2$ finomítással:
$$I_*(f) + I_*(g) \leq I_*(f+g) \leq I^*(f+g) \leq I^*(f) + I^*(g).$$
Mivel $f, g \in R[a,b]$, ezért $I_*(f+g) = I^*(f+g)$, tehát $f + g \in R[a,b]$ és az integrál additív.

**3°** (i) $f, g \geq 0$ esetén az oszcillációs összegek alkalmazásával:
$$\Omega(f \cdot g, \tau) \leq M \cdot (\Omega(g,\tau) + \Omega(f,\tau)),$$
ahol $M = \sup|f|, \sup|g|$ korlátból adódik. Mivel $f, g \in R[a,b]$, $\Omega(f,\tau), \Omega(g,\tau) < \varepsilon$ elérhető, ezért $f \cdot g \in R[a,b]$.

(ii) Általános eset: $m_f = \inf_{[a,b]} f$, $m_g = \inf_{[a,b]} g$. Ekkor $f - m_f \geq 0$ és $g - m_g \geq 0$, és
$$(f - m_f)(g - m_g) = f \cdot g - m_g \cdot f - m_f \cdot g + m_f \cdot m_g \in R[a,b],$$
amiből $f \cdot g \in R[a,b]$ következik.

**4°** Elég $\frac{1}{g} \in R[a,b]$-t igazolni. Tetszőleges $x, y \in [x_{i-1}, x_i]$ pontban:
$$\left|\frac{1}{g(x)} - \frac{1}{g(y)}\right| = \frac{|g(y) - g(x)|}{|g(x) \cdot g(y)|} \leq \frac{|g(y) - g(x)|}{m^2},$$
ezért $\Omega\!\left(\frac{1}{g},\tau\right) \leq \frac{1}{m^2} \cdot \Omega(g,\tau)$. Mivel $g \in R[a,b]$, ezért $\frac{1}{g} \in R[a,b]$. $\blacksquare$

## Kapocs

- [[concepts/analii/riemann-fuggveny]] — példa integrálható függvényre
- [[concepts/analii/riemann-integral-tulajdonsagok]] — további tulajdonságok
