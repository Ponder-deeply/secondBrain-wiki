---
tags: [concept]
sources: [EA3_spark.pdf, "2026_27_1 ESATL8-IP-18KVIBDAG - Big Data architektúrák és elemző módszerek Gy_ 2. Gyakorlat _ ELTE Moodle.md"]
references: ["spark.apache.org/docs/latest/api/python/reference/api/pyspark.RDD.persist.html"]
derivation: source
kind: procedure
element: earth
updated: 2026-10-07
---

# Spark perzisztencia (cache / persist)

Az RDD alapból csak átmenetileg, egy job végrehajtása idejére tárolódik; a `persist`/`cache` hívással azonban a felhasználó explicit módon megőrizheti egy RDD tartalmát ismételt felhasználásra, elkerülve az újraszámolást.

## Tartalom

A perzisztencia szintjei (`Persistence Level`) azt szabályozzák, hol és milyen formában tárolódik egy RDD adatai:

| Persistence Level | Leírás |
|---|---|
| `MEMORY_ONLY` | Az RDD-t deszerializált Java objektumként tároljuk. Ha nem fér el a memóriában, újraszámoljuk. |
| `MEMORY_AND_DISK` | Az RDD-t deszerializált Java objektumként tároljuk. Ha nem fér el a memóriában, a lemezen tároljuk. |
| `MEMORY_ONLY_SER` | Ugyanaz, mint `MEMORY_ONLY`, csak szerializálva tároljuk a memóriában. |
| `MEMORY_AND_DISK_SER` | Ugyanaz, mint `MEMORY_AND_DISK`, csak szerializálva tároljuk a memóriában. |
| `DISK_ONLY` | Az adatokat kizárólag a lemezen tároljuk. |
| `MEMORY_ONLY_2`, `DISK_ONLY_2` | Ugyanaz, mint feljebb, csak a partíciókat replikáljuk a klaszterben. |

A cache-elt adatot az [[concepts/bigdata/spark-architektura|executor]] tárolja (JVM Heap vagy HDD), és ez adja a Spark egyik fő performanciaelőnyét a Hadoop MapReduce-hoz képest: a HDD-t csak egyszer kell olvasni, utána a memóriában tárolt, deszerializált objektumokon dolgozik a további [[concepts/bigdata/spark-transzformaciok-es-akciok|transzformációk és akciók]] sorozata.

### Gyakorlati megjegyzés

A `cache()` a `persist(MEMORY_ONLY)` rövidítése, de **lusta**: a hívás önmagában nem hajtja végre a számítást, az első akció (`collect()`, `first()`, `take(3)`...) tölti fel a cache-t; a további akciók már a tárolt partíciókból dolgoznak (`sc.parallelize(range(10)).cache()` példa a 2026-os gyakorlaton).

### Paraméterek

*Dokumentáció alapján, nem a gyakorlati forrásból.*

- `persist(storageLevel)` — a szint a fenti táblázatból.
  - A `cache()` RDD-n `MEMORY_ONLY`, DataFrame-en `MEMORY_AND_DISK`.
  - PySparkban az adat mindig szerializálva (pickle) tárolódik, így a `_SER` változatok nem jelentenek különbséget.
  - Egy már perzisztált RDD szintje nem módosítható; előbb `unpersist()` kell.
- `unpersist(blocking=False)` — felszabadítja a cache-t; `blocking=True` megvárja a törlést.
- A Spark UI Storage fülén látszik, a partíciók hány százaléka van cache-ben.

## Kapocs

- [[concepts/bigdata/rdd]] — az az adatszerkezet, amit a perzisztencia szintjei cache-elnek
- [[concepts/bigdata/spark-architektura]] — az executor tárolja a cache-elt partíciókat
- [[concepts/bigdata/lusta-kiertekeles-es-dag-utemezes]] — a cache elkerüli az ismételt lineage-újraszámolást
- [[concepts/bigdata/spark-particionalas]] — a cache partíciónként tárolódik
