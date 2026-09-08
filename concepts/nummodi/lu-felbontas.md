---
tags: [concept]
sources: [NM1_ea03.pdf, NM1_ea04.pdf]
derivation: source
updated: 2026-08-05
---

# LU-felbontás

Az $A = LU$ felbontás az együtthatómátrixot egy egységátlójú alsó háromszögmátrix ($L \in \mathcal{L}_1$) és egy felső háromszögmátrix ($U \in \mathcal{U}$) szorzataként állítja elő. Ez a felbontás hatékonyan teszi lehetővé lineáris egyenletrendszerek megoldását, determináns kiszámítását és mátrix invertálását.

## Definíció

**Definíció — LU-felbontás:**
Az $A$ mátrix *LU-felbontásának* nevezzük az $L \cdot U$ szorzatot, ha

$$A = L \cdot U, \quad L \in \mathcal{L}_1, \quad U \in \mathcal{U}.$$

## LU-felbontás Gauss-eliminációval

A [[concepts/nummodi/gauss-eliminacio|Gauss-elimináció]] lépései [[concepts/nummodi/haromszogmatrixok|alsó háromszögmátrix]]-szorzásokként írhatók fel: a $k$-adik lépés az $L_k$ mátrixszal való bal oldali szorzás. Ezért az összes lépés elvégzése után:

$$L_{n-1} \cdots L_2 \cdot L_1 \cdot A = U,$$

amiből — az inverzeikkel átszorva —

$$A = L_1^{-1} \cdot L_2^{-1} \cdots L_{n-1}^{-1} \cdot U = L \cdot U.$$

Az $L$ mátrix elemei közvetlenül a GE-s hányadosokból állnak: az $L_k^{-1}$ mátrix inverzeinek szorzatára vonatkozó tétel alapján az összes $\ell_k$ vektort egy mátrixba gyűjthetjük, mátrix-szorzás nélkül:

$$L = L_1^{-1} \cdots L_{n-1}^{-1} = I + \ell_1 e_1^\top + \ell_2 e_2^\top + \ldots + \ell_{n-1} e_{n-1}^\top.$$

### $L$ és $U$ elemei GE-vel

$$L \in \mathcal{L}_1, \quad l_{ij} = \frac{a_{ij}^{(j-1)}}{a_{jj}^{(j-1)}} \quad (i > j),$$
$$U \in \mathcal{U}, \quad u_{ij} = a_{ij}^{(i-1)} \quad (i \le j).$$

### Példa (GE-vel)

$$A = \begin{bmatrix} 2 & 0 & 3 \\ -4 & 5 & -2 \\ 6 & -5 & 4 \end{bmatrix}$$

**1. lépés** ($L_1$ szorzók: $l_{21} = -2$, $l_{31} = 3$):

$$A^{(1)} = L_1 \cdot A = \begin{bmatrix} 2 & 0 & 3 \\ 0 & 5 & 4 \\ 0 & -5 & -5 \end{bmatrix}$$

**2. lépés** ($L_2$ szorzó: $l_{32} = -1$):

$$A^{(2)} = L_2 \cdot A^{(1)} = \begin{bmatrix} 2 & 0 & 3 \\ 0 & 5 & 4 \\ 0 & 0 & -1 \end{bmatrix} =: U$$

$$L = L_1^{-1} \cdot L_2^{-1} = \begin{bmatrix} 1 & 0 & 0 \\ -2 & 1 & 0 \\ 3 & -1 & 1 \end{bmatrix}$$

Ellenőrzés: $A = L \cdot U$. ✓

## LU-felbontás közvetlen kiszámítása

A felbontás a $LU = A$ mátrixszorzat elemeit tartalmazó egyenletrendszer jó sorrendben való megoldásával is elvégezhető — GE nélkül.

### Közvetlen képletek

**Tétel — az LU-felbontás közvetlen kiszámítása:**

$$i \le j \text{ (felső)}: \quad u_{ij} = a_{ij} - \sum_{k=1}^{i-1} l_{ik} \cdot u_{kj},$$

$$i > j \text{ (alsó)}: \quad l_{ij} = \frac{1}{u_{jj}} \left( a_{ij} - \sum_{k=1}^{j-1} l_{ik} \cdot u_{kj} \right).$$

