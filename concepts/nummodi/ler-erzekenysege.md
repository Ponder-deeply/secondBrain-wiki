---
tags: [concept]
sources: [NM1_ea07.pdf]
derivation: source
updated: 2026-08-05
---

# LER érzékenysége — perturbációs tételek

A $Ax = b$ lineáris egyenletrendszer numerikus megoldásakor a jobboldali vektor $b$ és az együtthatómátrix $A$ csak közelítőleg ismert (mérési pontatlanság, kerekítési hiba). Az érzékenységi tételek megmutatják, hogy a bemeneti hiba legfeljebb annyiszorosára fúvódhat fel a megoldásban, amennyi a mátrix [[concepts/nummodi/kondicioszam|kondíciószáma]].

## LER érzékenysége a jobboldal perturbációjára

### Felállítás

Adott az $Ax = b$ LER. A jobboldalt perturbáljuk: legyen az „igazi" jobboldal $b + \Delta b$, ekkor a módosult LER megoldása $x + \Delta x$:

$$A(x + \Delta x) = b + \Delta b.$$

### Tétel

Ha $A$ invertálható és $b \neq 0$, akkor illeszkedő normákban

$$\frac{1}{\|A\| \cdot \|A^{-1}\|} \cdot \frac{\|\Delta b\|}{\|b\|} \leq \frac{\|\Delta x\|}{\|x\|} \leq \|A\| \cdot \|A^{-1}\| \cdot \frac{\|\Delta b\|}{\|b\|},$$

azaz

$$\frac{1}{\operatorname{cond}(A)} \cdot \delta b \leq \delta x \leq \operatorname{cond}(A) \cdot \delta b,$$

ahol $\delta b := \frac{\|\Delta b\|}{\|b\|}$ és $\delta x := \frac{\|\Delta x\|}{\|x\|}$ a relatív hibák.

### Bizonyítás

**(1)** $A(x + \Delta x) = b + \Delta b$-ből kivonjuk az $Ax = b$ LER-t: $A\Delta x = \Delta b$.

**(2)** Viszont $x = A^{-1}b$ és $\Delta x = A^{-1}\Delta b$.

**(3)** Négy alap-egyenlőtlenség (illeszkedő norma):
- (a) $\|b\| = \|Ax\| \leq \|A\|\cdot\|x\|$, tehát $\|x\| \geq \frac{\|b\|}{\|A\|}$.
- (b) $\|\Delta b\| = \|A\Delta x\| \leq \|A\|\cdot\|\Delta x\|$, tehát $\|\Delta x\| \geq \frac{\|\Delta b\|}{\|A\|}$.
- (c) $\|x\| = \|A^{-1}b\| \leq \|A^{-1}\|\cdot\|b\|$.
- (d) $\|\Delta x\| = \|A^{-1}\Delta b\| \leq \|A^{-1}\|\cdot\|\Delta b\|$.

**(4)** Alsó becslés (b) és (c) alapján:

$$\frac{\|\Delta x\|}{\|x\|} \geq \frac{\frac{\|\Delta b\|}{\|A\|}}{\|A^{-1}\|\cdot\|b\|} = \frac{1}{\|A\|\cdot\|A^{-1}\|}\cdot\frac{\|\Delta b\|}{\|b\|}.$$

**(5)** Felső becslés (a) és (d) alapján:

$$\frac{\|\Delta x\|}{\|x\|} \leq \frac{\|A^{-1}\|\cdot\|\Delta b\|}{\frac{\|b\|}{\|A\|}} = \|A\|\cdot\|A^{-1}\|\cdot\frac{\|\Delta b\|}{\|b\|}. \quad \square$$

### Numerikus példa

$$A = \begin{bmatrix}4{,}1 & 2{,}8 \\ 9{,}7 & 6{,}6\end{bmatrix}, \quad b = \begin{bmatrix}4{,}1 \\ 9{,}7\end{bmatrix}, \quad x = \begin{bmatrix}1 \\ 0\end{bmatrix}.$$

Módosított jobboldal: $b + \Delta b = \begin{bmatrix}4{,}11 \\ 9{,}7\end{bmatrix}$, megoldás: $x + \Delta x = \begin{bmatrix}0{,}34 \\ 0{,}97\end{bmatrix}$.

- $\delta b = \frac{\|\Delta b\|}{\|b\|} = 9{,}4959 \times 10^{-4}$
- $\delta x = \frac{\|\Delta x\|}{\|x\|} = 1{,}1732$
- $\delta x / \delta b = 1235{,}5$
- $\operatorname{cond}(A) = 1623$

A kondíciószám felső becslést ad a hányados $\delta x / \delta b$-re. $\square$

## LER érzékenysége a mátrix perturbációjára

### Felállítás

Most a mátrixot perturbáljuk: a módosult LER

$$(A + \Delta A)(x + \Delta x) = b.$$

### Tétel

Ha $A$ invertálható, $b \neq 0$ és $\|\Delta A\| \cdot \|A^{-1}\| < 1$, akkor indukált mátrixnormában

