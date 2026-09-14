---
tags: [concept]
sources: [EA1_bevezetes.pdf]
derivation: source
updated: 2026-09-12
---

# Big Data ökoszisztéma

A Big Data architektúra (lásd [[concepts/bigdata/big-data-architektura]])
egyes funkcionális komponenseit megvalósító, egymással jellemzően együtt
használt nyílt forráskódú technológiák áttekintése (a
`hadoopecosystemtable.github.io` felsorolása alapján, nem teljes körű lista).
Ez a lap csak a technológiák szerepét és egymáshoz való viszonyát vázolja fel
áttekintés szinten; az egyes rendszerek belső működése (pl. HDFS, YARN,
MapReduce, illetve a Spark RDD-modellje) külön fogalomlapok tárgya.

## Tartalom

### Tárolás és erőforrás-kezelés

- **Hadoop / HDFS (Hadoop Distributed File System)** — az adatok elosztott
  tárolásáért felelős alaprendszer, amelyre a legtöbb más komponens épül.
- **HBase** — oszloporientált NoSQL adatbázis a HDFS fölött.
- **Zookeeper** — a klaszter komponensei közötti koordinációért felelős
  szolgáltatás.

### Feldolgozás

- **Hadoop MapReduce** — elosztott programozási keretrendszer batch
  feldolgozáshoz.
- **Spark** — általános célú, memóriában dolgozó elosztott feldolgozó motor;
  a batch mellett stream feldolgozásra is alkalmas.
- **GraphX** — a Spark gráffeldolgozó komponense.
- **Apache Giraph** — dedikált, nagy léptékű gráffeldolgozó rendszer.

### Adatintegráció

- **Sqoop** — strukturált (relációs) adatforrások és a HDFS közötti
  adatátvitelre szolgál.
- **Flume** — elsősorban log- és eseményadatok (streaming jellegű) begyűjtésére
  és a HDFS-be juttatására szolgál.

### Lekérdezés és elemzés

- **Pig** — magas szintű adatfolyam-nyelv MapReduce feladatok
  megfogalmazásához.
- **Hive** — SQL-szerű lekérdezőnyelvet (HiveQL) biztosít a HDFS-en tárolt
  adatok felett.
- **Impala** — skálázható, interaktív SQL-lekérdező motor.
- **Apache Drill** — skálázható, interaktív lekérdezőrendszer, változatos
  adatforrások (pl. félig strukturált adat) felett.
- **Mahout** — adatbányászati (data mining) algoritmuskönyvtár.

### Munkafolyamat-kezelés és felhasználói felület

- **Oozie** — a fenti komponensek közötti feladatok munkafolyamatának (job
  workflow) ütemezője — az architektúra "orchestration" komponensének egy
  megvalósítása (lásd [[concepts/bigdata/big-data-architektura]]).
- **Hue** — webes felhasználói konzol a Hadoop-ökoszisztéma eléréséhez.

### Kapcsolódó tárolási minta: Data Lake

Egy jellemző modern felépítésben a különböző forrásokból (relációs
adatbázisok, külső feedek, streaming adat) érkező nyers adat egy közös
"data lake"-be (pl. dokumentumtárolóval, mint a MongoDB, illetve Hadoop/Spark
alapú elosztott feldolgozással) kerül, ahonnan a downstream rendszerek és
riportok merítenek.

## Kapocs

- [[concepts/bigdata/big-data-architektura]] — az architektúra, amelynek
  komponenseit ezek a technológiák megvalósítják
- [[concepts/bigdata/big-data]] — a Big Data fogalma és motivációja
