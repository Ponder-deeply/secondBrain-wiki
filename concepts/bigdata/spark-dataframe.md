---
tags: [concept]
sources: [EA3_spark.pdf, "2026_27_1 ESATL8-IP-18KVIBDAG - Big Data architektúrák és elemző módszerek Gy_ 3. Gyakorlat _ ELTE Moodle.md"]
references: ["spark.apache.org/docs/latest/api/python/reference/pyspark.sql/api/pyspark.sql.DataFrameWriter.mode.html"]
derivation: source
kind: definition
element: earth
updated: 2026-10-07
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

### PySpark gyakorlat: DataFrame létrehozása, séma, I/O

A belépési pont a [[concepts/bigdata/spark-session]] (a fenti `SQLContext` modern utódja).

**Létrehozás Python adatokból**, oszlopnevekkel (a típusokat a Spark kikövetkezteti):

```python
dfLoc = spark.createDataFrame(valuesLoc, ["location", "city", "id"]).cache()
dfLoc.printSchema(); dfLoc.show()
```

**Explicit séma** (`StructType`):

```python
LocSchema = StructType([
    StructField("location", StringType(), False),
    StructField("city",     StringType(), True),
    StructField("id",       IntegerType(), False),
])
dfLoc = spark.createDataFrame(valuesLoc, LocSchema)
```

| Elem | Jelentés |
|---|---|
| `StructType` | a teljes séma |
| `StructField` | egy oszlop leírása (név, típus, nullable) |
| `StringType`, `IntegerType` | szöveges, egész típus |
| `False` / `True` | NULL érték engedélyezett-e |

**Kiírás [[concepts/bigdata/hdfs|HDFS]]-re** — a `save()` egy *könyvtárat* kap, benne partíciónként egy `part-....csv` fájllal:

```python
dfLoc.write.mode("overwrite").option("header", True).format("csv") \
     .save("hdfs://namenode:8020/data/raw/sensors/location")
```

- Egyetlen part-fájlhoz: `dfLoc.coalesce(1).write...`. Nagy adatnál nem ajánlott: egy partícióra kényszeríti az adatot, ezzel csökken a párhuzamosság. Kis eredménynél hasznos.
- A part-fájlok száma a DataFrame partíciószámát követi (`df.rdd.getNumPartitions()`).

**Beolvasás:**

```python
spark.read.format("csv").option("header", True).option("inferSchema", True).load(path)
spark.read.json("hdfs://namenode:8020/data/raw/sensors/sensors100.json")
```

- `inferSchema=True`: a Spark kitalálja a típusokat. `inferSchema=False` esetén a CSV minden oszlopa `string` lesz (az `id` is), ezért pontos típusokhoz explicit séma kell.
- A JSON sémáját a Spark a rekordokból következteti ki.

### Műveletek összefoglalója

**Join** — `df.join(dfLoc, df.location == dfLoc.location, how="left").drop(dfLoc.location)`, vagy azonos nevű oszlopra `df.join(dfLoc, on="location", how="left")` (ez nem duplikálja az oszlopot).

| Join | Megmaradó rekordok |
|---|---|
| `inner` | csak az illeszkedők |
| `left` | a bal oldal összes rekordja |
| `right` | a jobb oldal összes rekordja |
| `full` | mindkét oldal összes rekordja |

**Cache hatása:** cache nélkül minden akció (`show()`, `count()`) újraszámolja a joint is; `.cache()` után az első akció betölti az eredményt a [[concepts/bigdata/spark-perzisztencia|memóriába]], a többi onnan olvas (a Spark UI-ban látszik a különbség).

**Oszlopválasztás és kifejezések:**

```python
dfAll.select("location", "sensor_type")
dfAll.selectExpr("*", "concat(location,' ',sensor_type) as LocSensor")
df.selectExpr("avg(value)", "count(distinct(sensor_id))")
```

