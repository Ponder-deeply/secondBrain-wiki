---
tags: [concept]
sources: ["2026_27_1 ESATL8-IP-18KVIBDAG - Big Data architektúrák és elemző módszerek Gy_ 2. Gyakorlat _ ELTE Moodle.md"]
references: ["spark.apache.org/docs/latest/api/python/reference/pyspark.html#rdd-apis"]
derivation: source
kind: procedure
element: earth
updated: 2026-10-07
---

# Spark partíciók: glom, repartition, coalesce

Az [[concepts/bigdata/rdd]] adatai partíciókra bontva élnek a klaszterben; egy partíciót egy task dolgoz fel, ezért a partíciószám a párhuzamosság mértéke.

## Tartalom

- **Partíció:** az RDD adatainak logikai része; egy stage minden partícióra egy taskot indít.
- **`rdd.getNumPartitions()`** — a partíciók száma.
- **`glom()`** — partíciónként listába gyűjti az elemeket, így látható az elosztás: `rdd.repartition(4).glom().collect()` négy listát ad.
- **`repartition(n)`** — tetszőleges új partíciószám, általában teljes **shuffle**-lel; növelni és csökkenteni is lehet.
- **`coalesce(n)`** — elsősorban a partíciószám **csökkentésére**; meglévő partíciókat von össze, tipikusan shuffle nélkül, ezért olcsóbb. Növelésre alapértelmezetten nem hat (shuffle nélkül nem tud új partíciót létrehozni), míg `repartition` igen.

| Művelet | Irány | Költség |
|---|---|---|
| `repartition(n)` | fel és le | shuffle |
| `coalesce(n)` | főleg le | kevesebb/nincs shuffle |

A gyakorlaton a négy kombinációt (repartition/coalesce, 4 és 8 partíció) `glom()`-mal hasonlították össze egy `range(20)` RDD-n.

Kapcsolódó vizsgapont: a `fold` kezdőértéke partíciónként érvényesül, így az eredmény a partíciószámtól függ ([[concepts/bigdata/spark-transzformaciok-es-akciok]]).

### Paraméterek

*Dokumentáció alapján, nem a gyakorlati forrásból.*

- `repartition(n)` — mindig shuffle. DataFrame-en `repartition(n, "oszlop")`: az oszlop hash-e szerint oszt szét, az azonos kulcsok egy partícióba kerülnek.
- `coalesce(n, shuffle=False)` — shuffle nélkül csak csökkenteni tudja a partíciók számát, ezért a `coalesce(8)` nem ad több partíciót, mint amennyi volt.
  - `shuffle=True` esetén ugyanaz, mint a `repartition`.
  - A `coalesce(1)` az egész számítást egyetlen taskra kényszerítheti.
- `parallelize(c, numSlices)`, `textFile(path, minPartitions)` — a kezdő partíciószám. Alapértelmezés: `spark.default.parallelism`, illetve a fájl blokkjainak száma.
- `spark.sql.shuffle.partitions` — DataFrame-en a shuffle utáni partíciószám (alapból 200).

## Kapocs

- [[concepts/bigdata/rdd]] — az adatszerkezet, amelynek partíciói vannak
- [[concepts/bigdata/spark-transzformaciok-es-akciok]] — shuffle-t okozó és keskeny műveletek
- [[concepts/bigdata/spark-perzisztencia]] — cache partíciónként
- [[concepts/bigdata/spark-architektura]] — executorok, taskok
