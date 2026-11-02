---
tags: [concept]
sources: [DimatIIEa07.pdf, Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf, dm2gy11_Polinomok.pdf]
derivation: source
kind: theorem
element: water
updated: 2026-10-21
---

# Primitív polinom és Gauss lemmája

Egy egész együtthatós polinom primitív, ha együtthatóinak legnagyobb közös osztója $1$; Gauss lemmája szerint primitív polinomok szorzata is primitív, és ebből következik, hogy a $\mathbb{Z}[x]$ és a $\mathbb{Q}[x]$ fölötti felbonthatóság ugyanaz.

## Tartalom

### Primitív polinom

**Definíció.** $f \in \mathbb{Z}[x]$-et **primitív polinomnak** nevezzük, ha az együtthatóinak legnagyobb közös osztója $1$.

### Gauss lemmája

**Lemma (Gauss).** Ha $f, g \in \mathbb{Z}[x]$ primitív polinomok, akkor $fg$ is primitív polinom.

*Bizonyítás.* Indirekt tegyük fel, hogy $fg$ nem primitív polinom. Ekkor van olyan $p \in \mathbb{Z}$ prím, ami osztja $fg$ minden együtthatóját. Legyen $i$, illetve $j$ a legkisebb olyan index, amire $p \nmid f_i$, illetve $p \nmid g_j$ (ilyenek léteznek, mert $f$ és $g$ primitív). Ekkor $fg$-nek az $(i+j)$ indexű együtthatója

$$f_0g_{i+j} + \dots + f_ig_j + \dots + f_{i+j}g_0,$$

és ebben az összegben $p$ nem osztja $f_ig_j$-t (prím lévén nem oszthatja egyik tényezőt sem), de osztója az összes többi tagnak (mindegyikben szerepel egy $p$-vel osztható tényező). Akkor viszont nem osztója az összegnek, ami ellentmondás. $\square$

### Primitív rész kiemelése

**Állítás.** Minden $0 \neq f \in \mathbb{Z}[x]$ polinom felírható $f = df^*$ alakban, ahol $0 \neq d \in \mathbb{Z}$, és $f^* \in \mathbb{Z}[x]$ egy primitív polinom. A felírás lényegében egyértelmű.

*Bizonyítás.* Ha $f$-ből az együtthatók legnagyobb közös osztóját kiemeljük, és azt választjuk $d$-nek, akkor megkapjuk a megfelelő előállítást. Az előállítás előjelektől eltekintve egyértelmű, így $f^*$ főegyütthatóját pozitívnak választva teljesen egyértelmű.

**Állítás.** Minden $0 \neq f \in \mathbb{Q}[x]$ polinom felírható $f = af^*$ alakban, ahol $0 \neq a \in \mathbb{Q}$, és $f^* \in \mathbb{Z}[x]$ primitív polinom; a felírás lényegében egyértelmű.

*Bizonyítás.* Írjuk fel $f$ együtthatóit egész számok hányadosaként. Ha végigszorozzuk $f$-et az együtthatói nevezőinek $c$ szorzatával, majd kiemeljük a kapott $\mathbb{Z}[x]$-beli polinom együtthatóinak $d$ legnagyobb közös osztóját, akkor megkapjuk a megfelelő előállítást $a = d/c$-vel.

### Gauss tétele $\mathbb{Z}[x]$-re

**Tétel (Gauss).** Ha egy $f \in \mathbb{Z}[x]$ előállítható két nem konstans $g, h \in \mathbb{Q}[x]$ polinom szorzataként, akkor előállítható két nem konstans $g^*, h^* \in \mathbb{Z}[x]$ polinom szorzataként is.

*Bizonyítás.* Tegyük fel, hogy $f = gh$, ahol $g, h \in \mathbb{Q}[x]$ nem konstansok. Legyen $f = df^*$, ahol $d \in \mathbb{Z}$, és $f^* \in \mathbb{Z}[x]$ primitív, pozitív főegyütthatóval. Ha $g$-t $ag^{**}$, $h$-t $bh^{**}$ alakban írjuk fel a fenti $\mathbb{Q}[x]$-es állítás szerint (ahol $g^{**}, h^{**} \in \mathbb{Z}[x]$ primitívek, pozitív főegyütthatóval), akkor

$$df^* = f = gh = ab\,g^{**}h^{**}.$$

Gauss lemmája szerint $g^{**}h^{**}$ is primitív, és a primitív polinom szerinti felírás lényegében egyértelmű, ezért $f^* = g^{**}h^{**}$ és $d = ab$, vagyis $f = d\,g^{**}h^{**}$; például a $g^* = dg^{**}$, $h^* = h^{**}$ választással kapjuk $f$ kívánt felbontását. $\square$

