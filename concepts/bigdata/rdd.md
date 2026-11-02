---
tags: [concept]
sources: [EA3_spark.pdf, "2026_27_1 ESATL8-IP-18KVIBDAG - Big Data architektúrák és elemző módszerek Gy_ 2. Gyakorlat _ ELTE Moodle.md"]
references: ["spark.apache.org/docs/latest/api/python/reference/api/pyspark.SparkContext.textFile.html"]
derivation: source
kind: definition
element: earth
updated: 2026-10-07
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

### Gyakorlati megközelítés (2026-os gyakorlat)

- **Létrehozás:** meglévő kollekcióból `sc.parallelize(range(20))`, fájlból `sc.textFile(...)`. Klaszterben olyan fájlt kell használni, amelyet az executorok is elérnek, ezért kerül az adat [[concepts/bigdata/hdfs]]-re (`hdfs://namenode:8020/...`); `textFile` soronként egy elemet ad (pl. egy JSON-sor egy string, `json.loads`-szal értelmezhető).
- **Fogalmak a Spark UI-ban:** *driver* (a vezérlő program, itt a notebook), *master* (erőforrás-koordinátor), *worker* (számítási csomópont), *job* (egy akció által indított feldolgozás), *stage* (a job szakasza), *task* (egy stage egy partíción végzett munkája), *partition* (az RDD logikai része, amelyet egy task dolgoz fel).
- **Partíciókról** részletesen: [[concepts/bigdata/spark-particionalas]].

### Paraméterek

*Dokumentáció alapján, nem a gyakorlati forrásból.*

- `sc.parallelize(c, numSlices=None)` — a `c` Python-kollekció a driverről kerül szétosztásra, ezért csak kis adatra való. A `numSlices` a partíciószám.
- `sc.textFile(name, minPartitions=None)`
  - `name` lehet fájl, könyvtár, joker (`*.json`) vagy vesszővel elválasztott lista.
  - A `hdfs://namenode:8020/` a NameNode RPC-címe.
  - A `minPartitions` csak alsó korlát; alapból a blokkok száma dönt.

## Kapocs

- [[concepts/bigdata/spark-transzformaciok-es-akciok]] — az RDD-ken végezhető két műveletfajta
- [[concepts/bigdata/lusta-kiertekeles-es-dag-utemezes]] — az RDD lineage alapján épített végrehajtási terv
- [[concepts/bigdata/spark-perzisztencia]] — az RDD tartalmának cache-elése memóriában/lemezen
- [[concepts/bigdata/spark-architektura]] — hol futnak és tárolódnak az RDD partíciói
- [[concepts/bigdata/spark-particionalas]] — az RDD partíciói, `glom`, `repartition` vs `coalesce`
- [[concepts/bigdata/spark-kulcs-ertek-muveletek]] — kulcs-érték RDD-k műveletei
