---
tags: [concept]
sources: [SimonP-Anal2.pdf, 06_ea_An3_2022_tavasz.pdf, An_III_Gyak_2022_tavasz.pdf, Analizis-3-gyakorlati-jegyzet-ELTE-IK.pdf, gyakorlat.pdf, ElozetesMegajanlottVizsgaTetelek1.pdf, RopzhKerdesek.pdf, ElozetesKerdesekMegajanlottVizsgajegyhez1.pdf, 06_gyak_An_III_2022_tavasz.pdf]
references: ["Simon Péter: Analízis II., 4.3.1. Tétel"]
derivation: source
kind: theorem
element: water
updated: 2026-10-21
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

### Bizonyítás vázlata ($n=2$, $s=2$ esetre visszavezetve)

Legyen $r>0$ úgy, hogy $K_r(a) \subset D_f$, és $u,v \in (-r,r)$ esetén

$$\Delta(u,v) := f(a_1+u, a_2+v) - f(a_1+u,a_2) - f(a_1,a_2+v) + f(a_1,a_2).$$

Rögzített $v$-re a $\varphi(u) := f(a_1+u,a_2+v) - f(a_1+u,a_2)$ függvényre $\Delta(u,v) = \varphi(u) - \varphi(0)$, és a feltételek miatt $\varphi$ differenciálható, tehát a Lagrange-középértéktétellel $\exists \xi$ a $0$ és $u$ között, hogy $\varphi(u)-\varphi(0) = \varphi'(\xi)\cdot u = \big(\partial_1 f(a_1+\xi,a_2+v) - \partial_1 f(a_1+\xi,a_2)\big)u$. Mivel $\partial_1 f$ maga is differenciálható $a$-ban, ez a lineáris közelítés tételével $\partial_{12}f(a)\cdot uv$-hez tart, amikor $u,v \to 0$; így adódik, hogy $\lim_{u\to 0} \Delta(u,u)/u^2 = \partial_{12}f(a)$.

Szimmetrikusan, $v$ szerint felírva $\Delta$-t (rögzített $u$-val, majd a $\partial_2 f$-re alkalmazva ugyanezt), ugyanaz a $\Delta(v,v)/v^2$ határérték $\partial_{21}f(a)$-hoz tart. Mivel a két határérték ugyanannak a kifejezésnek ($\Delta(u,u)/u^2$, illetve annak átjelölése) a limesze, $\partial_{12}f(a) = \partial_{21}f(a)$.

### Mit tesz lehetővé

- A [[concepts/analiii/hesse-matrix|Hesse-mátrix szimmetriáját]] — enélkül nem volna kvadratikus alak.
- A [[concepts/analiii/tobbvaltozos-taylor-polinom|multiindexes jelölést]]: a $\partial^i f$ szimbólum csak akkor jóldefiniált, ha a sorrend közömbös.
- A [[concepts/analiii/rotaciomentes-vektormezo|rotációmentesség]] $\partial_i f_j = \partial_j f_i$ szükséges feltételét primitív függvény létezéséhez.

### Feladatok

**A tétel feltétel nélkül hamis.** $f=xy\dfrac{x^2-y^2}{x^2+y^2}$, $f(0,0)=0$. $\partial_2f(x,0)=\lim_{y\to0}\dfrac{f(x,y)}{y}=x$, így $\partial_{21}f(0,0)=\partial_1(\partial_2f)(0,0)=\lim_{x\to0}\dfrac{x}{x}=1$. Hasonlóan $\partial_1f(0,y)=-y$, tehát $\partial_{12}f(0,0)=\partial_2(\partial_1f)(0,0)=-1$ (a lap jelölése: $\partial_{ij}=\partial_j\partial_i$). CORRECTION: korábban $\partial_{12}=1$, $\partial_{21}=-1$ állt, ami a lap saját jelölésével ellentmondott; a gyak 6. lap 4. feladata szerint $\partial_{12}f(0,0)=-1$, $\partial_{21}f(0,0)=1$. A két vegyes derivált létezik, de nem egyenlő; ezért $f$ nem kétszer differenciálható az origóban (a Young-tétel feltétele, a $D^2\{a\}$, nem teljesül).

- **Hivatalos megoldás (gyak 6. lap 4. feladat).** $\partial_1f(0,0)=\partial_2f(0,0)=0$ (a $f(t,0)=f(0,t)=0$ miatt). $(x,y)\ne0$ esetén $\partial_1f=y\frac{x^2-y^2}{x^2+y^2}+\frac{4x^2y^3}{(x^2+y^2)^2}$, $\partial_2f=x\frac{x^2-y^2}{x^2+y^2}-\frac{4x^3y^2}{(x^2+y^2)^2}$. A másodrendűek a definícióból: $\partial_{12}f(0,0)=\lim_{t\to0}\frac{\partial_1f(0,t)-\partial_1f(0,0)}{t}=\frac{-t}t=-1$, $\partial_{21}f(0,0)=\lim\frac{\partial_2f(t,0)-0}t=1$. Ha $f$ kétszer differenciálható lenne az origóban, a Young-tétel szerint egyezniük kellene — tehát nem az.

## Kapocs

- [[concepts/analiii/magasabbrendu-parcialis-derivaltak]] — a felcserélendő deriváltak definíciója.
- [[concepts/analiii/hesse-matrix]] — a szimmetria közvetlen haszna.
- [[concepts/analiii/tobbvaltozos-taylor-polinom]] — a multiindexes jelölés jogalapja.
- [[concepts/analiii/rotaciomentes-vektormezo]] — ahol a szimmetria szükséges feltételként jelenik meg.
- [[concepts/analiii/differencialhatosagi-fogalmak-hierarchiaja]] — ugyanaz az „egydimenziós információ kevés" mintázat.
- [[concepts/analiii/vizsgakerdesek-es-bizonyitando-tetelek]] — a témához tartozó megajánlott vizsgajegy- és röpdolgozat-kérdések.
