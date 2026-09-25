---
tags: [concept, bigdata/hadoop-okoszisztema]
sources: [EA2_hadoop.pdf]
derivation: source
updated: 2026-09-12
---

# YARN (Yet Another Resource Negotiator)

A Hadoop 2.x-től bevezetett erőforrás-kezelő és feladatütemező réteg, amely
leválasztja a klaszter-erőforrások kezelését a konkrét feldolgozási
modelltől (MapReduce), és így tetszőleges elosztott alkalmazás futtatását
támogatja.

## Tartalom

### Előzmény: Hadoop 1.x architektúra

A Hadoop 1.x-ben nem volt önálló erőforrás-kezelő réteg — a MapReduce motor
egyben a klaszter-menedzsment feladatát is ellátta:

- **JobTracker**: a MapReduce jobok kezelése, kommunikáció a klienssel,
  feladatok kiosztása a TaskTrackereknek.
- **TaskTracker**: az adott node-on futó taskok (map, shuffle, reduce)
  elvégzése.

**Probléma:** a JobTracker szűk keresztmetszetté vált — több kliens
kiszolgálásakor túlterhelődött —, és kizárólag MapReduce jobokat volt képes
kezelni, semmi mást.

### Hadoop 2.x architektúra — YARN komponensek

A YARN szétválasztja az erőforrás-kezelést és a job-felügyeletet:

- **Resource Manager (RM)**: kapcsolatot tart a kliensekkel, felügyeli a
  jobokat, ismeri a klaszter teljes erőforráskészletét, és containereket hoz
  létre.
- **Node Manager**: az adott node erőforrásainak ismerete és kezelése.
- **Application Master**: tetszőleges alkalmazás (nem csak MapReduce)
  felügyelete és kezelése — ezáltal a YARN-on Spark, Hive stb. is futtatható.

Ez az architektúra oldja fel a Hadoop 1.x JobTracker szűk keresztmetszetét: a
job-specifikus felügyeletet (Application Master) leválasztja a
klaszter-szintű erőforrás-kezeléstől (Resource Manager).

### Hadoop 3.x újdonságok

A Hadoop 3.x továbbfejleszti a YARN-alapú architektúrát: GPU-k támogatása,
több standby NameNode támogatása, több névtérhez (namespace) tartozó több
NameNode támogatása, a tárolási overhead csökkentése (kb. 200%-ról 50%-ra,
lásd az erasure coding leírását a [[concepts/bigdata/hdfs]] lapon), valamint
node-on belüli lemez-kiegyenlítés (intra-node disk balancing).

### Hibakezelés

**Application Master hiba:** a Resource Manager folyamatosan figyeli az
Application Mastert. Hiba esetén egy új containerben új Application Mastert
indít. Ha a kliens nem éri el a régi Application Mastert, az új címét a
Resource Managertől kérdezi le.

**Resource Manager hiba:** a Resource Manager checkpointokat tárol egy
perzisztens háttértáron (HDFS vagy ZooKeeper). Hiba esetén vagy egy
adminisztrátor indít új Resource Managert, vagy egy előre beállított standby
Resource Manager veszi át a szerepet.

A taskszintű hibák kezelése megegyezik a MapReduce v1-es viselkedésével —
lásd [[concepts/bigdata/mapreduce-hibatures]].

## Kapocs

- [[concepts/bigdata/hdfs]] — a tárolási réteg, amelyen a YARN által
  felügyelt alkalmazások dolgoznak
- [[concepts/bigdata/mapreduce]] — a YARN-on (illetve elődjén, a Hadoop
  1.x JobTracker/TaskTracker architektúrán) futó batch-feldolgozási
  paradigma
- [[concepts/bigdata/yarn-utemezok]] — a YARN Resource Managerbe épített
  ütemezők (FIFO, Capacity, Fair)
- [[concepts/bigdata/mapreduce-hibatures]] — a MapReduce v1 és a YARN
  hibakezelési mechanizmusainak részletes összevetése
- [[concepts/bigdata/hadoop-korlatai]] — a Hadoop-architektúra (HDFS + YARN +
  MapReduce) korlátai
