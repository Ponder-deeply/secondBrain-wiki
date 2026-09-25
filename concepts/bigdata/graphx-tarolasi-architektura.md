---
tags: [concept, bigdata/spark-graphx]
sources: [EA4_spark_graphx.pdf]
derivation: source
updated: 2026-09-12
---

# GraphX tárolási architektúra

A GraphX az elosztott property graph-ot három RDD-táblára bontva tárolja
(vertex table, edge table, routing table), és a csúcsok szerverek közti
elosztására hash-alapú vagy lokalitás-alapú particionálást használ.

## Tartalom

### Elosztott gráf mint táblák (RDD-k)

A GraphX belsőleg nem egyetlen gráf-objektumként, hanem RDD-k halmazaként
reprezentálja a [[concepts/bigdata/property-graph]] modellt:

- **Property Graph Table** — a logikai nézet: csúcsok és élek a
  tulajdonságaikkal.
- **Vertex Table (RDD)** — particionált csúcs-attribútum tár.
- **Edge Table (RDD)** — particionált él-attribútum tár, particiónként a
  saját éleivel.
- **Routing Table (RDD)** — nyilvántartja, hogy egy adott csúcs mely
  él-particiókban szerepel, hogy az üzenetküldés (l.
  [[concepts/bigdata/pregel-modell]]) csak a releváns partíciókat érje el.

Ez a felbontás teszi lehetővé, hogy a gráf-műveletek Spark-natív
particionált, elosztott RDD-transzformációkként fussanak, miközben a
vertex/edge/routing táblák együtt tartják karban a gráf topológiáját.

### Csúcstárolási stratégiák

Kulcskérdés: honnan tudjuk, melyik csúcs melyik szerveren tárolódik? Két fő
lehetőség:

- **Hash-alapú particionálás**: `Hash(csúcs id) mod num(server)` — egyszerű,
  hasonló elven működik, mint egy P2P rendszer, de nem veszi figyelembe a
  gráf topológiáját, így szomszédos csúcsok könnyen különböző szerverekre
  kerülhetnek.
- **Lokalitás-alapú particionálás**: a szomszédos csúcsokat igyekszik azonos
  szerveren tárolni, így csökkenti a szerverek közötti kommunikációt az
  iteratív gráfszámítások (pl. Pregel-supersteppek) során — ez a
  kommunikációs költség a nagy, elosztottan tárolt gráfok fő kihívása.

### Gráfelemzési pipeline

Egy tipikus nagy gráfos elemzés (pl. Wikipédia hivatkozási gráfon PageRank
számítása) három fázisra bomlik: előfeldolgozás (ETL, pl. nyers XML-ből
kezdeti gráf építése HDFS-ről), számítás (pl. subgraph kiválasztás +
PageRank iterálás), majd utófeldolgozás (pl. top-N eredmény kiválasztása).
A forrás egy benchmarkot is közöl, amely szerint a GraphX ezen a pipeline-on
versenyképes futásidőt ér el tisztán Spark-alapú, illetve Giraph+Spark és
GraphLab+Spark kombinációkkal szemben.

## Kapocs

- [[concepts/bigdata/property-graph]] — a logikai adatmodell, amit ez az
  architektúra fizikailag tárol
- [[concepts/bigdata/pregel-modell]] — a számítási modell, amely ezen a
  tárolási rétegen fut és a routing table-t használja az üzenetküldéshez
</content>
