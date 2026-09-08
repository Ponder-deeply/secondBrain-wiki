---
tags: [concept]
sources: [NM1_ea04.pdf]
derivation: source
updated: 2026-08-05
---

# Progonka módszer (rövidített GE)

A progonka módszer (rövidített Gauss-elimináció) tridiagonális (háromátlós) lineáris egyenletrendszerek hatékony megoldására szolgál. A tárolási igény $3n - 2$ elem, a műveletigény $8n + \mathcal{O}(1)$ — szemben az általános GE $\frac{2}{3}n^3 + \mathcal{O}(n^2)$ igényével.

## Motiváció

A [[concepts/nummodi/gauss-eliminacio|Gauss-elimináció]] a [[concepts/nummodi/schur-komplementer|Schur-komplementer]] megmaradási tételei szerint megtartja a sávszélességet. Tridiagonális esetben a GE végén kapott $U$ mátrix is csak két átlót tartalmaz, ezért a visszahelyettesítés is egyszerűsíthető. A speciális alakot felhasználva hatékonyabb algoritmus készíthető.

## Jelölések

Legyen $A = \operatorname{tridiag}(\beta_{i-1}, \alpha_i, \gamma_i)$, vagyis:

$$A = \begin{bmatrix}
\alpha_1 & \gamma_1 &  &  & 0 \\
\beta_1 & \alpha_2 & \gamma_2 &  &  \\
 & \beta_2 & \ddots & \ddots &  \\
 &  & \ddots & \alpha_{n-1} & \gamma_{n-1} \\
0 &  &  & \beta_{n-1} & \alpha_n
\end{bmatrix}, \quad
x = \begin{bmatrix} x_1 \\ x_2 \\ \vdots \\ x_{n-1} \\ x_n \end{bmatrix}, \quad
b = \begin{bmatrix} b_1 \\ b_2 \\ \vdots \\ b_{n-1} \\ b_n \end{bmatrix}.$$

Tárolás: $3n - 2$ elem (az $n$ darab $\alpha_i$, az $n-1$ darab $\beta_i$ és az $n-1$ darab $\gamma_i$).

## Az algoritmus levezetése

### Előrelépés (1. lépés)

Az $i$-edik egyenlet ($i = 1, \ldots, n$):
$$\beta_{i-1} x_{i-1} + \alpha_i x_i + \gamma_i x_{i+1} = b_i.$$

Keressük $x_i$-t $f_i x_{i+1} + g_i$ alakban. Az 1. egyenletből ($\beta_0 x_0 = 0$ tag nincs):

$$\alpha_1 x_1 + \gamma_1 x_2 = b_1 \quad \Rightarrow \quad x_1 = -\frac{\gamma_1}{\alpha_1} x_2 + \frac{b_1}{\alpha_1},$$

tehát $f_1 = -\dfrac{\gamma_1}{\alpha_1}$ és $g_1 = \dfrac{b_1}{\alpha_1}$.

Tegyük fel, hogy $f_1, \ldots, f_{i-1}$ és $g_1, \ldots, g_{i-1}$ ismertek, és $x_{i-1} = f_{i-1} x_i + g_{i-1}$. Az $i$-edik egyenletbe behelyettesítve $x_{i-1}$ helyére:

$$\beta_{i-1}(f_{i-1} x_i + g_{i-1}) + \alpha_i x_i + \gamma_i x_{i+1} = b_i,$$
$$(\alpha_i + \beta_{i-1} f_{i-1}) x_i = -\gamma_i x_{i+1} + (b_i - \beta_{i-1} g_{i-1}),$$
$$x_i = -\frac{\gamma_i}{\alpha_i + \beta_{i-1} f_{i-1}} x_{i+1} + \frac{b_i - \beta_{i-1} g_{i-1}}{\alpha_i + \beta_{i-1} f_{i-1}}.$$

Tehát a rekurzió ($i = 2, \ldots, n-1$):

$$f_i = -\frac{\gamma_i}{\alpha_i + \beta_{i-1} f_{i-1}}, \qquad g_i = \frac{b_i - \beta_{i-1} g_{i-1}}{\alpha_i + \beta_{i-1} f_{i-1}}.$$

Az $n$-edik egyenletből ($\gamma_n = 0$ tag nincs):

$$\beta_{n-1}(f_{n-1} x_n + g_{n-1}) + \alpha_n x_n = b_n \quad \Rightarrow \quad x_n = \frac{b_n - \beta_{n-1} g_{n-1}}{\alpha_n + \beta_{n-1} f_{n-1}} =: g_n.$$

**Megjegyzés:** Kényelmes $f_n := 0$, $x_{n+1} := 0$ jelöléssel is indítható a 2. lépés, ekkor $x_n = f_n x_{n+1} + g_n = g_n$.

### Visszalépés (2. lépés)

$$x_n := g_n, \qquad x_i = f_i x_{i+1} + g_i \quad (i = n-1, n-2, \ldots, 1).$$

## Az algoritmus tömör összefoglalása

**1. lépés (előre):**
$$f_1 := -\frac{\gamma_1}{\alpha_1}, \quad g_1 := \frac{b_1}{\alpha_1};$$
$$i = 2, \ldots, n-1: \quad f_i := -\frac{\gamma_i}{\alpha_i + \beta_{i-1} f_{i-1}}, \quad g_i := \frac{b_i - \beta_{i-1} g_{i-1}}{\alpha_i + \beta_{i-1} f_{i-1}};$$
$$g_n := \frac{b_n - \beta_{n-1} g_{n-1}}{\alpha_n + \beta_{n-1} f_{n-1}}.$$

**2. lépés (vissza):**
$$x_n := g_n, \qquad x_i = f_i x_{i+1} + g_i \quad (i = n-1, n-2, \ldots, 1).$$

## Műveletigény

**1. lépés (előre):**
- $f_1, g_1$: 2 művelet.
- $i = 2, \ldots, n-1$ ciklus: $f_i$ kiszámítása 2 db, $g_i$ kiszámítása 3 db = 5 db/lépés, összesen $5(n-2)$ művelet.
- $g_n$: 3 db.

Összesen az 1. lépésben: $2 + 5(n-2) + 3 = 5n - 5$ művelet.

**2. lépés (vissza):**
- $i = n-1, n-2, \ldots, 1$ esetén: $2(n-1)$ művelet.

**Összesen:** $5n - 5 + 2 + 2(n-1) = 7n - 5 = 8n + \mathcal{O}(1)$ (ha $f_n$-t is tároljuk: a ciklus indexelése egységesíthető, pontos szám: $8n - 7$).

Az előadáson megadott teljes számolás: $2 + 6(n-2) + 5 + 2(n-1) = 8n - 7 = 8n + \mathcal{O}(1)$. $\square$

## Alkalmazás — köbös spline

A progonka módszer tipikus alkalmazása: köbös spline-interpoláció esetén a simassági feltételek tridiagonális LER-t adnak (ahogy a kurzus bevezetőjében látott év eleji példán is).

## Kapocs

- [[concepts/nummodi/gauss-eliminacio]] — az általános GE, amelynek speciális esete a progonka módszer
- [[concepts/nummodi/schur-komplementer]] — megmaradási tételek; sávszélesség megőrzése indokolja az algoritmus helyességét
- [[concepts/nummodi/haromszogmatrixok]] — a tridiagonális GE végén kapott $U$ mátrix struktúrája
- [[subjects/nummodi]] — kurzus áttekintése
