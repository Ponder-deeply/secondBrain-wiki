---
tags: [concept]
sources: [Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf]
derivation: source
kind: theorem
element: water
updated: 2026-10-21
---

# Egyszerű testbővítés

A $K(\alpha)$ egyszerű bővítés, ha $\alpha$ $n$-ed fokú algebrai elem $K$ fölött, izomorf a $K[x]/\langle g \rangle$ faktorgyűrűvel, foka $n$, és bázisa a hatványbázis $\langle 1, \alpha, \dots, \alpha^{n-1} \rangle$; minden irreducibilis polinomhoz létezik olyan bővítés, ahol gyöke van.

## Tartalom

### Bővítés elemhalmazzal

**Definíció.** Legyen $K$ részteste $F$-nek, $M \subseteq F$. $K(M)$ a $K$ test **$M$ halmazzal való bővítése**: $F$-nek a legszűkebb olyan résztestje, amely $K$-t és $M$-et is tartalmazza. Ha $M = \{\alpha\}$, akkor $K(\alpha)$ **egyszerű bővítés** az **$\alpha$ bővítő elemmel**.

### Szerkezeti tételek

Legyen $\alpha \in F$ $n$-edfokú algebrai elem $K$ felett, $g$ a $K$ feletti minimálpolinomja (lásd [[concepts/dimatii/algebrai-elem-es-minimalpolinom]]).

**Tétel (izomorfia faktorgyűrűvel).** $K(\alpha) \cong K[x]/\langle g \rangle$.

**Tétel (az egyszerű bővítés bázisa).** $[K(\alpha) : K] = n$, és $K(\alpha)$ bázisa $K$ fölött $\langle 1, \alpha, \dots, \alpha^{n-1} \rangle$ (**hatványbázis**).

**Következmény.** Minden $c \in K(\alpha)$ felírható $c = b_0 + b_1\alpha + \dots + b_{n-1}\alpha^{n-1}$ alakban, $b_i \in K$ — vagyis $c$ egy legfeljebb $n-1$-edfokú $K$ fölötti polinom helyettesítési értéke $\alpha$-nál.

### Létezés

**Tétel.** Ha $f \in K[x]$ irreducibilis polinom a $K$ test fölött, akkor létezik $K$-nak olyan egyszerű algebrai bővítése, ahol a bővítő elem $f$-nek gyöke.

*Bizonyítás (vázlat).* $L = K[x]/\langle f \rangle$ test (irreducibilis $f$ esetén; lásd [[concepts/dimatii/maximalis-es-primideal]]), elemei a $[h] = h + \langle f \rangle$ maradékosztályok. Az $a \mapsto [a]$ ($a \in K$) leképezés izomorfizmus, így $K$ beágyazható $L$-be, és $L : K$ bővítés; az $[x]$ osztály gyöke $f$-nek. $\square$

Ez ugyanaz a konstrukció, amellyel $\mathbb{Z}_p$ fölött $p^n$ elemű testet építettünk ([[concepts/dimatii/veges-testek]]).

## Kapocs

- [[concepts/dimatii/algebrai-elem-es-minimalpolinom]] — a $g$ minimálpolinom
- [[concepts/dimatii/testbovites-es-primresztest]] — bővítés foka, fokszámtétel
- [[concepts/dimatii/faktorgyuru]] — a $K[x]/\langle g \rangle$ konstrukció
- [[concepts/dimatii/veges-testek]] — a véges testek építése ugyanezzel a módszerrel
- [[concepts/dimatii/irreducibilis-polinom]] — a létezéstétel feltétele
