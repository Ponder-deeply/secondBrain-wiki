---
tags: [concept]
sources: ["2026_27_1 ESATL8-IP-18KVIBDAG - Big Data architektúrák és elemző módszerek Gy_ 5. Gyakorlat _ ELTE Moodle.md"]
references: ["spark.apache.org/docs/latest/streaming/structured-streaming-kafka-integration.html"]
derivation: source
kind: procedure
element: earth
updated: 2026-10-07
---

# Spark–Kafka integráció

A Spark Structured Streaming a `kafka` formátummal olvas topicokat; a rekord értéke bináris, ezért JSON esetén stringgé kell alakítani és sémával kibontani.

## Tartalom

### Connector

Spark 4.0.1 és Scala 2.13 esetén a koordináta `org.apache.spark:spark-sql-kafka-0-10_2.13:4.0.1`. A connectornek a driver és az executorok környezetében is elérhetőnek kell lennie.

### Olvasás

```python
def read_kafka(topic):
    return (spark.readStream
            .format("kafka")
            .option("kafka.bootstrap.servers", "kafka:9092")
            .option("subscribe", topic)
            .option("startingOffsets", "latest")
            .load())
```

- `subscribe` — a feliratkozott topic.
- `startingOffsets`: `latest` az újonnan érkező rekordoktól indít, `earliest` a topic elejéről olvas.

### Bináris érték és séma

A `value` mező bináris: `F.col("value").cast("string")`, majd `F.from_json(..., schema).alias("data")` és `select("data.*")` adja a szétbontott oszlopokat. A séma `StructType` (pl. `log_schema`: timestamp, srcip, dstip, method, url String, status Integer; szenzornál `value` Double; koordinátánál `lat`, `lon` Double). Az időbélyeg a laborban String típusú.

### Feldolgozási minták

Minden feladathoz két megoldás készül: RDD-alapú mikrobatch (`foreachBatch`) és natív Structured Streaming (DataFrame, ablakos aggregáció, `writeStream`) — l. [[concepts/bigdata/spark-foreachbatch-es-checkpoint]]. A régi DStream API-t nem használják.

### Streaming query-k kezelése

`query.stop()` leállít egy lekérdezést; a `spark.streams.active` listázza az aktívakat (`q.id`, `q.status`), ciklusban mind leállítható.

### Paraméterek

*Dokumentáció alapján, nem a gyakorlati forrásból.*

| Opció | Jelentés |
|---|---|
| `kafka.bootstrap.servers` | Kötelező. A `kafka.` előtagú opciókat a Spark változatlanul továbbadja a Kafka-kliensnek. |
| `subscribe` | Vesszővel elválasztott topiclista; `subscribePattern`: reguláris kifejezés. A kettő közül csak az egyik adható meg. |
| `startingOffsets` | `latest` (streamingben alapértelmezés), `earliest`, vagy partíciónkénti JSON (`-2` = earliest, `-1` = latest). Csak új, checkpoint nélküli lekérdezésnél hat. |
| `maxOffsetsPerTrigger` | Felső korlát a batchenként feldolgozott rekordok számára. `earliest` indításnál ez akadályozza meg, hogy egyetlen óriási első batch jöjjön. |
| `failOnDataLoss` | `true` (alapértelmezés): a lekérdezés leáll, ha offsetek vesztek el (pl. lejárt a retention). |

- A beolvasott oszlopok: `key`, `value` (bináris), `topic`, `partition`, `offset`, `timestamp`.
- `F.from_json(col, schema)` — a sémára nem illeszkedő sorból `null` lesz, nem hiba; a hibás sorok utána kiszűrhetők.

## Kapocs

- [[concepts/bigdata/kafka-alapfogalmak]] — topic, partíció, offset.
- [[concepts/bigdata/spark-structured-streaming]] — a streaming modell.
- [[concepts/bigdata/streaming-ablakok-es-watermark]] — ablakos aggregációk a Kafka-adatokon.
- [[concepts/bigdata/spark-dataframe]] — a beolvasott adat DataFrame.
- [[concepts/bigdata/spark-broadcast-valtozo]] — az antennatábla broadcastolása.
