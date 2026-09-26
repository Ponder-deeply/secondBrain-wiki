---
title: Analízis II — Integrál képletgyűjtemény
---

# Analízis II — Integrál képletgyűjtemény

## 1. Alapintegrálok ($+c$ minden sorban)

| $f(x)$ | $\int f$ | ÉT |
|---|---|---|
| $x^\alpha$, $\alpha\neq-1$ | $\dfrac{x^{\alpha+1}}{\alpha+1}$ | $(0,\infty)$; $\alpha\in\mathbb N$: $\mathbb R$ |
| $1/x$ | $\ln x$ / $\ln(-x)$ | $(0,\infty)$ / $(-\infty,0)$ |
| $e^x$ | $e^x$ | $\mathbb R$ |
| $a^x$ ($a>0,a\neq1$) | $a^x/\ln a$ | $\mathbb R$ |
| $\sin x$ | $-\cos x$ | $\mathbb R$ |
| $\cos x$ | $\sin x$ | $\mathbb R$ |
| $1/\cos^2 x$ | $\operatorname{tg} x$ | $(-\pi/2,\pi/2)$ |
| $1/\sin^2 x$ | $-\operatorname{ctg} x$ | $(0,\pi)$ |
| $1/(1+x^2)$ | $\operatorname{arctg} x$ | $\mathbb R$ |
| $1/\sqrt{1-x^2}$ | $\arcsin x$ | $(-1,1)$ |
| $\operatorname{sh} x$ | $\operatorname{ch} x$ | $\mathbb R$ |
| $\operatorname{ch} x$ | $\operatorname{sh} x$ | $\mathbb R$ |
| $1/\operatorname{ch}^2 x$ | $\operatorname{th} x$ | $\mathbb R$ |

Speciális: $\int\sqrt x\,dx=\tfrac23 x^{3/2}$, $\int\tfrac1{\sqrt x}dx=2\sqrt x$.

## 2. Határozatlan integrál — szabályok

**Linearitás.** $\int(\alpha f+\beta g)=\alpha\int f+\beta\int g$.

**I. helyettesítés** ($g\in D(I)$, $\mathcal R_g\subset J$, $F\in\int f$):
$$\int f(g(x))\,g'(x)\,dx = F(g(x))+c.$$

