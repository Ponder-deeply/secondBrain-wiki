---
tags: [concept]
sources: [01_ea_an_ii_a_b_merged.pdf]
references: ["An II A/B 10. előadás"]
derivation: source
updated: 2026-09-04
---

# Newton–Leibniz-tétel

A határozott integrál és a primitív függvény összekapcsolásának alaptétele: ha $f \in R[a,b]$ és van primitív függvénye $[a,b]$-n, akkor az integrál értéke pontosan a primitív függvény értékkülönbsége.

## A tétel

**Newton–Leibniz-tétel.** Ha $f \in R[a,b]$ és $f$-nek van primitív függvénye az $[a,b]$ intervallumon, akkor

$$\int_a^b f(x)\, dx = F(b) - F(a) =: \bigl[F(x)\bigr]_a^b,$$

ahol $F$ az $f$ függvény egy (tetszőleges) primitív függvénye.

## Bizonyítás

Legyen $\tau = \{a = x_0 < x_1 < \cdots < x_n = b\} \in \mathcal{F}[a,b]$ tetszőleges felosztás. A Lagrange-középértéktétel szerint minden $i = 1, \ldots, n$ indexre $\exists\, \xi_i \in (x_{i-1}, x_i)$:

$$F(x_i) - F(x_{i-1}) = F'(\xi_i) \cdot (x_i - x_{i-1}) = f(\xi_i) \cdot (x_i - x_{i-1}).$$

Összeadva $i = 1, \ldots, n$-re, a bal oldal teleszkopikus összeg, kiesik minden tag kivéve $F(x_n) = F(b)$ és $F(x_0) = F(a)$:

$$F(b) - F(a) = \sum_{i=1}^n f(\xi_i)\cdot(x_i - x_{i-1}) = \sigma(f, \tau, \xi),$$

ahol $\xi := (\xi_1, \ldots, \xi_n)$. Mivel $\inf_{[x_{i-1},x_i]} f \leq f(\xi_i) \leq \sup_{[x_{i-1},x_i]} f$, ezért

$$s(f, \tau) \leq \sigma(f, \tau, \xi) = F(b) - F(a) \leq S(f, \tau, \xi) = S(f,\tau).$$

Következésképpen

$$I_*(f) = \sup_{\tau \in \mathcal{F}[a,b]} s(f,\tau) \leq F(b)-F(a) \leq \inf_{\tau \in \mathcal{F}[a,b]} S(f,\tau) = I^*(f).$$

Mivel $f \in R[a,b]$, ezért $I_*(f) = I^*(f) = \int_a^b f$. Így

$$F(b) - F(a) = \int_a^b f(x)\, dx. \qquad \blacksquare$$

## Megjegyzések

- A tétel **két feltétele egymástól független** (egyikből nem következik a másik):
  - $f \in R[a,b]$, de $f$-nek nincs primitív függvénye $[a,b]$-n: pl. $f(x) := x^2 \cdot \sin\frac{1}{x^2}$ ($x \neq 0$), $f(0) := 0$ — $f$ korlátos, nem $\in R[0,1]$; ennek folytatása nem egyszerű.
  - $f$-nek van primitív függvénye, de $f \notin R[a,b]$: pl. az $F'(x) = f(x)$ ahol $f \notin R[0,1]$ — Volterra-függvény.
- Ha $f \in C[a,b]$, mindkét feltétel teljesül (folytonosság $\Rightarrow$ integrálható + van primitív függvénye az [[concepts/analii/integralfuggveny|integrálfüggvényen]] keresztül).
- **Alkalmazás ($\pi$ irracionalitása).** A Newton–Leibniz-tétel alapvető eszköze annak bizonyításában, hogy $\pi \notin \mathbb{Q}$ (Niven, 1947): az $\int_0^\pi f(x)\sin x\, dx$ egy egész szám és $(0,1)$ közé esik, ami ellentmondás.
- **Alkalmazás (példa).** $\int_0^\pi \sin x\, dx = [-\cos x]_0^\pi = (-\cos\pi) - (-\cos 0) = 2.$

## Kapocs

- [[concepts/analii/integralfuggveny]] — az integrálfüggvény deriválhatóságának tétele adja az elégséges feltételt
- [[concepts/analii/primitiv-fuggveny]] — primitív függvény definíciója; $[a,b]$-n vett fogalom
- [[concepts/analii/hatarozott-integral-ertelmezese]] — Riemann-integrálhatóság ($R[a,b]$) definíciója
- [[concepts/analii/kozeptertekek]] — a bizonyításban a Lagrange-középértéktételt alkalmazzuk
- [[concepts/analii/folytonos-fuggvenyek-integralhatasaga]] — $C[a,b] \subset R[a,b]$; folytonos $\Rightarrow$ integrálható
- [[concepts/analii/hatarozott-integral-parcialisintegrals]] — parciális integrálás határozott integrálra, N–L alkalmazása
- [[concepts/analii/hatarozott-integral-helyettesites]] — helyettesítéssel való integrálás határozott integrálra
