---
tags: [concept]
sources: [DimatIIEa07.pdf]
derivation: source
updated: 2026-09-08
---

# Irreducibilis polinom

Egy nem-nulla, nem egység polinom felbonthatatlan (irreducibilis), ha minden szorzat-előállításában valamelyik tényező egység; test fölött ez a fogalom a fokszám segítségével alacsony fokokra teljesen tisztázható.

## Tartalom

### Definíció

Legyen $R$ egységelemes integritási tartomány, és legyen $0 \neq f \in R[x]$ nem egység. Ezt az $f$ nem-nulla polinomot pontosan akkor nevezzük **felbonthatatlannak** (**irreducibilisnek**), ha minden $a, b \in R[x]$-re

$$f = a\cdot b \implies (a \text{ egység} \vee b \text{ egység}).$$

Ha $0 \neq f \in R[x]$ nem egység és nem felbonthatatlan, akkor **felbonthatónak** (**reducibilisnek**) nevezzük — azaz van nemtriviális szorzat-előállítása, olyan, amelyben egyik tényező sem egység.

A konstans nulla polinomot sem felbonthatatlannak, sem felbonthatónak nem nevezzük.

### Egységek test fölött

**Állítás.** Legyen $(F; +, \cdot)$ test. Ekkor $f \in F[x]$ pontosan akkor egység, ha $\deg(f) = 0$.

*Bizonyítás.* ($\Leftarrow$) Ha $\deg(f) = 0$, akkor $f$ nem-nulla konstans polinom: $f(x) = f_0$. Mivel $F$ test, létezik $f_0^{-1} \in F$, amire $f_0f_0^{-1} = 1$, így $f$ valóban egység. ($\Rightarrow$) Ha $f$ egység, akkor létezik $g \in F[x]$, amire $f\cdot g = 1$, és így $\deg(f) + \deg(g) = \deg(1) = 0$, ami csak $\deg(f) = \deg(g) = 0$ esetén lehetséges. $\square$

### Alacsony fokú polinomok test fölött

**Elsőfokú polinomnak van gyöke.** Ha $F$ test és $\deg(f) = 1$, azaz $f(x) = f_1x + f_0$ ($f_1 \neq 0$), akkor $c = -f_0f_1^{-1}$ gyöke $f$-nek.

**Elsőfokú polinom felbonthatatlan.** Ha $f = g\cdot h$, akkor $\deg(g) + \deg(h) = 1$, tehát $\deg(g) = 0$ vagy $\deg(h) = 0$; az előbbi esetben $g$, az utóbbiban $h$ egység.

**Megjegyzés.** Ha $(R; +, \cdot)$ nem test, akkor egy $R$ fölötti elsőfokú polinomnak nem feltétlenül van gyöke — például $2x - 1 \in \mathbb{Z}[x]$-nek nincs egész gyöke. (Emlékezzünk: $R[x]$-beli polinomoknak csak $R$-beli gyökeit definiáltuk.)

**Másod- és harmadfokú polinom.** Ha $F$ test és $2 \le \deg(f) \le 3$, akkor $f$ **pontosan akkor felbontható, ha van gyöke.**

*Bizonyítás.* ($\Leftarrow$) Ha $c$ gyöke $f$-nek, akkor $f(x) = (x-c)g(x)$ egy nemtriviális felbontás. ($\Rightarrow$) Mivel $2 = 0+2 = 1+1$, illetve $3 = 0+3 = 1+2$, és más összegként nem állnak elő, ezért ha $f$-nek van nemtriviális felbontása, akkor van elsőfokú osztója. Annak van gyöke, és az nyilván $f$ gyöke is. $\square$

**Figyelem:** nem igaz, hogy egy felbonthatatlan polinomnak nem lehet gyöke — az elsőfokú polinom egyszerre felbonthatatlan és gyökös. Az ekvivalencia csak a $2 \le \deg(f) \le 3$ tartományban áll fenn, és negyedfokú polinomtól kezdve elromlik (két gyöktelen másodfokú szorzata gyöktelen, mégis felbontható).

## Kapocs

- [[concepts/dimatii/felbonthatatlan-es-prim]] — a felbonthatatlanság általános, gyűrűbeli fogalma
- [[concepts/dimatii/egyseg-es-asszocialt]] — a definícióban szereplő egység fogalma
- [[concepts/dimatii/polinom-foka]] — a fokösszegzés az egész elemzés eszköze
- [[concepts/dimatii/test]] — a fenti állítások feltétele
- [[concepts/dimatii/irreducibilis-polinomok-c-es-r-folott]] — a teljes osztályozás $\mathbb{C}$ és $\mathbb{R}$ fölött
- [[concepts/dimatii/schonemann-eisenstein-kriterium]] — elégséges feltétel $\mathbb{Z}[x]$-beli irreducibilitásra
- [[concepts/dimatii/veges-testek]] — irreducibilis polinommal faktorizálva építünk $p^n$ elemű testet
