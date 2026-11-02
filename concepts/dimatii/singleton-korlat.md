---
tags: [concept]
sources: [DimatIIEa09.pdf, DimatIIEa10.pdf, dm2gy11.pdf, dm2gy12.pdf]
derivation: source
kind: theorem
element: water
updated: 2026-10-21
---

# Singleton-korlát

Felső korlát egy adott hosszúságú és távolságú kód méretére; az egyenlőséget elérő kódok az MDS-kódok.

## Tartalom

### A tétel

**Tétel.** Ha $K \subset A^n$, $|A| = q$ és $d(K) = d$, akkor
$$|K| \le q^{\,n-d+1} .$$

*Bizonyítás.* Ha minden kódszóból elhagyunk $d-1$ betűt (ugyanazokból a pozíciókból), akkor az így kapott szavak még mindig különbözőek, és $n-d+1$ hosszúak. Az ilyen hosszú szavak száma szerepel az egyenlőtlenség jobb oldalán. $\square$

A korlát tartalma: hosszabb minimális távolságot csak a kódszavak számának rovására kaphatunk.

### MDS-kód

Ha egy kódra a Singleton-korlát egyenlőséggel teljesül, akkor azt **maximális távolságú szeparábilis kódnak** (**MDS-kód**) nevezzük.

**Példa.** Az $n$-szeri ismétlés kódja. Ekkor $d = n$, és $|K| = q$, tehát $q = q^{\,n-n+1}$.

### Lineáris alak

Egy $[n,k,d]_q$ lineáris kód esetén a Singleton-korlát alakja egyszerűsödik:
$$q^k \le q^{\,n-d+1} \iff k \le n - d + 1 .$$

### Feladattípusok és módszerek: MDS és perfekt kódok ellenőrzése (2024. 11–12. sorozat)

**MDS-teszt.** Számoljuk ki $n,k$-t és $d$-t; MDS pontosan akkor, ha $d=n-k+1$. Nem lineáris kódnál $|C|=q^{n-d+1}$ a teszt. A sorozatok lineáris kódjai: $(c_1,c_2,c_3,c_1+c_2+c_3)$ binárisan $[4,3,2]$, MDS; az $\mathbb{F}_5$/$\mathbb{F}_7$ feletti $(c_1,c_2,c_1+c_2)$ $[3,2,2]$, MDS; az $\mathbb{F}_5$ feletti $(c_1,c_2,c_3,\sum c_i,\,c_1+2c_2+3c_3)$ $[5,3,3]$, MDS; $\mathbb{F}_3$ fölött $(c_1,c_2,c_3,c_1+c_2,c_1+c_3)$ $[5,3,2]$, nem MDS, és a hatodik komponenssel bővített $[6,3,3]$ sem ($d<n-k+1=4$).

**Perfekt-teszt.** Perfekt kódnál a $t=\lfloor\frac{d-1}2\rfloor$ sugarú gömbök a teret lefedik: $|C|\cdot\sum_{j\le t}\binom nj(q-1)^j=q^n$. $d\le2$ esetén ($t=0$) ez csak az egész tér lehetne, ezért a fenti $d=2$ kódok **nem perfektek**; a $[6,3,3]_2$ kódnál $8\cdot7=56<64$, az $[5,3,3]_5$ kódnál $125\cdot21=2625<3125$, szintén nem perfekt. A perfekt példa a $[7,4,3]$ Hamming-kód ([[concepts/dimatii/hamming-kod]]).

**Tipikus hiba.** MDS-nek hinni minden olyan kódot, amelyben a paritásszegmens „sok” ellenőrzést tartalmaz; vagy a perfekt és az MDS fogalmát összekeverni — egyik sem következik a másikból.

## Kapocs

- [[concepts/dimatii/hamming-tavolsag]] — a kód távolsága, amelyre a korlát vonatkozik
- [[concepts/dimatii/hamming-korlat]] — a másik klasszikus korlát, a hibajavító képességből
- [[concepts/dimatii/linearis-kod]] — a korlát lineáris kódra vett paraméteres alakja
- [[concepts/dimatii/hamming-tavolsag]] — távolság és súly számolási példák
