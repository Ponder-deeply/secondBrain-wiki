---
tags: [concept]
sources: [EA3_spark.pdf]
derivation: source
updated: 2026-09-12
---

# Lusta kiértékelés és DAG-ütemezés

A Spark a [[concepts/bigdata/spark-transzformaciok-es-akciok|transzformációkat]] nem futtatja le azonnal, hanem egy irányított körmentes gráfba (DAG) gyűjti, amit csak egy akció meghívásakor optimalizál és ütemez le.

## Tartalom

### Lusta kiértékelés (lazy evaluation)

A Hadoop MapReduce-hoz képest ez a Spark egyik fő performanciaelőnye: a job-ot a Spark **optimalizálja, mielőtt lefuttatná**. Emellett memória alapú cache-et használ (a HDD-t csak egyszer olvassa, utána a memóriában dolgozik), így hatékony pipeline-t épít, és a folyamatok közötti adatátadás nem igényel lemezműveletet — szemben a tipikus Hive-lekérdezéssel, amely 3-5 különálló MapReduce Job-ból áll.

### DAG Scheduler

Amikor a driver programban egy **akció** végrehajtódik (pl. `rdd.count()`), a Spark:

1. Az [[concepts/bigdata/rdd|RDD]] lineage-ből felépíti a **operátor DAG-ot**.
2. A DAG Scheduler ezt a gráfot **stage-ekre** bontja — egy stage azon transzformációk sorozata, amelyet egy worker megszakítás (shuffle) nélkül, egy önálló folyamatként el tud végezni.
3. A Task Scheduler minden stage-hez **task**-okat rendel (egy task egy stage futtatása az adat egy partícióján), és a klaszter menedzseren (cluster manager) keresztül elindítja őket a worker node-okon futó executor-okon.

### Alkalmazás dekompozíció

A Spark futtatási modellje négy szintű:

- **Alkalmazás (Application)** — egy `SparkContext`, amely tárolja az adatot a feldolgozáshoz és ütemezi a jobok sorozatát.
- **Job** — RDD transzformációk sorozata, amely egy akcióval vagy adatkiírással végződik; a driver alkalmazás vezérli.
- **Stage** — transzformációk egy olyan sorozata, amelyet egy független worker el tud végezni (shuffle-határ választja el a stage-eket).
- **Task** — egy stage futtatása az adat egy partícióján.

A WordCount példában (`sc.textFile → flatMap → map → reduceByKey → foreach`) a `reduceByKey` shuffle-je két stage-re bontja a jobot: az első stage-ben 4 task dolgozza fel a HDFS particionált bemenetét egészen a `map`-ig, a `reduceByKey` után pedig egy második stage (pl. 2 task) végzi a `foreach`-öt az újraparticionált adaton.

## Kapocs

- [[concepts/bigdata/rdd]] — a lineage, amiből a DAG épül
- [[concepts/bigdata/spark-transzformaciok-es-akciok]] — mi indítja el a kiértékelést (akció) és mi csak regisztrálja azt (transzformáció)
- [[concepts/bigdata/spark-architektura]] — driver, cluster manager és executor szerepe a task-ok futtatásában
