---
tags: [concept]
sources: [05-06.grafker.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-10-12
---

# Mélységi és szélességi gráfkeresés

A mélységi gráfkeresés az $f=-g$, a szélességi az $f=g$ kiértékelő függvényű általános gráfkereső; a fekete-fehér kirakón mindkettő végigkövethető kézzel.

## Tartalom

Mindkét algoritmus az [[concepts/mesint/altalanos-grafkereso]] speciális esete: csak a kiértékelő függvényt rögzítjük, amely a nyílt csúcsok közül a következő kiterjesztendőt kijelöli (a legkisebb $f$ értékű csúcsot választjuk). A kiértékelés itt kizárólag a start csúcstól mért eddigi költségre, $g$-re épül, heurisztikát nem használ.

### Mélységi gráfkeresés ($f=-g$)

- A legmélyebben lévő (legnagyobb $g$-jű) nyílt csúcs kerül sorra, ezért a keresés egy úton halad előre, és csak zsákutcában lép vissza.
- A fekete-fehér kirakón ($B\,W\,W\,\_$ start, $W\,\_\,W\,B$ cél) a csúcsok $f$ értéke $0,-1,-2,-3,-4,-5$ a mélységgel. A keresés az egyik ágon lemegy a célig (5 lépés), a másik ágat csak egy 4. szinten lévő testvércsúcs erejéig érinti.
- Az eredmény nem feltétlenül optimális: a talált megoldás 5 lépéses, miközben létezik 4 lépéses.

### Szélességi gráfkeresés ($f=g$)

- A start-hoz legközelebbi (legkisebb $g$-jű) nyílt csúcs kerül sorra, így a gráfot szintenként járja be.
- Ugyanazon a példán minden szint teljesen kiterjesztődik, a keresés a 4. szinten megtalálja a célt, tehát a 4 lépéses, **optimális** megoldást adja.
- Ára a nagyobb keresési gráf: az elemzési táblázat szerint 10 csúcs keletkezik (a mélységi 8-cal szemben).

### Összehasonlítás a példán

A dia elemző táblázata ($\mathit{mo}$ a megoldás hossza, $G$ a keresési gráf csúcsainak száma, $\Gamma$ a kiterjesztések száma; az oszlopok jelentését a dia nem magyarázza, ez az olvasat a számokból következik):

| $f$ | algoritmus | $\mathit{mo}$ | $G$ | $\Gamma$ |
|---|---|---|---|---|
| $-g$ | mélységi | 5 | 8 | 5 |
| $g$ | szélességi | 4 | 10 | 8 |

A szélességi keresés a példán optimális, de többet dolgozik; a mélységi olcsóbb, de nem garantál optimumot. A heurisztikus változatokat ld. [[concepts/mesint/elore-tekinto-grafkereses]] és [[concepts/mesint/a-algoritmus]].

## Kapocs

- [[concepts/mesint/altalanos-grafkereso]] — az általános keretalgoritmus, amelynek ez két $f$-választása
- [[concepts/mesint/kiertekelo-fuggveny-es-mukodesi-grafikon]] — az $f$ szerepe és a működési grafikon
- [[concepts/mesint/nevezetes-grafkereso-algoritmusok]] — a nevezetes változatok áttekintése
- [[concepts/mesint/fekete-feher-kirako]] — a szemléltető feladat
- [[concepts/mesint/elore-tekinto-grafkereses]] — ugyanaz a példa $f=I$-vel
