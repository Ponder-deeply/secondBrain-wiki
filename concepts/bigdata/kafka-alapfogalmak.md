---
tags: [concept]
sources: ["2026_27_1 ESATL8-IP-18KVIBDAG - Big Data architektúrák és elemző módszerek Gy_ 5. Gyakorlat _ ELTE Moodle.md"]
references: ["kafka.apache.org/documentation/#basic_ops"]
derivation: source
kind: definition
element: earth
updated: 2026-10-07
---

# Apache Kafka alapfogalmai

Az Apache Kafka elosztott eseményfolyam-platform: a producerek eseményeket írnak topicokba, a consumerek olvassák őket. A gyakorlaton a Spark streaming bemeneti forrása.

## Tartalom

| Fogalom | Jelentés |
|---|---|
| Broker | Kafka szerver, amely tárolja és kiszolgálja az eseményeket. |
| Topic | Logikai eseményfolyam (pl. `logs`). |
| Partition | A topic párhuzamosítható, rendezett naplórészlete. |
| Producer | Eseményeket ír a topicba. |
| Consumer | Eseményeket olvas. |
| Offset | Rekordpozíció az adott partíción belül. |
| Consumer group | Fogyasztók csoportja, amely megoszthatja a partíciók olvasását. |
| Replication | Partícióadatok másolása rendelkezésre állás céljából. |

### Topic létrehozása

A topicot a `kafka-topics.sh` eszközzel hozzák létre a `--partitions` (itt 3) és `--replication-factor` (itt 1, egyetlen brokernél) paraméterekkel; a `--list` kilistázza, a `--describe --topic <név>` leírja a topicokat. Docker hálózaton belül a broker címe `kafka:9092` (`bootstrap.servers`).

### A labor topicjai

| Topic | Mezők | Feladatok |
|---|---|---|
| `logs` | timestamp, srcip, dstip, method, url, status | URL-statisztika, támadásdetektálás |
| `sensors` | sensor_id, timestamp, type, value | szenzorstatisztika, tűzriasztás |
| `tweets` | user, timestamp, text, hashtag | hashtag, hangulat |
| `coordinates` | phone_id, timestamp, lat, lon | rácscellák, antennaelemzés |

Az üzenetek értéke JSON; a generátorprojektben a topicnevek eltérhetnek (`server_logs`, `sensors_stream`, `phones`), ilyenkor a kódban a tényleges nevet kell használni.

### Offsetek és újraindítás

Az offset a rekord pozíciója a partíción belül. A Spark `startingOffsets` opciója szabja meg, honnan indul az olvasás ([[concepts/bigdata/spark-kafka-integracio]]); újraindításnál a checkpoint és az offsetek viselkedését érdemes külön megvizsgálni ([[concepts/bigdata/spark-foreachbatch-es-checkpoint]]).

### Paraméterek

*Dokumentáció alapján, nem a gyakorlati forrásból.*

| Paraméter | Jelentés |
|---|---|
| `--bootstrap-server` | Egy broker címe; a többit a klaszter adja meg. |
| `--partitions` | A párhuzamosság felső korlátja: egy consumer groupban partíciónként legfeljebb egy consumer olvas. Csak növelhető; növeléskor megváltozik a kulcs → partíció leképezés. |
| `--replication-factor` | Legfeljebb a brokerek száma. Az 1 azt jelenti, hogy nincs hibatűrés. |
| `group.id` | Az azonos groupba tartozó consumerek megosztják a partíciókat; a különböző groupok mind a teljes topicot olvassák. |
| `auto.offset.reset` | Ha nincs commitolt offset: `latest` (alapértelmezés) vagy `earliest`. |

## Kapocs

- [[concepts/bigdata/spark-kafka-integracio]] — hogyan olvassa a Spark a Kafka topicokat.
- [[concepts/bigdata/spark-structured-streaming]] — a feldolgozó motor.
- [[concepts/bigdata/storm-architektura]] — a Storm streaming bemenete (spout) hasonló forrásszerepű; az összevetés nem a forrásból származik, hanem a wiki kontextusából.