Ha jó sorrendben számolunk (sorfolytonosan, oszlopfolytonosan vagy parkettaszerűen), a jobb oldal minden mennyisége ismert.

**Bizonyítás:** Az $A = LU$ egyenlet $i \le j$ esetén:

$$a_{ij} = \sum_{k=1}^{n} l_{ik} \cdot u_{kj} = \sum_{k=1}^{i} l_{ik} \cdot u_{kj} = u_{ij} + \sum_{k=1}^{i-1} l_{ik} \cdot u_{kj},$$

(mert $k > i \Rightarrow l_{ik} = 0$ és $l_{ii} = 1$), amiből $u_{ij}$ kifejezhető.

$i > j$ esetén:

$$a_{ij} = \sum_{k=1}^{j} l_{ik} \cdot u_{kj} = l_{ij} \cdot u_{jj} + \sum_{k=1}^{j-1} l_{ik} \cdot u_{kj},$$

(mert $k > j \Rightarrow u_{kj} = 0$), amiből — ha $u_{jj} \ne 0$ — $l_{ij}$ kifejezhető. $\square$

### Példa (közvetlen)

Ugyanaz az $A$ mátrix. $U$ 1. sora = $A$ 1. sora ($u_{1j} = a_{1j}$). A 2. sor számítása:

$$l_{21} \cdot 2 = -4 \implies l_{21} = -2, \quad u_{22} = 5, \quad u_{23} = -2 - (-2)\cdot 3 = 4.$$

A 3. sor számítása:

$$l_{31} = 3, \quad l_{32} = \frac{-5}{5} = -1, \quad u_{33} = 4 - 3\cdot 3 - (-1)\cdot 4 = -1.$$

Eredmény: ugyanaz az $L$ és $U$, mint GE-vel.

## LU-felbontás létezése és egyértelműsége

**Tétel — létezés:**
Ha a Gauss-elimináció végrehajtható sor- és oszlopcsere nélkül (azaz $a_{kk}^{(k-1)} \ne 0$ minden $k = 1, \ldots, n-1$-re), akkor az $A$ mátrix LU-felbontása létezik.

**Megjegyzések:**
- $u_{kk} = a_{kk}^{(k-1)}$ és $D_k = a_{11} \cdot a_{22}^{(1)} \cdots a_{kk}^{(k-1)}$ (a $k$-adik főminor).
- Ha van LU-felbontása $A$-nak és $U$ átlóján nem nullák állnak, akkor $u_{kk} = a_{kk}^{(k-1)} \ne 0$.
- $a_{nn}^{(n-1)} \ne 0 \iff \det(A) = D_n \ne 0$.
- Ha a GE végrehajtható, de $a_{nn}^{(n-1)} = 0$, akkor létezik LU-felbontás, de $\det(A) = \det(L) \cdot \det(U) = 0$-ból $u_{nn} = 0$.

**Tétel — létezés és egyértelműség (főminorokkal):**

- Ha $D_k \ne 0$ ($k = 1, \ldots, n-1$), akkor létezik az $A$ mátrix LU-felbontása és $u_{kk} \ne 0$ ($k = 1, \ldots, n-1$).
- Ha $\det(A) \ne 0$, akkor a felbontás egyértelmű.

**Bizonyítás — egyértelműség:** Tegyük fel indirekt, hogy az invertálható $A$ mátrixnak legalább két különböző LU-felbontása létezik:

$$A = L_1 \cdot U_1 = L_2 \cdot U_2.$$

$U_2^{-1}$-gyel jobbról, majd $L_1^{-1}$-gyel balról szorozva:

$$U_1 \cdot U_2^{-1} = L_1^{-1} \cdot L_2.$$

A bal oldal felső háromszögmátrix, a jobb oldal egységátlójú alsó háromszögmátrix. Ez csak akkor lehetséges, ha mindkét oldal az egységmátrix, tehát $U_1 = U_2$ és $L_1 = L_2$ — ellentmondás. $\square$

## Miért hasznos az LU-felbontás?

Ha $Ax = b$ megoldható és rendelkezésre áll az $A = LU$ felbontás, akkor az $Ax = L \underbrace{Ux}_{y} = b$ helyett két háromszögmátrixú LER-t oldunk meg:

