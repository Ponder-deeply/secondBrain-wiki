---
tags: [concept, nummodi/qr-felbontas-es-ortogonalizacio]
sources: [NM1_ea05.pdf]
derivation: source
updated: 2026-08-05
---

# QR-felbontás

Az $A \in \mathbb{R}^{n \times n}$ mátrix **QR-felbontásának** nevezzük a $Q \cdot R$ szorzatot, ha $A = QR$, ahol $Q \in \mathbb{R}^{n \times n}$ ortogonális mátrix, $R \in \mathcal{U}$ pedig felső háromszögmátrix.

## Létezés és egyértelműség

**Tétel:** Ha $\det(A) \neq 0$ (vagyis $A$ oszlopvektorai lineárisan függetlenek), akkor $A$-nak létezik QR-felbontása. Ha még feltesszük, hogy $r_{ii} > 0$ $\forall i$-re, akkor egyértelmű is.

### Létezés bizonyítása

A bizonyítást a [[concepts/nummodi/gram-schmidt-ortogonalizacio|Gram–Schmidt-féle ortogonalizációs eljárás]] adja: az $A$ mátrix oszlopaiból — amelyek a feltétel értelmében lineárisan függetlenek — előállítjuk a $Q$ oszlopait és $R$ ismeretlen elemeit.

Tekintsük a $Q \cdot R = A$ mátrixszorzást oszloponként:

$$\begin{bmatrix} q_1 & q_2 & \cdots & q_n \end{bmatrix} \cdot \begin{bmatrix} r_{11} & r_{12} & \cdots & r_{1n} \\ 0 & r_{22} & \cdots & r_{2n} \\ \vdots & & \ddots & \vdots \\ 0 & \cdots & 0 & r_{nn} \end{bmatrix} = \begin{bmatrix} a_1 & a_2 & \cdots & a_n \end{bmatrix}.$$

**1. lépés** ($k=1$): Az első oszlopból $r_{11} \cdot q_1 = a_1$, ezért

$$r_{11} := \|a_1\|_2, \qquad q_1 := \frac{1}{r_{11}} a_1.$$

**$k$-adik lépés** (általánosan): Tegyük fel, hogy $Q$ első $k-1$ oszlopát már előállítottuk (normáltak, egymásra merőlegesek), és $R$ első $k-1$ oszlopát is ismerjük. Az $a_k$ oszlopra:

$$a_k = \sum_{j=1}^{k} r_{jk} \cdot q_j \implies q_k = \frac{1}{r_{kk}}\left(a_k - \sum_{j=1}^{k-1} r_{jk} \cdot q_j\right).$$

Az $r_{jk}$ értékek ($j = 1, \ldots, k-1$) meghatározásához skalárisan szorzunk $q_i$-vel ($i = 1, \ldots, k-1$):

$$0 = \langle q_k, q_i \rangle \implies r_{ik} = \langle a_k, q_i \rangle.$$

Majd $r_{kk}$-t a normálási feltételből kapjuk:

$$r_{kk} = \left\|a_k - \sum_{j=1}^{k-1} r_{jk} \cdot q_j\right\|_2.$$

Így $q_k$ ortogonális az összes eddigi $q_i$ vektorra, és normált. $\square$

### Egyértelműség bizonyítása (indirekt)

Tegyük fel, hogy legalább két különböző QR-felbontásunk van:

$$A = Q_1 R_1 = Q_2 R_2,$$

ahol $R_1$ és $R_2$ diagonális elemei pozitívak. $A$-t szorozzuk balról $Q_2^{-1} = Q_2^\top$-val és jobbról $R_1^{-1}$-gyel:

$$\underbrace{(Q_2^\top Q_1)}_{\text{ortogonális}} = \underbrace{(R_2 R_1^{-1})}_{\in \mathcal{U}}.$$

Legyen $R := R_2 R_1^{-1}$. Mivel $Q := Q_2^\top Q_1$ ortogonális, $Q^\top Q = I = R^\top R$.

Az $R^\top R = I$ szorzatból (ahol $R$ felső háromszögmátrix):
- $r_{11} \cdot r_{11} = 1$, amiből $r_{11} > 0$ miatt $r_{11} = 1$.
- $j \neq 1$-re: $r_{11} \cdot r_{1j} = 0 \implies r_{1j} = 0$.
- $r_{22} \cdot r_{22} = 1 \implies r_{22} = 1$; $r_{22} \cdot r_{2j} = 0 \implies r_{2j} = 0$ ($j \neq 2$).
- A többi sorra hasonlóan: $R = I$, tehát $R_1 = R_2$ és $Q_1 = Q_2$. $\square$

**Megjegyzés:** Két különböző QR-felbontás esetén létezik olyan $D := \text{diag}(\pm 1, \ldots, \pm 1)$ mátrix, amelyre $A = \widetilde{Q} \cdot D \cdot D \cdot \widetilde{R} = \widetilde{Q} \cdot \widetilde{R}$.

## Miért jó a QR-felbontás?

Tegyük fel, hogy az $Ax = b$ LER megoldható és rendelkezésre áll az $A = QR$ felbontás. Ekkor $Ax = Q \cdot R \cdot x = b$ helyett:

1. **$Qy = b$ LER megoldása:** $y = Q^\top b$ (mivel $Q^{-1} = Q^\top$) — $2n^2 + \mathcal{O}(n)$ művelet.
2. **$Rx = y$ LER megoldása** (felső háromszögű): $n^2 + \mathcal{O}(n)$ művelet.

Együtt: oldjuk meg az $Rx = Q^\top b$ LER-t.

**Előállítás:** $\frac{2}{3}n^3 + \mathcal{O}(n^2)$ — ugyanannyi, mint a Gauss-elimináció (Num. mód. 2A tétel).

**Előny:** Ha sokszor ugyanaz az $A$ jobboldala változik, a QR-felbontást elég egyszer elvégezni. Numerikusan **stabilabb**, mint a közvetlen GE (különösen Householder-transzformációkkal).

## Kapcsolat más felbontásokkal

| Felbontás | Feltétel | Tényezők |
|---|---|---|
| [[concepts/nummodi/lu-felbontas]] | $\det(A_k)\neq 0$ | $L \in \mathcal{L}_1$, $U \in \mathcal{U}$ |
| [[concepts/nummodi/ldu-felbontas]] | szimmetrikus, pos. def. | $L, D, U$ ill. $LL^\top$ |
| QR | $\det(A) \neq 0$ | $Q$ ortogonális, $R \in \mathcal{U}$ |

## Kapocs

- [[concepts/nummodi/ortogonalis-matrixok]] — az ortogonális mátrix fogalma, tulajdonságai
- [[concepts/nummodi/gram-schmidt-ortogonalizacio]] — QR előállításának algoritmusa Gram–Schmidt-ortogonalizációval
- [[concepts/nummodi/householder-transzformacio]] — alternatív numerikusan stabil QR-előállítás
- [[concepts/nummodi/haromszogmatrixok]] — $\mathcal{U}$ (felső háromszögmátrixok) definíciója és tulajdonságai
- [[concepts/nummodi/lu-felbontas]] — az LU-felbontás mint rokon módszer
- [[concepts/nummodi/gauss-eliminacio]] — Gauss-elimináció alapjai
- [[concepts/nummodi/linearis-egyenletrendszerek]] — LER megoldási módszerek áttekintése
- [[subjects/nummodi]] — kurzus áttekintése
