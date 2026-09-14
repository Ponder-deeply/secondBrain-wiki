---
tags: [concept]
sources: [EA3_spark.pdf]
derivation: source
updated: 2026-09-12
---

# RDD (Resilient Distributed Dataset)

Az RDD a Spark alapvető adatszerkezete: az adatpartíciók kollekciója, amelyek a klaszter worker node-jain vannak tárolva, és amelyeken keresztül a Spark az összes adatmódosítást végzi.

## Tartalom

**Egyszerű definíció.** Az RDD az adatpartíciók kollekciója, amelyek a worker node-okon vannak tárolva.

**Komplex definíció.** Az RDD egy interfész az adat transzformációjához: átmenetileg tárolja az adatokat, és **nem módosítható** (immutable) — egy RDD-n végzett transzformáció mindig egy új RDD-t hoz létre, az eredeti változatlan marad.

### Metainformációk

Minden RDD az alábbi metainformációkat tárolja:

- **Partitions** — mely adatok kapcsolódnak ehhez az RDD-hez.
- **Dependencies** — a "szülő" RDD-k listája.
- **Compute** — a szülő RDD-ken végzendő függvény.
- **Preferred Locations** — hol van a legjobb hely a számítás elvégzésére (data locality).
- **Partitioner** — hogyan vágjuk szét az adatot partíciókba.

Ez a metaadat-lánc (Dependencies + Compute) alkotja az RDD-k közötti **lineage**-et (leszármazási gráfot), amelyből a [[concepts/bigdata/lusta-kiertekeles-es-dag-utemezes]] felépíti a végrehajtási gráfot, és amely hiba esetén az RDD újraszámolását is lehetővé teszi elveszett partíciók pótlására.

Az RDD az egyetlen lehetőség az adatok módosítására Spark-ban: erre szolgálnak a [[concepts/bigdata/spark-transzformaciok-es-akciok]].

## Kapocs

- [[concepts/bigdata/spark-transzformaciok-es-akciok]] — az RDD-ken végezhető két műveletfajta
- [[concepts/bigdata/lusta-kiertekeles-es-dag-utemezes]] — az RDD lineage alapján épített végrehajtási terv
- [[concepts/bigdata/spark-perzisztencia]] — az RDD tartalmának cache-elése memóriában/lemezen
- [[concepts/bigdata/spark-architektura]] — hol futnak és tárolódnak az RDD partíciói
