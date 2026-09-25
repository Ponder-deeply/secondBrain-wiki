---
tags: [concept, nummodi/iterativ-modszerek-ler-re]
sources: [NM1_ea08.pdf]
derivation: source
updated: 2026-08-05
---

# Jacobi-iteráció és csillapított Jacobi-iteráció

A Jacobi-iteráció az $Ax = b$ LER megoldásának legegyszerűbb iteratív módszere: az $A = L + D + U$ felbontásból $P = D$ választással adódik. A csillapított változat egy $\omega$ relaxációs paraméterrel gyorsíthatja (vagy stabilizálhatja) a konvergenciát.

## Jacobi-iteráció

### Levezetés

Az [[concepts/nummodi/iteracios-modszerek-ler|iterációs módszerek]] általános keretéből indulunk ki, az $A = L + D + U$ felbontással (ahol $L, D, U$ az elemek pozíciója szerint meghatározott részek — **nem** az [[concepts/nummodi/lu-felbontas|LU-felbontás]] mátrixai). $P = D$ választással:

$$Dx = -(L+U)x + b \iff x = -D^{-1}(L+U)x + D^{-1}b.$$

**Definíció — Jacobi-iteráció:**

$$x^{(k+1)} = \underbrace{-D^{-1}(L+U)}_{B_J} \cdot x^{(k)} + \underbrace{D^{-1}b}_{c_J} = B_J \cdot x^{(k)} + c_J.$$

### Komponensenkénti alak

**Állítás:** A Jacobi-iteráció komponensenkénti alakja:

$$x_i^{(k+1)} = \frac{-1}{a_{ii}} \left( \sum_{j=1,\, j\neq i}^{n} a_{ij} x_j^{(k)} - b_i \right) \quad (i = 1, \ldots, n).$$

**Bizonyítás:** Házi feladat — egyszerű, az $i$-edik sorból közvetlenül.

### Reziduum-vektoros algoritmus

A reziduumvektort ($r^{(k)} := b - Ax^{(k)}$) felhasználva hatékonyan megírható az iteráció.

Írjuk fel a Jacobi-lépést reziduum alakban:

$$x^{(k+1)} = -D^{-1}(L+U)x^{(k)} + D^{-1}b = D^{-1}\bigl((D-A)x^{(k)} + b\bigr) = x^{(k)} + D^{-1}r^{(k)}.$$

Bevezetjük az $s^{(k)} := D^{-1}r^{(k)}$ **segédvektort** (azaz $Ds^{(k)} = r^{(k)}$ LER megoldása), ekkor:

$$x^{(k+1)} = x^{(k)} + s^{(k)}.$$

Az új reziduumvektor:

$$r^{(k+1)} = b - Ax^{(k+1)} = b - A(x^{(k)} + s^{(k)}) = r^{(k)} - As^{(k)}.$$

**Algoritmus: Jacobi-iteráció**

$$r^{(0)} := b - Ax^{(0)}$$
$$k = 1, \ldots, \text{leállásig:}$$
$$\quad s^{(k)} := D^{-1}r^{(k)} \iff Ds^{(k)} = r^{(k)} \text{ (diag. LER)}$$
$$\quad x^{(k+1)} := x^{(k)} + s^{(k)}$$
$$\quad r^{(k+1)} := r^{(k)} - As^{(k)}$$

**Megjegyzés:** $x^{(k+1)} - x^{(k)} = s^{(k)}$, tehát a tapasztalati kontrakciós együtthatók számításához lépésenként egy normaértéket és egy osztást kell elvégezni.

### Konvergenciatétel: szigorúan diagonálisan domináns eset

**Definíció:** Az $A$ mátrix **szigorúan diagonálisan domináns (SDD) a soraira nézve**, ha

$$\forall i : |a_{ii}| > \sum_{j=1,\, j\neq i}^{n} |a_{ij}|.$$

