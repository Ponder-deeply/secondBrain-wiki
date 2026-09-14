---
tags: [concept]
sources: [SimonP-Anal2.pdf, 04_ea_An3_2022_tavasz.pdf]
references: ["Simon Péter: Analízis II., 3.1.3. és 3.1.4. Tétel"]
derivation: source
updated: 2026-09-14
---

# A gradiens és a Jacobi-mátrix a parciális deriváltakból

Ha egy függvény differenciálható egy pontban, akkor ott minden változója szerint parciálisan is deriválható, és a gradiens komponensei éppen a parciális deriváltak. Ez teszi a Jacobi-mátrixot ténylegesen kiszámíthatóvá.

## Tartalom

### A gradiens komponensei

**3.1.3. Tétel.** Legyen $1 \le n \in \mathbb{N}$, $h \in \mathbb{R}^n \to \mathbb{R}$, $a \in D_h$, és tegyük fel, hogy $h \in D\{a\}$. Ekkor $h$ az $a$-ban minden $i = 1, \dots, n$ változó szerint parciálisan deriválható, és

$$\operatorname{grad} h(a) = \bigl(\partial_1 h(a), \dots, \partial_n h(a)\bigr).$$

*Bizonyítás.* A $h \in D\{a\}$ feltevés miatt $a \in \operatorname{int} D_h$, tehát alkalmas $r > 0$ sugárral $K_r(a) \subset D_h$; a $\|\cdot\|_\infty$ normát használva ez azt jelenti, hogy $(a_i - r, a_i + r) \subset D^{(a)}_{h,i}$, azaz $a_i \in \operatorname{int} D^{(a)}_{h,i}$ minden $i$-re. Legyen $(d_1, \dots, d_n) := \operatorname{grad} h(a)$, ekkor alkalmas $\eta \to 0$ függvénnyel

$$h(a+x) - h(a) = \sum_{j=1}^n d_j x_j + \eta(x)\cdot\|x\|_\infty .$$

Válasszuk speciálisan $x := (0, \dots, 0, t, 0, \dots, 0)$-t ($t$ az $i$-edik helyen). Ekkor $\|x\|_\infty = |t|$, és

$$h_{a,i}(a_i + t) - h_{a,i}(a_i) = d_i t + \eta(x)\cdot|t| \qquad (|t| < r).$$

Mivel $\lim_{t\to 0}\eta(0,\dots,0,t,0,\dots,0) = 0$, ez pontosan az $h_{a,i} \in D\{a_i\}$ egyváltozós differenciálhatóság kritériuma, $h_{a,i}'(a_i) = d_i$. Tehát $\partial_i h(a) = d_i$ minden $i$-re. $\square$

Fontos: a tétel **egyirányú**. A parciális deriváltak létezéséből nem következik a differenciálhatóság — lásd [[concepts/analiii/differencialhatosagi-fogalmak-hierarchiaja|az ellenpéldákat]] és [[concepts/analiii/differencialhatosag-elegseges-feltetele|a megfordítás feltételeit]].

### A Jacobi-mátrix elemei

Az előzőt a [[concepts/analiii/koordinatafuggvenyek-differencialhatosaga|koordinátafüggvényekre vonatkozó tétellel]] összetéve:

**3.1.4. Tétel.** Ha $f = (f_1, \dots, f_m) \in \mathbb{R}^n \to \mathbb{R}^m$ differenciálható az $a \in D_f$ pontban, akkor

$$f'(a) = \begin{pmatrix}
\partial_1 f_1(a) & \partial_2 f_1(a) & \cdots & \partial_n f_1(a) \\
\partial_1 f_2(a) & \partial_2 f_2(a) & \cdots & \partial_n f_2(a) \\
\vdots & \vdots & \ddots & \vdots \\
\partial_1 f_m(a) & \partial_2 f_m(a) & \cdots & \partial_n f_m(a)
\end{pmatrix} \in \mathbb{R}^{m\times n}.$$

Tehát az $i$-edik sor $k$-adik eleme $\partial_k f_i(a)$: a **sorindex a koordinátafüggvényt, az oszlopindex a változót** jelöli.

Az $n = 1$ speciális esetben $\partial_1 f_i(a) = f_i'(a)$, azaz $f'(a) = \bigl(f_1'(a), \dots, f_m'(a)\bigr)$ — a deriváltvektor koordinátánként deriválódik.

### Példa

Az $f(x,y) := (x^2 - y,\ x + 2y,\ y^2) \in \mathbb{R}^3$ függvény koordinátafüggvényei differenciálhatók, ezért $f \in D$, és

$$f'(x,y) = \begin{pmatrix} 2x & -1 \\ 1 & 2 \\ 0 & 2y \end{pmatrix} \qquad \bigl((x,y) \in \mathbb{R}^2\bigr).$$

Egy $\mathbb{R}^2 \to \mathbb{R}^3$ függvény Jacobi-mátrixa tehát $3\times 2$-es — az alak $\mathbb{R}^{m\times n}$, nem $\mathbb{R}^{n\times m}$.

## Kapocs

- [[concepts/analiii/fuggvenygrafikon-erintosikja]] — az $n=2$, $m=1$ eset: a gradiens az érintősík normálvektorának első két koordinátája.
- [[concepts/analiii/parcialis-derivalt]] — a mátrixelemek definíciója és kiszámítása.
- [[concepts/analiii/koordinatafuggvenyek-differencialhatosaga]] — a másik fele a 3.1.4. Tételnek.
- [[concepts/analiii/jacobi-matrix]] — a mátrix mint a derivált reprezentációja.
- [[concepts/analiii/differencialhatosag-elegseges-feltetele]] — a hiányzó megfordítás.
- [[concepts/analiii/iranymenti-derivalt]] — az $\partial_e f(a) = f'(a)e$ formula, amely a gradienst irányokra alkalmazza.
