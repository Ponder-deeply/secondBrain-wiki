---
tags: [concept]
sources: [EA1_bevezetes.pdf]
derivation: source
updated: 2026-09-12
---

# Big Data architektúra

Az a rendszerarchitektúra-osztály, amely folyamatos, nagy volumenű (jellemzően
napi > 1 TB) adatfolyamok elosztott tárolására és párhuzamos feldolgozására
épül, több gépből álló klaszteren.

## Tartalom

### Alapelvek

- Az adatok **elosztva tárolódnak** a klaszter gépein (pl. HDFS-en).
- A számítások **párhuzamosítva** futnak (pl. MapReduce-szal).
- A kapacitás **horizontálisan** növelhető: új gépek csatlakoztatásával a
  klaszterhez, nem egy meglévő gép erősítésével.

Egy tipikus adatközponti hálózati topológia (Common Data Center Topology)
réteges felépítésű: core (gerinc, réteg-3 router), aggregation (réteg-2/3
switch) és access (réteg-2 switch, közvetlenül a szerverekhez kapcsolódva)
rétegekből áll.

### Egy Big Data architektúra tulajdonságai

- párhuzamos adatfeldolgozás a teljesítmény érdekében,
- skálázhatóság,
- szabad választás a meglévő rendszerek/technológiák közül,
- átjárhatóság különböző rendszerek között — ugyanaz az architektúra tud
  működni IoT (Internet of Things) jellegű, illetve BI (Business
  Intelligence) jellegű felhasználásra is.

### Architektúra-komponensek

Egy Big Data architektúra jellemző funkcionális komponensei:

- **adatforrás** — ahonnan az adat érkezik,
- **adattárolás** — az adat tartós, elosztott tárolása,
- **batch feldolgozás** — nagy, statikus adathalmazok időszakos feldolgozása,
- **real-time adattárolás** — a folyamatosan érkező (streaming) adat átmeneti
  tárolása,
- **real-time feldolgozás** — a streaming adat azonnali feldolgozása,
- **analitikai adattárolás** — a feldolgozott, elemzésre kész adat tárolása,
- **elemzés és kimutatás** — riportok, dashboardok,
- **orchestration** — a fenti komponensek közötti munkafolyamatok
  összehangolása és ütemezése.

### Lambda architektúra

A batch és a real-time feldolgozást egyaránt támogató, széles körben használt
minta. Az érkező adatfolyamot két párhuzamos ágra osztja:

- **batch layer**: az összes adatot eltárolja, és batch feldolgozó
  függvényekkel batch nézeteket (batch views) számol,
- **speed layer**: csak a legújabb adatot dolgozza fel stream feldolgozó
  függvényekkel, valós idejű nézeteket (real-time views) állítva elő.

A **serving layer** a batch és a real-time nézeteket egyesíti (merging), és
ezen keresztül válaszol a lekérdezésekre (query). A batch réteg biztosítja a
pontosságot és a teljességet, a speed réteg az alacsony késleltetést.

### Kappa architektúra

A Lambda architektúra egyszerűsített változata, amely elhagyja a külön batch
réteget: minden adat egyetlen, streaming alapú útvonalon (pl. Apache Kafka
mint ingestion tool) halad át, naplózva (datalogging) és szükség esetén
újrajátszva (dataloading) a logokból. Egyetlen speed layer végzi a stream
feldolgozó függvényekkel a számítást, amely közvetlenül táplálja a serving
layert. Előnye az egyszerűbb, egységes kódbázis (nincs kétszer megírt
feldolgozási logika batch-re és stream-re is), hátránya, hogy nem minden
feladat oldható meg tisztán streaming módon.

### Disztribúciók

A Big Data ökoszisztéma komponensei (lásd
[[concepts/bigdata/big-data-okoszisztema]]) többféle disztribúcióban
érhetők el:

- **Apache**: az egyes komponensek külön-külön, opensource módon érhetők el;
  telepítésükre pl. az Ambari eszköz használható.
- **Cloudera (korábban Hortonworks is)**: komplett, előre összeállított
  telepítőrendszer, fizetős support és tréning szolgáltatásokkal.

## Kapocs

- [[concepts/bigdata/big-data]] — a Big Data fogalma és motivációja
- [[concepts/bigdata/big-data-5v]] — a Big Data jellemző dimenziói
- [[concepts/bigdata/big-data-okoszisztema]] — az architektúra komponenseit
  megvalósító konkrét technológiák