**Tétel:** Ha $A$ szigorúan diagonálisan domináns a soraira, akkor az $Ax = b$ LER-re felírt Jacobi-iteráció konvergens bármely $x^{(0)}$ esetén.

**Bizonyítás:** Írjuk fel a $B_J$ mátrix elemeit: $b_{ii} = 0$ és $b_{ij} = -a_{ij}/a_{ii}$ ($j \neq i$). Ekkor:

$$\|B_J\|_\infty = \left\|-D^{-1}(L+U)\right\|_\infty = \max_{i=1}^n \sum_{j=1,\, j\neq i}^n \frac{|a_{ij}|}{|a_{ii}|}.$$

Ha $A$ SDD a soraira, akkor $\forall i : |a_{ii}| > \sum_{j\neq i}|a_{ij}|$, azaz $1 > \sum_{j\neq i}|a_{ij}|/|a_{ii}|$. Tehát minden sor összege egynél kisebb, maximumuk is az, vagyis:

$$\|B_J\|_\infty = \max_{i=1}^n \sum_{j=1,\, j\neq i}^n \frac{|a_{ij}|}{|a_{ii}|} < 1.$$

A [[concepts/nummodi/banach-fixponttetel-rn|Banach-féle fixponttétel]] következménye alapján az iteráció konvergens. $\square$

---

## Csillapított Jacobi-iteráció

### Az alapötlet

A **csillapítás** (vagy **tompítás**) alapötlete: az új $x_J^{(k+1)}$ Jacobi-lépés helyett az előző $x^{(k)}$ és az új érték $\omega$-súlyozott kombinációját vesszük:

$$x^{(k+1)} := (1-\omega) \cdot x^{(k)} + \omega \cdot x_J^{(k+1)}.$$

- $0 < \omega < 1$: **alulrelaxálás** (konzervatívabb lépés),
- $\omega > 1$: **túlrelaxálás** (nagyobb lépés),
- $\omega = 1$: az eredeti Jacobi-módszer.

### Definíció és mátrixos alak

A Jacobi-módszerből és a „helyben hagyásból" ($x = x$) $\omega$- és $(1-\omega)$-súlyozott összeget képzünk:

$$x = \bigl[(1-\omega)I - \omega D^{-1}(L+U)\bigr] \cdot x + \omega D^{-1}b.$$

**Definíció — csillapított Jacobi-iteráció $J(\omega)$:**

$$x^{(k+1)} = \underbrace{\bigl[(1-\omega)I - \omega D^{-1}(L+U)\bigr]}_{B_{J(\omega)}} \cdot x^{(k)} + \underbrace{\omega D^{-1}b}_{c_{J(\omega)}}.$$

### Komponensenkénti alak

**Állítás:** A $J(\omega)$ iteráció komponensenkénti alakja:

$$x_i^{(k+1)} = (1-\omega) \cdot x_i^{(k)} + \omega \cdot x_{i,J}^{(k+1)},$$

ahol $x_{i,J}^{(k+1)}$ a hagyományos Jacobi-módszer ($J = J(1)$) által adott érték:

$$x_{i,J}^{(k+1)} = \frac{-1}{a_{i,i}} \left(\sum_{j=1,\, j\neq i}^n a_{i,j} x_j^{(k)} - b_i\right).$$

**Bizonyítás:** Házi feladat — nem nehéz.

### Reziduum-vektoros algoritmus

Hasonlóan a Jacobi-iterációhoz:

$$x^{(k+1)} = x^{(k)} + \omega D^{-1}r^{(k)} = x^{(k)} + s^{(k)},$$

ahol $s^{(k)} := \omega D^{-1}r^{(k)}$ (azaz $Ds^{(k)} = \omega r^{(k)}$ LER megoldása).

**Algoritmus: csillapított Jacobi-iteráció $J(\omega)$**

