---
tags: [concept]
sources: [dimat2gyak02mo.pdf, dm2gy03_Szamelmelet.pdf, Lehman-Leighton-Meyer-Mathematics-for-Computer-Science.pdf]
references: [Lehman–Leighton–Meyer, Mathematics for Computer Science, 9.6–9.7]
derivation: source
kind: procedure
element: fire
updated: 2026-10-22
---

# Nemlineáris kongruenciák

Ha az ismeretlen nem csak elsőfokon szerepel, nincs általános képlet: kis modulusnál egy teljes maradékrendszer elemeit végignézzük, nagyobbnál alkalmas esetszétválasztást vagy szorzattá alakítást használunk.

## Tartalom

### Teljes maradékrendszer végigpróbálása

Mivel $f(x) \bmod m$ csak $x \bmod m$-től függ, elég egy teljes maradékrendszer elemeit behelyettesíteni ([[concepts/dimatii/teljes-maradekrendszer]]); a megoldás ekkor a talált maradékosztályok uniója.

| kongruencia | próbált $x$ | megoldás |
|---|---|---|
| $x^2 \equiv 1 \pmod 5$ | $1,2,3,4,5$: $x^2 \equiv 1,4,4,1,0$ | $x \equiv \pm1 \pmod 5$ |
| $x^2 \equiv 1 \pmod 6$ | $1,\dots,6$: $x^2 \equiv 1,4,3,4,1,0$ | $x \equiv \pm1 \pmod 6$ |
| $x^4 \equiv 1 \pmod 5$ | $1,2,3,4$ mindegyik $1$, $5$: $0$ | minden, öttel nem osztható szám |
| $x(x-2) \equiv 0 \pmod 8$ | $1,\dots,8$: $7,0,3,0,7,0,3,0$ | $x$ páros |

Az $x^4 \equiv 1 \pmod 5$ eredménye az Euler–Fermat-tétel következménye ([[concepts/dimatii/euler-fermat-tetel]]).

**Az $x(x-2) \equiv 0 \pmod 8$ esete észrevétellel.** Páratlan $x$-re $x(x-2)$ páratlan, így nem osztható $8$-cal. Páros $x = 2k$ esetén $x(x-2) = 4k(k-1)$, és $k(k-1)$ két szomszédos szám szorzata, tehát páros, így $8 \mid x(x-2)$.

### Több megoldás, mint a fokszám

A $\mathbb{Z}_m$ nem test, ha $m$ összetett, ezért egy $n$-edfokú kongruenciának $n$-nél több megoldása is lehet, és szorzat nullával való egyszerűsítés tilos: $x(x-2) \equiv 0 \pmod 8$-nak négy megoldásosztálya van. Hasonlóan $x^2 \equiv 1 \pmod 8$-ra mind a négy páratlan maradék megoldás. Lásd [[concepts/dimatii/gyoktenyezo-es-gyokok-szama]] a polinomos megfelelőre.

### Hatvány-feltételek

Ha $n^{100} \bmod 73 = 57$ és $n^{101} \bmod 73 = 11$, akkor $n \cdot n^{100} \equiv 11$, azaz $57n \equiv 11 \pmod{73}$ ($n$ nem lehet osztható $73$-mal, mert akkor $n^{100} \equiv 0$ lenne). Mivel $(57,73) = 1$, $57^{-1} \equiv 13 \pmod{73}$ és $n \equiv 11 \cdot 13 = 143 \equiv 13$. Ellenőrzés: $13^{100} \equiv 57$ és $13^{101} \equiv 11 \pmod{73}$.

### Maradékos kizárás

Ha egy modulus szerint a bal oldal lehetséges maradékai közt nincs a jobb oldal maradéka, nincs megoldás ($x^2 - 4y^2 = 3$ az $x^2 \equiv 3 \pmod 4$ miatt, lásd [[concepts/dimatii/linearis-diofantikus-egyenlet]]). Hasonlóan: ha $3 \nmid n$, akkor $n^2 \equiv 1 \pmod 3$.

## Kapocs

- [[concepts/dimatii/linearis-kongruencia]] — az elsőfokú eset teljes elmélete
- [[concepts/dimatii/teljes-maradekrendszer]] — a végigpróbálás alapja
- [[concepts/dimatii/gyoktenyezo-es-gyokok-szama]] — miért lehet több megoldás a fokszámnál
- [[concepts/dimatii/linearis-diofantikus-egyenlet]] — a maradékos kizárás módszere
- [[concepts/dimatii/invertalhatosag-zm-ben]] — a nullosztók miatt nem szabad egyszerűsíteni
