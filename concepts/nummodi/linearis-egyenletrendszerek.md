---
tags: [concept, nummodi/linearis-egyenletrendszerek-es-gauss-eliminacio]
sources: [NM1_ea02.pdf]
derivation: source
updated: 2026-08-05
---

# Lineáris egyenletrendszerek

Lineáris egyenletrendszer (LER) fogalma, mátrixos alakja, megoldhatóságának feltételei és a megoldási módszerek áttekintése.

## Definíció

**Lineáris egyenletrendszer (LER)** hagyományos alakja:

$$a_{11}x_1 + a_{12}x_2 + \cdots + a_{1n}x_n = b_1$$
$$a_{21}x_1 + a_{22}x_2 + \cdots + a_{2n}x_n = b_2$$
$$\vdots$$
$$a_{n1}x_1 + a_{n2}x_2 + \cdots + a_{nn}x_n = b_n$$

$n$ egyenlet, $n$ ismeretlen.

**Mátrixos alak:**

$$A \cdot x = b, \quad A \in \mathbb{R}^{n \times n},\; b,x \in \mathbb{R}^n.$$

ahol $A$ az **együtthatómátrix**, $b$ a **jobboldali vektor**, $x$ az ismeretlen vektor. A feladat: $A$ és $b$ adottak, keressük $x$-et.

## Megoldhatóság — tétel (lin. alg.-ból)

- A LER megoldható $\iff$ $b$ felírható az $A$ oszlopvektorainak lineáris kombinációjaként.
- **Egyértelműen** létezik megoldás $\iff$ $A$ oszlopai lineárisan függetlenek $\iff$ $\operatorname{rang}(A) = n$ $\iff$ $\det(A) \ne 0$ $\iff$ $A$ invertálható (és ekkor $x = A^{-1}b$).

**Megjegyzések:**
- Ha $A$ speciális alakú (pl. diagonális vagy háromszög alakú), a megoldás egyszerűen megkapható.
- A Cramer-szabályt legfeljebb $3 \times 3$-as mátrixokra érdemes alkalmazni.

## Motiváló alkalmazások

### Kriptaritmétikai feladat
A MATEK betűk 5 különböző számjegyet jelölnek; az
$$M+A+T+E+K=25,\quad M+A=11,\quad A+T=10,\quad T+E=12,\quad E+K=10$$
feltételek 5 egyenletből álló lineáris rendszert alkotnak 5 ismeretlennel.

### Gazdasági ráfordítások (Leontief-modell)
Egy üzem termékei közötti közvetlen ráfordítások mátrixa $K$; a **teljes ráfordítások mátrixa**
$$T = (I - K)^{-1}.$$
$x$ alapanyagból $y = (I-K)\cdot x$ végtermék lesz; $y$-hoz $x = T \cdot y = (I-K)^{-1} \cdot y$ alapanyag kell.

### Hálózatok stacionárius modellezése
Villamos hálózatok, víz- és gázellátó csőrendszerek irányított gráffal írhatók le. Az első **Kirchhoff-féle törvény** (csomóponti törvény: a csomópontban találkozó élek áramainak összege nulla) minden csomópontra egy lineáris relációt ad — ezek összessége adja a LER-t.

## Megoldási módszerek áttekintése

### Direkt módszerek (véges lépésszám, „pontos" megoldás)
- **[[concepts/nummodi/gauss-eliminacio|Gauss-elimináció]]**, progonka módszer
- **[[concepts/nummodi/lu-felbontas|LU-felbontás]]**, $LDU$-, $LL^T$- (Cholesky-)felbontás
  - **[[concepts/nummodi/qr-felbontas|QR-felbontás]]**: [[concepts/nummodi/gram-schmidt-ortogonalizacio|Gram–Schmidt-ortogonalizáció]], [[concepts/nummodi/householder-transzformacio|Householder-transzformáció]]
- ILU-felbontás

### Iterációs módszerek (vektorsorozat, mely a megoldáshoz „tart")
- Mátrixnormák, [[concepts/nummodi/banach-fixponttetel-rn|Banach-féle fixponttétel]]
- [[concepts/nummodi/iteracios-modszerek-ler|Iterációs módszerek általános kerete]] ($A=P+Q$ felbontás)
- [[concepts/nummodi/jacobi-iteracio|Jacobi-iteráció]] és csillapított Jacobi-iteráció
- Gauss–Seidel-iteráció
- Richardson-iteráció
- ILU-algoritmus

### Variációs módszerek (egy „célfüggvény" minimalizálása által)
- Gradiens-módszer
- Konjugált gradiens-módszer

## Kapocs

- [[concepts/nummodi/gauss-eliminacio]] — a Gauss-elimináció részletes algoritmusa és elemzése
- [[concepts/nummodi/lu-felbontas]] — LU-felbontás: definíció, létezés, egyértelműség, közvetlen kiszámítás
- [[concepts/nummodi/haromszogmatrixok]] — alsó/felső háromszögmátrixok, $L_k$ elimináló mátrixok
- [[concepts/nummodi/tematika]] — kurzus tematikája, összes módszer listája
- [[concepts/nummodi/hibaszamitas]] — a megoldás numerikus pontosságát befolyásoló hibák
- [[concepts/nummodi/algoritmus-stabilitas]] — stabil vs. instabil algoritmus fogalma
- [[concepts/nummodi/kondicioszam]] — mátrix kondíciószáma; érzékenység mérőszáma
- [[concepts/nummodi/ler-erzekenysege]] — LER perturbációs tételei: jobboldal és mátrix perturbációja
- [[concepts/nummodi/relativ-maradek]] — maradékvektor ($r = b - A\tilde{x}$) és relatív maradék ($\eta$)
- [[concepts/nummodi/iteracios-modszerek-ler]] — iterációs módszerek általános kerete, $A=L+D+U$ felbontás, $A=P+Q$ keret
- [[concepts/nummodi/banach-fixponttetel-rn]] — fixponttétel, kontrakció, $\varrho(B)<1$ ekvivalens konvergenciafeltétel
- [[concepts/nummodi/jacobi-iteracio]] — Jacobi-iteráció és csillapított Jacobi-iteráció ($J(\omega)$)
- [[concepts/nummodi/qr-felbontas]] — QR-felbontás definíciója, létezés/egyértelműség, LER-es alkalmazás
- [[concepts/nummodi/gram-schmidt-ortogonalizacio]] — Gram–Schmidt-ortogonalizáció algoritmusa, $2n^3$ műveletigény
- [[concepts/nummodi/householder-transzformacio]] — Householder-tükrözés, numerikusan stabil QR-előállítás
- [[concepts/nummodi/ortogonalis-matrixok]] — ortogonális mátrix, ortonormált rendszer
- [[subjects/nummodi]] — kurzus áttekintése
