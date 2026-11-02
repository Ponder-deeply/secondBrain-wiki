---
tags: [concept]
sources: ["2026_27_1 ESATL8-IP-18KVIBDAG - Big Data architektúrák és elemző módszerek Gy_ 4. Gyakorlat _ ELTE Moodle.md"]
references: ["spark.apache.org/docs/latest/api/python/reference/pyspark.sql/api/pyspark.sql.functions.broadcast.html"]
derivation: source
kind: procedure
element: earth
updated: 2026-10-07
---

# Broadcast referenciaadat (broadcast join)

Kis referenciatáblát (pl. antennák) minden végrehajtóra elküldünk, így a nagy adathalmazzal való összekapcsolásához nem kell a nagy oldalt shuffle-ölni.

## Tartalom

- `F.broadcast(df)` jelzi, hogy a DataFrame kicsi, és eljuttatandó a végrehajtókhoz. Indok a forrásból: a nagyobb streaming adathalmaz feldolgozásakor ne kelljen szükségtelenül nagy shuffle-t végrehajtani. Shuffle-ről: [[concepts/bigdata/spark-architektura]].

### Példa: telefon legközelebbi antennája

1. Statikus `antennas` DataFrame (`antenna_id, lat, lon`), sémával létrehozva (`createDataFrame`).
2. Streaming `coords`: socketről `phone_id, event_time, lat, lon` (hibás sorok kiszűrve: `size(p) == 4`, `event_time` nem null).
3. `coords.crossJoin(F.broadcast(antennas))` — minden telefonpozícióhoz minden antenna; `distance2 = (lat-alat)^2 + (lon-alon)^2` (egyszerűsített négyzetes távolság; valódi földrajzi távolsághoz geodéziai függvény kell).
4. Legközelebbi: watermark az `event_time`-on, `groupBy(window("event_time","20 seconds","5 seconds"), "phone_id")`, `agg(F.min(F.struct("distance2","antenna_id")))` — a struct az első mező szerint rendeződik, így a minimum a legkisebb távolságú antennát adja. Kiírás append módban ([[concepts/bigdata/streaming-output-modok]]).

Megjegyzés: a Spark Core szintű `sc.broadcast` változó az alacsony szintű megfelelő; a forrás csak a DataFrame-szintű `F.broadcast` joint mutatja.

### Paraméterek

*Dokumentáció alapján, nem a gyakorlati forrásból.*

- `F.broadcast(df)` — csak tipp az optimalizálónak: a kis tábla minden executorra átmásolódik, a nagy oldal így shuffle nélkül kapcsolódik hozzá. A kis táblának el kell férnie az executor memóriájában.
- `spark.sql.autoBroadcastJoinThreshold` — e méret (alapból 10 MB) alatt a Spark tipp nélkül is broadcastol; `-1` kikapcsolja.
- `crossJoin(other)` — feltétel nélküli Descartes-szorzat; csak akkor használható, ha az egyik oldal kicsi.
- `F.struct(...)` — mezősorrend szerint, lexikografikusan hasonlít össze, ezért kell a `distance2`-nek az első helyen állnia.

## Kapocs

- [[concepts/bigdata/spark-structured-streaming]] — a streaming környezet
- [[concepts/bigdata/streaming-ablakok-es-watermark]] — az ablak és a watermark a példában
- [[concepts/bigdata/spark-dataframe]] — DataFrame-műveletek, join
