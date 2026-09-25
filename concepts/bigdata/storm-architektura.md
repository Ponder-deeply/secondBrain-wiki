---
tags: [concept, bigdata/storm-stream-feldolgozas]
sources: [EA5_storm.pdf]
derivation: source
updated: 2026-09-12
---

# Storm klaszter-architektúra

Az Apache Storm klaszterének komponensei — a **Nimbus** master node, a
**Zookeeper**-együttes és a **Supervisor**/**Worker** node-ok — és ezek
üzenetváltása a topológia indításakor és futtatásakor.

## Tartalom

### Komponensek

- **Nimbus (Master Node)** — feladatokat oszt ki, és figyeli a hibákat
  (task assignment, failure monitoring). A klaszter egyetlen belépési
  pontja a topológiák beküldésére.
- **Zookeeper** — a Nimbus és a Supervisor-ok klaszterállapotát tárolja;
  tipikusan több (jellemzően 3) Zookeeper-példány alkot együttest a
  rendelkezésre állás érdekében.
- **Supervisor** — a Zookeeperen keresztül kommunikál a Nimbusszal a
  topológiákról és a rendelkezésre álló erőforrásokról.
- **Worker** — a kiosztott munkára figyel, és végrehajtja az alkalmazást.

A hierarchia: Nimbus ↔ Zookeeper-együttes ↔ Supervisor-ok ↔ Worker-ek —
minden Supervisor több Workert futtat.

### Komponensek közötti interakció

Egy topológia beküldésének és futtatásának folyamata:

1. A **Client** beküldi (submit) a topológiát a **Nimbus**-nak.
2. A Nimbus meghirdeti (advertise) a topológiát a **Supervisor**-oknak,
   amelyek "matchmaking"-gel válaszolnak (erőforrás-egyeztetés).
3. A Supervisor-ok **Worker**-eket indítanak (spawn).
4. A Workerek **Executor**-okat hoznak létre, amelyek a tényleges
   feladatokat (tasks) dolgozzák fel.

Az egészséges állapotot rendszeres eseményekkel (heartbeat protokoll)
tartják fenn: a heartbeat 15, a supervisor-szinkronizáció 10, a
folyamat-szinkronizáció 3 másodpercenként fut.

### Nagy rendelkezésre állású telepítés

A klaszter kibővíthető egy **másodlagos (secondary) Nimbus**-szal, amely
akkor veszi át a szerepet, ha az elsődleges Nimbus átmenetileg
elérhetetlenné válik. Az egyes Spoutok (lásd
[[concepts/bigdata/storm-topologia]]) különböző protokollú és
formátumú adatforrásokból is termelhetnek tuple-öket; az adott réteg
Boltjai a szűrésért, aggregálásért és elemzésért felelnek.

## Kapocs

- [[concepts/bigdata/storm-topologia]] — a Nimbus/Supervisor/Worker által
  futtatott topológia belső modellje (spout, bolt, stream)
- [[concepts/bigdata/storm-megbizhato-feldolgozas]] — a klaszter által
  garantált feldolgozási szemantika
- [[concepts/bigdata/storm-vs-kotegelt-feldolgozas]] — összevetés a
  Hadoop/Spark kötegelt architektúrájával
- [[concepts/bigdata/yarn]] — a Hadoop erőforrás-kezelője, amelynek a
  Storm Nimbus/Supervisor párosa a funkcionális megfelelője
</content>
