---
tags: [concept, nummodi/lu-felbontas]
sources: [NM1_ea03.pdf]
derivation: source
updated: 2026-08-05
---

# Háromszögmátrixok

Alsó és felső háromszögmátrixok definíciója, halmazaik zártsági tulajdonságai, az $L_k$ elimináló mátrixok és inverzeik, valamint szorzatuk kompakt alakja — mindez az [[concepts/nummodi/lu-felbontas|LU-felbontás]] elméleti alapja.

## Definíciók

**Definíció — alsó háromszögmátrix:**
Az $L \in \mathbb{R}^{n \times n}$ mátrixot *alsó háromszögmátrixnak* nevezzük, ha $i < j$ esetén $l_{ij} = 0$ (a főátló felett csupa nulla).

$$\mathcal{L} := \{ L \in \mathbb{R}^{n \times n} : l_{ij} = 0 \;(i < j) \},$$
$$\mathcal{L}_1 := \{ L \in \mathbb{R}^{n \times n} : l_{ij} = 0 \;(i < j),\; l_{ii} = 1 \}.$$

**Definíció — felső háromszögmátrix:**
Az $U \in \mathbb{R}^{n \times n}$ mátrixot *felső háromszögmátrixnak* nevezzük, ha $i > j$ esetén $u_{ij} = 0$ (a főátló alatt csupa nulla).

$$\mathcal{U} := \{ U \in \mathbb{R}^{n \times n} : u_{ij} = 0 \;(i > j) \},$$
$$\mathcal{U}_1 := \{ U \in \mathbb{R}^{n \times n} : u_{ij} = 0 \;(i > j),\; u_{ii} = 1 \}.$$

## Háromszögmátrixok halmazának zártsági tulajdonságai

**Állítás:**

1. Ha $L', L'' \in \mathcal{L}$, akkor $L' \cdot L'' \in \mathcal{L}$.
2. Ha $U', U'' \in \mathcal{U}$, akkor $U' \cdot U'' \in \mathcal{U}$.
3. Ha $L', L'' \in \mathcal{L}_1$, akkor $L' \cdot L'' \in \mathcal{L}_1$.
4. Ha $U', U'' \in \mathcal{U}_1$, akkor $U' \cdot U'' \in \mathcal{U}_1$.
5. Ha $L \in \mathcal{L}$ és $\exists L^{-1}$, akkor $L^{-1} \in \mathcal{L}$.
6. Ha $U \in \mathcal{U}$ és $\exists U^{-1}$, akkor $U^{-1} \in \mathcal{U}$.
7. Ha $L \in \mathcal{L}_1$, akkor $\exists L^{-1}$ és $L^{-1} \in \mathcal{L}_1$.
8. Ha $U \in \mathcal{U}_1$, akkor $\exists U^{-1}$ és $U^{-1} \in \mathcal{U}_1$.

*Bizonyítás:* házi feladat (beadható).

## Az $L_k$ elimináló mátrixok

A [[concepts/nummodi/gauss-eliminacio|Gauss-elimináció]] $k$-adik lépése felírható egy alsó háromszögmátrixszal való bal oldali szorzásként.

**Definíció — $L_k$:**

$$L_k := I - \ell_k e_k^\top \in \mathbb{R}^{n \times n},$$

ahol $\ell_k \in \mathbb{R}^n$, $(\ell_k)_i = 0\;(i \le k)$, és $e_k \in \mathbb{R}^n$ a $k$-adik egységvektor. Konkrétan:

$$L_k = \begin{pmatrix} 1 & & & 0 \\ & \ddots & & \vdots \\ & & 1 & \\ -l_{k+1,k} & & & 1 \\ \vdots & & & \ddots \\ -l_{nk} & & & & 1 \end{pmatrix},$$

ahol $l_{ik} = \dfrac{a_{ik}^{(k-1)}}{a_{kk}^{(k-1)}}$ ($i = k+1,\ldots,n$) a GE-s hányadosok. Ekkor $L_k \cdot A^{(k-1)} = A^{(k)}$.

### $L_k$ inverze

**Állítás:**

$$L_k^{-1} = I + \ell_k e_k^\top.$$

**Bizonyítás:**
$$L_k \cdot L_k^{-1} = (I - \ell_k e_k^\top)(I + \ell_k e_k^\top) = I - \ell_k \underbrace{e_k^\top \ell_k}_{0} e_k^\top - \ell_k \underbrace{e_k^\top \ell_k}_{0} e_k^\top = I. \quad \square$$

(A szorzat zéró, mert $e_k^\top \ell_k = (\ell_k)_k = 0$.)

Szemléletesen: $L_k^{-1}$ ugyanolyan alakú, mint $L_k$, csak az átló alatti elemek előjele megfordul.

### $L_k$ mátrixok szorzata

**Állítás:**

$$L_1^{-1} \cdot L_2^{-1} \cdots L_{n-1}^{-1} = I + \ell_1 e_1^\top + \ell_2 e_2^\top + \ldots + \ell_{n-1} e_{n-1}^\top.$$

**Bizonyítás:** indukcióval.

*Alap:* $L_1^{-1} \cdot L_2^{-1} = (I + \ell_1 e_1^\top)(I + \ell_2 e_2^\top) = I + \ell_1 e_1^\top + \ell_2 e_2^\top + \ell_1 \underbrace{e_1^\top \ell_2}_{0} e_2^\top = I + \ell_1 e_1^\top + \ell_2 e_2^\top$.

*Lépés:* Tegyük fel, hogy $k+1 \le n-1$ és $L_1^{-1} \cdots L_k^{-1} = I + \ell_1 e_1^\top + \ldots + \ell_k e_k^\top$. Ekkor

$$L_1^{-1} \cdots L_k^{-1} \cdot L_{k+1}^{-1} = (I + \ell_1 e_1^\top + \ldots + \ell_k e_k^\top)(I + \ell_{k+1} e_{k+1}^\top)$$
$$= I + \ell_1 e_1^\top + \ldots + \ell_k e_k^\top + \ell_{k+1} e_{k+1}^\top + \underbrace{\ell_j e_j^\top \ell_{k+1}}_{0} e_{k+1}^\top$$
$$= I + \ell_1 e_1^\top + \ldots + \ell_k e_k^\top + \ell_{k+1} e_{k+1}^\top, \quad \square$$

ahol a kiesnek jelölt tagok nullák, mert $e_j^\top \ell_{k+1} = (\ell_{k+1})_j = 0$ minden $j \le k$-ra (a $\ell_{k+1}$ vektornál az első $k+1$ komponens nulla).

**Következmény:** Az $L = L_1^{-1} \cdots L_{n-1}^{-1}$ mátrix elemi $\ell_k$ vektorokból közvetlenül összeolvasható: az $\mathcal{L}_1$-beli mátrix $k$-adik oszlopába az $\ell_k$ vektor átló alatti részeit írjuk be, az átlón egyes állnak.

## Kapocs

- [[concepts/nummodi/lu-felbontas]] — az LU-felbontás definíciója, létezése, egyértelműsége, közvetlen kiszámítása
- [[concepts/nummodi/gauss-eliminacio]] — a Gauss-elimináció algoritmusa, melynek lépéseit az $L_k$ mátrixok írják le
- [[concepts/nummodi/linearis-egyenletrendszerek]] — LER fogalma és megoldási módszerek
