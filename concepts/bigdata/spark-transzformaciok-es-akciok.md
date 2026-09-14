---
tags: [concept]
sources: [EA3_spark.pdf, gyak7.pdf]
derivation: source
updated: 2026-09-12
---

# Spark transzformációk és akciók

A Spark-ban az RDD-k módosítására kizárólag kétféle művelet szolgál: a **transzformáció** (RDD → RDD) és az **akció** (RDD → skalár/kimenet).

## Tartalom

Az [[concepts/bigdata/rdd]] egyetlen lehetőség az adatok módosítására Spark-ban, ez két műveletcsoporton keresztül történik:

- **Transformations**: RDD → RDD. Példák: `map(func)`, `flatMap(func)`, `filter(func)`, `groupByKey()`, `reduceByKey(func)`, `mapValues(func)`, `sample(...)`, `union(other)`, `distinct()`, `sortByKey()`.
- **Actions**: RDD → skalár vagy kiírt eredmény. Példák: `reduce(func)`, `collect()`, `count()`, `first()`, `take(n)`, `saveAsTextFile(path)`, `countByKey()`, `foreach(func)`.

A transzformációk **nem futnak le azonnal** — csak egy új RDD-t definiálnak a szülő RDD lineage-éhez fűzve. Csak egy akció meghívásakor kényszerül ki a tényleges számítás; ezt a viselkedést nevezzük [[concepts/bigdata/lusta-kiertekeles-es-dag-utemezes]]-nek.

### REPL példa

Interaktív Scala shell-ben (`spark-shell`) egy tipikus transzformáció-lánc:

```scala
scala> var ex = sc.parallelize(List("szoveg 1", "szoveg 2", "szoveg bla bla"))
scala> ex.map(line => line.split(" "))
scala> res4.flatMap(a => a)
scala> res8.filter(l => l.contains("ove"))
scala> res8.map(w => (w,1)).reduceByKey(_ + _)
```

Az utolsó sor egy `ShuffledRDD`-t hoz létre — a `reduceByKey` kulcs szerinti újraparticionálást (shuffle-t) igényel, szemben a `map`/`filter`/`flatMap` egy-egy partíción belül végrehajtható, ún. "keskeny" (narrow) transzformációival.

A WordCount példa (`sc.textFile → flatMap → map → reduceByKey → foreach`) jól mutatja, hogy a `reduceByKey` előtti és utáni RDD-k külön **stage**-ekbe kerülnek a shuffle miatt — lásd [[concepts/bigdata/lusta-kiertekeles-es-dag-utemezes]].

### Kiegészítő API-áttekintés (gyakorlati példák)

RDD létrehozható meglévő kollekcióból (`sc.parallelize(...)`) vagy szöveges
fájlból (`sc.textFile(...)`).

A fent felsoroltakon túl a gyakorlaton előkerülő további transzformációk és
akciók:

- **További transzformációk**: `zipWithIndex()` (minden elemhez hozzárendeli
  a sorindexét), `join(other)`, `leftOuterJoin(other)`,
  `rightOuterJoin(other)`, `fullOuterJoin(other)` (kulcs szerinti
  párosítások, az SQL join-okhoz hasonlóan), `sortBy(func)` (tetszőleges
  kulcsfüggvény szerinti rendezés, szemben a csak kulcs szerint rendező
  `sortByKey()`-vel).
- **További akciók**: `fold(zero)(func)` (a `reduce`-hoz hasonló, de explicit
  kezdőértékkel rendelkező összesítés), `countByValue()` (az egyes értékek
  előfordulási gyakoriságát számolja meg), `aggregate(zero)(seqOp, combOp)`
  (általánosított összesítés, ahol a partíción belüli és a partíciók közötti
  kombinálás külön függvénnyel adható meg).

## Kapocs

- [[concepts/bigdata/rdd]] — az a szerkezet, amelyen a transzformációk és akciók dolgoznak
- [[concepts/bigdata/lusta-kiertekeles-es-dag-utemezes]] — mikor és hogyan hajtódnak végre ténylegesen a transzformációk
- [[concepts/bigdata/spark-perzisztencia]] — ismételt akciók előtt érdemes cache-elni egy RDD-t
