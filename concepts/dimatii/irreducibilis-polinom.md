---
tags: [concept]
sources: [DimatIIEa07.pdf, Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf, dm2gy09.pdf, dm2gy10_Polinomok.pdf]
derivation: source
kind: definition
element: air
updated: 2026-10-21
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

### Farkas-diák megjegyzései

Test fölött a polinomok euklideszi gyűrűt alkotnak, ezért a felbonthatatlanok és a prímek egybeesnek; minden nem-nulla konstans polinom egység, és minden elsőfokú polinom felbonthatatlan.

### Feladattípusok és módszerek: irreducibilitás és felbontás $\mathbb{Z}_p$ fölött (2020. 10., 2024. 9. sorozat)

**Módszer.** $\mathbb{Z}_p$ fölött véges sok osztó van, ezért a döntés kimerítő: egy $n$-edik fokú $f$ pontosan akkor irreducibilis, ha nincs nála legfeljebb $\lfloor n/2\rfloor$ fokú főpolinom osztója.

- $\deg f\in\{2,3\}$: elég a gyököket végigpróbálni $\mathbb{Z}_p$-ben (az elemek behelyettesítése).
- $\deg f=4$ (és 5): a gyökmentesség **nem elég**, még a másodfokú osztókat is ki kell zárni. Példa: $x^4+x^2+1\in\mathbb{Z}_2[x]$-nek nincs gyöke ($f(0)=f(1)=1$), mégis felbontható: $=(x^2+x+1)^2$ — a 2024. 9. sorozat 9a feladata. Ugyanígy $x^4+1=(x+1)^4$ $\mathbb{Z}_2$ fölött. Ezzel szemben $x^4+x+1\in\mathbb{Z}_2[x]$ irreducibilis: nincs gyöke, és az egyetlen irreducibilis másodfokú főpolinom, $x^2+x+1$, nem osztja.
- Felbontásnál az ismert kis irreducibilisekkel osztunk sorban (előbb elsőfokúakkal, azaz a gyökök kiemelésével), amíg a maradék irreducibilis.

**Az irreducibilis polinomok listája.** $\mathbb{Z}_2$ fölött legfeljebb harmadfokig: $x,\ x+1,\ x^2+x+1,\ x^3+x+1,\ x^3+x^2+1$. $\mathbb{Z}_3$ fölött az irreducibilis másodfokú főpolinomok: $x^2+1,\ x^2+x+2,\ x^2+2x+2$ (a $9-6=3$ maradék a $\binom{3+1}{2}=6$ reducibilis után).

**Számlálás.** $\mathbb{Z}_p$ fölött a reducibilis másodfokú főpolinomok száma $\binom{p+1}{2}=\tfrac{p(p+1)}2$ (két elsőfokú tényező szorzata, ismétlődés megengedett), az irreducibiliseké $p^2-\tfrac{p(p+1)}2=\tfrac{p(p-1)}2$. $p=7$: $28$ reducibilis, $21$ irreducibilis; $p=3$: $6$ és $3$ — az irreducibilisek száma egyezik a fenti listával.

**Felbontások (az algoritmussal számolva).** $\mathbb{Z}_2$ fölött: $x^7+1=(x+1)(x^3+x+1)(x^3+x^2+1)$; $x^8+x^6+x^5+x^3+x^3+x^2+x+1$ (a két $x^3$ kiejti egymást: $x^3+x^3=0$) $=(x+1)^5(x^3+x^2+1)$. $\mathbb{Z}_3$ fölött $x^7+2x^4+x^2+2x+2=(x+1)(x^3+2x+1)(x^3+2x^2+2x+2)$ — tehát felbontható; a két harmadfokú tényező gyökmentes, ezért irreducibilis. $\mathbb{Z}_5$ fölött $x^3+x+1$, $x^3+x^2+1$, $x^3+4x^2+4x+4$ irreducibilisek (gyökmentesek, harmadfokúak): a $\mathbb{F}_{125}$ konstrukció bemenetei.

**Tipikus hibák.** Negyedfokúnál a gyökmentességből irreducibilitást következtetni; $\mathbb{Z}_2$-ben a $2x^3=0$ típusú tagokat nem elhagyni; az együtthatókat redukálni felejteni a tényezők szorzásakor.

## Kapocs

- [[concepts/dimatii/felbonthatatlan-es-prim]] — a felbonthatatlanság általános, gyűrűbeli fogalma
- [[concepts/dimatii/egyseg-es-asszocialt]] — a definícióban szereplő egység fogalma
- [[concepts/dimatii/polinom-foka]] — a fokösszegzés az egész elemzés eszköze
- [[concepts/dimatii/test]] — a fenti állítások feltétele
- [[concepts/dimatii/irreducibilis-polinomok-c-es-r-folott]] — a teljes osztályozás $\mathbb{C}$ és $\mathbb{R}$ fölött
- [[concepts/dimatii/schonemann-eisenstein-kriterium]] — elégséges feltétel $\mathbb{Z}[x]$-beli irreducibilitásra
- [[concepts/dimatii/veges-testek]] — irreducibilis polinommal faktorizálva építünk $p^n$ elemű testet
- [[concepts/dimatii/veges-testek]] — az irreducibilis polinomokkal épülő véges testek
