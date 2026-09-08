---
tags: [concept]
sources: [DimatIIEa07.pdf]
derivation: source
updated: 2026-09-08
---

# Véges testek

Minden $p$ prím és $n$ pozitív egész esetén létezik $p^n$ elemű test, amit a $\mathbb{Z}_p[x]$ polinomgyűrűnek egy $n$-ed fokú irreducibilis polinom szerinti maradékosztályaiként állítunk elő; véges test elemszáma mindig prímhatvány, és az azonos elemszámú testek izomorfak.

## Tartalom

### A konstrukció

Tekintsük valamely $p$ prímre a $\mathbb{Z}_p$ testet, továbbá egy $f(x) \in \mathbb{Z}_p[x]$ felbonthatatlan főpolinomot. Vezessük be a

$$g(x) \equiv h(x) \pmod{f(x)}, \quad \text{ha} \quad f(x) \mid \big(g(x) - h(x)\big)$$

relációt. Ez ekvivalenciareláció, ezért meghatároz egy osztályozást $\mathbb{Z}_p[x]$-en.

### Az osztályok száma

Minden osztálynak van $\deg(f)$-nél alacsonyabb fokú **reprezentánsa** (osszuk el maradékosan az osztály bármely elemét $f$-fel), és ha $\deg(g), \deg(h) < \deg(f)$, továbbá $g$ és $h$ ugyanabban az osztályban van, akkor egyenlőek (különbségük foka kisebb $\deg(f)$-nél, de osztható $f$-fel, tehát nulla).

Tehát $\deg(f) = n$ esetén bijekciót létesíthetünk az $n$-nél kisebb fokú polinomok és az osztályok között — így **$p^n$ darab osztály van** (mindegyik együttható $p$-féle lehet).

### A műveletek

Az osztályok között a természetes módon értelmezhetjük a műveleteket: az $n$-nél alacsonyabb fokú reprezentánsokkal végezzük őket, és ha a szorzat foka nem kisebb, mint $n$, akkor az $f(x)$-szel vett osztási maradékot vesszük.

**Multiplikatív inverz.** Ha $f \nmid g$, akkor a bővített euklideszi algoritmus alapján léteznek $u, v$ polinomok, amelyekre

$$d(x) = u(x)f(x) + v(x)g(x).$$

Mivel $f(x)$ felbonthatatlan, ezért $d(x) = d$ konstans polinom, így $\frac{v(x)}{d}$ multiplikatív inverze lesz $g(x)$-nek.

**Tétel.** Az ekvivalenciaosztályok halmaza a rajta értelmezett összeadással és szorzással **testet alkot**.

### Következmények

- **Tetszőleges $p$ prím és $n$ pozitív egész esetén létezik $p^n$ elemű test**, mert létezik $n$-ed fokú felbonthatatlan polinom $\mathbb{Z}_p$-ben.
- **Véges test elemszáma prímhatvány**, továbbá az azonos elemszámú testek **izomorfak** — ezért beszélhetünk *a* $q$ elemű testről, jelölése $\mathbb{F}_q$.

### Példa: $\mathbb{F}_9 = \mathbb{Z}_3[x]/(x^2+1)$

Tekintsük az $x^2 + 1 \in \mathbb{Z}_3[x]$ felbonthatatlan polinomot (nincs gyöke $\mathbb{Z}_3$-ban: $0^2+1 = 1$, $(\pm1)^2+1 = 2$, és másodfokú lévén ez elég az irreducibilitáshoz). A legfeljebb elsőfokú polinomok, azaz a kilenc osztály reprezentánsai:

$$0,\ 1,\ 2,\ x,\ x+1,\ x+2,\ 2x,\ 2x+1,\ 2x+2.$$

Az összeadás komponensenként, $\mathbb{Z}_3$-ban történik, például

$$(2x+2) + (x+1) = 3x + 3 \overset{\mathbb{Z}_3}{=} x.$$

A szorzásnál a szorzat után $x^2+1$-gyel maradékosan osztunk, például

$$(2x+2)(2x+1) = 4x^2 + 6x + 2 \overset{\mathbb{Z}_3}{=} x^2 + 2 = (x^2+1) + 1 \equiv 1.$$

Vagyis $2x+2$ és $2x+1$ egymás multiplikatív inverzei $\mathbb{F}_9$-ben.

## Kapocs

- [[concepts/dimatii/irreducibilis-polinom]] — a konstrukció bemenete: felbonthatatlan főpolinom
- [[concepts/dimatii/polinomok-bovitett-euklideszi-algoritmusa]] — a multiplikatív inverz kiszámítása
- [[concepts/dimatii/polinomok-maradekos-osztasa]] — a műveletek elvégzésének technikai alapja
- [[concepts/dimatii/test]] — az eredményül kapott struktúra
- [[concepts/dimatii/gyuru]] — a faktorizált polinomgyűrű
