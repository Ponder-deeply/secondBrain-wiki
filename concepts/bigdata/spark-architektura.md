---
tags: [concept]
sources: [EA3_spark.pdf]
derivation: source
updated: 2026-09-12
---

# Spark architektúra (driver / cluster manager / executor)

A Spark futtatási modellje egy központi **driver** programból, egy **cluster manager**-ből és a worker node-okon futó **executor**-okból áll, amelyek a tényleges tasko(ka)t végzik.

## Tartalom

### Telepítési módok

A Spark három módon futhat a klaszteren:

- **(a) Standalone** — Spark saját ütemezőjével, közvetlenül a HDFS fölött.
- **(b) Over YARN** — a Spark a Hadoop YARN erőforrás-kezelőjére támaszkodik.
- **(c) Spark in MR (SIMR)** — minden Spark worker egy Hadoop MapReduce map-folyamatban fut, a meglévő Hadoop MR klaszter fölé települve.

### Komponensek

- **Driver** (más néven a Spark alkalmazás maga):
  - itt érhető el a Spark Shell (Scala, Python, R, Java);
  - itt készül el a `SparkContext`;
  - az RDD-t lekérdezési gráffá (DAG) alakítja — lásd [[concepts/bigdata/lusta-kiertekeles-es-dag-utemezes]];
  - a lépéseket stage-ekbe pakolja;
  - ütemezi a task-okat és irányítja a futásukat;
  - tárolja az RDD-k metaadatait;
  - WebUI-t futtat.
- **Cluster Manager** (más néven Master) — erőforrásokat allokál, worker node-okat/executor-okat rendel a job-hoz, nyomon követi a beküldött job-okat és visszajelzi az állapotukat.
- **Worker node / Slave** — a klaszter egy gépe, amelyen egy vagy több **Executor** fut.
- **Executor**:
  - tárolja az adatot a cache-ben (JVM Heap, HDD) — lásd [[concepts/bigdata/spark-perzisztencia]];
  - olvassa az adatot külső forrásról;
  - írja az adatot külső forrásra;
  - elvégzi a tényleges adatfeldolgozásokat (task-ok futtatása).

### Végrehajtási folyamat

A driver a `SparkContext`-en keresztül kommunikál a cluster managerrel; az kiosztja az erőforrásokat a worker node-oknak, amelyek executor-okat indítanak. Az executor-ok egy vagy több task-ot futtatnak párhuzamosan, és a köztes eredményeket (RDD-blokkokat) a saját cache-ükben tárolják — egy adott RDD blokkjai jellemzően több worker node között oszlanak meg, részleges átfedéssel a hibatűrés érdekében.

## Kapocs

- [[concepts/bigdata/rdd]] — az adatszerkezet, amelynek partíciói a worker node-okon tárolódnak
- [[concepts/bigdata/lusta-kiertekeles-es-dag-utemezes]] — a driver ezt a lépést végzi a DAG Scheduler segítségével
- [[concepts/bigdata/spark-perzisztencia]] — az executor cache-ének tartalmát szabályozó perzisztencia-szintek