$$r^{(0)} := b - Ax^{(0)}$$
$$k = 1, \ldots, \text{leállásig:}$$
$$\quad s^{(k)} := \omega D^{-1}r^{(k)} \iff Ds^{(k)} = \omega r^{(k)}$$
$$\quad x^{(k+1)} := x^{(k)} + s^{(k)}$$
$$\quad r^{(k+1)} := r^{(k)} - As^{(k)}$$

### Konvergenciatétel

**Tétel — $J(\omega)$ konvergenciája:**

Ha az $Ax = b$ LER-re a Jacobi-iteráció konvergens minden kezdőértékre, akkor $0 < \omega < 1$-re a csillapított Jacobi-iteráció is az.

**Bizonyítás:** A $B_{J(\omega)}$ átmenetmátrix sajátértékeit meghatározzuk $B_J$ sajátértékeiből. Legyen $\lambda_i$ a $B_J$ egy sajátértéke, $v_i$ a megfelelő sajátvektor. Ekkor:

$$B_{J(\omega)} v_i = \bigl((1-\omega)I + \omega B_J\bigr)v_i = (1-\omega)v_i + \omega\lambda_i v_i = \underbrace{(1-\omega) + \omega\lambda_i}_{\mu_i} \cdot v_i,$$

tehát a $B_{J(\omega)}$ sajátértékei $\mu_i = (1-\omega) + \omega\lambda_i$, sajátvektorai $v_i$ (azonosak $B_J$-ével).

A konvergencia elégséges feltétele: $\varrho(B_{J(\omega)}) < 1$. Ha $\varrho(B_J) < 1$, azaz minden $|\lambda_i| < 1$, és $0 < \omega < 1$, akkor:

$$|\mu_i| \leq (1-\omega) + \omega|\lambda_i| < (1-\omega) + \omega = 1 \quad (i = 1, \ldots, n).$$

Tehát minden $|\mu_i| < 1$, vagyis $\varrho(B_{J(\omega)}) < 1$, és a csillapított iteráció konvergens. $\square$

### Matlab-példa: tapasztalati kontrakciós együtthatók

Az $A = \begin{bmatrix}4 & -1 & 0 \\ -1 & 4 & -1 \\ 0 & -1 & 4\end{bmatrix}$, $b = \begin{bmatrix}3\\2\\3\end{bmatrix}$, $x^* = \begin{bmatrix}1\\1\\1\end{bmatrix}$ LER esetén különböző $\omega$ értékekre a tapasztalati kontrakciós együtthatók:

| $\omega$ | $q \approx$ | Megjegyzés |
|----------|-------------|------------|
| $1.0$  | $0.3536$ | konvergens |
| $0.8$  | $0.4828$ | konvergens, lassabb |
| $0.6$  | $0.6118$ | konvergens, még lassabb |
| $1.2$  | $0.6243$ | konvergens (túlrelaxálás) |
| $1.8$  | $q > 1$  | divergens |
| $-0.1$ | $q > 1$  | divergens |

A példa mutatja, hogy $\omega = 1$ (eredeti Jacobi) adja a legjobb konvergenciát ennél a mátrixnál; az alulrelaxálás ($\omega < 1$) lassít, a túlrelaxálás $\omega \gtrsim 1.5$ esetén divergenciát okoz.

## Kapocs

- [[concepts/nummodi/iteracios-modszerek-ler]] — általános iterációs keret, $A = L+D+U$ felbontás
- [[concepts/nummodi/banach-fixponttetel-rn]] — fixponttétel, kontrakció, $\varrho(B) < 1$ feltétel
- [[concepts/nummodi/linearis-egyenletrendszerek]] — LER fogalma, megoldási módszerek áttekintése
- [[concepts/nummodi/matrixnormak]] — $\|\cdot\|_\infty$ (sornorma), spektrálsugár $\varrho$
- [[concepts/nummodi/kondicioszam]] — kondíciószám, LER érzékenysége
- [[concepts/nummodi/relativ-maradek]] — maradékvektor $r = b - Ax^{(k)}$, iterációs megállási kritérium
