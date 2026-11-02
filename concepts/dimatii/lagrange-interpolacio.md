---
tags: [concept]
sources: [DimatIIEa05.pdf, DimatIIEa06.pdf, dm2gy08.pdf, dm2gy09.pdf, dm2gy11_Polinomok.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-10-21
---

# Lagrange-interpoláció

Test fölött $n+1$ különböző helyen előírt értékhez mindig található legfeljebb $n$-ed fokú polinom, és az explicit előállítást az alappolinomokból összerakott Lagrange-formula adja.

## Tartalom

### A tétel

**Tétel.** Legyen $R$ test, $c_0, c_1, \dots, c_n \in R$ különbözőek, továbbá $d_0, d_1, \dots, d_n \in R$ tetszőlegesek. Ekkor létezik olyan legfeljebb $n$-ed fokú polinom, amelyre $f(c_j) = d_j$ minden $j = 0, 1, \dots, n$ esetén.

*Bizonyítás.* Legyen

$$\ell_j(x) = \frac{\prod_{i \neq j}(x - c_i)}{\prod_{i \neq j}(c_j - c_i)}$$

a $j$-edik **Lagrange-interpolációs alappolinom**, és legyen

$$f(x) = \sum_{j=0}^{n} d_j\ell_j(x).$$

Az állítás abból következik, hogy $\ell_j(c_i) = 0$, ha $i \neq j$, és $\ell_j(c_j) = 1$. $\square$

Az egyértelműséget a gyökök számáról szóló következmény adja: két legfeljebb $n$-ed fokú polinom, amely $n+1$ helyen megegyezik, egyenlő — lásd [[concepts/dimatii/gyoktenyezo-es-gyokok-szama]].

### Példa

Adjunk meg olyan $f \in \mathbb{R}[x]$ polinomot, amelyre $f(0) = 3$, $f(1) = 3$, $f(4) = 7$ és $f(-1) = 0$.

A feladat szövege alapján $c_0 = 0$, $c_1 = 1$, $c_2 = 4$, $c_3 = -1$, illetve $d_0 = 3$, $d_1 = 3$, $d_2 = 7$, $d_3 = 0$. Az alappolinomok:

$$\ell_0(x) = \frac{(x-1)(x-4)(x+1)}{(0-1)(0-4)(0+1)} = \tfrac14x^3 - x^2 - \tfrac14x + 1,$$
$$\ell_1(x) = \frac{(x-0)(x-4)(x+1)}{(1-0)(1-4)(1+1)} = -\tfrac16x^3 + \tfrac12x^2 + \tfrac23x,$$
$$\ell_2(x) = \frac{(x-0)(x-1)(x+1)}{(4-0)(4-1)(4+1)} = \tfrac{1}{60}x^3 - \tfrac{1}{60}x,$$
$$\ell_3(x) = \frac{(x-0)(x-1)(x-4)}{(-1-0)(-1-1)(-1-4)} = -\tfrac{1}{10}x^3 + \tfrac12x^2 - \tfrac25x.$$

Innen

$$f(x) = 3\ell_0(x) + 3\ell_1(x) + 7\ell_2(x) + 0\ell_3(x) = \tfrac{22}{60}x^3 - \tfrac32x^2 + \tfrac{68}{60}x + 3.$$

Az eredmény Horner-elrendezéssel ellenőrizhető a négy helyettesítési helyen.

### Alkalmazás: titokmegosztás

A Lagrange-interpoláció használható titokmegosztásra. Legyen $1 \le m < n$ egész, továbbá $s \in \mathbb{N}$ a titok, amit $n$ ember között akarunk szétosztani úgy, hogy bármely $m$ részéből a titok rekonstruálható legyen, kevesebből ne.

1. Válasszunk a titok maximális lehetséges értékénél és $n$-nél is nagyobb $p$ prímet.
2. Válasszunk $a_1, \dots, a_{m-1} \in \mathbb{Z}_p$ véletlen együtthatókat, és határozzuk meg az
   $$f(x) = a_{m-1}x^{m-1} + a_{m-2}x^{m-2} + \dots + a_1x + s$$
   polinom $f(i)$ értékeit; ezek az $i$-edik ember részei ($i = 1, 2, \dots, n$).

Bármely $m$ helyettesítési értékből a Lagrange-interpolációval megkapható a polinom, így annak konstans tagja, a titok is. Ha $m$-nél kevesebb helyettesítési értéket ismerünk, akkor nem tudjuk meghatározni a titkot: tetszőleges $t$ esetén az $f(0) = t$ értéket a többihez hozzávéve létezik olyan legfeljebb $(m-1)$-ed fokú polinom, aminek konstans tagja $t$, és az adott helyeken megfelelő a helyettesítési értéke — a részek tehát semmit nem árulnak el.

**Példa.** Legyen $m = 3$, $n = 4$, $s = 5$, $p = 7$, továbbá $a_1 = 3$ és $a_2 = 4$. Ekkor $f(x) = 4x^2 + 3x + 5 \in \mathbb{Z}_7[x]$, a titokrészletek pedig $f(1) = 5$, $f(2) = 6$, $f(3) = 1$, $f(4) = 4$. Ha rendelkezünk például az $f(1) = 5$, $f(3) = 1$ és $f(4) = 4$ információkkal, akkor a $c_0 = 1$, $c_1 = 3$, $c_2 = 4$, $d_0 = 5$, $d_1 = 1$, $d_2 = 4$ értékekkel alkalmazva a Lagrange-interpolációt visszakapjuk $f$-et, és ebből a titkot: $f(0) = 5$.

### Feladattípusok és módszerek: konkrét interpolációs polinom (gyakorlati feladatsor, 8. hét)

**Építőelem:** olyan polinom, amely az adott helyeken $0$, és egy kijelölt helyen $y$ értéket vesz fel: $y\cdot\prod_{j\ne i}(x-a_j)\big/\prod_{j\ne i}(a_i-a_j)$ (az osztás a test fölött invertálással).

- $\mathbb{Q}$: $g(3)=g(5)=0$, $g(0)=1$: $g=\tfrac{(x-3)(x-5)}{15}$. $g(0)=g(3)=0$, $g(5)=2$: $g=\tfrac{x(x-3)}{5}$. $f(0)=1,f(3)=0,f(5)=2$: $f=\tfrac{(x-3)(x-5)}{15}+\tfrac{2x(x-3)}{10}=\tfrac{4x^2-17x+15}{15}$.
- $\mathbb{Z}_7$: $g(1)=g(2)=0$, $g(6)=2$: $g=5(x-1)(x-2)$ ($5\cdot5\cdot4=100\equiv2$). $g(2)=g(6)=0$, $g(1)=3$: $g=2(x-2)(x-6)$ ($2\cdot(-1)(-5)=10\equiv3$). $f(1)=3,f(2)=0,f(6)=2$: $f=2(x-2)(x-6)+5(x-1)(x-2)$.
- **Ötlet, ha az értékek „majdnem egy egyenesen” vannak:** $\mathbb{Z}_5$-ben $f(0..4)=1,2,3,4,1$: az $x+1$ az első négy helyen jó, de $4$-nél $0$-t ad; kijavítás $c\,x(x-1)(x-2)(x-3)$ taggal, amely $0..3$-nál eltűnik és $4$-nél $24c\equiv4c$-t ad; $4c=1\Rightarrow c=4$, tehát $f=x+1+4x(x-1)(x-2)(x-3)$. $\mathbb{Z}_7$-ben $f(0),f(1),f(2),f(3),f(5)=6,5,4,3,4$: $6-x$ jó $0..3$-nál, $5$-nél $1$-et ad; a korrekciós tag $c\,x(x-1)(x-2)(x-3)$ értéke $5$-nél $120c\equiv c$, így $c=3$ és $f=6-x+3x(x-1)(x-2)(x-3)$.

**Ellenőrzés:** minden jelölt helyen helyettesíteni (Horner-táblával, lásd [[concepts/dimatii/horner-elrendezes]]); a megoldás nem egyértelmű, ha kevesebb adat van, mint amennyi a fokot rögzítené.

### Feladattípusok és módszerek: interpoláció $\mathbb{R}$, $\mathbb{Z}_p$ fölött és titokmegosztás (2020. 11., 2024. 9. sorozat)

**Newton-féle (osztott differenciás) alak mint gyorsabb kézi módszer.** Ha az adatok „majdnem egyenesen” vannak, a Lagrange-alappolinomok helyett lépésenként bővítjük az interpolációs polinomot egy olyan taggal, amely az eddigi helyeken eltűnik. *Példa* ($\mathbb{R}$, helyek $0;1;2;3;4$, értékek $1;2;3;4;6$): $1+x$ az első négy helyen jó, $4$-nél $5$-öt ad, a hiányzó $1$-et a $c\,x(x-1)(x-2)(x-3)$ tag pótolja, $c\cdot 24=1$, tehát $f=1+x+\tfrac1{24}x(x-1)(x-2)(x-3)$ (ellenőrzés: $f(4)=1+4+1=6$).

**$\mathbb{Z}_7$ fölött** az $f(1)=5$, $f(2)=0$, $f(3)=6$, $f(4)=1$, $f(5)=5$ adatokhoz (legfeljebb negyedfokú polinom) a Lagrange-képlet a $\mathbb{Z}_7$-beli inverzekkel az $f=x^3+3x^2+1$ polinomot adja (öt helyen ellenőrizve); az alacsony fok az adatok szerkezetéből jön, nem hiba.

**Titokmegosztás $\mathbb{Z}_{19}$ fölött.** Az $(3,12)$, $(6,14)$, $(9,17)$, $(14,4)$, $(17,10)$ párokból a Lagrange-interpolációval $f=x^3+x+1$ adódik, a titok az $f(0)=1$. Mivel a polinom harmadfokú, négy rész elég a rekonstrukcióhoz; az ötödik pár csak ellenőrzés (mind az öt pár illeszkedik). Ha a küszöb nem ismert, az összes részből interpolálunk, és a kapott polinom foka árulja el a lehetséges küszöböt. A titok a $0$ helyen vett érték, nem a legmagasabb együttható.

**Tipikus hibák.** A nevezőben a különbségek előjelének elrontása ($(c_j-c_i)$ és nem $(c_i-c_j)$); $\mathbb{Z}_p$ fölött a tört helyett inverz használata elmarad; az interpolációs polinom foka legfeljebb a pontok száma mínusz egy, de lehet kisebb.

## Kapocs

- [[concepts/dimatii/gyoktenyezo-es-gyokok-szama]] — az interpolációs polinom egyértelműsége
- [[concepts/dimatii/horner-elrendezes]] — az eredmény ellenőrzése
- [[concepts/dimatii/test]] — a tétel feltétele: az alappolinomok nevezőivel osztani kell tudni
- [[concepts/kript/titokmegosztás]] — ugyanez az alkalmazás Shamir-féle küszöbsémaként, kriptográfiai nézőpontból
