---
tags: [concept]
sources: [03_gyak_An_III_2022_tavasz.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-10-21
---

# Függvénysorozat konvergenciája $C[a,b]$-ben

Az $(f_k)\subset C[a,b]$ függvénysorozat konvergenciája a $\|\cdot\|_p$ normákban ($1\le p\le\infty$), kapcsolata a pontonkénti és az egyenletes konvergenciával, és a gyakorlatokon használt számolási módszer.

## Tartalom

### Definíciók

- $f_k\to f$ a $(C[a,b],\|\cdot\|_p)$ térben, ha $r_k:=\|f_k-f\|_p\to0$.
- $p=\infty$: $\|f_k-f\|_\infty=\max_{x\in[a,b]}|f_k(x)-f(x)|\to0$, azaz $\forall\varepsilon\ \exists k_0\ \forall k>k_0\ \forall x\in[a,b]:|f_k(x)-f(x)|<\varepsilon$ — ez az **egyenletes konvergencia** (az $f\pm\varepsilon$ sávban fut az $f_k$ grafikonja).
- $p=1$: $\|f_k-f\|_1=\int_a^b|f_k-f|\to0$ (integrál szerinti konvergencia).
- **Pontonkénti határfüggvény:** $f(x):=\lim_k f_k(x)$ ott, ahol a limesz létezik.

### Tétel (3. gyakorlat)

Ha $f_k\to f$ a $\|\cdot\|_\infty$ normában, akkor

1. $f$ szükségképpen egyenlő a pontonkénti határfüggvénnyel (mert $|f_k(t)-f(t)|\le\|f_k-f\|_\infty\to0$ minden $t$-re);
2. $f_k\to f$ a $\|\cdot\|_1$ normában is, mert $\|f_k-f\|_1\le(b-a)\|f_k-f\|_\infty$.

Megfordítva: $\|\cdot\|_1$-ben konvergens sorozat nem feltétlenül konvergens $\|\cdot\|_\infty$-ben — a két norma nem ekvivalens ([[concepts/analiii/ekvivalens-normak]]).

### Módszer

1. Számoljuk ki a pontonkénti határfüggvényt $g$-t. Ha nincs vagy $g\notin C[a,b]$, akkor $\|\cdot\|_\infty$-ben a sorozat divergens.
2. Ha $g$ folytonos, számoljuk ki $r_k=\|f_k-g\|_\infty=\max|f_k-g|$-t (szélsőérték: derivált, monotonitás, Weierstrass-tétel); $r_k\to0\iff$ egyenletes konvergencia.
3. $\|\cdot\|_1$-ben: $\int|f_k-g|$ közvetlen kiszámítása, vagy a fenti becslés.
4. Divergencia bizonyítása: indirekt módon feltesszük, hogy a limesz $g'$; akkor $g'=g$ (pontonkénti limesz), és $r_k\not\to0$ ellentmondás.

### Megoldott példák (a gyakorlat megoldása szerint)

**1. példa.** $f_k(x)=\dfrac{k^2x^3}{1+k^2x^4}$, $x\in[1,2]$. Pontonként $f_k(t)=\dfrac{t^3}{\frac1{k^2}+t^4}\to\dfrac1t$, így $f(x)=\frac1x$. Továbbá
$$r_k=\max_{x\in[1,2]}\Bigl|f_k(x)-\tfrac1x\Bigr|=\max\frac1{x(1+k^2x^4)}=\frac1{1+k^2}\to0,$$
mert a nevező ($x\cdot(1+k^2x^4)$, deriváltja $1+5k^2x^4>0$) szigorúan nő, tehát a maximum $x=1$-ben van. Így $f_k\to\frac1x$ $\|\cdot\|_\infty$-ben, és a tétel miatt $\|\cdot\|_1$-ben is.

**2. példa.** $f_k(x)=x^k-x^{2k}$, $x\in[0,1]$.
- (a) $\|\cdot\|_1$-ben $f_k\to0$: $\|f_k\|_1=\int_0^1(x^k-x^{2k})\,dx=\frac1{k+1}-\frac1{2k+1}=\frac k{(k+1)(2k+1)}\to0$.
- (b) $\|\cdot\|_\infty$-ben divergens: a pontonkénti limesz $0$; $f_k'(x)=kx^{k-1}(1-2x^k)$, ezért a maximum $x_k=2^{-1/k}$-nál van, értéke $\frac12-\frac14=\frac14$ minden $k$-ra, tehát $r_k=\frac14\not\to0$.

A tanulság: itt $\|\cdot\|_1$-ben konvergens, $\|\cdot\|_\infty$-ben divergens sorozatot kapunk.

## Kapocs

- [[concepts/analiii/konvergencia-metrikus-terben]] — a $C[a,b]$-beli konvergencia mint egyenletes konvergencia, további példák táblázata
- [[concepts/analiii/normalt-vektorter]] — a $\|\cdot\|_p$ normák $C[a,b]$-n
- [[concepts/analiii/cauchy-sorozat-es-teljes-ter]] — $(C[a,b],\|\cdot\|_\infty)$ teljes, $\|\cdot\|_1$-ben nem
- [[concepts/analiii/ekvivalens-normak]] — a két norma nem ekvivalens
