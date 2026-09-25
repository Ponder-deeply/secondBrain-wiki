---
tags: [concept, bigdata/storm-stream-feldolgozas]
sources: [EA5_storm.pdf]
derivation: source
updated: 2026-09-12
---

# Storm topológia (spout, bolt, stream grouping)

A Storm számítási modellje: egy **topológia** irányított gráf, amelynek
csúcsai (**spout**, **bolt**) számítást, élei pedig **tuple**-ökből álló
**stream**-ek folyását reprezentálják.

## Tartalom

### Alapfogalmak

- **Stream** — tuple-ök folyama, amely a topológián keresztül áramlik.
- **Spout** — külső forrásokból olvas be tuple-öket a topológiába.
- **Bolt** — az alkalmazás tényleges logikáját foglalja magába: tuple-öket
  fogyaszt, feldolgozza (szűrés, aggregálás, elemzés), és opcionálisan
  új tuple-öket emittál tovább.

A topológia tehát egy gráf, ahol a csúcsok (spout-ok, bolt-ok) a
számítást, az élek pedig az adatáramlást (stream) jelentik.

### Stream grouping

Amikor egy bolt (A) több párhuzamos taszkja tuple-öket küld egy másik
bolt (B) párhuzamos taszkjainak, a **stream grouping** stratégia
határozza meg a szétosztás módját:

- **Shuffle grouping** — a tuple-ök véletlenszerűen, egyenletes
  elosztásban kerülnek A taszkjaitól B taszkjaihoz.
- **Fields grouping** — a tuple-ök egy megadott mező(k) (pl. `word`)
  értéke alapján kerülnek mindig ugyanahhoz a B-taszkhoz (ez teszi
  lehetővé pl. a kulcs szerinti számlálást).
- **All grouping** — minden tuple-t minden B-taszkhoz eljuttat
  (broadcast).
- **Global grouping** — a teljes stream egyetlen (mindig ugyanazon)
  B-taszkhoz kerül.

### Topológia példa

A klasszikus szóban forgó "word count" topológia felépítése
`TopologyBuilder`-rel:

```java
TopologyBuilder builder = new TopologyBuilder();
builder.setSpout("sentences-spout", new SentenceSpout());
builder.setBolt("split-bolt", new SplitSentenceBolt())
    .shuffleGrouping("sentences-spout");
builder.setBolt("count-bolt", new WordCountBolt())
    .fieldsGrouping("split-bolt", new Fields("word"));
```

A topológia futtatása helyi klaszteren:

```java
LocalCluster cluster = new LocalCluster();
cluster.submitTopology(TOPOLOGY_NAME, config, builder.createTopology());
waitForSeconds(10);
cluster.killTopology(TOPOLOGY_NAME);
cluster.shutdown();
```

A `SplitSentenceBolt` az `execute(Tuple tuple)` metódusában szavakra
bontja a mondatot, és minden szót külön tuple-ként emittál
(`declareOutputFields` deklarálja a `word` mezőt); a `WordCountBolt`
a kapott szavakat egy `HashMap<String, Long>`-ban számolja, és nem
emittál tovább semmit.

## Kapocs

- [[concepts/bigdata/storm-architektura]] — a klaszter, amely a
  topológiát futtatja (Nimbus, Supervisor, Worker)
- [[concepts/bigdata/storm-megbizhato-feldolgozas]] — hogyan
  garantálja a topológia, hogy egy tuple ténylegesen végigfut rajta
- [[concepts/bigdata/storm-vs-kotegelt-feldolgozas]] — a topológia mint
  örökké futó folyamat, szemben a véges MapReduce/Spark job-okkal
</content>
