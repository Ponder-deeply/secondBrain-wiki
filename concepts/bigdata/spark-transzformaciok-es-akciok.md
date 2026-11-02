---
tags: [concept]
sources: [EA3_spark.pdf, gyak7.pdf, "2026_27_1 ESATL8-IP-18KVIBDAG - Big Data architektúrák és elemző módszerek Gy_ 2. Gyakorlat _ ELTE Moodle.md"]
references: ["spark.apache.org/docs/latest/api/python/reference/pyspark.html#rdd-apis"]
derivation: source
kind: procedure
element: earth
updated: 2026-10-07
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

### Gyakorlati műveletek részletesen (2026-os gyakorlat)

- `map(f)` — minden elem átalakítása 1:1 (`rdd.map(lambda x: x*2)`, `rdd2.map(len)`). `filter(p)` — a feltételt teljesítő elemek (`x%2==0`, `"Buda" in x`).
- `zipWithIndex()` — `(elem, index)` párokat ad; így a pár `[1]` komponensére szűrhető (`x[1] > 5`).
- `flatMap(f)` — a függvény listát ad, az eredmény lapított: `["one two","two three"]` + `split(" ")` → `one, two, two, three`; `flatMap(list)` egy stringet karakterekre bont. Különbség: `map` után listák listája marad.
- `reduce(f)` — akció; az `f`-nek **asszociatívnak és kommutatívnak** kell lennie, mert a partíciók párhuzamosan dolgoznak és a sorrend nem garantált (összeg, maximum: `a if a>b else b`; stringek összefűzése sorrendfüggő eredményt adhat).
- `fold(zero, f)` — mint a `reduce`, de kezdőértékkel. A `zero` **minden partícióban** és az összevonásnál is bekerül, ezért nem-semleges értéknél az eredmény a partíciószámtól függ: `rdd.fold(-5, +)` = az összeg $-5\cdot(\text{partíciók száma}+1)$-gyel eltolva.
- `aggregate(zero, seqOp, combOp)` — az eredm,ény típusa eltérhet az elemétől: `seqOp` egy partíción belül az akkumulátorba olvaszt, `combOp` a partíciók akkumulátorait egyesíti. Átlag: `zero=(0,0)`, `seqOp=(s+x, n+1)`, `combOp=(s1+s2, n1+n2)`, majd `s/n`; min és max egyszerre: `zero=(inf,-inf)`.
- `distinct()` — duplikátumok eltávolítása (shuffle); `sortBy(keyfunc, ascending=...)` — tetszőleges kulcs szerinti rendezés (`sortBy(len)`, `sortBy(lambda x: x[1])`).
- Kulcs-érték műveletek (`reduceByKey`, `groupByKey`, `join` változatok): [[concepts/bigdata/spark-kulcs-ertek-muveletek]].
- `cache()` önmagában nem számol: lusta, az első akció tölti fel — lásd [[concepts/bigdata/spark-perzisztencia]].

### Paraméterek

*Dokumentáció alapján, nem a gyakorlati forrásból.*

- `take(n)` — csak annyi partíciót olvas, amennyi `n` elemhez kell; a `collect()` mindent a driverre hoz.
- `sample(withReplacement, fraction, seed=None)` — `fraction` a várható arány (nem pontos darabszám); a `seed` teszi megismételhetővé.
- `union(other)` — nincs shuffle és nincs duplikátumszűrés.
- `countByKey()`, `countByValue()` — az eredmény a driverre kerül, Python dictként; csak kevés különböző érték mellett használható.
- `saveAsTextFile(path)` — könyvtárat ír, partíciónként egy `part-*` fájllal; ha a könyvtár már létezik, hibát dob.

## Kapocs

- [[concepts/bigdata/rdd]] — az a szerkezet, amelyen a transzformációk és akciók dolgoznak
- [[concepts/bigdata/lusta-kiertekeles-es-dag-utemezes]] — mikor és hogyan hajtódnak végre ténylegesen a transzformációk
- [[concepts/bigdata/spark-perzisztencia]] — ismételt akciók előtt érdemes cache-elni egy RDD-t
- [[concepts/bigdata/spark-kulcs-ertek-muveletek]] — `reduceByKey` vs `groupByKey`, join-ok, feladatminták
- [[concepts/bigdata/spark-particionalas]] — a partíciószám és az újraparticionálás
