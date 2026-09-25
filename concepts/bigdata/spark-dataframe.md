---
tags: [concept, bigdata/spark]
sources: [EA3_spark.pdf]
derivation: source
updated: 2026-09-12
---

# Spark DataFrame (Shark SQL API)

A DataFrame a Spark SQL modul (a forrásban "Shark" néven említett SQL API) alapfogalma: egy elosztott, nevesített oszlopokkal rendelkező adathalmaz, amely az [[concepts/bigdata/rdd|RDD]]-nél magasabb szintű, táblaszerű lekérdezést tesz lehetővé.

## Tartalom

**DataFrame** — elosztott adatset, nevesített oszlopokkal. Forrása lehet:

- Hive tábla,
- külső adatbázis,
- meglévő RDD,
- fájl (pl. JSON).

### Példa (Scala API)

```scala
val sc: SparkContext                      // meglévő SparkContext
val sqlContext = new org.apache.spark.sql.SQLContext(sc)
val df = sqlContext.jsonFile("examples/src/main/resources/people.json")

df.show()
df.printSchema()
df.select("name").show()
df.select(df("name"), df("age") + 1).show()
df.filter(df("age") > 21).show()
df.groupBy("age").count().show()
```

Közvetlen SQL is futtatható a `SQLContext`-en keresztül:

```scala
val df = sqlContext.sql("SELECT * FROM table")
```

A DataFrame API tehát a [[concepts/bigdata/spark-transzformaciok-es-akciok|RDD transzformációk és akciók]] fölé egy deklaratív, SQL-szerű réteget húz, de a végrehajtás ugyanúgy [[concepts/bigdata/lusta-kiertekeles-es-dag-utemezes|lustán kiértékelt]] DAG-ütemezésen keresztül történik.

## Kapocs

- [[concepts/bigdata/rdd]] — a DataFrame egyik lehetséges forrása, és az alatta futó végrehajtási réteg
- [[concepts/bigdata/spark-transzformaciok-es-akciok]] — a DataFrame műveletei ugyanazt a transzformáció/akció modellt követik
- [[concepts/bigdata/lusta-kiertekeles-es-dag-utemezes]] — a DataFrame-műveletek is csak egy akcióra hajtódnak végre
