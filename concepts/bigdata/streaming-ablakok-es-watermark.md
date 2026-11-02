---
tags: [concept]
sources: ["2026_27_1 ESATL8-IP-18KVIBDAG - Big Data architektúrák és elemző módszerek Gy_ 4. Gyakorlat _ ELTE Moodle.md"]
references: ["spark.apache.org/docs/latest/streaming/apis-on-dataframes-and-datasets.html#window-operations-on-event-time"]
derivation: source
kind: definition
element: earth
updated: 2026-10-07
---

# Streaming ablakok, event time és watermark

Végtelen adatfolyamon az aggregációt időablakokra kell bontani; az ablakot az esemény időbélyege (event time) határozza meg, a watermark pedig megmondja, meddig várunk késő eseményekre.

## Tartalom

### Fix (tumbling) ablak

`F.window(időoszlop, "10 minutes")` — egymást nem fedő, egyenlő hosszú szeletek; minden esemény pontosan egy ablakba esik.

```python
df.groupBy(F.window("ingest_time", "10 minutes"), "urls").count()
```

### Csúszó (sliding) ablak

`F.window(időoszlop, "10 minutes", "5 minutes")` — ablakhossz és csúszás (slide); az ablakok átfedik egymást, egy esemény hossz/csúszás darab ablakba esik. Gyakoribb frissítés, simább trend, de több állapot. A DStream megfelelője: `window(2, 1)`.

### Processing time vs. event time

- **Processing / ingest time:** mikor dolgozza fel a Spark az eseményt (pl. `F.current_timestamp()` hozzáadott oszlop).
- **Event time:** az eseményben szereplő időpont (pl. a szenzor vagy telefon időbélyege, `F.to_timestamp(...)`).
- Streamingben az event time számít, mert az események késve, rendezetlenül érkezhetnek.

### Watermark

```python
df.withWatermark("event_time", "10 seconds")
```

- Azt adja meg, meddig vár a rendszer a késő eseményekre (általános definíció: a látott legnagyobb event time mínusz a tűrés).
- Segít a streaming **state méretének korlátozásában**: az elég régi ablakok lezártnak tekinthetők, állapotuk törölhető.
- Ez teszi lehetővé az **append** módot ablakos aggregációra ([[concepts/bigdata/streaming-output-modok]]): az ablak eredménye a lezárása után végleges.
- Példa: legközelebbi antenna, `withWatermark("event_time", "1 seconds")`, 20 s-os ablak 5 s csúszással ([[concepts/bigdata/spark-broadcast-valtozo]]).
- Kísérlet a gyakorlaton: késő időbélyegű adat watermarkkal és anélkül; megfigyelhető, mikor zárul le egy ablak.
- Megjegyzés: a forrás példái az `ingest_time` oszlopra is tesznek watermarkot; ez a szenzoroknál valójában a szenzor időbélyegéből parse-olt érték.

### Paraméterek

*Dokumentáció alapján, nem a gyakorlati forrásból.*

- `F.window(timeColumn, windowDuration, slideDuration=None, startTime=None)`
  - `timeColumn`: `timestamp` típusú oszlop.
  - `slideDuration`: ha elmarad, az ablak fix (tumbling). Nem lehet nagyobb az ablakhossznál; egy esemény hossz / csúszás darab ablakba esik.
  - `startTime`: az ablakhatárok eltolása.
  - Az eredmény egy `window` struct oszlop, `window.start` és `window.end` mezővel.
- `withWatermark(eventTime, delayThreshold)`
  - Az aggregáció *előtt* kell hívni, ugyanarra az oszlopra, amelyen a `window` dolgozik; különben az állapot nem takarítódik.
  - Watermark = a legnagyobb eddig látott event time − `delayThreshold`. Az ennél régebbi ablak lezárul: append módban ekkor íródik ki, és az állapota törlődik.
  - A tűrésen belül érkező késő adat garantáltan bekerül; a tűrésen túli eldobható.
- `F.to_timestamp(col, format)` — pl. `"yyyy-MM-dd'T'HH:mm:ss"`; ha nem tudja értelmezni, `null`-t ad.

## Kapocs

- [[concepts/bigdata/spark-structured-streaming]] — a streaming modell
- [[concepts/bigdata/streaming-output-modok]] — a watermark és az append mód kapcsolata
- [[concepts/bigdata/spark-broadcast-valtozo]] — ablakos példa broadcast joinnal
