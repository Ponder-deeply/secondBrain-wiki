---
tags: [concept]
sources: [EA5_storm.pdf]
references: ["Chintapalli et al., Benchmarking Streaming Computation Engines: Storm, Flink and Spark Streaming, IEEE IPDPS Workshops 2016"]
derivation: source
updated: 2026-09-12
---

# Storm vs. kötegelt feldolgozás (Hadoop, Spark)

A Storm valós idejű **stream-feldolgozó** modellje szemben a Hadoop
**kötegelt (batch)** MapReduce-modelljével és a Spark
mikroköteg-alapú feldolgozásával: a fő különbség, hogy egy Storm
**topológia örökké fut**, míg egy MapReduce job vagy Spark job
egyszer lefut és véget ér.

## Tartalom

### Storm vs. Hadoop

A Storm klaszter felületesen hasonlít egy Hadoop-klaszterre, de a
futtatott egység alapvetően más:

| | Storm | Hadoop |
|---|---|---|
| Feldolgozási modell | valós idejű stream-feldolgozás | kötegelt (batch) feldolgozás |
| Állapot | stateless | stateful |
| Master/slave elnevezés | **Nimbus** / **Supervisor**-ok | **JobTracker** / **TaskTracker**-ek |
| Futási egység | topológia — örökké fut, amíg le nem állítják | MapReduce job — véges, egyszer lefut és befejeződik |
| Áteresztőképesség | tízezer üzenet/mp nagyságrend klaszterenként | percekig-óráig tartó, nagy adatmennyiségű feldolgozás ([[concepts/bigdata/mapreduce]]) |
| Hibatűrés | ha a Nimbus/Supervisor leáll, újraindítás után onnan folytatja, ahol abbamaradt | ha a JobTracker leáll, az összes futó job elveszik |

Mindkettő elosztott és hibatűrő rendszer, mindkettő ZooKeeper-alapú
koordinációt (is) használhat. A Hadoop architektúráját és a
[[concepts/bigdata/mapreduce]] modellt lásd a dedikált lapokon; a
Storm oldali komponenseket lásd a
[[concepts/bigdata/storm-architektura]] lapon.

### Storm vs. Spark

- A **Storm** valódi (tuple-alapú) stream-feldolgozó rendszerként
  viselkedik, alacsonyabb latenciával.
- A **Spark** (lásd [[concepts/bigdata/spark-architektura]]) nagyobb
  áteresztőképességre képes, valamivel magasabb latencia mellett — ez
  összhangban áll azzal, hogy a Spark alapvetően mikroköteg-alapú
  (nem tuple-önkénti) feldolgozást végez.
- Valós idejű adatfeldolgozásra a forrás a Stormot tartja jobb
  választásnak.

Egy 2016-os Yahoo-benchmark (Storm, Flink, Spark Streaming
összehasonlítása, 150 000 üzenet/mp terhelésen) szerint a
Storm és a Flink lényegesen alacsonyabb és stabilabb late window
update time-ot, illetve 94. percentilis latenciát mutatott, mint a
Spark, amelynek latenciája a növekvő áteresztőképességgel meredeken
nőtt.

### Felhasználási esetek

A Stormot éles környezetben többek közt a Twitter (adatbázis- és
üzenetküldő infrastruktúra monitorozása), a Yahoo!, a Groupon
(nagy mennyiségű, nem egyedi adatpont valós idejű tisztítása és
normalizálása) és az Alibaba (alkalmazásnaplók és adatbázis-változások
valós idejű feldolgozása) használja. Jellemző iparági
alkalmazási minták: "prevent" jellegű (pl. csalásészlelés,
hálózati kimaradások, minőségbiztosítás) és "optimize" jellegű
(pl. árazás, útvonaltervezés, személyre szabott tartalom) use case-ek
a pénzügy, telekom, kiskereskedelem, gyártás, közlekedés és web
területén.

### Storm előnyei és hátrányai

Előnyök: magas hibatűrés, nagyon alacsony latencia, valós idejű
stream-feldolgozási modell, tetszőleges programozási nyelv
használhatósága, legalább egyszeri feldolgozási garancia (lásd
[[concepts/bigdata/storm-megbizhato-feldolgozas]]), magas
skálázhatóság.

Hátrányok: a natív ütemező és erőforrás-kezelő (Nimbus) szűk
keresztmetszetté válhat; a szálakra és adatfolyamokra bontott
felépítés megnehezíti a hibakeresést.

## Kapocs

- [[concepts/bigdata/storm-architektura]] — a Storm klaszter komponensei
- [[concepts/bigdata/storm-topologia]] — a topológia mint örökké futó
  spout/bolt-gráf
- [[concepts/bigdata/storm-megbizhato-feldolgozas]] — az at-least-once
  garancia mechanizmusa
- [[concepts/bigdata/mapreduce]] — a Hadoop kötegelt feldolgozási
  paradigmája, amellyel a Storm szembeállítható
- [[concepts/bigdata/spark-architektura]] — a Spark futtatási modellje
</content>
