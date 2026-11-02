---
tags: [concept]
sources: [NM1_ea04.pdf]
derivation: source
kind: procedure
element: water
updated: 2026-10-21
---

# LDU-felbontás

Az $A = LDU$ felbontás az [[concepts/nummodi/lu-felbontas|LU-felbontás]] finomítása: a diagonális elemeket kiemeli egy külön $D$ mátrixba, így $L$ és $U$ egyaránt egységátlójú lesz. Szimmetrikus mátrix esetén $U = L^\top$ — ez az $LDL^\top$-felbontás. Pozitív definit szimmetrikus mátrix esetén $D$ pozitív, ezért bevezethető a $\sqrt{D}$, és az $A = LL^\top$ **Cholesky-felbontás** adódik.

## LDU-felbontás

### Definíció

Az $A \in \mathbb{R}^{n \times n}$ mátrix *LDU-felbontásának* nevezzük az $L \cdot D \cdot U$ szorzatot, ha

$$A = L \cdot D \cdot U, \quad L \in \mathcal{L}_1, \quad D \text{ diagonális mátrix}, \quad U \in \mathcal{U}_1.$$

### Előállítás LU-felbontásból

Legyen $A = L \cdot \widetilde{U}$ az LU-felbontás ($L \in \mathcal{L}_1$, $\widetilde{U} \in \mathcal{U}$). Legyen $D = \operatorname{diag}(\widetilde{u}_{11}, \ldots, \widetilde{u}_{nn})$. Definiáljuk $U := D^{-1} \widetilde{U}$ — azaz minden $i$-re $\widetilde{U}$ $i$-edik sorát $\widetilde{u}_{ii}$-vel osztjuk. Ekkor:

$$A = L\widetilde{U} = LD \cdot (D^{-1}\widetilde{U}) = LDU.$$

### Közvetlen kiszámítás

**Tétel — az LDU-felbontás közvetlen kiszámítása:**

Az elemek jó sorrendben (lásd LU-felbontás) számolva:

$$i = j \text{ (diag):} \quad d_{ii} = a_{ii} - \sum_{k=1}^{i-1} l_{ik} \cdot d_{kk} \cdot u_{ki},$$

$$i < j \text{ (felső):} \quad u_{ij} = \frac{1}{d_{ii}} \left( a_{ij} - \sum_{k=1}^{i-1} l_{ik} \cdot d_{kk} \cdot u_{kj} \right),$$

$$i > j \text{ (alsó):} \quad l_{ij} = \frac{1}{d_{jj}} \left( a_{ij} - \sum_{k=1}^{j-1} l_{ik} \cdot d_{kk} \cdot u_{kj} \right).$$

### Szimmetrikus mátrix LDU-felbontása — $LDL^\top$

**Tétel:** Ha $A$ szimmetrikus, akkor az LDU-felbontásban $U = L^\top$.

**Bizonyítás:** Szorozzuk a $A = LDU$ bal oldalát $L^{-1}$-gyel, jobb oldalát $(L^{-1})^\top$-vel:

$$L^{-1} A (L^{-1})^\top = L^{-1}(LDU)(L^{-1})^\top = DU(L^{-1})^\top.$$

A bal oldali mátrix szimmetrikus (mert $A$ szimmetrikus), a jobb oldali felső háromszögmátrix. Ebből következik, hogy a jobb oldali mátrix diagonális. $U(L^{-1})^\top \in \mathcal{U}_1$, így $U(L^\top)^{-1} = I$, azaz $U = L^\top$. $\square$

**Következmény:** Szimmetrikus mátrix esetén az $A = LDU$ felbontás valójában $A = LDL^\top$-felbontás. Elegendő $L$-t és $D$-t tárolni (csak az alsó háromszög rész). Ez a tárolási- és műveletigényt kb. a felére csökkenti: $\frac{1}{3}n^3 + \mathcal{O}(n^2)$.

### $LDL^\top$-felbontás közvetlen kiszámítása

**Tétel:** Az $L$ és $D$ mátrix elemei:

$$i = j \text{ (diag):} \quad d_{ii} = a_{ii} - \sum_{k=1}^{i-1} l_{ik} \cdot d_{kk} \cdot l_{ik},$$

$$i > j \text{ (alsó):} \quad l_{ij} = \frac{1}{d_{jj}} \left( a_{ij} - \sum_{k=1}^{j-1} l_{ik} \cdot d_{kk} \cdot l_{jk} \right).$$

Ha jó sorrendben számolunk, a jobb oldal mindig ismert.

### Numerikus példa ($LDL^\top$)

$$A = \begin{bmatrix} 1 & 2 & 1 \\ 2 & 8 & 6 \\ 1 & 6 & 6 \end{bmatrix}$$

GE-hányadosokat az eliminált pozíciókon tároljuk; $\sqrt{D}$-vel nem osztunk. Az elimináció lépésenkénti mátrixa (piros = tárolandó hányados, kék = maradék):

1. lépés: 1. oszlopban $l_{21}=2$, $l_{31}=1$; a jobb alsó $2\times 2$ maradékon folytatjuk.
2. lépés: $d_{22} = 4$, $l_{32}=1$; maradék: $d_{33}=1$.

Leolvasva: $d_{11}=1$, $d_{22}=4$, $d_{33}=1$, és

$$L = \begin{bmatrix} 1 & 0 & 0 \\ 2 & 1 & 0 \\ 1 & 1 & 1 \end{bmatrix}, \quad D = \begin{bmatrix} 1 & 0 & 0 \\ 0 & 4 & 0 \\ 0 & 0 & 1 \end{bmatrix}, \quad L^\top = \begin{bmatrix} 1 & 2 & 1 \\ 0 & 1 & 1 \\ 0 & 0 & 1 \end{bmatrix}. \quad \square$$

## Cholesky-felbontás röviden

Szimmetrikus, pozitív definit $A$ esetén $D$ átlója pozitív, így $A = LDL^\top = (L\sqrt{D})(L\sqrt{D})^\top = LL^\top$: ez a **Cholesky-felbontás**. Definíció, létezés és egyértelműség bizonyítása, a közvetlen képletek, műveletigény és alkalmazás: [[concepts/nummodi/cholesky-felbontas]] (9. tétel).

## Kapocs

- [[concepts/nummodi/lu-felbontas]] — LU-felbontás; az LDU és Cholesky közvetlen elődje
- [[concepts/nummodi/haromszogmatrixok]] — az $\mathcal{L}_1$, $\mathcal{U}_1$ mátrixhalmazok definíciói és zártsági tulajdonságai
- [[concepts/nummodi/schur-komplementer]] — megmaradási tételek; pozitív definitség öröklődése igazolja a Cholesky-felbontás elvégezhetőségét
- [[concepts/nummodi/gauss-eliminacio]] — GE alapjai; a Cholesky 2. módszere GE-alapon
- [[concepts/nummodi/linearis-egyenletrendszerek]] — LER megoldhatósága és módszerosztályok
- [[subjects/nummodi]] — kurzus áttekintése
- [[concepts/nummodi/cholesky-felbontas]] — a Cholesky-felbontás részletesen: bizonyítások, műveletigény, $LDL^\top$-vel való összevetés (9. tétel)
