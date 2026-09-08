---
tags: [concept]
sources: [SimonP-Anal2.pdf]
references: ["Simon Péter: Analízis II., 4.3. szakasz, 4.4. iv)–v) megjegyzés"]
derivation: source
updated: 2026-09-07
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

### Miért nem elég a determináns

Az, hogy $\det f''(a) \ne 0$, önmagában semmit sem mond a szélsőértékről; a **definitség** kell, amit $n = 2$-ben a Sylvester-kritérium a $d_1 = \partial_{11}f(a)$ és $d_2 = \det f''(a)$ sarokdeterminánsokból olvas ki.

## Kapocs

- [[concepts/analiii/magasabbrendu-parcialis-derivaltak]] — a mátrix elemeinek definíciója.
- [[concepts/analiii/young-tetel]] — a szimmetria forrása.
- [[concepts/analiii/kvadratikus-alak-definitsege]] — amit a mátrixból ki kell olvasni.
- [[concepts/analiii/lokalis-szelsoertek-feltetelei]] — a fő alkalmazás.
- [[concepts/analiii/tobbvaltozos-taylor-formula]] — a másodrendű tag.