Speciális esetek:
$$\int \frac{f'(x)}{f(x)}dx=\ln f(x)+c\ (f>0);\quad \int f^\alpha f'\,dx=\frac{f^{\alpha+1}}{\alpha+1}+c\ (\alpha\neq-1);\quad \int f(ax+b)\,dx=\frac{F(ax+b)}{a}+c.$$

**II. helyettesítés** ($g:J\to I$ bijekció, $g\in D$, $g'\neq0$):
$$\int f(x)\,dx = \int f(g(t))\,g'(t)\,dt\,\bigg|_{t=g^{-1}(x)}.$$

**Parciális integrálás** ($f,g\in D(I)$):
$$\int f g'\,dx = fg - \int f' g\,dx.$$

## 3. Riemann-integrál — alaptulajdonságok

Felosztás $\tau\in\mathcal F[a,b]$; $s(f,\tau)=\sum m_i\Delta x_i$, $S(f,\tau)=\sum M_i\Delta x_i$.
$$I_*(f)=\sup_\tau s(f,\tau),\quad I^*(f)=\inf_\tau S(f,\tau);\quad f\in R[a,b]\iff I_*(f)=I^*(f)=:\int_a^b f.$$

Bármely $\tau_1,\tau_2$: $s(f,\tau_1)\le S(f,\tau_2)$.

**Elégséges feltételek.** $C[a,b]\subset R[a,b]$; monoton $[a,b]\to\mathbb R$ $\in R[a,b]$.

**Műveletek $R[a,b]$-n.** $f,g\in R[a,b]\Rightarrow \alpha f+\beta g,\ f\cdot g,\ |f|\in R[a,b]$; $|1/f|$ alulról korlátos $\Rightarrow 1/f\in R$.

**Linearitás:** $\int_a^b(\alpha f+\beta g)=\alpha\int_a^b f+\beta\int_a^b g$.
**Intervallum-additivitás:** $\int_a^b f=\int_a^c f+\int_c^b f$ ($a<c<b$).
**Monotonitás:** $f\le g\Rightarrow \int_a^b f\le\int_a^b g$.
**Háromszög:** $\bigl|\int_a^b f\bigr|\le\int_a^b|f|\le M(b-a)$ ahol $M=\sup|f|$.
**Konvenció:** $\int_a^a f:=0$, $\int_b^a f:=-\int_a^b f$.
**Véges sok ponton való módosítás** nem változtat sem integrálhatóságon, sem értéken.

## 4. Integrálfüggvény, Newton–Leibniz

$$F(x):=\int_a^x f\quad(x\in[a,b],\ f\in R[a,b]).$$
$F$ Lipschitz $[a,b]$-n. Ha $f$ folytonos $x_0$-ban, akkor $F'(x_0)=f(x_0)$. Speciálisan $f\in C[a,b]\Rightarrow F\in C^1$, $F'=f$ — primitív függvény létezik.

**Newton–Leibniz.** $f\in R[a,b]$ + $\exists$ primitív $F$:
$$\int_a^b f(x)\,dx = F(b)-F(a) = [F(x)]_a^b.$$

## 5. Határozott integrál technikák

**Helyettesítés** ($f\in C[a,b]$, $g\in C^1[\alpha,\beta]$, $g:[\alpha,\beta]\to[a,b]$):
$$\int_{g(\alpha)}^{g(\beta)} f = \int_\alpha^\beta f(g(t))\,g'(t)\,dt.$$
Határokat is transzformálni — visszahelyettesítés nem kell.

**Parciális** ($f,g\in D[a,b]$, $f',g'\in R[a,b]$):
$$\int_a^b f g'\,dx = [fg]_a^b - \int_a^b f' g\,dx.$$

## 6. Integrál-középérték

$f\in C[a,b]\Rightarrow \exists\,\xi\in[a,b]$:
$$\int_a^b f = f(\xi)\,(b-a),\qquad \bar f := \frac{1}{b-a}\int_a^b f.$$
Általános súlyozott alak: $g\ge0$, $g\in R[a,b]\Rightarrow \int_a^b fg=f(\xi)\int_a^b g$.

## 7. Improprius integrál

**(A) Nem korlátos intervallum.** $f\in R[a,t]\ \forall t>a$:
$$\int_a^{+\infty} f := \lim_{t\to+\infty}\int_a^t f,\quad \text{konv., ha véges.}$$
Analóg $\int_{-\infty}^a$. Kétoldali: $\int_{-\infty}^{+\infty} f=\int_{-\infty}^z f+\int_z^{+\infty} f$ ($z$ tetszőleges, ha mindkettő konv.).

**(B) Nem korlátos integrandus** ($f:(a,b]\to\mathbb R$, $f\in R[t,b]\ \forall t\in(a,b)$):
$$\int_a^b f := \lim_{t\to a+0}\int_t^b f.$$
Belső szingularitás $c\in(a,b)$: hasítás $c$-nél.

**Newton–Leibniz kiterjesztett.** $f\in R[u,v]\ \forall a<u<v<b$, $F$ primitív $(a,b)$-n:
$$\int_a^b f = \lim_{b-0} F - \lim_{a+0} F.$$

**Nevezetes:**
$$\int_1^{+\infty}\!\!\!\frac{dx}{x^\alpha}=\frac{1}{\alpha-1}\ (\alpha>1),\ +\infty\ (\alpha\le1);\quad \int_0^1\!\!\frac{dx}{x^\alpha}=\frac{1}{1-\alpha}\ (\alpha<1),\ +\infty\ (\alpha\ge1).$$
$$\int_{-\infty}^{+\infty}\!\!\frac{dx}{1+x^2}=\pi,\quad \int_{-1}^{1}\!\!\frac{dx}{\sqrt{1-x^2}}=\pi,\quad \int_0^{+\infty} e^{-x^2}dx=\frac{\sqrt\pi}{2}.$$

**Konvergencia-kritériumok.** $0\le f\le g$ $(a,b)$-n:
$\int g$ konv. $\Rightarrow\int f$ konv.; $\int f$ div. $\Rightarrow\int g$ div.
**Abszolút konvergens** ($\int|f|$ konv.) $\Rightarrow$ konvergens, $\left|\int f\right|\le\int|f|$.

**Integrálkritérium sorokra.** $f\searrow$, $f\ge0$: $\sum_{k=0}^\infty f(k)$ konv. $\iff \int_0^{+\infty} f$ konv.
Pl. $\sum 1/n^\alpha$ konv. $\iff \alpha>1$.

## 8. Geometriai alkalmazások

| Mennyiség | Képlet | Feltétel |
|---|---|---|
| Görbe alatti terület ($f\ge0$) | $\int_a^b f$ | $f\in R[a,b]$ |
| Két görbe közötti terület | $\int_a^b (g-f)$ | $f\le g$, $f,g\in R[a,b]$ |
| Forgástest térfogata ($x$-tengely) | $\pi\int_a^b f^2$ | $0\le f\in R[a,b]$ |
| Ívhossz | $\int_a^b\sqrt{1+(f')^2}\,dx$ | $f\in C^1[a,b]$ |
| Forgásfelület felszíne | $2\pi\int_a^b f\sqrt{1+(f')^2}\,dx$ | $0\le f\in C^1[a,b]$ |

**Nevezetes értékek.** Körlap $\pi R^2$; gömb $V=\tfrac{4\pi R^3}{3}$, $T=4\pi R^2$; kör kerülete $2\pi R$ ($\int_{-R}^{R}\frac{dx}{\sqrt{1-(x/R)^2}}$).

## 9. Sorok és integrál összehasonlítás

$f\searrow,\ f\ge0$ $[M,\infty)$-n:
$$\sum_{k=M+1}^N f(k)\ \le\ \int_M^N f(x)\,dx\ \le\ \sum_{k=M}^{N-1} f(k).$$
Részletösszegek konvergenciája és $\int$ konvergenciája ekvivalens.
