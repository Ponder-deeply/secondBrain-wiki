---
tags: [concept]
sources: [EA2_hadoop.pdf]
derivation: source
updated: 2026-09-12
---

# Hadoop korlátai

A HDFS + YARN + MapReduce alapú Hadoop-architektúra tervezéséből fakadó
strukturális korlátok, amelyek később új feldolgozási motorok (pl. Spark)
kifejlesztését motiválták.

## Tartalom

### 1. Kis fájlok problémája

A HDFS-t nagy fájlok tárolására tervezték, ezért sok, a blokkméretnél
lényegesen kisebb fájl kezelésére nem hatékony: a NameNode minden egyes
fájlhoz metaadatot tárol, és emiatt sok kis fájl esetén a NameNode több
adatot tárolhat, mint amennyi maga a tényleges fájltartalom.

### 2. Lassú feldolgozás

A MapReduce taskok elindítása költséges — az inicializálás sok ideig tart.
Emellett a részeredmények taskok közötti mozgatása lemezen és hálózaton
keresztül történik, ami tovább növeli a feldolgozási időt.

### 3. Csak batch feldolgozás

A Hadoop nem hatékony stream jellegű (folyamatosan érkező) adatok
feldolgozására — kizárólag a statikusan, HDFS-en már eltárolt adatokon tud
dolgozni.

### 4. Nem hatékony iteratív feldolgozásra

A Hadoopban iteratív algoritmusokat csak jobok láncolásával lehet
megvalósítani: egy job felel meg egy iterációnak. Mivel a jobok közötti
adatmozgatás (jellemzően a HDFS-en keresztül, lemezre írva/olvasva) drága,
az iteratív feldolgozás — pl. gépi tanulási algoritmusok — költséges Hadoop
felett.

### 5. Nehezen használható

Nincs interaktív futtatási mód, és a MapReduce kód nehezen debug-olható.

### 6. Biztonsági hiányosságok

Az adat nincs kódolva a közösen használt tárterületen, és a HDFS-en nincs
megfelelő, finomszemcsés felhasználó-kezelés.

### 7. Nincs cache

A Hadoop nem biztosít beépített lehetőséget az ismételten használt adatok
memóriában tartására — minden feldolgozási lépés a HDFS-ről olvas és oda ír
vissza.

### Következmény

Ezek a korlátok — különösen az iteratív feldolgozás drágasága és a cache
hiánya — motiválták az olyan újabb, memóriaközpontú feldolgozási motorok
kifejlesztését, mint a Spark, amelynek alapvető adatszerkezete
([[concepts/bigdata/rdd]]) éppen a Hadoop e két hiányosságára ad választ.

## Kapocs

- [[concepts/bigdata/hdfs]] — a tárolási réteg, amelynek tervezése a kis
  fájlok problémáját okozza
- [[concepts/bigdata/mapreduce]] — a batch-feldolgozási paradigma, amelynek
  korlátai (nincs stream, nincs cache, drága iteráció) itt vannak leírva
- [[concepts/bigdata/rdd]] — a Spark adatszerkezete, amely a Hadoop cache- és
  iteráció-hiányát oldja meg
