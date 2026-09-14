---
tags: [subject]
sources: [Big-Data-architekturak-es-elemzo-modszerek-targyleiras.pdf, EA1_bevezetes.pdf, EA2_hadoop.pdf, EA3_spark.pdf, EA4_spark_graphx.pdf, EA5_storm.pdf, gyak2.pdf, gyak3.pdf, gyak4.pdf, gyak7.pdf, BDAEM-2022-EA7.pptx, BDAEM-2022-EA8.pptx, BDAEM-2022-EA9.pptx, BDAEM-2022-EA10.pptx, BDAEM-2022-EA11.pdf, BDAEM-2022-EA12.pdf]
references: [Tom White, Hadoop: The Definitive Guide, Nick Pentreath, Machine Learning with Spark (Packt, ISBN 9781783288519), Raúl Garreta, Learning scikit-learn: Machine Learning in Python (Packt, ISBN 9781783281930)]
derivation: source
updated: 2026-09-12
---

# Big Data architektúrák és elemző módszerek (bigdata)

A tárgy két, egymásra épülő félidőből áll: az első fele az elosztott
adattárolás és -feldolgozás architektúráit (Hadoop, Spark, Spark GraphX, Storm)
tárgyalja, a második fele pedig a rájuk épülő gépi tanulási és adatelemző
módszertárat — osztályozás, klaszterezés, dimenziócsökkentés, ajánlórendszerek,
és egy bevezető deep learning szakasz.

## Tárgykör

A tantárgyleírás szerint: nagy adattömegek (Big Data) tárolási és feldolgozási
kihívásai; elosztott fájlrendszerek és klaszter-menedzsment (HDFS, YARN);
kötegelt feldolgozás (MapReduce, Pig, Hive); memóriaalapú kötegelt feldolgozás
(Spark, RDD, DataFrame); stream feldolgozás (Storm, Flink, Kafka); gráf
feldolgozás (Spark GraphX, Pregel modell); gépi tanulási alapmódszerek
(osztályozás, regresszió, klaszterezés, dimenziócsökkentés); ensemble-módszerek;
ajánlórendszerek; deep learning bevezetés; adatvizualizáció.

A tárgy 5 kredites, kötelező, kollokviummal és gyakorlati jeggyel összevont
számonkérésű (2 ea + 2 gy + 1 konz, 5. félév). Előtanulmányi feltétel:
Programozási nyelvek I. Oktató: **Gombos Gergő Dr.**; a 2022-es félév második
felét (a BDAEM-2022-EA7..EA12 anyagok) **Laki Sándor** adta elő — ez egy korábbi
félév archív anyaga, nem a jelenlegi kurzus élő része.

## Fogalomlapok

### Bevezetés
- Mi a Big Data, motiváció és alkalmazási területek — [[concepts/bigdata/big-data]]
- Az 5V modell (Volume, Velocity, Variety, Veracity, Value) — [[concepts/bigdata/big-data-5v]]
- Big Data architektúra rétegei — [[concepts/bigdata/big-data-architektura]]
- A Big Data ökoszisztéma áttekintése (Hadoop, Spark, Storm és társai) — [[concepts/bigdata/big-data-okoszisztema]]
- A data scientist szerepköre — [[concepts/bigdata/data-scientist]]

### Hadoop ökoszisztéma
- HDFS: elosztott fájlrendszer, replikáció, hibatűrés — [[concepts/bigdata/hdfs]]
- YARN: klaszter-menedzsment — [[concepts/bigdata/yarn]]
- YARN ütemezők — [[concepts/bigdata/yarn-utemezok]]
- MapReduce programozási modell — [[concepts/bigdata/mapreduce]]
- MapReduce hibatűrés — [[concepts/bigdata/mapreduce-hibatures]]
- A Hadoop korlátai — [[concepts/bigdata/hadoop-korlatai]]
- Apache Pig — [[concepts/bigdata/apache-pig]]
- Hive — [[concepts/bigdata/hive]]

### Spark
- Spark architektúra — [[concepts/bigdata/spark-architektura]]
- RDD (Resilient Distributed Dataset) — [[concepts/bigdata/rdd]]
- Spark transzformációk és akciók — [[concepts/bigdata/spark-transzformaciok-es-akciok]]
- Lusta kiértékelés és DAG-ütemezés — [[concepts/bigdata/lusta-kiertekeles-es-dag-utemezes]]
- Spark perzisztencia (cache, persist) — [[concepts/bigdata/spark-perzisztencia]]
- Spark DataFrame — [[concepts/bigdata/spark-dataframe]]

### Spark GraphX
- Property graph modell — [[concepts/bigdata/property-graph]]
- GraphX tárolási architektúra — [[concepts/bigdata/graphx-tarolasi-architektura]]
- Pregel modell — [[concepts/bigdata/pregel-modell]]
- PageRank GraphX-ben — [[concepts/bigdata/pagerank-graphx]]
- Háromszög-számlálás Pregellel — [[concepts/bigdata/haromszog-szamlalas-pregel]]
- Összefüggő komponensek Pregellel — [[concepts/bigdata/osszefuggo-komponensek-pregel]]

