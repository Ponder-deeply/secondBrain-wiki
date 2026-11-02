---
tags: [concept]
sources: [SimonP-Anal2.pdf, 06_ea_An3_2022_tavasz.pdf, 07_ea_An3_2022_tavasz.pdf, RopzhKerdesek.pdf, ElozetesKerdesekMegajanlottVizsgajegyhez1.pdf, 07_gyak_An_III_2022_tavasz.pdf]
references: ["Simon Péter: Analízis II., 4.3. szakasz, 4.4. iv)–v) megjegyzés"]
derivation: source
kind: definition
element: fire
updated: 2026-10-21
---

# Hesse-mátrix (második deriváltmátrix)

Az $f \in D^2\{a\}$ függvény második deriváltja a másodrendű parciális deriváltakból álló $f''(a) \in \mathbb{R}^{n\times n}$ mátrix, amely a Young-tétel miatt szimmetrikus, és amelyhez tartozó kvadratikus alak dönti el a szélsőérték kérdését.

## Tartalom

### A mátrix

Ha $f \in \mathbb{R}^n \to \mathbb{R}$ és $f \in D^2\{a\}$, akkor

$$f''(a) := \big(\partial_{ij} f(a)\big)_{i,j=1}^n = \begin{bmatrix} \partial_{11}f(a) & \dots & \partial_{1n}f(a)\\ \vdots & \ddots & \vdots \\ \partial_{n1}f(a) & \dots & \partial_{nn}f(a)\end{bmatrix} \in \mathbb{R}^{n\times n}.$$

A [[concepts/analiii/young-tetel|Young-tétel]] szerint ez **szimmetrikus** mátrix.

### Példa

$f(x,y,z) := x^3 + y^2 z + z^3 + xyz$ esetén

$$f''(1,0,2) = \begin{bmatrix} 6 & 2 & 0 \\ 2 & 4 & 1 \\ 0 & 1 & 12\end{bmatrix}.$$

### A hozzá tartozó kvadratikus alak

Az $f''(a)$ szimmetrikus, ezért meghatároz egy [[concepts/analiii/kvadratikus-alak-definitsege|kvadratikus alakot]]:

$$Q^f_a(x) := \langle f''(a)x,\, x\rangle = \sum_{i=1}^n\sum_{k=1}^n \partial_{ik}f(a)\, x_i x_k \qquad (x \in \mathbb{R}^n).$$

**Ez a mátrix egyetlen igazi felhasználása.** A [[concepts/analiii/tobbvaltozos-taylor-formula|Taylor-formula]] másodrendű tagja $\tfrac12 Q^f_a(h)$, és a [[concepts/analiii/lokalis-szelsoertek-feltetelei|szélsőérték-feltételek]] mind $Q^f_a$ definitségéről szólnak. Egy dimenzióban $Q^f_a(x) = f''(a)x^2$, tehát a definitség épp az $f''(a)$ előjele — a többváltozós elmélet ezt a szám-előjelet cseréli mátrix-definitségre.

### A Hesse-mátrix a Taylor-polinomban (gyak 7. lap)

A másodrendű Taylor-polinomban a $|i|=2$ multiindexek összege és a Hesse-mátrixos alak megegyezik. $n=2$-ben $i\in\{(2,0),(1,1),(0,2)\}$, $i!=2,1,2$, $h^i=h_1^2,h_1h_2,h_2^2$, ezért (a Young-tétel miatt $\partial_{12}f=\partial_{21}f$)

$$\sum_{|i|=2}\frac{\partial^i f(a)}{i!}h^i=\tfrac12\partial_1^2f(a)h_1^2+\partial_{12}f(a)h_1h_2+\tfrac12\partial_2^2f(a)h_2^2=\tfrac12\sum_{j,l=1}^2\partial_{jl}f(a)h_jh_l=\tfrac12\langle f''(a)\cdot h,h\rangle .$$

Itt $f''(a)\cdot h$ az oszlopvektor, amelynek $l$-edik koordinátája $\sum_j\partial_{lj}f(a)h_j$. Általános $n$-ben a vegyes tagokat ($j<l$, $i!=1$) és a négyzetes tagokat ($i_r=2$, $i!=2$) összevonva ugyanez adódik: $\sum_{|i|=2}\frac{\partial^if(a)}{i!}h^i=\langle f''(a)h,h\rangle/2$ (gyak 7. lap, 1. feladat).

**Számolási példa.** $P=2x^2-xy-y^2-6x-3y+5$ esetén $P''(a)=\begin{bmatrix}4&-1\\-1&-2\end{bmatrix}$ minden $a$-ban (állandó), és $\tfrac12\langle P''h,h\rangle=2h_1^2-h_1h_2-h_2^2$.

### Miért nem elég a determináns

Az, hogy $\det f''(a) \ne 0$, önmagában semmit sem mond a szélsőértékről; a **definitség** kell, amit $n = 2$-ben a Sylvester-kritérium a $d_1 = \partial_{11}f(a)$ és $d_2 = \det f''(a)$ sarokdeterminánsokból olvas ki.

## Kapocs

- [[concepts/analiii/magasabbrendu-parcialis-derivaltak]] — a mátrix elemeinek definíciója.
- [[concepts/analiii/young-tetel]] — a szimmetria forrása.
- [[concepts/analiii/kvadratikus-alak-definitsege]] — amit a mátrixból ki kell olvasni.
- [[concepts/analiii/lokalis-szelsoertek-feltetelei]] — a fő alkalmazás.
- [[concepts/analiii/tobbvaltozos-taylor-formula]] — a másodrendű tag.
- [[concepts/analiii/vizsgakerdesek-es-bizonyitando-tetelek]] — a témához tartozó megajánlott vizsgajegy- és röpdolgozat-kérdések.
