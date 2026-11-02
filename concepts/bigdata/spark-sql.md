---
tags: [concept]
sources: ["2026_27_1 ESATL8-IP-18KVIBDAG - Big Data architektúrák és elemző módszerek Gy_ 3. Gyakorlat _ ELTE Moodle.md"]
references: ["spark.apache.org/docs/latest/api/python/reference/pyspark.sql/api/pyspark.sql.DataFrame.explain.html"]
derivation: source
kind: procedure
element: earth
updated: 2026-10-07
---

# Spark SQL: temp view és végrehajtási terv

A DataFrame SQL-lekérdezésként is elérhető egy temp view-n keresztül; az `explain()` megmutatja, milyen tervvé fordul a DataFrame- vagy SQL-lekérdezés.

## Tartalom

### Temp view és `spark.sql`

```python
df.createOrReplaceTempView("sensorTemp")

spark.sql("""
SELECT sensor_type, count(*)
FROM sensorTemp
GROUP BY sensor_type
""").show()
```

- A temp view **nem** fizikai tábla és nem kerül HDFS-re: az aktuális [[concepts/bigdata/spark-session|SparkSession]]-höz kötött név a DataFrame-hez.
- A `spark.sql(...)` eredménye DataFrame, tehát láncolható (`.filter`, `.show`, ...).

### Végrehajtási terv: `explain()`

```python
spark.sql("SELECT sensor_type, count(*) FROM sensorTemp GROUP BY sensor_type").explain()
df.groupBy("sensor_type").count().explain()
```

- Az `explain()` a Spark által létrehozott végrehajtási tervet írja ki; a gyakorlat célja a DataFrame- és az SQL-változat tervének összevetése, azaz hogy mindkettő hogyan fordul Spark tervvé. Ugyanaz a lekérdezés a két API-n át azonos optimalizálón megy át, ezért jellemzően hasonló tervet kapunk (részaggregáció, shuffle, végső aggregáció).
- A terv olvasása alulról felfelé történik (forrás, majd szűrés/aggregáció, végül kimenet).
- Az `explain()` nem hajt végre semmit; a végrehajtás a [[concepts/bigdata/lusta-kiertekeles-es-dag-utemezes|lusta kiértékelés]] szerint az akciónál indul.

### Paraméterek

*Dokumentáció alapján, nem a gyakorlati forrásból.*

- `createOrReplaceTempView(name)` — felülírja a meglévő azonos nevű view-t. A `createTempView` ilyenkor hibát dob. A `createGlobalTempView` minden sessionből látszik, `global_temp.<név>` alakban.
- `explain(mode)`
  - `"simple"` (alapértelmezés): csak a fizikai terv.
  - `"extended"` (vagy `explain(True)`): a logikai tervek is, vagyis látszik, mit alakított át az optimalizáló.
  - `"formatted"`: a legolvashatóbb forma.
  - A tervben az `Exchange` jelöli a shuffle-t. A két `HashAggregate` a shuffle előtti részaggregáció és az utána következő végső aggregáció.
- `show(n=20, truncate=True)` — `truncate=False` esetén nem vágja le a hosszú cellákat.

## Kapocs

- [[concepts/bigdata/spark-dataframe]] — a DataFrame API, amelynek műveletei SQL-ként is kifejezhetők
- [[concepts/bigdata/spark-session]] — a view hatóköre a session
- [[concepts/bigdata/lusta-kiertekeles-es-dag-utemezes]] — a terv végrehajtása akcióra történik
