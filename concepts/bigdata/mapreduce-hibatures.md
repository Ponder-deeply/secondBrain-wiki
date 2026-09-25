---
tags: [concept, bigdata/hadoop-okoszisztema]
sources: [EA2_hadoop.pdf]
derivation: source
updated: 2026-09-12
---

# MapReduce hibatűrés

A MapReduce v1 (JobTracker/TaskTracker) és a YARN-alapú MapReduce
hibakezelési mechanizmusai — hogyan ismeri fel és javítja ki a rendszer a
task-, tracker- és a központi komponensek hibáit.

## Tartalom

### MapReduce v1 — Task hiba

A TaskTracker hibásnak jelöli a taskot, ha:

- kivétel keletkezik a map vagy a reduce folyamatban,
- a JVM leáll,
- a task nem küld státuszfrissítést — ekkor a TaskTracker maga lövi le a
  JVM-et.

Ilyenkor a JobTracker újraindítja a taskot egy másik TaskTrackeren, ha ez
lehetséges. Ha egy adott taskot 4 vagy több alkalommal sem sikerül
lefuttatni, az egész job hibásnak lesz jelölve.

### MapReduce v1 — TaskTracker hiba

A JobTracker heartbeat üzenetek alapján érzékeli, hogy egy adott TaskTracker
működik-e. Ha egy TaskTracker nem válaszol, a JobTracker a rajta futó és már
lefutott taskokat egy másik TaskTrackerre ütemezi át. A JobTracker figyeli,
hogy az egyes TaskTrackerek hány taskot nem tudtak elvégezni; ha a hibák
száma elér egy limitet, a TaskTracker feketelistára kerül, és a JobTracker
egy ideig (pl. egy napig) nem ad neki új feladatot — a kizárás egy idő után
elévül.

### MapReduce v1 — JobTracker hiba

A JobTracker a MapReduce v1 architektúra kritikus, egyetlen hibapontja
(single point of failure): ha a JobTracker meghibásodik, minden futó job
elveszik, és mindegyiket újra kell indítani.

### YARN hiba

A YARN-alapú (Hadoop 2.x/3.x) MapReduce esetén a taskszintű hibakezelés
megegyezik a MapReduce v1-es viselkedésével (lásd fent). A központi
komponensek hibáira azonban a YARN felbontott architektúrája miatt
finomabb megoldás létezik:

- **Application Master hiba**: a Resource Manager folyamatosan figyeli az
  Application Mastert, és hiba esetén egy új containerben új Application
  Mastert indít. Ha a kliens nem éri el a régi címet, az újat a Resource
  Managertől kérdezi le.
- **Resource Manager hiba**: a Resource Manager checkpointokat tárol egy
  perzisztens háttértáron (HDFS vagy ZooKeeper). Hiba esetén vagy egy
  adminisztrátor indít új Resource Managert, vagy egy előre konfigurált
  standby Resource Manager veszi át a szerepet.

A YARN architektúra tehát a JobTracker egyetlen hibapontját két, egymástól
függetlenül kezelhető komponensre (Application Master, Resource Manager)
bontja szét, ami jelentősen csökkenti egy központi hiba hatását a futó
jobokra.

## Kapocs

- [[concepts/bigdata/yarn]] — a Resource Manager / Application Master
  architektúra, amelynek hibakezelését ez a lap részletezi
- [[concepts/bigdata/mapreduce]] — a feldolgozási paradigma, amelynek
  task-szintű futása itt leírt hibakezelés alatt áll
