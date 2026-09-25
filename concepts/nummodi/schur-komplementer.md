---
tags: [concept, nummodi/megmaradasi-tetelek-es-specialis-felbontasok]
sources: [NM1_ea04.pdf]
derivation: source
updated: 2026-08-05
---

# Schur-komplementer

A Schur-komplementer leírja, hogy egy blokkos LER particionálása után melyik mátrixon kell a Gauss-eliminációt folytatni. Segítségével kompakt módon fogalmazhatók meg a GE megmaradási tételei.

## Definíció

Legyen az $A \in \mathbb{R}^{n \times n}$ mátrix particionálva ($k < n$, $k \in \mathbb{N}$):

$$\begin{bmatrix} A_{11} & A_{12} \\ A_{21} & A_{22} \end{bmatrix} \cdot \begin{bmatrix} x_1 \\ x_2 \end{bmatrix} = \begin{bmatrix} b_1 \\ b_2 \end{bmatrix},$$

ahol $A_{11} \in \mathbb{R}^{k \times k}$ invertálható. Az $A$ mátrix $A_{11}$-re vonatkozó **Schur-komplementere**:

$$[A \mid A_{11}] := A_{22} - A_{21} A_{11}^{-1} A_{12}.$$

Ez egy $(n-k) \times (n-k)$-s mátrix.

## Motiváció — blokkos GE-lépés

A particionált LER egyenletei:
$$A_{11} x_1 + A_{12} x_2 = b_1,$$
$$A_{21} x_1 + A_{22} x_2 = b_2.$$

Végezzünk el egy blokkos GE-s lépést: a 2. egyenletből vonjuk ki a $(A_{21} \cdot A_{11}^{-1})$-szeres 1. egyenletet:

$$(A_{22} - A_{21} A_{11}^{-1} A_{12})\, x_2 = b_2 - A_{21} A_{11}^{-1} b_1.$$

A keletkező együtthatómátrix pontosan a Schur-komplementer. Blokkos felső háromszög alakban:

$$\begin{bmatrix} A_{11} & A_{12} \\ 0 & A_{22} - A_{21} A_{11}^{-1} A_{12} \end{bmatrix} \cdot \begin{bmatrix} x_1 \\ x_2 \end{bmatrix} = \begin{bmatrix} b_1 \\ b_2 - A_{21} A_{11}^{-1} b_1 \end{bmatrix}.$$

A GE-t tehát a jobb alsó $(n-k) \times (n-k)$-s részen, a Schur-komplementeren kell folytatni. $k=1$ esetén $A_{11} = (a_{11})$, és a szokásos (nem blokkos) GE 1. lépését kapjuk, feltéve $a_{11} \ne 0$.

## Megmaradási tételek

A [[concepts/nummodi/gauss-eliminacio|Gauss-elimináció]] során a következő tulajdonságok öröklődnek $A$-ról a Schur-komplementerre:

| # | Ha $A$ … | akkor $[A \mid A_{11}]$ is … |
|---|---|---|
| 1 | $\det(A) \ne 0$ | $\det([A \mid A_{11}]) \ne 0$ |
| 2 | szimmetrikus | szimmetrikus |
| 3 | pozitív definit | pozitív definit |
| 4 | szigorúan diagonálisan domináns (sor) | szigorúan diagonálisan domináns (sor) |
| 5 | fél sávszélessége $s$ | fél sávszélessége $\le s$ |
| 6 | GE során a profilnál soronként és oszloponként nullák az első nem nulla elemig megmaradnak | megmarad |

**Tétel (megmaradási tételek a GE-ra):** Az 1–6 tulajdonságok mind öröklődnek.

### Bizonyítások (vázlat)

**1. Determináns:** A GE determináns-tartó, ezért $\det(A) = \det(A^{(1)}) \ne 0$. Mivel $A^{(1)}$ blokk-felső háromszögmátrix:
$$\det(A^{(1)}) = \det(A_{11}) \cdot \det([A \mid A_{11}]),$$
és $\det(A_{11}) \ne 0$, ezért $\det([A \mid A_{11}]) \ne 0$. $\square$

