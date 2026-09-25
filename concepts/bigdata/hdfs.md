---
tags: [concept, bigdata/hadoop-okoszisztema]
sources: [EA2_hadoop.pdf]
derivation: source
updated: 2026-09-12
---

# HDFS (Hadoop Distributed File System)

A Hadoop elosztott fájlrendszere: nagy méretű fájlok blokkokra bontott,
replikált tárolására tervezett fájlrendszer, amely a klaszter több gépén
(node-ján) helyezi el az adatot.

## Tartalom

### Terminológia

- **Klaszter**: összetartozó számítógépek (node-ok) halmaza.
- **Rack**: egy fizikai vagy virtuális csoportba tartozó gépek, amelyek
  jellemzően azonos áram- és hálózati elérésen keresztül érhetők el.
- **Node**: a klaszter egy számító egysége, tipikusan egy számítógép.

Egy Hadoop klaszter több rackből áll, mindegyik rackben több node-dal — ez a
felosztás a replikáció és a hibatűrés alapja (lásd lentebb).

### Tervezési célok

A HDFS meglévő (op. rendszerbeli) fájlrendszerekre épül, de:

- nagyobb mennyiségű hiba kezelésére tervezték (a replikák miatt),
- nagy méretű fájlok folytonos (streaming jellegű) olvasására hatékony —
  véletlen elérés nincs,
- a fájlokat **blokkokra** bontja, és ezeket a blokkokat tárolja szét a
  klaszteren.

### Blokkok

A HDFS blokkjai nem azonosak az operációs rendszer fájlrendszerének
blokkjaival — a HDFS több különböző operációs rendszeren tárolja a saját
blokkjait. Alap blokkméret: **128 MB** (régebben 64 MB volt). Egy fájl mérete
meghaladhatja bármely egyedi lemez kapacitását a klaszterben, mert a fájl
blokkjai több node-on tárolódnak. Ha egy fájl kisebb, mint a blokkméret, csak a
ténylegesen szükséges rész kerül tárolásra (egy 128MB-os blokkméret mellett egy
kisebb fájl utolsó blokkja is csak annyi helyet foglal, amennyi ténylegesen
kell, pl. 66MB).

### Replikáció

A blokkok több node-on is el vannak tárolva — ez a **replikáció**, ami
biztosítja, hogy hiba esetén ne legyen adatvesztés.

- Alapértelmezett replikaszám: **3**.
- Szabály: legalább egy replikának mindig egy másik rackben kell lennie
  (rack-awareness), hogy egy teljes rack kiesése se okozzon adatvesztést.

**Replika készítés folyamata:**

1. A blokk elküldésre kerül egy node-nak.
2. Az a node elküldi a blokkot egy másik rackben lévő node-nak.
3. Ez a node továbbküldi az adatot egy harmadik node-nak a saját rackjében.
4. Minden node visszaigazolja, hogy sikeresen letárolta az adatot.

A klaszter állapota (hiányzó blokkok száma, nem replikált blokkok száma) a
`hdfs dfsadmin --report` paranccsal vagy az Ambari felülettel ellenőrizhető.

### Hibatűrés

Ha egy DataNode kiesik, az általa tárolt blokkok — replikáció miatt — más
DataNode-okon továbbra is elérhetők. Ha a kiesett DataNode tartósan nem válik
újra elérhetővé, a NameNode új replikákat készít a hiányzó replikák pótlására.

**Erasure coding (Hadoop 3.x):** a hagyományos 3x replikáció helyett a Hadoop
3.x paritásalapú hibajavító kódolást (erasure coding) is támogat: az input
fájlt blokkokra bontja, majd a blokkokból paritásértéket számol (pl. XOR vagy
Reed-Solomon kód alapján). Ha egy blokk elveszik, a többi blokk és a paritás
alapján visszaállítható.

- **Előny**: kevesebb tárhely — a 200%-os overheadet jelentő 3x replikációhoz
  képest csak kb. 50%-os overhead.
- **Hátrány**: a kódolás/dekódolás számítási költsége miatt további CPU- és
  hálózati terhelés.

### NameNode és DataNode

A Hadoop 1.x architektúrában a HDFS két fő komponense:

- **NameNode**: a HDFS könyvtárstruktúráját kezeli, ellenőrzi a fájlok
  meglétét (replikaszám, hiányzó blokkok), és az összes ezzel kapcsolatos
  információt memóriában tartja. Egy klaszterben lehet belőle kettő (aktív +
  standby jellegű redundancia).
- **DataNode**: a tényleges fájlblokkokat tárolja a HDFS-en.

Ezek a szerepkörök a Hadoop 2.x/3.x YARN-alapú architektúrában is megmaradnak —
a NameNode/DataNode a tárolási réteg, míg a feladatütemezést a YARN veszi át
(lásd [[concepts/bigdata/yarn]]).

### Korlátok

A blokk-alapú, nagy fájlokra optimalizált tervezés következménye, hogy a HDFS
kis fájlokra (a blokkméretnél lényegesen kisebb fájlokra) nem hatékony: a
NameNode minden fájlhoz metaadatot tárol, ami sok kis fájl esetén aránytalanul
nagy memóriaterhelést jelent. Lásd bővebben:
[[concepts/bigdata/hadoop-korlatai]].

## Kapocs

- [[concepts/bigdata/yarn]] — az erőforrás-kezelő és ütemező réteg, amely a
  HDFS-en tárolt adatot dolgozza fel
- [[concepts/bigdata/mapreduce]] — a HDFS-en tárolt adaton futó
  batch-feldolgozási paradigma, amely a data locality elvét a HDFS
  blokk-elhelyezésére építi
- [[concepts/bigdata/hadoop-korlatai]] — a HDFS/Hadoop tervezéséből fakadó
  korlátok
- [[concepts/bigdata/big-data]] — a Big Data fogalmi háttere, amelynek a HDFS
  a tárolási megoldása
