---
tags: [concept]
sources: [05-06.grafker.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-10-12
---

# A algoritmus

Az $A$ algoritmus az $f=g+h$ kiértékelő függvényű gráfkereső: a start-tól megtett út költségét és a célig becsült költséget összegzi. Megengedhető heurisztikával ez az $A^*$ ([[concepts/mesint/a-csillag-algoritmus]]).

## Tartalom

A kiértékelés két tagja kiegyensúlyozza a szélességi ($f=g$) és az előre tekintő ($f=h$) keresést: a $g$ tag a szélességi keresés biztonságát, a $h$ tag a heurisztika irányítását adja. A heurisztika a fekete-fehér kirakón az $I$ (hány fehér áll fekete után), illetve annak finomított változata.

### Három heurisztika ugyanazon a feladaton

Start: $B\,W\,W\,\_$; a megtalált célállapot a $W\,W\,B\,\_$ (a végállapot nem egyetlen állapot).

| $f$ | start értéke | megoldás | $G$ | $\Gamma$ |
|---|---|---|---|---|
| $g+I$ | $0+2$ | 4 lépés | 9 | 7 |
| $g+2\cdot I$ | $0+4$ | 4 lépés | 8 | 6 |
| $g+2\cdot I-1$ (ha van $BW\_$ vagy $\_BW$) | $0+4$ | 4 lépés | 7 | 5 |

(Az oszlopok jelentése a dián: $G$ a keresési gráf csúcsainak száma, $\Gamma$ a kiterjesztések száma; az olvasat a számokból következik.)

- $g+I$: a start gyermekei $1+2$; a jobb oldali ágon $2+1,\ 3+1,\ 4+0$, így a cél 4 lépésben megvan.
- $g+2\cdot I$: erősebben súlyozott heurisztika, amely határozottabban irányít: a keresés a jobb ágon halad le a célig, a bal ág csúcsai $1+4,\ 2+4,\ 4+2$ értékűek, ezek a keresés során nem kerülnek előtérbe.
- $g+2\cdot I-1$: ez az $M$ módosított inverziószám ([[concepts/mesint/fekete-feher-kirako]]); a start gyermekeinek értéke $1+4$ és $1+3$, a cél $4+0$. Itt keletkezik a legkevesebb csúcs.

A táblázat mindhárom sora a diákon $A^c$ alg jelölést kap (a jelölés pontos jelentését az ide tartozó diák nem magyarázzák), és mindhárom 4 lépéses, optimális megoldást ad. A szélességi keresés ($g$, 10 csúcs, 8 kiterjesztés) az összehasonlítás alapja: a jobb heurisztikák ennél kevesebb csúcsot hoznak létre. A pontosabb (nagyobb, de $h^*$-t meg nem haladó) becslés kisebb keresési gráfot jelent.

## Kapocs

- [[concepts/mesint/a-csillag-algoritmus]] — megengedhető heurisztika esetén optimális
- [[concepts/mesint/a-csillag-memoriaigenye]] — a különböző heurisztikák összehasonlítása
- [[concepts/mesint/melysegi-es-szelessegi-grafkereses]] — $f=\pm g$
- [[concepts/mesint/elore-tekinto-grafkereses]] — $f=h$
- [[concepts/mesint/heurisztikus-fuggveny-tulajdonsagai]] — megengedhetőség, monotonitás