1. $Ly = b$ — alsó háromszögű LER: $n^2 + \mathcal{O}(n)$ művelet (előrehelyettesítés),
2. $Ux = y$ — felső háromszögű LER: $n^2 + \mathcal{O}(n)$ művelet (visszahelyettesítés).

Összehasonlításul: egy mátrix-vektor szorzás $n \cdot (2n-1) = 2n^2 + \mathcal{O}(n)$ művelet.

**Előny:** Ha sok LER-t kell megoldani ugyanarra az $A$ mátrixra (különböző $b$ jobboldallal), az LU-felbontást ($\frac{2}{3}n^3 + \mathcal{O}(n^2)$) csak egyszer kell elvégezni; ezután minden egyes megoldás csak $2n^2 + \mathcal{O}(n)$ műveletet igényel.

## Háromszögmátrixú LER megoldásának műveletigénye

**Tétel:** Az $Ux = y$ megoldásának műveletigénye $n^2 + \mathcal{O}(n)$.

*Bizonyítás:* ugyanaz, mint a GE visszahelyettesítésnél.

**Tétel:** Az $Ly = b$ megoldásának (előrehelyettesítés) műveletigénye $n^2 + \mathcal{O}(n)$.

*Bizonyítás:* Rögzített $i$-re $(i-1)$ szorzás és $(i-1)$ összeadás szükséges. Összesen:

$$\sum_{i=2}^{n} 2(i-1) = \sum_{s=1}^{n-1} 2s = 2 \cdot \frac{n(n-1)}{2} = n^2 + \mathcal{O}(n). \quad \square$$

## LU-felbontás műveletigénye

**Tétel:** Az LU-felbontás műveletigénye

$$\frac{2}{3}n^3 + \mathcal{O}(n^2).$$

*Bizonyítás:* Triviális a GE-ből, mert az LU-felbontás a GE-vel együtt állítható elő, és az $L$ mátrix elemei (GE-s hányadosok) többletmüvelet nélkül adódnak.

A közvetlen képletekből: rögzített $j$-re $u_{ij}$ kiszámítása $2(i-1)$ műveletet igényel; rögzített $i$-re $l_{ij}$ kiszámítása $2j-1$ műveletet igényel. Az összes műveletet összegezve:

$$\sum_{j=1}^{n} \sum_{i=1}^{j} 2(i-1) + \sum_{i=2}^{n} \sum_{j=1}^{i-1} (2j-1) = \frac{2}{3}n^3 + \mathcal{O}(n^2). \quad \square$$

## Kapcsolat az LDU- és Cholesky-felbontással

Az $A = L\widetilde{U}$ LU-felbontásból az $\widetilde{U}$ főátlóbeli elemeit kiemelve kapjuk az $A = LDU$ **LDU-felbontást** (ahol $U \in \mathcal{U}_1$ egységátlójú). Szimmetrikus $A$ esetén $U = L^\top$, azaz $A = LDL^\top$. Pozitív definit szimmetrikus $A$ esetén $D$ pozitív elemű, bevezethető $\sqrt{D}$, és $A = LL^\top$ — ez a **Cholesky-felbontás**. Részletesen: [[concepts/nummodi/ldu-felbontas|ldu-felbontas]].

## Kapocs

- [[concepts/nummodi/haromszogmatrixok]] — alsó/felső háromszögmátrixok definíciói, zártsági tulajdonságok, $L_k$ mátrixok
- [[concepts/nummodi/gauss-eliminacio]] — a Gauss-elimináció algoritmusa, melynek mátrixos átírása adja az LU-felbontást
- [[concepts/nummodi/linearis-egyenletrendszerek]] — LER fogalma, megoldhatóság; az LU-felbontás itt a direkt módszerek között szerepel
- [[concepts/nummodi/ldu-felbontas]] — LDU-felbontás és Cholesky-felbontás: az LU finomításai szimmetrikus és pozitív definit esetekre
- [[concepts/nummodi/schur-komplementer]] — megmaradási tételek; magyarázza, mikor végezhető el az LU sortcsere nélkül
- [[concepts/nummodi/hibaszamitas]] — kondíciószám, numerikus stabilitás és az LU-felbontás pontossága
- [[subjects/nummodi]] — kurzus áttekintése
