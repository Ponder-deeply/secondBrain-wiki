---
tags: [concept, bigdata/spark]
sources: [EA3_spark.pdf]
derivation: source
updated: 2026-09-12
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

## Kapocs

- [[concepts/bigdata/rdd]] — az az adatszerkezet, amit a perzisztencia szintjei cache-elnek
- [[concepts/bigdata/spark-architektura]] — az executor tárolja a cache-elt partíciókat
- [[concepts/bigdata/lusta-kiertekeles-es-dag-utemezes]] — a cache elkerüli az ismételt lineage-újraszámolást
