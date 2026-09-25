---
tags: [concept, nummodi/ler-erzekenysege-es-kondicionaltsag]
sources: [NM1_ea07.pdf]
derivation: source
updated: 2026-08-05
---

# Kondíciószám (mátrixok)

Az $A$ mátrix kondíciószáma megmutatja, hogy a $Ax = b$ lineáris egyenletrendszer megoldása mennyire érzékeny a bemeneti adatok kis perturbációjára. Nagy kondíciószám rosszul kondicionált feladatot jelent: a jobboldali vektor vagy a mátrix apró változása a megoldásban aránytalanul nagy változást okozhat.

## Definíció

Adott $A \in \mathbb{R}^{n \times n}$ invertálható mátrix és $\|\cdot\|$ mátrixnorma esetén a

$$\operatorname{cond}(A) := \|A\| \cdot \|A^{-1}\|$$

mennyiséget az $A$ mátrix **kondíciószámának** nevezzük. Jele: $\kappa(A)$ (kappa).

**Megjegyzések:**
- Csak invertálható mátrixokra értelmezett.
- Értéke függ a normaválasztástól: $\operatorname{cond}_1(A)$, $\operatorname{cond}_2(A)$, stb.

## Tulajdonságok

### 1. rész

**(a)** Indukált mátrixnorma esetén $\operatorname{cond}(A) \geq 1$.

**Biz.:** $1 = \|I\| = \|A \cdot A^{-1}\| \leq \|A\| \cdot \|A^{-1}\| = \operatorname{cond}(A)$. $\square$

**(b)** $\operatorname{cond}(cA) = \operatorname{cond}(A)$ tetszőleges $c \in \mathbb{R}$, $c \neq 0$ esetén.

**Biz.:** $\operatorname{cond}(cA) = \|cA\| \cdot \|(cA)^{-1}\| = |c|\cdot\|A\| \cdot \frac{1}{|c|}\|A^{-1}\| = \operatorname{cond}(A)$. $\square$

**(c)** Ha $Q$ ortogonális, akkor $\operatorname{cond}_2(Q) = 1$.

**Biz.:** $\|Q\|_2 = \sup_{x\neq 0}\frac{\|Qx\|_2}{\|x\|_2} = \sup_{x\neq 0}\frac{\sqrt{x^\top Q^\top Q x}}{\|x\|_2} = 1$ és $\|Q^{-1}\|_2 = \|Q^\top\|_2 = 1$, tehát $\operatorname{cond}_2(Q) = 1$. $\square$

### 2. rész

**(d)** Ha $A$ szimmetrikus, akkor $\operatorname{cond}_2(A) = \dfrac{\max |\lambda_i(A)|}{\min |\lambda_i(A)|}$.

**Biz.:** $\|A\|_2 = \sqrt{\max \lambda_i(A^\top A)}$. Mivel $\lambda_i(A^\top A) = \lambda_i(A^2) = (\lambda_i(A))^2$, ezért $\|A\|_2 = \max |\lambda_i(A)|$. Az inverze: $\|A^{-1}\|_2 = \max |\lambda_i(A^{-1})| = \frac{1}{\min |\lambda_i(A)|}$. $\square$

**(e)** Ha $A$ szimmetrikus pozitív definit, akkor $\operatorname{cond}_2(A) = \dfrac{\max \lambda_i(A)}{\min \lambda_i(A)}$.

**Biz.:** Pozitív definitség miatt az abszolút érték nem kell. $\square$

**(f)** Ha $A$ invertálható, akkor $\operatorname{cond}(A) \geq \dfrac{\max |\lambda_i(A)|}{\min |\lambda_i(A)|}$.

**Biz.:** $\|A\| \geq \varrho(A) = \max |\lambda_i(A)|$ és $\|A^{-1}\| \geq \varrho(A^{-1}) = \frac{1}{\min |\lambda_i(A)|}$. $\square$

## Kondíciószám és szorzatfelbontások

### LU-felbontás hatása

Az $LU$-felbontás **nem javítja** a kondíciószámot. Formálisan:

$$\operatorname{cond}(A) \leq \operatorname{cond}(L) \cdot \operatorname{cond}(U).$$

**Biz.:** $Ax = b \Rightarrow LUx = b$; $\|A\| \leq \|L\|\cdot\|U\|$ és $\|A^{-1}\| \leq \|U^{-1}\|\cdot\|L^{-1}\|$. $\square$

Sőt, $\operatorname{cond}(L)$, $\operatorname{cond}(U) \gg \operatorname{cond}(A)$ előfordulhat, tehát Gauss-elimináció nagyon pontatlan eredményt adhat.

### QR-felbontás és Cholesky-felbontás hatása

A $QR$-felbontás **nem változtatja** meg a feladat kondícionáltságát, mivel $\operatorname{cond}_2(Q) = 1$. Hasonlóan a Cholesky-felbontás sem ront a kondíciószámon. Ez indokolja a $QR$- és Cholesky-alapú módszerek stabilitását.

## Numerikus példák: kondíciószám és mátrixcsaládok

### Hilbert-mátrix

Az $n \times n$-es Hilbert-mátrix $H_n = \left(\frac{1}{i+j-1}\right)_{i,j=1}^n$. Kondíciószáma exponenciálisan nő a mérettel:

$$\operatorname{cond}_2(H_n) \approx \exp(3{,}1 n) \approx 22^n.$$

A $H_5$ esetén $\operatorname{cond}_2(H_5) \approx 4{,}7661 \times 10^5$. Ez azt jelenti: ha a jobboldali vektort $\delta b \approx 3 \times 10^{-3}$ relatív hibával adjuk meg, a megoldás relatív hibája $\delta x \approx 114$ is lehet — a megoldás gyakorlatilag elvész.

### Vandermonde-mátrix

Az $[0,1]$ intervallum egyenletes felosztású pontjaiból képzett Vandermonde-mátrixra:

$$\operatorname{cond}_2(V_n) \approx \exp(1{,}85 n) \approx 6{,}4^n.$$

### Véletlenszerű és tridiagonális mátrixok

A tridiag$(-1, 2, -1)$ típusú mátrixok és véletlen (rand$_n$) mátrixok kondíciószáma mérsékeltebb növekedést mutat.

## Kapocs

- [[concepts/nummodi/matrixnormak]] — mátrixnormák definíciója, indukált normák, spektrálsugár
- [[concepts/nummodi/ler-erzekenysege]] — LER érzékenységének tételei (jobboldal és mátrix perturbációja)
- [[concepts/nummodi/hibaszamitas]] — kondíciószám skaláris eset: $c(f,a)$; hibaanalízis alapjai
- [[concepts/nummodi/linearis-egyenletrendszerek]] — LER megoldási módszerei
- [[concepts/nummodi/lu-felbontas]] — LU-felbontás és kondíciószám kapcsolata
- [[concepts/nummodi/qr-felbontas]] — QR-felbontás stabilitása, kondíciószám megmarad
- [[subjects/nummodi]] — kurzus áttekintése
