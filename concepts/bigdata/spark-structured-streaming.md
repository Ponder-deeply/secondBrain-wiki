---
tags: [concept]
sources: ["2026_27_1 ESATL8-IP-18KVIBDAG - Big Data architektúrák és elemző módszerek Gy_ 4. Gyakorlat _ ELTE Moodle.md"]
references: ["spark.apache.org/docs/latest/streaming/apis-on-dataframes-and-datasets.html"]
derivation: source
kind: model
element: earth
updated: 2026-10-07
---

# Spark Structured Streaming

A Structured Streaming a Spark jelenlegi stream-feldolgozó motorja: a végtelen bemenetet egy folyton bővülő táblaként kezeli, és rá ugyanazokat a DataFrame-műveleteket alkalmazza, mint a kötegelt adatra. A régi DStream API-t váltja le.

## Tartalom

### Modell: végtelen tábla

- A `spark.readStream` **streaming DataFrame**-et ad; minden új beérkező sor a bemeneti tábla új sora.
- A szokásos transzformációk (`withColumn`, `split`, `filter`, `groupBy`, `agg`, `join`) itt is működnek, lásd [[concepts/bigdata/spark-dataframe]] és [[concepts/bigdata/spark-transzformaciok-es-akciok]]. A lekérdezés lusta: csak a `writeStream ... .start()` indítja el.
- A kimenet írásának módját a [[concepts/bigdata/streaming-output-modok]] szabályozza; az időalapú aggregációt a [[concepts/bigdata/streaming-ablakok-es-watermark]] írja le.

### Socket forrás (gyakorlati példa)

Kafka nélküli, oktatási forrás: egy Python adatgenerátor TCP socketeken ad adatot (szerverlog, szenzor, tweet, telefonkoordináta külön porton).

```python
def socket_stream(port):
    return (spark.readStream.format("socket")
            .option("host", "sensorStream")
            .option("port", port)
            .load())
```

- A socket forrás egyetlen `value` string oszlopot ad soronként; a mezőket `F.split("value", " ")` bontja szét, majd `getItem(i)` / `[i]` és `cast` adja a típusos oszlopokat.
- Kiírás: `df.writeStream.format("console").outputMode(...).start()`; a visszaadott lekérdezésobjektum `.stop()`-jával állítható le.
- A socket csak tanuláshoz való; éles forrás pl. Kafka ([[concepts/bigdata/spark-kafka-integracio]]), az állapotkezelés és checkpoint: [[concepts/bigdata/spark-foreachbatch-es-checkpoint]].

### Példa: legnépszerűbb URL-ek

Ablak nélkül: `groupBy("urls").count().orderBy(desc).limit(5)` az indulás óta eltelt teljes adatra számol (complete mód kell hozzá). Ablakkal ugyanez időszeletenként, lásd [[concepts/bigdata/streaming-ablakok-es-watermark]].

### Szenzorriasztás: küszöb vs. ablakos szabály

- **Egyszerű küszöb:** `filter(sensor_type == "temperature" & value >= 35)` — minden egyetlen túllépő mérés riasztás. Egyetlen zajos mérés is fals alarmot okoz.
- **Ablakos szabály (fals alarmok csökkentése):** 10 másodperces ablakban legalább 3 mérés 80 °C fölött. `groupBy(window(...), "sensor_id")`, `sum(when(value >= 80, 1).otherwise(0))` számlálóval, majd `where("high_measurements >= 3")`. A riasztás így tartós túllépést jelez, nem egyetlen kiugrást.
- Fix és csúszó ablak egyaránt kipróbálható; a csúszó ablak gyakrabban értékel, de ugyanaz a mérés több ablakba is beleesik.

### DStream (örökség)

A **Spark Streaming / DStream** a korábbi generáció: `StreamingContext`, `ssc.socketTextStream`, RDD-alapú `map`/`reduceByKey`/`window(hossz, csúszás)`, `foreachRDD`, majd `ssc.start()` és `ssc.stop(...)`. Már nem fejlesztik; új alkalmazáshoz Structured Streaming ajánlott. A Structured Streaming deklaratív, DataFrame/SQL-alapú, és támogatja az event time-ot és a watermarkot. Összevetés a Storm tuple-alapú modelljével: [[concepts/bigdata/storm-vs-kotegelt-feldolgozas]].

### Önálló feladat-minták (a forrásból)

Top hashtag / top szavak ablakos aggregációval; tweet-hangulat szólexikonnal (+1/−1/0, az ablak átlaga); támadásdetektálás: 30 s-os ablakban egy `srcip` legalább 5 különböző `dstip`-re küld kérést, illetve megfordítva legalább 5 `srcip` ugyanarra a `dstip`-re. (Általános Spark-tudás, nem a forrásból: streaming DataFrame-en a `countDistinct` nem támogatott, helyette `approx_count_distinct` használható.)

### Paraméterek

*Dokumentáció alapján, nem a gyakorlati forrásból.*

- `format("socket")` + `host`, `port` — nem hibatűrő, mert nem tud adatot újrajátszani.
- `F.split(str, pattern)` — a `pattern` reguláris kifejezés: a `.` és a `|` karaktert escape-elni kell.
- `getItem(i)` — 0-tól indexel; nem létező indexre `null`-t ad. Sikertelen `cast` szintén `null`-t ad.
- `F.when(cond, v).otherwise(w)` — `otherwise` nélkül a nem teljesülő sorok `null`-t kapnak.
- `writeStream`
  - `format("console")` + `option("truncate", False)`: a hosszú cellák teljes kiírása.
  - `trigger(processingTime=...)`: a batch-gyakoriság.
  - `option("checkpointLocation", ...)`: l. [[concepts/bigdata/spark-foreachbatch-es-checkpoint]].
- `start()` — `StreamingQuery`-t ad vissza. Scriptben `awaitTermination()` kell utána, különben a program azonnal kilép.

## Kapocs

- [[concepts/bigdata/streaming-ablakok-es-watermark]] — ablakok, event time, watermark
- [[concepts/bigdata/streaming-output-modok]] — append / update / complete
- [[concepts/bigdata/spark-broadcast-valtozo]] — referenciaadat-join streamen
- [[concepts/bigdata/spark-architektura]] — a Spark futtatási modellje
- [[concepts/bigdata/storm-topologia]] — a Storm mint másik stream-feldolgozó
