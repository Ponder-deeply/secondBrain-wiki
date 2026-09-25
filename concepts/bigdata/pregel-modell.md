---
tags: [concept, bigdata/spark-graphx]
sources: [EA4_spark_graphx.pdf]
references: ["Valiant, L. G. (1990): A bridging model for parallel computation — Bulk Synchronous Parallel (BSP) modell eredeti forrása"]
derivation: source
updated: 2026-09-12
---

# Pregel modell (superstep, üzenetküldés)

A Pregel a GraphX iteratív gráf-számítási modellje: a Bulk Synchronous
Parallel (BSP) elvre épül, "gondolkodj csúcsként" (think like a vertex)
szemlélettel, ahol a számítás egymást követő superstepekben, csúcsok közti
üzenetküldéssel halad előre.

## Tartalom

### Bulk Synchronous Parallel (BSP) modell

A BSP modellt eredetileg Valiant vezette be (1990) párhuzamos számítási
modellként. Alapelve: "think like a vertex" — a programozó egyetlen csúcs
szemszögéből fogalmazza meg a logikát, és ez a logika minden csúcson
párhuzamosan, egymástól függetlenül fut le egy-egy körben (superstepben). A
superstepek szinkronizációs pontokkal (barrier) választódnak el: egy
superstep addig nem ér véget, amíg minden csúcs be nem fejezte a saját
lépését és el nem küldte az üzeneteit a következő superstepre.

### Pregel API GraphX-ben

A Pregel API konfigurációja két részből áll:

**Első lista — beállítások:**
- inicializáló üzenet (initial message)
- max iterációszám
- aktív él irány — melyik irányba menjenek az üzenetek; a következő
  iterációban csak azokkal az élekkel foglalkozik a rendszer, amelyek kaptak
  üzenetet; alapbeállítás mindkét irány

**Második lista — a számítás logikája:**
- **vertex program (vprog)** — hogyan frissíti egy csúcs a saját állapotát a
  beérkezett (aggregált) üzenet alapján
- **üzenet küldése (sendMsg)** — mely szomszédoknak, milyen tartalmú üzenetet
  küld egy csúcs egy triplet (forrás-attribútum, él-attribútum,
  cél-attribútum) alapján
- **üzenet aggregálása (mergeMsg / aggrMsg)** — ha egy csúcshoz több üzenet
  is érkezik egy superstepben, hogyan vonódnak össze egyetlen értékké

Ez a három függvény (`vprog`, `sendMsg`, `mergeMsg`) írja le teljesen az
algoritmust; a konkrét gráfalgoritmusok (l. [[concepts/bigdata/pagerank-graphx]],
[[concepts/bigdata/osszefuggo-komponensek-pregel]],
[[concepts/bigdata/haromszog-szamlalas-pregel]]) mindegyike ennek a mintának a
behelyettesítése.

### Példa: legrövidebb út keresése Pregellel

```scala
// starting vertex
val sourceId: VertexId = 13024

// élsúlyok kiszámítása (pl. légitáv-ár)
val gg = graph.mapEdges(e => 50.toDouble + e.attr.toDouble / 20)

// kezdeti gráf: a forráscsúcs távolsága 0, minden más csúcsé végtelen
val initialGraph = gg.mapVertices((id, _) =>
  if (id == sourceId) 0.0 else Double.PositiveInfinity)

val sssp = initialGraph.pregel(Double.PositiveInfinity)(
  // Vertex Program: a jelenlegi és az új távolság minimuma
  (id, distCost, newDistCost) => math.min(distCost, newDistCost),
  // Send Message: csak akkor küld, ha rövidebb utat talál
  triplet => {
    if (triplet.srcAttr + triplet.attr < triplet.dstAttr) {
      Iterator((triplet.dstId, triplet.srcAttr + triplet.attr))
    } else {
      Iterator.empty
    }
  },
  // Merge Message: több beérkező javaslat minimuma
  (a, b) => math.min(a, b)
)
```

Ez a minta közvetlenül a legrövidebb út keresésének (single-source shortest
path) klasszikus relaxációs elvét valósítja meg superstepenként ismételve,
amíg egyetlen csúcs sem talál már javítást.

## Kapocs

- [[concepts/bigdata/graphx-tarolasi-architektura]] — a routing table biztosítja,
  hogy a superstepek közti üzenetek csak a releváns partíciókba menjenek
- [[concepts/bigdata/pagerank-graphx]] — PageRank mint Pregel-instanciáció
- [[concepts/bigdata/osszefuggo-komponensek-pregel]] — összefüggő komponensek
  keresése Pregellel
- [[concepts/bigdata/haromszog-szamlalas-pregel]] — háromszögszámlálás
  Pregel-szerű üzenetküldéssel
</content>
