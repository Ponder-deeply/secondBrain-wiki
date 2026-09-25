---
tags: [concept, bigdata/spark-graphx]
sources: [EA4_spark_graphx.pdf]
derivation: source
updated: 2026-09-12
---

# PageRank GraphX-ben (Pregel-instanciáció)

A PageRank a csúcsok fontosságát méri egy gráfban a beérkező élek (hivatkozások)
súlyozott figyelembevételével; a GraphX-ben a
[[concepts/bigdata/pregel-modell]] egy konkrét behelyettesítéseként
implementálható.

## Tartalom

### A feladat

A PageRank egy gráf-feldolgozási alapfeladat: célja a csúcsok relatív
fontosságának (node fontosság) meghatározása a beérkező kapcsolatok alapján —
tipikus alkalmazás a weboldalak rangsorolása a rájuk mutató linkek alapján.

### Pregel-paraméterezés

A PageRank a Pregel API három függvényével írható le:

- `vprog: 0.15 + 0.85 * msg` — egy csúcs új rangja a beérkező (aggregált)
  üzenet 0,85-szöröse plusz a fix 0,15 "leszállási valószínűség" (damping
  factor kiegészítője).
- `sendMsg: n1 send n1.p * edge.attr` — egy csúcs a saját aktuális rangját
  (`n1.p`) az él attribútumával (jellemzően az él súlya, pl. `1/kimenő
  fokszám`) megszorozva küldi tovább a szomszédjainak.
- `aggrMsg: sum(a,b)` — egy csúcshoz több irányból érkező üzenetet
  összegzéssel (`sum`) aggregál.

### Végrehajtás lépésről lépésre

A forrás egy kis példagráfon (csúcsok: 2, 3, 5, 7) mutatja be az iterációkat:

1. Kezdetben minden csúcs rangja egyenletesen van elosztva (pl. `1/2`,
   `1/2`), az élsúlyok a kimenő fokszám reciprokai.
2. Az első superstepben minden csúcs elküldi a `sendMsg` szerinti üzenetet a
   szomszédainak (pl. `0.15*1`, `0.15*0.5` alakú részletszámítások jelennek
   meg a példában).
3. A `vprog` alkalmazásával a csúcsok frissítik a rangjukat: a példában a
   rangok `0.15` kezdőértékekről `0.30`, `0.23`, `0.34` stb. értékekre
   változnak az első iteráció után.
4. Az iterációk a Pregel superstep-mechanizmusán keresztül ismétlődnek, amíg
   a rangok konvergálnak, vagy el nem éri a konfigurált max iterációszámot.

## Kapocs

- [[concepts/bigdata/pregel-modell]] — az általános superstep/üzenetküldés
  keretrendszer, amelynek ez a PageRank egy konkrét behelyettesítése
- [[concepts/bigdata/property-graph]] — az adatmodell, amin a PageRank fut
</content>