### Storm / stream feldolgozás
- Storm architektúra — [[concepts/bigdata/storm-architektura]]
- Storm topológia (spout, bolt) — [[concepts/bigdata/storm-topologia]]
- Storm megbízható feldolgozás — [[concepts/bigdata/storm-megbizhato-feldolgozas]]
- Storm vs. kötegelt feldolgozás — [[concepts/bigdata/storm-vs-kotegelt-feldolgozas]]

### Gépi tanulás: alapfogalmak és előkészítés
- Gépi tanulás alapfogalmak — [[concepts/bigdata/gepi-tanulas-alapfogalmak]]
- Adat-előkészítés gépi tanuláshoz — [[concepts/bigdata/adat-elokeszites-gepi-tanulashoz]]
- Adattisztítás — [[concepts/bigdata/adattisztitas]]
- Modellértékelés, keresztvalidáció — [[concepts/bigdata/modellertekeles-keresztvalidacio]]
- Távolság- és hasonlóságmérések — [[concepts/bigdata/tavolsag-hasonlosag-meresek]]
- Szöveg reprezentáció — [[concepts/bigdata/szoveg-reprezentacio]]

### Gépi tanulás: osztályozás és regresszió
- Lineáris regresszió — [[concepts/bigdata/linearis-regresszio]]
- Logisztikus regresszió — [[concepts/bigdata/logisztikus-regresszio]]
- K-legközelebbi szomszéd (KNN) — [[concepts/bigdata/k-legkozelebbi-szomszed]]
- Döntési fa — [[concepts/bigdata/dontesi-fa]]
- SVM (support vector machine) — [[concepts/bigdata/svm]]
- Naiv Bayes — [[concepts/bigdata/naive-bayes]]
- Ensemble-módszerek áttekintése — [[concepts/bigdata/ensemble-modszerek]]
- Bagging — [[concepts/bigdata/bagging]]
- AdaBoost — [[concepts/bigdata/adaboost]]
- Random forest — [[concepts/bigdata/random-forest]]

### Gépi tanulás: klaszterezés és dimenziócsökkentés
- K-Means — [[concepts/bigdata/k-means]]
- Hierarchikus klaszterezés — [[concepts/bigdata/hierarchikus-klaszterezes]]
- DBSCAN — [[concepts/bigdata/dbscan]]
- Dimenziócsökkentés áttekintése — [[concepts/bigdata/dimenziocsokkentes]]
- PCA (főkomponens-analízis) — [[concepts/bigdata/pca]]
- Kovariancia — [[concepts/bigdata/kovariancia]]
- Sajátvektor és sajátérték — [[concepts/bigdata/sajatvektor-sajatertek]]

### Ajánlórendszerek
- Ajánlórendszerek alapjai — [[concepts/bigdata/ajanlorendszerek-alapjai]]
- Felhasználó-alapú kollaboratív szűrés — [[concepts/bigdata/felhasznalo-alapu-kollaborativ-szures]]
- Elem-alapú kollaboratív szűrés — [[concepts/bigdata/elem-alapu-kollaborativ-szures]]
- Mátrixfaktorizáció ajánlórendszerekben — [[concepts/bigdata/matrixfaktorizacio-ajanlorendszerekben]]

### Deep learning bevezetés
- Mesterséges neuron — [[concepts/bigdata/mesterseges-neuron]]
- Perceptron — [[concepts/bigdata/perceptron]]
- Aktivációs függvények — [[concepts/bigdata/aktivacios-fuggvenyek]]
- Hibavisszaterjesztés (backpropagation) — [[concepts/bigdata/hibavisszaterjesztes]]
- Konvolúciós hálózat — [[concepts/bigdata/konvolucios-halozat]]

## Lefedettségi hiányok

A staged forrásanyag jelenleg **nem** fedi le a tematika néhány pontját — ezek
egy jövőbeli ingest tárgyai, ha a hozzájuk tartozó anyag letöltésre kerül, nem
pedig kitalálandó tartalom most:

- **Kafka** — az `EA6-kafka.txt` csak egy Canvas-linket tartalmazott, a tényleges
  anyag nincs letöltve.
- **Flink** — a tematika említi (12. pont, stream feldolgozás), de nincs hozzá
  staged forrás.
- **Python/R adatelemző eszköztár önálló témaként** (Jupyter, Pandas, NumPy,
  SciPy, scikit-learn mint a tematika 2., 3., 6. pontja) — csak a `gyak`
  feladatlapokban felbukkanó, esetleges használat van lefedve, önálló
  fogalomlapok nélkül.
- Az adatvizualizáció (matplotlib, d3.js, Zeppelin, Lightning — 20. pont) sem
  jelenik meg önálló lapon.

## Kapocs

- [[subjects/dimatii]] — a mátrixfaktorizáció és sajátérték-számítás lineáris
  algebrai előismeretei
