---
tags: [concept]
sources: [NM1_ea05.pdf]
derivation: source
updated: 2026-09-04
---

# Ortogonális mátrixok

Egy $Q \in \mathbb{R}^{n \times n}$ mátrix **ortogonális**, ha az inverze a transzponáltja: $Q^\top Q = I$. Ekkor $QQ^\top = I$ is teljesül, és $Q^{-1} = Q^\top$.

## Alapfogalmak

### Skaláris szorzat

Az $x, y \in \mathbb{R}^n$ vektorok **skaláris szorzata**:

$$\langle x, y \rangle := y^\top x = \sum_{k=1}^{n} x_k \cdot y_k.$$

### Kettes norma (vektor „hossza")

$$\|v\|_2 := \sqrt{\langle v, v \rangle} = \sqrt{v^\top v} = \left(\sum_{k=1}^{n} v_k^2\right)^{1/2}.$$

### Ortonormált rendszer

A $q_1, \ldots, q_n \in \mathbb{R}^n$ vektorok **ortonormált rendszert** alkotnak, ha

$$\langle q_i, q_j \rangle = \delta_{ij} = \begin{cases} 0 & \text{ha } i \neq j, \\ 1 & \text{ha } i = j. \end{cases}$$

Jelölések és fogalmak:
- $\langle q_i, q_j \rangle = \delta_{ij}$ — Kronecker-féle delta.
- $q_i \perp q_j \iff \langle q_i, q_j \rangle = 0$ ($i \neq j$): az oszlopok **merőlegesek** egymásra.
- $\|q_i\|_2 = 1$: minden oszlopvektor **normált** (egységnyi hosszú).

### Ortogonális rendszer (normálás nélkül)

A $q_1, \ldots, q_n \in \mathbb{R}^n$ vektorok **ortogonális rendszert** alkotnak, ha

$$\langle q_i, q_j \rangle = 0 \qquad (i \neq j).$$

## Állítások ortogonális mátrixokról

**Állítás 1 — oszlopvektorok ortonormált rendszert alkotnak:**
Egy $Q \in \mathbb{R}^{n \times n}$ ortogonális mátrix oszlopai mint vektorok ortonormált rendszert alkotnak.

*Bizonyítás:* Gondoljuk bele: $Q^\top Q = I$. $\square$

**Állítás 2 — ortogonális rendszerből álló mátrix:**
Ha $q_1, \ldots, q_n \in \mathbb{R}^n$ vektorok ortogonális rendszert alkotnak, akkor a $Q := (q_1, \ldots, q_n) \in \mathbb{R}^{n \times n}$ mátrix esetén a $Q^\top Q$ szorzatmátrix **diagonális**. ($QQ^\top$ általában nem.)

*Bizonyítás:* Gondoljuk bele: $Q^\top Q = D$ diagonális mátrix. $\square$

**Állítás 3 — ortogonális mátrixok szorzata:**
Ha $Q_1, Q_2 \in \mathbb{R}^{n \times n}$ ortogonális mátrixok, akkor a szorzatuk, $Q_1 Q_2$ is ortogonális.

*Bizonyítás:*

$$(Q_1 Q_2)^\top (Q_1 Q_2) = Q_2^\top \underbrace{Q_1^\top Q_1}_{I} Q_2 = Q_2^\top Q_2 = I. \quad \square$$

## Példák ortogonális mátrixokra

$$\begin{pmatrix} 1 & 0 \\ 0 & 1 \end{pmatrix}, \qquad \frac{1}{\sqrt{2}}\begin{pmatrix} 1 & -1 \\ 1 & 1 \end{pmatrix}, \qquad \begin{pmatrix} \cos\varphi & -\sin\varphi \\ \sin\varphi & \cos\varphi \end{pmatrix}.$$

## Kapocs

- [[concepts/nummodi/qr-felbontas]] — a QR-felbontás $Q$ tényezője ortogonális mátrix
- [[concepts/nummodi/gram-schmidt-ortogonalizacio]] — ortogonális/ortonormált rendszer előállítási módszere
- [[concepts/nummodi/householder-transzformacio]] — speciális ortogonális mátrixok (tükrözések)
- [[concepts/nummodi/haromszogmatrixok]] — felső háromszögmátrixok, a QR másik tényezője
- [[subjects/nummodi]] — kurzus áttekintése
- [[concepts/linalg/szemleltetesek]] — az ortogonális leképezések geometriai szemléltetése (Gram–Schmidt/QR jelenet)