$$\frac{\|\Delta x\|}{\|x\|} \leq \frac{\|A\| \cdot \|A^{-1}\|}{1 - \|\Delta A\| \cdot \|A^{-1}\|} \cdot \frac{\|\Delta A\|}{\|A\|} = \frac{\operatorname{cond}(A)}{1 - \operatorname{cond}(A) \cdot \frac{\|\Delta A\|}{\|A\|}} \cdot \frac{\|\Delta A\|}{\|A\|}.$$

### Segédlemma

Ha $\|M\| < 1$, akkor $(I + M)$ invertálható és indukált mátrixnormában

$$\|(I + M)^{-1}\| \leq \frac{1}{1 - \|M\|}.$$

**Biz.:** Az $I + M$ sajátértékeire $\varrho(M) \leq \|M\| < 1$, ezért $|\lambda_i(M)| < 1$, vagyis az egységsugarú körön kívül helyezkednek el, így $1 + \lambda_i(M) \neq 0$, tehát $I + M$ invertálható. Vizsgáljuk az inverz normáját:

$$(I+M)^{-1} = I \cdot (I+M)^{-1} = (I+M-M)(I+M)^{-1} = I - M(I+M)^{-1},$$

$$\|(I+M)^{-1}\| \leq \|I\| + \|M\| \cdot \|(I+M)^{-1}\|,$$

$$(1 - \|M\|)\cdot\|(I+M)^{-1}\| \leq \|I\| = 1 \Rightarrow \|(I+M)^{-1}\| \leq \frac{1}{1 - \|M\|}. \quad \square$$

### Bizonyítás (a tételé)

Az $(A + \Delta A)(x + \Delta x) = b$-ből $Ax = b$-t kivonva és $A$-val balról osztva:

$$(I + A^{-1}\Delta A)\Delta x = -A^{-1}\Delta A \cdot x.$$

Mivel $\|A^{-1}\Delta A\| \leq \|A^{-1}\|\cdot\|\Delta A\| < 1$, a lemma alapján $(I + A^{-1}\Delta A)$ invertálható:

$$\Delta x = -(I + A^{-1}\Delta A)^{-1} A^{-1}\Delta A \cdot x.$$

Az inverz norma-becslésével:

$$\|\Delta x\| \leq \frac{1}{1 - \|A^{-1}\Delta A\|} \cdot \|A^{-1}\|\cdot\|\Delta A\|\cdot\|x\|,$$

$$\frac{\|\Delta x\|}{\|x\|} \leq \frac{\|A^{-1}\|\cdot\|\Delta A\|}{1 - \|A^{-1}\|\cdot\|\Delta A\|} = \frac{\|A\|\cdot\|A^{-1}\|}{1 - \|A\|\cdot\|A^{-1}\|\cdot\frac{\|\Delta A\|}{\|A\|}}\cdot\frac{\|\Delta A\|}{\|A\|} = \frac{\operatorname{cond}(A)}{1 - \operatorname{cond}(A)\cdot\frac{\|\Delta A\|}{\|A\|}}\cdot\frac{\|\Delta A\|}{\|A\|}. \quad \square$$

### Numerikus példa

Ugyanaz az $A$ mátrix, $\Delta A = \begin{bmatrix}0{,}01 & 0 \\ 0 & 0\end{bmatrix}$:

- $\delta A = \frac{\|\Delta A\|}{\|A\|} = 7{,}8495 \times 10^{-4}$
- $\delta x = \frac{\|\Delta x\|}{\|x\|} = 3{,}4507$
- $\delta x / \delta A = 4396{,}1$
- $\operatorname{cond}(A) = 1623$

## Egyesített tétel

Ha mind $A$, mind $b$ megváltozik ($(A + \Delta A)(x + \Delta x) = b + \Delta b$), és $\|\Delta A\|\cdot\|A^{-1}\| < 1$, akkor

$$\frac{\|\Delta x\|}{\|x\|} \leq \frac{\operatorname{cond}(A)}{1 - \operatorname{cond}(A)\cdot\frac{\|\Delta A\|}{\|A\|}} \cdot \left(\frac{\|\Delta A\|}{\|A\|} + \frac{\|\Delta b\|}{\|b\|}\right).$$

A kondíciószám tehát egyformán korlátozza a mátrix- és a jobboldal-perturbációból eredő hibát.

## Kapocs

- [[concepts/nummodi/kondicioszam]] — kondíciószám definíciója és tulajdonságai
- [[concepts/nummodi/relativ-maradek]] — maradékvektor és relatív maradék, mint a megoldás minőségének mérőszáma
- [[concepts/nummodi/matrixnormak]] — illeszkedő normák; indukált mátrixnormák
- [[concepts/nummodi/linearis-egyenletrendszerek]] — LER fogalma, megoldhatóság
- [[concepts/nummodi/hibaszamitas]] — hibaanalízis alapjai; relatív hiba fogalma
- [[subjects/nummodi]] — kurzus áttekintése