**Szűrés:** `filter` és `where` azonos. Feltételek: `&`, `|`, `~`, zárójelezve:

```python
df.where((df["location"] == "Buda") & (df["sensor_type"] == "temperature"))
df.where(~(df["location"] == "Buda") & (df["sensor_type"] == "temperature"))
```

**Egyedi értékek:** `df.select("location").distinct().count()`.

**Rendezés:** `df.orderBy(df["location"], df["timestamp"].desc())` (`sort` szinonima).

**Csoportosítás, aggregáció:**

```python
df.groupBy("sensor_type").avg("value")        # sum, count, ...
df.groupBy("sensor_type").agg(
    sum("value").alias("Sum_value"),
    avg("value").alias("Avg_value"),
    min("value").alias("min_value")
).filter("Avg_value > 20")
```

Az alias-szal elnevezett aggregált oszlopra az aggregáció után lehet szűrni (SQL-ben `HAVING`).

**SQL-lekérdezés** temp view-n és a végrehajtási terv: [[concepts/bigdata/spark-sql]].

### Gyakorlati feladatok: RDD vs. DataFrame

Ugyanaz a feladat (a szenzoradat legmelegebb napja, napi átlaghőmérséklet) mindkét API-val megoldható:

- **DataFrame:** `filter` (temperature), `to_date(timestamp)`, majd `groupBy`/`agg(max)` vagy `orderBy(desc)`. Szenzoronkénti darabszám: `groupBy("sensor_id").count()` csökkenő rendezéssel.
- **RDD:** `textFile`, `map` (feldolgozás), `filter`, `reduce` vagy `sortBy` a maximumhoz; napi átlag: `map` `(date, (value, 1))` párokra, `reduceByKey` az (összeg, darabszám) előállításához, majd az osztás ([[concepts/bigdata/rdd]], [[concepts/bigdata/spark-transzformaciok-es-akciok]]).

A DataFrame változat rövidebb és az optimalizáló számára átlátható; az RDD változatban a feldolgozást és a típuskezelést magunknak kell megírni.

### Paraméterek

*Dokumentáció alapján, nem a gyakorlati forrásból.*

- `write.mode(m)` — `"error"` (alapértelmezés: létező célnál hiba), `"overwrite"`, `"append"` vagy `"ignore"` (létező célnál nem ír semmit).
- `read.option(...)`
  - `header`: az első sor oszlopnév.
  - `inferSchema`: egy plusz menetben végigolvassa az adatot a típusok kitalálásához, ezért lassabb.
  - `sep`: elválasztó.
  - Gyorsabb és biztosabb: `.schema(StructType)`.
- `join(other, on, how="inner")` — `how` értéke: `inner`, `left`, `right`, `full`, `left_semi` (csak a bal oldal illeszkedő sorai, a jobb oszlopai nélkül), `left_anti` (a bal oldal nem illeszkedő sorai).
- `orderBy(*cols, ascending=True)` — oszloponként listával is megadható: `ascending=[True, False]`.
- `to_date(col, format=None)` — formátum nélkül ISO dátumot vár; ha nem tudja értelmezni, `null`-t ad.

## Kapocs

- [[concepts/bigdata/rdd]] — a DataFrame egyik lehetséges forrása, és az alatta futó végrehajtási réteg
- [[concepts/bigdata/spark-transzformaciok-es-akciok]] — a DataFrame műveletei ugyanazt a transzformáció/akció modellt követik
- [[concepts/bigdata/lusta-kiertekeles-es-dag-utemezes]] — a DataFrame-műveletek is csak egy akcióra hajtódnak végre
- [[concepts/bigdata/spark-session]] — a DataFrame-ek belépési pontja
- [[concepts/bigdata/spark-sql]] — temp view, SQL és explain()
- [[concepts/bigdata/hdfs]] — CSV/JSON írás és olvasás HDFS-en
- [[concepts/bigdata/spark-perzisztencia]] — a cache() hatása