**2. Szimmetria:** Ha $A$ szimmetrikus, akkor $A_{11}$ és $A_{22}$ is szimmetrikus, továbbá $A_{21}^\top = A_{12}$:
$$[A \mid A_{11}]^\top = (A_{22} - A_{21} A_{11}^{-1} A_{12})^\top = A_{22}^\top - A_{12}^\top (A_{11}^{-1})^\top A_{21}^\top = A_{22} - A_{12}(A_{11}^\top)^{-1} A_{21} = [A \mid A_{11}]. \quad \square$$

**3. Pozitív definitség:** Legyen $x_2 \ne 0$ tetszőleges. Válasszunk $x_1 := -A_{11}^{-1} A_{12} x_2$ vektort, hogy $Ax$ első $k$ komponense 0 legyen. Ekkor $x = [x_1; x_2] \ne 0$, ezért $\langle Ax, x \rangle > 0$. Kifejtés után:
$$0 < \langle Ax, x \rangle = \langle (A_{22} - A_{21} A_{11}^{-1} A_{12}) x_2, x_2 \rangle = \langle [A \mid A_{11}] x_2, x_2 \rangle. \quad \square$$

**4. Szigorúan diagonálisan domináns:** A bizonyítás $k=1$ esetén elvégezhető; az általános eset analóg. Az 1. sort a GE változatlanul hagyja; $i = 2, \ldots, n$-re a GE-képlet behelyettesítése és $|a_{11}|$-gyel való szorzás után az egyenlőtlenség az eredeti domináns feltételből igazolható (részletesen: az előadás dián). $\square$

## Kapcsolat az LU-felbontással

A megmaradási tételek alapján: ha $A$ pozitív definit, akkor minden GE-lépés pozitív definitségű maradékot ad, tehát a főátlón pozitív elemek maradnak — az LU-felbontás sortcsere nélkül elvégezhető.

## Mátrixtulajdonságok szótára

**Szimmetria:** $A = A^\top$.

**Pozitív definit mátrix** (ekvivalens jellemzések):
1. $\langle Ax, x \rangle = x^\top A x > 0$ minden $0 \ne x \in \mathbb{R}^n$-re,
2. minden főminora $D_k = \det(A_k) > 0$,
3. minden sajátértéke pozitív.

**Szigorúan diagonálisan domináns (sorra):** $|a_{ii}| > \sum_{j=1,j\ne i}^{n} |a_{ij}|$ ($i=1,\ldots,n$).

**Szigorúan diagonálisan domináns (oszlopra):** $|a_{ii}| > \sum_{j=1,j\ne i}^{n} |a_{ji}|$ ($i=1,\ldots,n$).

**Fél sávszélesség** $s \in \mathbb{N}$: $\forall\, i,j : |i-j| > s \Rightarrow a_{ij} = 0$ és $\exists\, k,l : |k-l| = s, a_{kl} \ne 0$.

**Profil:** Az $A$ mátrix profilja sorokra a $(k_1, \ldots, k_n)$, oszlopokra az $(l_1, \ldots, l_n)$ számok, ahol $k_i$ (ill. $l_j$) az adott sor (ill. oszlop) első nem nulla eleme előtti nullák száma. A GE a profilnál nem hoz létre újabb nemzéró elemet.

## Kapocs

- [[concepts/nummodi/gauss-eliminacio]] — a GE lépései, amelyeken a megmaradási tételek alapulnak
- [[concepts/nummodi/lu-felbontas]] — LU-felbontás; a Schur-komplementer magyarázza, mikor végezhető el sortcsere nélkül
- [[concepts/nummodi/ldu-felbontas]] — LDU-felbontás; szimmetrikus esetben a Schur-komplementer szimmetriája teszi lehetővé az $LDL^\top$-formát
- [[concepts/nummodi/haromszogmatrixok]] — háromszögmátrix-struktúra és blokk-felbontás összefüggései
- [[subjects/nummodi]] — kurzus áttekintése
