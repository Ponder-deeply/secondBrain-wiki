---
tags: [concept]
sources: [DimatIIEa05.pdf, DimatIIEa06.pdf]
derivation: source
updated: 2026-09-08
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

Bármely $m$ helyettesítési értékből a Lagrange-interpolációval megkapható a polinom, így annak konstans tagja, a titok is. Ha $m$-nél kevesebb helyettesítési értéket ismerünk, akkor nem tudjuk meghatározni a titkot: tetszőleges $t$ esetén az $f(0) = t$ értéket a többihez hozzávéve létezik olyan legfeljebb $m$-ed fokú polinom, aminek konstans tagja $t$, és az adott helyeken megfelelő a helyettesítési értéke — a részek tehát semmit nem árulnak el.

**Példa.** Legyen $m = 3$, $n = 4$, $s = 5$, $p = 7$, továbbá $a_1 = 3$ és $a_2 = 4$. Ekkor $f(x) = 4x^2 + 3x + 5 \in \mathbb{Z}_7[x]$, a titokrészletek pedig $f(1) = 5$, $f(2) = 6$, $f(3) = 1$, $f(4) = 4$. Ha rendelkezünk például az $f(1) = 5$, $f(3) = 1$ és $f(4) = 4$ információkkal, akkor a $c_0 = 1$, $c_1 = 3$, $c_2 = 4$, $d_0 = 5$, $d_1 = 1$, $d_2 = 4$ értékekkel alkalmazva a Lagrange-interpolációt visszakapjuk $f$-et, és ebből a titkot: $f(0) = 5$.

## Kapocs

- [[concepts/dimatii/gyoktenyezo-es-gyokok-szama]] — az interpolációs polinom egyértelműsége
- [[concepts/dimatii/horner-elrendezes]] — az eredmény ellenőrzése
- [[concepts/dimatii/test]] — a tétel feltétele: az alappolinomok nevezőivel osztani kell tudni
- [[concepts/kript/titokmegosztás]] — ugyanez az alkalmazás Shamir-féle küszöbsémaként, kriptográfiai nézőpontból
