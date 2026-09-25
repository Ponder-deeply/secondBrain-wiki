---
tags: [concept, nummodi/qr-felbontas-es-ortogonalizacio]
sources: [NM1_ea05.pdf]
derivation: source
updated: 2026-08-05
---

# Gram–Schmidt-féle ortogonalizáció

A Gram–Schmidt-ortogonalizáció adott $a_1, \ldots, a_n \in \mathbb{R}^n$ lineárisan független vektorrendszerből ortonormált (ill. csak ortogonális) vektorrendszert állít elő — és ezáltal elvégzi az $A$ mátrix [[concepts/nummodi/qr-felbontas|QR-felbontását]].

## Feladat

Adott $a_1, \ldots, a_n \in \mathbb{R}^n$ lineárisan független vektorrendszer. Keressünk $q_1, \ldots, q_n \in \mathbb{R}^n$ ortonormált vektorrendszert úgy, hogy $q_k$ csak $a_1, \ldots, a_k$-tól függ ($k = 1, 2, \ldots, n$).

Mátrixszorzás alakban: $QR = A$, ahol $Q$ ortogonális, $R \in \mathcal{U}$ felső háromszög.

## Gram–Schmidt-ortogonalizáció (normálással)

**Definíció:**

Adott az $a_1, \ldots, a_n \in \mathbb{R}^n$ lineárisan független vektorrendszer.

1. $r_{11} := \|a_1\|_2$,
2. $q_1 := \dfrac{1}{r_{11}} a_1$ — „lenormáljuk".

A $k$-adik lépésben ($k = 2, \ldots, n$):

3. $r_{jk} := \langle a_k, q_j \rangle \quad (j = 1, \ldots, k-1)$,
4. $s_k := a_k - \displaystyle\sum_{j=1}^{k-1} r_{jk} \cdot q_j$,
5. $r_{kk} := \|s_k\|_2$ ($s_k$ segédvektor hossza),
6. $q_k := \dfrac{1}{r_{kk}} s_k$ — „lenormáljuk".

Az így nyert $q_1, \ldots, q_n$ vektorrendszer **ortonormált**.

**Levezetés:** lásd a [[concepts/nummodi/qr-felbontas|QR-felbontás]] létezés bizonyítását.

## Gram–Schmidt-ortogonalizáció (normálás nélkül)

**Definíció (normálás nélküli változat):**

Adott az $a_1, \ldots, a_n \in \mathbb{R}^n$ lineárisan független vektorrendszer.

1. $\widetilde{q}_1 := a_1$, $\widetilde{r}_{11} := 1$.

A $k$-adik lépésben ($k = 2, \ldots, n$):

2. $\widetilde{r}_{jk} := \dfrac{\langle a_k, \widetilde{q}_j \rangle}{\langle \widetilde{q}_j, \widetilde{q}_j \rangle} \quad (j = 1, \ldots, k-1)$,
3. $\widetilde{q}_k := a_k - \displaystyle\sum_{j=1}^{k-1} \widetilde{r}_{jk} \cdot \widetilde{q}_j$,
4. $\widetilde{r}_{kk} := 1$ (nem normálunk).

Az így nyert $\widetilde{q}_1, \ldots, \widetilde{q}_n$ vektorrendszer **ortogonális** (de általában nem normált).

**Megjegyzés:** Kézi számolásra alkalmasabb, mert elmarad a négyzetgyökvonás. Ne felejtsük el utólag normálni, ha az ortonormált alak kell!

**Normálás utólag:** $A = \widetilde{Q}\widetilde{R}$, ahol $D := \widetilde{Q}^\top \widetilde{Q} = \text{diag}(\langle \widetilde{q}_1, \widetilde{q}_1 \rangle, \ldots, \langle \widetilde{q}_n, \widetilde{q}_n \rangle)$, és

$$A = \widetilde{Q} \cdot \underbrace{\sqrt{D}^{-1}}_{\text{norm.}} \cdot \underbrace{\sqrt{D} \cdot \widetilde{R}}_{R} = Q \cdot R.$$

