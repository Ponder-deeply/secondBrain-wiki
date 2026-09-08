---
tags: [concept]
sources: [SimonP-Anal2.pdf]
references: ["Simon Péter: Analízis II., 4.3.1. Tétel"]
derivation: source
updated: 2026-09-07
---

# Young-tétel

Ha $f \in C^s\{a\}$, akkor az $s$-edrendű parciális deriváltak értéke nem függ a deriválás sorrendjétől: $\partial_{k_1\dots k_s} f(a) = \partial_{j_1 \dots j_s} f(a)$ tetszőleges permutációra.

## Tartalom

### A tétel

Legyen $2 \le n \in \mathbb{N}$, $f \in \mathbb{R}^n \to \mathbb{R}$, $a \in \operatorname{int} D_f$, $2 \le s \in \mathbb{N}$ és $f \in C^s\{a\}$. Ekkor tetszőleges $k_1, \dots, k_s \in \{1,\dots,n\}$ indexekre és azok bármely $j_1, \dots, j_s$ permutációjára

$$\partial_{k_1 \dots k_s} f(a) = \partial_{j_1\dots j_s} f(a).$$

Teljes indukcióval elég az $s = 2$, sőt $i \ne j$ és $n = 2$ esettel foglalkozni, azaz azt belátni, hogy $f \in D^2\{a\}$ esetén $\partial_{12} f(a) = \partial_{21} f(a)$.

### Az ellenpélda: feltétel nélkül hamis

$$f(x,y) := \begin{cases} xy\cdot\dfrac{x^2 - y^2}{x^2 + y^2} & (x^2 + y^2 \ne 0)\\[4pt] 0 & (x = y = 0)\end{cases}$$

Erre a függvényre **léteznek** a vegyes másodrendű parciális deriváltak az origóban, mégis

$$\partial_{12} f(0,0) = -1 \ne 1 = \partial_{21} f(0,0).$$

A számolás: $\partial_{12}f(0,0) = \varphi'(0)$, ahol $\varphi(t) := \partial_1 f(0,t)$. Ha $t \ne 0$, akkor

$$\varphi(t) = \lim_{\tau\to 0}\frac{f(\tau,t)}{\tau} = \lim_{\tau\to 0}\frac{t(\tau^2 - t^2)}{\tau^2 + t^2} = -t,$$

és $\varphi(0) = 0$, tehát $\varphi(t) = -t$ minden $t$-re, azaz $\varphi'(0) = -1$. A szimmetrikus számolás $\partial_{21}f(0,0) = 1$-et ad.

**A tanulság.** A puszta létezés nem elég; a felcserélhetőséghez a **környezetbeli, elég sokszori** differenciálhatóság kell. Ugyanaz a mintázat, mint a [[concepts/analiii/differencialhatosagi-fogalmak-hierarchiaja|differenciálhatósági fogalmaknál]]: az egydimenziós (parciális) információ nem határozza meg a kétdimenziós viselkedést.

### Mit tesz lehetővé

- A [[concepts/analiii/hesse-matrix|Hesse-mátrix szimmetriáját]] — enélkül nem volna kvadratikus alak.
- A [[concepts/analiii/tobbvaltozos-taylor-polinom|multiindexes jelölést]]: a $\partial^i f$ szimbólum csak akkor jóldefiniált, ha a sorrend közömbös.
- A [[concepts/analiii/rotaciomentes-vektormezo|rotációmentesség]] $\partial_i f_j = \partial_j f_i$ szükséges feltételét primitív függvény létezéséhez.

## Kapocs

- [[concepts/analiii/magasabbrendu-parcialis-derivaltak]] — a felcserélendő deriváltak definíciója.
- [[concepts/analiii/hesse-matrix]] — a szimmetria közvetlen haszna.
- [[concepts/analiii/tobbvaltozos-taylor-polinom]] — a multiindexes jelölés jogalapja.
- [[concepts/analiii/rotaciomentes-vektormezo]] — ahol a szimmetria szükséges feltételként jelenik meg.
- [[concepts/analiii/differencialhatosagi-fogalmak-hierarchiaja]] — ugyanaz az „egydimenziós információ kevés" mintázat.