**Következmény.** Egy $f \in \mathbb{Z}[x]$ primitív polinom pontosan akkor felbontható $\mathbb{Z}$ fölött, amikor felbontható $\mathbb{Q}$ fölött. ($\Rightarrow$) egy $\mathbb{Z}$ fölötti felbontás egyben $\mathbb{Q}$ fölötti felbontás is; ($\Leftarrow$) a Gauss-tételből következik.

Ez a következmény teszi lehetővé, hogy racionális együtthatós polinomok irreducibilitását egész együtthatós eszközökkel — például a Schönemann–Eisenstein-kritériummal — vizsgáljuk.

### Általánosítás Gauss-gyűrűre (Farkas-diák)

**Definíció.** Legyen $R$ Gauss-gyűrű. $R[x]$ egy elemét **primitív polinomnak** nevezzük, ha együtthatóinak legnagyobb közös osztója az egységelem.

**Gauss-tétel.** Legyen $R$ tetszőleges Gauss-gyűrű és $K$ a hányadosteste. Ekkor

1. ha egy $f \in R[x]$ polinom előállítható két nem konstans $g, h$ polinom szorzataként $K[x]$-ben, akkor $R[x]$-ben is előállítható két $g^*, h^*$ polinom szorzataként úgy, hogy $g$ és $g^*$, illetve $h$ és $h^*$ asszociáltak $K[x]$-ben;
2. $R[x]$ is Gauss-gyűrű.

**Megjegyzések.**

- $f(x) = 6x^2 + 12x + 12 = 2 \cdot 3 \cdot (x^2 + 2x + 2)$ $\mathbb{Q}[x]$-ben irreducibilis, de $\mathbb{Z}[x]$-ben nem (a $2 \cdot 3$ konstans tényezők nem egységek): a $\mathbb{Z}$ fölötti irreducibilitás-vizsgálatnál a primitivitás ezért kell.
- $f(x) = \tfrac13 x^2 + \tfrac12 x + 3 \in \mathbb{Q}[x]$ és $g(x) = 6f = 2x^2 + 3x + 18$ asszociáltak $\mathbb{Q}[x]$-ben, de $f \notin \mathbb{Z}[x]$: a konstanssal való szorzás visz át egész együtthatósba.
- $\mathbb{Z}$ euklideszi gyűrű, ezért Gauss-gyűrű, tehát $\mathbb{Z}[x]$ is Gauss-gyűrű (lásd [[concepts/dimatii/gauss-gyuru]]).

### Feladattípusok: felbontás $\mathbb{Z}$ és $\mathbb{Q}$ fölött (2020. 11. feladatsor)

A $\mathbb{Z}$ és a $\mathbb{Q}$ fölötti felbontás különbözik: $\mathbb{Z}[x]$-ben a tartalom is tényező, és az egységek $\pm1$.

- $6x+10=2(3x+5)$: $\mathbb{Z}$ fölött **felbontható** ($2$ nem egység), $\mathbb{Q}$ fölött irreducibilis (elsőfokú; a $2$ egység), $\mathbb{R}$, $\mathbb{C}$ fölött is.
- $6(x^2-2)(x^2+1)$: $\mathbb{Z}$ fölött $2\cdot3\cdot(x^2-2)(x^2+1)$ (négy irreducibilis tényező, a $6$ két prím); $\mathbb{Q}$ fölött $(x^2-2)(x^2+1)$ (a $6$ egység); $\mathbb{R}$ fölött $(x-\sqrt2)(x+\sqrt2)(x^2+1)$; $\mathbb{C}$ fölött $(x-\sqrt2)(x+\sqrt2)(x-i)(x+i)$.
- Primitív polinom $\mathbb{Z}$ fölött pontosan akkor irreducibilis, ha $\mathbb{Q}$ fölött az, ezért az irreducibilitási tesztek ($\mathbb{Z}$-ben) $\mathbb{Q}$-ra is érvényesek.

**Tipikus hiba:** egy konstans szorzót tartalmazó polinomot $\mathbb{Z}$ fölött „irreducibilisnek” nevezni, mert a nem konstans része irreducibilis. A tartalom és a primitív rész: [[concepts/dimatii/racionalis-gyokteszt]], [[concepts/dimatii/schonemann-eisenstein-kriterium]].

## Kapocs

- [[concepts/dimatii/irreducibilis-polinom]] — a felbonthatóság fogalma, amit itt $\mathbb{Z}$ és $\mathbb{Q}$ között átvezetünk
- [[concepts/dimatii/schonemann-eisenstein-kriterium]] — a következmény fő alkalmazása
- [[concepts/dimatii/racionalis-gyokteszt]] — szintén primitív $\mathbb{Z}[x]$-beli polinomokra épül
- [[concepts/dimatii/gauss-gyuru]] — a Gauss-tétel általános gyűrűje; $R[x]$ is Gauss-gyűrű
- [[concepts/dimatii/hanyadostest]] — a $K$ hányadostest, amelyben a $\mathbb{Q}$-fölötti felbontás él