Közvetlenül is használható: $\sqrt{D} = \text{diag}(\|\widetilde{q}_1\|_2, \ldots, \|\widetilde{q}_n\|_2)$.

## Műveletigény

**Tétel:** A Gram–Schmidt-ortogonalizáció műveletigénye

$$2n^3 + \mathcal{O}(n^2),$$

valamint $n$ darab négyzetgyökvonás is szükséges.

**Bizonyítás:** A $k$-adik lépésben:

| Művelet | Darabszám |
|---|---|
| Skaláris szorzatok ($r_{jk}$) | $(k-1)(2n-1)$ |
| Ortogonális vektor ($s_k$) | $(k-1)n + (k-1)n = (k-1)2n$ |
| Hossz ($r_{kk}$) | $2n-1$ |
| Osztás ($q_k$) | $n$ |

Összesen egy lépésben: $(k-1)(4n-1) + 3n - 1 = 4kn - n - k$.

Összegzve $k = 1$-től $n$-ig:

$$\sum_{k=1}^{n}(4kn - n - k) = 4n \cdot \frac{n(n+1)}{2} - n^2 - \frac{n(n+1)}{2} = 2n^3 + \mathcal{O}(n^2). \quad \square$$

## Numerikus példa

Készítsük el a következő mátrix QR-felbontását Gram–Schmidt-ortogonalizációval:

$$A = \begin{bmatrix} 1 & 2 \\ 2 & 1 \end{bmatrix} = \begin{bmatrix} q_1 & q_2 \end{bmatrix} \cdot \begin{bmatrix} r_{11} & r_{12} \\ 0 & r_{22} \end{bmatrix} = Q \cdot R.$$

**1. lépés** ($a_1 = [1, 2]^\top$):

$$r_{11} = \|a_1\|_2 = \sqrt{1^2 + 2^2} = \sqrt{5}, \qquad q_1 = \frac{1}{\sqrt{5}} \begin{bmatrix}1\\2\end{bmatrix}.$$

**2. lépés** ($a_2 = [2, 1]^\top$):

$$r_{12} = \langle a_2, q_1 \rangle = \left\langle \begin{bmatrix}2\\1\end{bmatrix}, \frac{1}{\sqrt{5}}\begin{bmatrix}1\\2\end{bmatrix} \right\rangle = \frac{1}{\sqrt{5}}(2 \cdot 1 + 1 \cdot 2) = \frac{4}{\sqrt{5}},$$

$$s_2 = a_2 - r_{12} q_1 = \begin{bmatrix}2\\1\end{bmatrix} - \frac{4}{\sqrt{5}} \cdot \frac{1}{\sqrt{5}}\begin{bmatrix}1\\2\end{bmatrix} = \frac{1}{5}\begin{bmatrix}10-4\\5-8\end{bmatrix} = \frac{3}{5}\begin{bmatrix}2\\-1\end{bmatrix},$$

$$r_{22} = \|s_2\|_2 = \frac{3}{5}\sqrt{4+1} = \frac{3}{\sqrt{5}}, \qquad q_2 = \frac{1}{\sqrt{5}}\begin{bmatrix}2\\-1\end{bmatrix}.$$

**Eredmény:**

$$Q = \frac{1}{\sqrt{5}}\begin{bmatrix}1 & 2\\2 & -1\end{bmatrix}, \qquad R = \frac{1}{\sqrt{5}}\begin{bmatrix}5 & 4\\0 & 3\end{bmatrix}.$$

## Kapocs

- [[concepts/nummodi/qr-felbontas]] — a QR-felbontás definíciója, létezés/egyértelműség tétele, LER-es alkalmazás
- [[concepts/nummodi/ortogonalis-matrixok]] — ortogonális mátrix és ortonormált rendszer fogalma
- [[concepts/nummodi/householder-transzformacio]] — numerikusan stabilabb alternatív QR-előállítás
- [[concepts/nummodi/haromszogmatrixok]] — felső háromszögmátrixok ($\mathcal{U}$)
- [[subjects/nummodi]] — kurzus áttekintése
