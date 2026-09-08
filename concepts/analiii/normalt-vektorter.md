---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf, SimonP-Anal2.pdf]
references: ["Simon Péter: Analízis II., 1.2. iv)–v) megjegyzés"]
derivation: source
updated: 2026-09-07
---

# Normált vektortér

A normált vektortér olyan vektortér, amelyen a vektorok „hossza" mérhető; a norma automatikusan metrikát indukál, így minden normált tér metrikus tér is. A legfontosabb példák az $\mathbb{R}^p$-beli $L^q$-normák és a $C[a,b]$-beli maximumnorma.

## Tartalom

### Definíció

**Normált vektortér:** a $\bigl(V, \|\cdot\|\bigr)$ pár, ahol $V \neq \emptyset$ valós vagy komplex vektortér, és $\|\cdot\| : V \to [0,\infty)$ *norma*:

1. $\forall x \in V:\ \|x\| \geq 0$, és $\|x\| = 0 \iff x = 0$;
2. $\forall x \in V,\ c \in \mathbb{R}$ (ill. $\mathbb{C}$): $\|cx\| = |c| \cdot \|x\|$ (homogenitás);
3. $\forall x, y \in V:\ \|x + y\| \leq \|x\| + \|y\|$ (háromszög-egyenlőtlenség).

A $d(x,y) = \|y - x\|$ függvény metrika, tehát minden normált vektortér [[concepts/analiii/metrikus-ter]] is. A megfordítás nem igaz: a diszkrét metrika például nem származik normából.

### Az $L^q$-norma

$0 < q < \infty$ és $x \in \mathbb{R}^p$ esetén

$$\|x\|_q = \bigl(|x_1|^q + \dots + |x_p|^q\bigr)^{1/q}, \qquad \|x\|_\infty = \max\bigl(|x_1|, \dots, |x_p|\bigr).$$

Speciálisan $\|x\|_2 = |x|$ az euklideszi hossz, és $\|x\|_\infty = \lim_{q \to \infty} \|x\|_q$. A gyakorlatban leggyakrabban $L^1$, $L^2$ és $L^\infty$ szerepel.

**Fontos megszorítás:** $\|\cdot\|_q$ csak $q \geq 1$ esetén norma — a háromszög-egyenlőtlenség $0 < q < 1$-re elromlik. Két dimenzióban például

$$\bigl\|(1,1)\bigr\|_q = 2^{1/q} > 2 = \bigl\|(1,0)\bigr\|_q + \bigl\|(0,1)\bigr\|_q.$$

Az $1 \leq q \leq \infty$ esetben a háromszög-egyenlőtlenség sem triviális; ezt a [[concepts/analiii/holder-es-minkowski-egyenlotlenseg]] adja meg.

### Normák $C[a,b]$-n

- $q \geq 1$ esetén $\|f\|_q = \Bigl(\int_a^b |f(t)|^q\, \mathrm{d}t\Bigr)^{1/q}$;
- $\|f\|_\infty = \max |f|$ — a *maximumnorma*, a leggyakoribb; sokszor egyszerűen $\|f\|$-fel jelöljük.

### Sorozatterek

A $\mathbb{K}^n$ végtelen dimenziós megfelelője a $0<p<+\infty$ mellett értelmezett

$$\ell^p := \Bigl\{(x_n):\mathbb{N}\to\mathbb{K} \ :\ \sum_{n=0}^\infty |x_n|^p < +\infty\Bigr\}, \qquad \|x\|_p = \Bigl(\sum_{n=0}^\infty |x_n|^p\Bigr)^{1/p},$$

illetve a korlátos sorozatok $\ell^\infty$ tere a $\|x\|_\infty = \sup\{|x_n| : n\in\mathbb{N}\}$ normával. Ezek $1\leq p\leq+\infty$ esetén mind normált — sőt teljes, azaz Banach- — terek.

## Kapocs

- [[concepts/analiii/metrikus-ter]] — a norma által indukált metrika alapstruktúrája
- [[concepts/analiii/holder-es-minkowski-egyenlotlenseg]] — az $L^q$-norma háromszög-egyenlőtlenségének bizonyítása
- [[concepts/analiii/ekvivalens-normak]] — véges dimenzióban minden norma ekvivalens
- [[concepts/analiii/cauchy-sorozat-es-teljes-ter]] — a teljes normált tér a Banach-tér
- [[concepts/analiii/skalaris-szorzat-ter]] — a norma erősebb rokona; $\|\cdot\|_p$ csak $p=2$-re származik skaláris szorzatból
- [[concepts/analiii/metrikus-terek-szorzata]] — szorzatnorma véges sok normált tér Descartes-szorzatán
