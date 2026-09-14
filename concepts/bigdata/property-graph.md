---
tags: [concept]
sources: [EA4_spark_graphx.pdf]
derivation: source
updated: 2026-09-12
---

# Property graph (tulajdonság-gráf)

A property graph egy irányított gráf $G=(V,E)$, ahol mind a csúcsokhoz, mind az
élekhez tetszőleges tulajdonságok (attribútumok) rendelhetők; ez a Spark GraphX
alapvető adatmodellje nagy gráfok elosztott feldolgozásához.

## Tartalom

### A gráf mint adatszerkezet

- $G=(V,E)$: $V$ a csúcsok (attribútummal rendelkezhetnek), $E$ az élek
  (szintén lehetnek attribútumaik), a gráf lehet irányított vagy irányítatlan.
- Valós példák nagy gráfokra: weboldalak és linkek közöttük, tudásbázisok
  (pl. Google Knowledge Graph), biológiai hálózatok (fehérje-kapcsolatok,
  DNS-kapcsolatok), logisztikai/útvonalkereső gráfok, ajánlórendszerek.
- Tipikus feladatok gráfokon: befolyásos csúcsok (influencerek) keresése,
  összefüggő csoportok azonosítása, ajánlások generálása, alapstatisztikák
  (be-/kimenő fokszám), klaszterezési együttható, legrövidebb út keresése,
  párosítás, PageRank, háromszögek keresése.

### Miért kell külön gráf-API?

Nagy gráfok elosztott tárolása és feldolgozása kihívást jelent: a csúcsok és
élek száma milliós nagyságrendű lehet, egyetlen szerveren a memóriakorlát és a
lassúság a probléma, elosztva tárolva viszont sok gép közötti kommunikációra
van szükség. A hagyományos megközelítésben a táblás (relációs) és a gráfos
nézet külön rendszereket, külön interfészeket igényelt, ami nehézkes és nem
hatékony: az adatokat költséges másolni a különböző rendszerek (pl. HDFS és
egy dedikált gráf-motor) között, és a korábbi számítási eredmények nem
használhatók fel könnyen újra.

A GraphX megoldása: egyetlen egységes reprezentáció, amely elmossa a
különbséget a táblák és a gráfok között — ugyanaz a fizikai adat egyszerre
érhető el tábla-nézetként (Spark RDD-műveletekkel: `map`, `filter`, `groupBy`,
`reduce`, `join`, stb.) és gráf-nézetként (dedikált gráfoperátorokkal),
mindkét nézetnek saját, hatékonyságra optimalizált operátorai vannak.

### Property Graph reprezentáció

A property graph két táblára bomlik:

- **Vertex Property Table**: `Id`, `Property (V)` — pl. egy közösségi gráfban
  `(Rxin, (Student, Berkeley))`.
- **Edge Property Table**: `SrcId`, `DstId`, `Property (E)` — pl.
  `(rxin, jegonzal, Friend)`.

Egy repülőtér-hálózat példáján (GraphX Scala API):

```scala
import org.apache.spark._
import org.apache.spark.graphx._
import org.apache.spark.rdd.RDD

// csúcs RDD: (Id, Name)
val vertices = Array((1L, ("SFO")), (2L, ("ORD")), (3L, ("DFW")))
val vRDD = sc.parallelize(vertices)

// él RDD: Edge(srcId, dstId, distance)
val edges = Array(Edge(1L, 2L, 1800), Edge(2L, 3L, 800), Edge(3L, 1L, 1400))
val eRDD = sc.parallelize(edges)

// property graph felépítése
val nowhere = "nowhere" // alapértelmezett csúcs-attribútum hiányzó végpontra
val graph = Graph(vRDD, eRDD, nowhere)
```

Alap lekérdezések a gráf-operátorokkal: `graph.numVertices`, `graph.numEdges`,
`graph.edges.filter(...)`, `graph.inDegrees`. A `graph.triplets` a
forrás- és céltulajdonságokat is hozzáfűzi az élekhez, így egy triplet
`((SFO), (ORD), 1800)` alakban rendelkezésre áll — ez teszi lehetővé pl. a
leghosszabb útvonalak lekérdezését `graph.triplets.sortBy(_.attr, ...)`
formában.

## Kapocs

- [[concepts/bigdata/graphx-tarolasi-architektura]] — hogyan tárolja és
  particionálja a GraphX a property graph-ot elosztottan
- [[concepts/bigdata/pregel-modell]] — a property graph-on futó iteratív
  számítási modell
</content>
