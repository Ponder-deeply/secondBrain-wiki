---
tags: [concept]
sources: ["2026_27_1 ESATL8-IP-18KVIBDAG - Big Data architektúrák és elemző módszerek Gy_ 5. Gyakorlat _ ELTE Moodle.md"]
references: ["spark.apache.org/docs/latest/streaming/apis-on-dataframes-and-datasets.html"]
derivation: source
kind: procedure
element: earth
updated: 2026-10-07
---

# foreachBatch, RDD-mikrobatch és natív streaming

A `foreachBatch()` minden mikrobatch DataFrame-jét átadja egy függvénynek, amelyben `.rdd`-vel RDD API-ra lehet váltani; ez még Structured Streaming, nem DStream.

## Tartalom

### RDD-alapú mikrobatch

```python
def process_batch(batch_df, batch_id):
    rdd = batch_df.rdd
    print("batch:", batch_id, rdd.take(2))

query = (stream_df.writeStream
         .foreachBatch(process_batch)
         .outputMode("append")
         .start())
```

- A függvény minden mikrobatch-re meghívódik; az RDD műveletek csak az adott batch rekordjait látják.
- A `collect()` és `takeOrdered()` a driverre gyűjt, ezért csak kis oktatási kimenetre használandó.

### Natív Structured Streaming

DataFrame műveletek (pl. `count()`), ablakos aggregációk, majd `writeStream` (pl. `format("console")`, `outputMode("complete")`).

### Összehasonlítás és buktató

| | RDD-mikrobatch | Natív |
|---|---|---|
| Hatókör | egy batch | a teljes folyam |
| Ablak | csak mikrobatch szintű közelítés (pl. a 30 s-os támadásdetektálás) | natív ablakos aggregáció |
| Kimenet | saját kód a batch-függvényben | `writeStream` + output mód |

A forrás a támadásdetektálásnál kifejezetten "mikrobatch szintű közelítés"-nek nevezi az RDD-megoldást: mivel az RDD-művelet csak az aktuális batchet látja, a batchek közötti állapot (ablak) nem kezelődik pontosan. A táblázat többi sora ebből következő összefoglalás (derivation szempontból inferred elem).

### Checkpoint és offsetek

A forrás csak annyit mond: újraindításnál a checkpoint és az offsetek viselkedését meg kell vizsgálni; a `startingOffsets` (latest/earliest) a kezdőpontot adja. Részletes checkpoint-mechanizmus nincs a forrásban.

### Paraméterek

*Dokumentáció alapján, nem a gyakorlati forrásból.*

- `foreachBatch(func)` — a `func(batch_df, batch_id)` mikrobatchenként egyszer fut le.
  - `batch_df`: statikus DataFrame, minden kötegelt művelet és sink használható rajta.
  - `batch_id`: hiba utáni újrafuttatáskor ugyanazt kapja, így vele tehető idempotenssé az írás.
- `option("checkpointLocation", path)` — itt tárolódnak az offsetek és az aggregációs állapot; enélkül egy újraindított lekérdezés nem tudja, hol tartott.
  - Minden lekérdezésnek saját könyvtár kell, megbízható tárolón (HDFS).
  - Ha már létezik checkpoint, a `startingOffsets`-et a Spark figyelmen kívül hagyja.
- `trigger(processingTime="10 seconds")` — milyen időközönként induljon batch. Alapból a következő batch azonnal indul, amint az előző végzett.
- `takeOrdered(n, key=None)` — csak `n` elemet hoz a driverre; a `collect()` mindent.

## Kapocs

- [[concepts/bigdata/spark-kafka-integracio]] — a bemeneti stream.
- [[concepts/bigdata/spark-structured-streaming]] — a motor.
- [[concepts/bigdata/streaming-output-modok]] — append, complete.
- [[concepts/bigdata/rdd]] — az RDD API a batchen belül.
- [[concepts/bigdata/storm-vs-kotegelt-feldolgozas]] — a Storm eseményenkénti feldolgozásával szemben a Spark mikrobatch-alapú (wiki-kontextus, nem e forrás állítása).
