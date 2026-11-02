---
tags: [concept]
sources: ["2026_27_1 ESATL8-IP-18KVIBDAG - Big Data architektúrák és elemző módszerek Gy_ 4. Gyakorlat _ ELTE Moodle.md"]
references: ["spark.apache.org/docs/latest/streaming/apis-on-dataframes-and-datasets.html#output-modes"]
derivation: source
kind: comparison
element: earth
updated: 2026-10-07
---

# Streaming output mode-ok (append, update, complete)

Az output mode azt határozza meg, hogy a streaming lekérdezés minden triggerkor az eredménytábla melyik részét írja ki a sinkbe.

## Tartalom

| Mód | Jelentés |
|---|---|
| **append** | Csak az új, végleges eredménysorokat írja ki. |
| **update** | Az adott triggerben módosult vagy új sorokat írja ki. |
| **complete** | A teljes aktuális eredménytáblát kiírja minden triggernél. |

```python
x = df2.writeStream.format("console").outputMode("complete").start()
```

- A gyakorlat top-5 URL példája (aggregáció, rendezés, `limit`) **complete** módban fut: az eredmény bármely sora változhat.
- A legközelebbi antenna példa (ablakos aggregáció watermarkkal) **append** módban fut: az ablak lezárása után lesz végleges ([[concepts/bigdata/streaming-ablakok-es-watermark]]).
- Gyakorlati feladat: ugyanazt az aggregációt mindhárom móddal kipróbálni, és megfigyelni, melyik mit enged.
- Általános Spark-tudás (nem a forrásból): a Spark hibát jelez, ha a mód nem kompatibilis a lekérdezéssel; pl. rendezés streaming aggregáció után csak complete módban lehetséges, aggregáció watermark nélkül append módban nem.

### Paraméterek

*Dokumentáció alapján, nem a gyakorlati forrásból.*

`outputMode(mode)` — alapértelmezés: `"append"`. Melyik lekérdezéshez melyik mód engedett:

| Lekérdezés | append | update | complete |
|---|---|---|---|
| Aggregáció nélkül | igen | igen | nem |
| Aggregáció watermark nélkül | nem | igen | igen |
| Ablakos aggregáció watermarkkal | igen (ablakzáráskor) | igen | igen (az állapot nem törlődik) |
| `orderBy` aggregáció után | nem | nem | igen |

A fájl-sink csak append módot fogad.

## Kapocs

- [[concepts/bigdata/spark-structured-streaming]] — a streaming modell és a writeStream
- [[concepts/bigdata/streaming-ablakok-es-watermark]] — ablakok és watermark
