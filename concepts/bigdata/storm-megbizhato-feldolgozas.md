---
tags: [concept, bigdata/storm-stream-feldolgozas]
sources: [EA5_storm.pdf]
derivation: source
updated: 2026-09-12
---

# Storm megbízható feldolgozás (at-least-once, ack/fail)

A Storm API-ja garantálja, hogy egy spout által emittált tuple-t a
topológia teljes egészében feldolgozza (**at-least-once szemantika**),
az egyes bolt-ok explicit **acknowledge**/**fail** visszajelzésein
keresztül.

## Tartalom

### Feldolgozási szemantikák

- **At-least-once (legalább egyszer)** — a topológiába bemenő minden
  tuple-t legalább egyszer feldolgoz a rendszer.
- **At-most-once (legfeljebb egyszer)** — minden tuple-t pontosan
  egyszer dolgoz fel, vagy hiba esetén eldob (nem próbálja újra).

### Garantált feldolgozás mechanizmusa

Egy tuple "fáját" (a belőle spawnolt összes további tuple-t) egy
feladatfa reprezentálja: a spout-tól kiindulva több bolt-on
elágazhat, majd összefuthat. A garantált feldolgozáshoz:

- A **spout oldalán** minden emittált tuple egyedi azonosítót (`msgID`)
  kap (`collector.emit(new Values(S), msgID)`); a spout implementálja
  az `ack(msgID)` (siker) és a `fail(msgID)` (hiba — pl. újraküldés)
  metódusokat.
- A **bolt oldalán** minden bolt `execute(Tuple tuple)`-jében vagy
  **acknowledge**-eli (`collector.ack(tuple)`), vagy **fail**-eli
  (`collector.fail(tuple)`) a kapott tuple-t. Az új tuple-ök emittálása
  az eredeti tuple-höz **anchor**-ölve történik (a `collector.emit`
  túlterhelt változatával), így a rendszer nyomon tudja követni a
  teljes leszármazási fát.
- A spout `ack` metódusa csak akkor fut le egy adott `msgID`-re, ha a
  tuple-fa **minden** csomópontja acknowledge-elte a hozzá tartozó
  tuple-t; egyetlen `fail` az egész fát elbuktatja, és a spout
  újraküldheti az eredeti tuple-t.

### Worker-állapotok

A Supervisor rendszeresen ellenőrzi a Worker-ek állapotát a
folyamatok kezeléséhez; egy Worker az alábbi állapotok egyikében
lehet: **timed out**, **not started**, **disallowed**, **valid**.

## Kapocs

- [[concepts/bigdata/storm-topologia]] — a spout/bolt/tuple modell,
  amelyre az ack/fail mechanizmus épül
- [[concepts/bigdata/storm-architektura]] — a Supervisor, amely a
  Worker-állapotokat figyeli
- [[concepts/bigdata/mapreduce-hibatures]] — a Hadoop/MapReduce
  hibatűrési mechanizmusa összehasonlításképp
</content>
