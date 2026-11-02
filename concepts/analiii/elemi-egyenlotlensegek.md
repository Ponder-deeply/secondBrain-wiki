---
tags: [concept]
sources: [gyakorlat.pdf]
derivation: source
kind: theorem
element: air
updated: 2026-10-21
---

# Elemi egyenlőtlenségek

A mértékelméleti és metrikus terek fejezetében használt alapegyenlőtlenségek gyűjteménye: számtani–mértani közép, Bernoulli, háromszög-, Cauchy–Schwarz- és Minkowski-egyenlőtlenség.

## Tartalom

### Számtani és mértani közép

$a_1,\dots,a_n\ge0$ esetén
$$\left(\frac{\sum a_i}{n}\right)^n\ge\prod a_i,$$
egyenlőség csak $a_1=\dots=a_n$ esetén. Következmények:

- $a>0\Rightarrow a+\frac1a\ge2$, egyenlőség csak $a=1$-nél;
- $\prod a_i=1$, $a_i>0\Rightarrow\prod(1+a_i)\ge2^n$ (a $\frac{1+a_i}{2}\ge\sqrt{a_i}$ becsléssel);
- $2\le\left(1+\frac1n\right)^n<4$ (a jobb oldalhoz az $1\cdot\frac12\cdot\frac12\cdot\left(1+\frac1n\right)\cdots$ alak), és $\left(1+\frac1n\right)^n<\left(1+\frac1{n+1}\right)^{n+1}$, ha az $1$-es tényezőt hozzávesszük.

### Bernoulli-egyenlőtlenség

$$\prod_{i=1}^n(1+a_i)\ge1+\sum_{i=1}^na_i\qquad(a_i\ge-1,\ \text{azonos előjelűek}).$$

Speciális eset: $(1+x)^n\ge1+nx$ ($x\ge-1$). Alkalmazás: $\sqrt[2k+1]{2}=1+h_k$ esetén $2>1+(2k+1)h_k$, vagyis $h_k<\frac1{2k+1}$; ebből a $\prod\left(2-\sqrt[2k+1]2\right)$ alsó becslése adódik, és az összehasonlító kritériummal a megfelelő sor divergenciája. Hasonló bizonyítási technika a teljes indukció: $\frac{a^n+b^n}{2}\ge\left(\frac{a+b}2\right)^n$ ($a+b\ge0$).

### Abszolút érték, háromszög-egyenlőtlenség

$|a+b|\le|a|+|b|$, $\bigl||a|-|b|\bigr|\le|a-b|$. Az abszolút értékes egyenlőtlenségeket (pl. $|2x-1|<|x-1|$) a belső kifejezések előjele szerint esetszétválasztással oldjuk meg. Síkbeli alak: $\sqrt{(x+u)^2+(y+v)^2}\le\sqrt{x^2+y^2}+\sqrt{u^2+v^2}$.

### Cauchy–Schwarz és Minkowski

- **Cauchy–Schwarz** $\mathbb R^n$-ben: $\left|\sum x_iy_i\right|\le\|x\|\,\|y\|$; geometriailag $|\langle x,y\rangle|\le\|x\|\|y\|$, egyenlőség lineárisan függő vektoroknál. Bizonyítás: a $\|x+ty\|^2\ge0$ másodfokú polinom diszkriminánsa nem pozitív.
- **Minkowski** (háromszög-egyenlőtlenség): $\|x+y\|\le\|x\|+\|y\|$; a Cauchy–Schwarz-ból következik, mert $\|x+y\|^2=\|x\|^2+2\langle x,y\rangle+\|y\|^2\le(\|x\|+\|y\|)^2$.

### Becslési minták indukcióval

$\prod_{k=1}^n\frac{2k-1}{2k}<\frac1{\sqrt{2n+1}}$, $\sum_{k=1}^n\frac1{\sqrt k}>\sqrt n$ ($n\ge2$), $n!<\left(\frac{n+1}2\right)^n$ (AM–GM), $n^n\le(n!)^2$.

## Kapocs

- [[concepts/analiii/holder-es-minkowski-egyenlotlenseg]] — a Minkowski-egyenlőtlenség általános $\|\cdot\|_q$ alakja.
- [[concepts/analiii/skalaris-szorzat-ter]] — a Cauchy–Schwarz-egyenlőtlenség absztrakt alakja.
- [[concepts/analiii/normalt-vektorter]] — a háromszög-egyenlőtlenség a norma axiómája.
- [[concepts/analii/integral-egyenlotlensegek]] — az integrálokra vonatkozó megfelelők.
