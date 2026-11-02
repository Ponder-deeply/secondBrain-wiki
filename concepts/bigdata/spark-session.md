---
tags: [concept]
sources: ["2026_27_1 ESATL8-IP-18KVIBDAG - Big Data architektúrák és elemző módszerek Gy_ 3. Gyakorlat _ ELTE Moodle.md"]
references: ["spark.apache.org/docs/latest/api/python/reference/pyspark.sql/spark_session.html"]
derivation: source
kind: definition
element: earth
updated: 2026-10-07
---

# SparkSession

A `SparkSession` a Spark SQL és a [[concepts/bigdata/spark-dataframe|DataFrame]] API egységes belépési pontja (PySpark-ban a `SparkContext` és az `SQLContext` helyett).

## Tartalom

```python
from pyspark.sql import SparkSession
from pyspark.sql.functions import avg, min, max, count, to_date, sum
from pyspark.sql.types import *

spark = SparkSession.builder.appName("BigDataGyak").getOrCreate()
```

- `appName` — az alkalmazás neve, ez látszik a Spark UI-ban.
- `getOrCreate()` — a meglévő session-t adja vissza, vagy újat hoz létre.
- `spark.version` — a Spark verziója.
- A session adja a `spark.createDataFrame(...)`, `spark.read...` és `spark.sql(...)` hívásokat; az [[concepts/bigdata/rdd|RDD]]-khez a mögötte lévő `spark.sparkContext` kell.
- A klaszter állapota a standalone master webes felületén követhető; a futó alkalmazások a Spark UI-n (jobok, stage-ek, Storage).
- A temp view-k a session-höz kötöttek ([[concepts/bigdata/spark-sql]]).

### Paraméterek

*Dokumentáció alapján, nem a gyakorlati forrásból.*

- `master(url)` — `"local[*]"` (helyben, minden maggal), `"spark://spark-master:7077"` (standalone klaszter) vagy `"yarn"`.
- `config(key, value)` — pl. `spark.jars.packages` (Maven-koordináta, pl. a Kafka-connectorhoz) vagy `spark.sql.shuffle.partitions`.
- `getOrCreate()` — ha már fut egy session, a builder statikus beállításai (master, jars, memória) nem érvényesülnek. Ilyenkor újra kell indítani a kernelt, vagy előbb meghívni a `spark.stop()`-ot.
- `spark.conf.set(key, value)` — futás közben állítható beállítások (főleg SQL-esek).

## Kapocs

- [[concepts/bigdata/spark-architektura]] — driver, executor, klaszter, amelyhez a session csatlakozik
- [[concepts/bigdata/spark-dataframe]] — a session által létrehozott DataFrame-ek
- [[concepts/bigdata/spark-sql]] — SQL a session-ön keresztül
