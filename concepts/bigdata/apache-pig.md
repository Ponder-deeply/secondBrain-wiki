---
tags: [concept, bigdata/hadoop-okoszisztema]
sources: [EA2_hadoop.pdf]
derivation: source
updated: 2026-09-12
---

# Apache Pig

Magas szintű scriptnyelv (Pig Latin) és futtatókörnyezet, amely a MapReduce
programozásának nehézkességét hidalja át azzal, hogy a scriptet automatikusan
MapReduce jobok sorozatává fordítja.

## Tartalom

### Célja és története

Célja, hogy könnyebb felületet biztosítson a MapReduce technikához, mint a
natív Java API. 2006-ban kutatási projektként indult a Yahoo-nál, 2007-ben
nyílt forráskódúvá vált, 2008-ban jelent meg az első release.

### Tulajdonságai

- Java helyett **Pig Latin** nyelven kell a scripteket megfogalmazni; a Pig
  Engine alakítja át a scriptet MapReduce jobokká.
- A Pig Latin az SQL nyelvhez hasonlít: van benne `join`, `filter`, `sort` stb.
- Van optimalizáló lehetőség, amely a taskok végrehajtási sorrendjét
  optimalizálja.
- Kiegészíthető: saját függvények írhatók hozzá különböző nyelveken, amelyek
  aztán a scriptben felhasználhatók.

### Architektúra / komponensek

- **Parser**: szintaxis- és típusellenőrzés, a szkript átalakítása az
  optimalizálónak megfelelő (logikai terv) formára.
- **Optimizer**: a logikai tervet optimalizálja, hasonlóan a relációs
  adatbázisok lekérdezésoptimalizálóihoz.
- **Compiler**: a logikai tervből MapReduce jobokat készít.
- **Execution Engine**: a MapReduce jobokat a megfelelő sorrendben elindítja.

A futtatás rétegződése: Pig Latin script → (Grunt shell / Pig Server → Parser
→ Optimizer → Compiler → Execution Engine) → MapReduce → HDFS.

### Pig Latin adatmodell

- **Atom**: atomi típusok — `int`, `float`, `long`, `double`, `char array`,
  `byte array`, pl. `"elte"`, `1635`.
- **Tuple**: rendezett halmaz, pl. `("elte", 1635)`.
- **Bag**: tuple-k halmaza, pl. `{("elte",1635),("beac", 1898)}`.
- **Map**: kulcs-érték párok halmaza, pl. `[nev#elte, alapitva#1635]`.

### Futtatási lehetőségek

- **Non-interaktív / script mód**: előre megírt scriptfájl futtatása.
- **Grunt shell / interaktív mód**: parancssori, soronkénti futtatás.
- **Embedded**: JDBC-n keresztül érhető el, más alkalmazásba ágyazva.

### Példa (Hello World / szóösszeszámlálás)

```
lines = LOAD '/user/hadoop/HDFS_File.txt' AS (line:chararray);
words = FOREACH lines GENERATE FLATTEN(TOKENIZE(line)) as word;
grouped = GROUP words BY word;
wordcount = FOREACH grouped GENERATE group, COUNT(words);
DUMP wordcount;
```

Ez ugyanazt a szóösszeszámlálási feladatot valósítja meg tömören, mint a natív
[[concepts/bigdata/mapreduce]] Word Count példája, csak Pig Latin szinten.

### Limitációk

- A hibaüzenetek nem beszédesek.
- Lassan fejlődik: évente 1-2 release jelenik meg, 2017-ben volt az utolsó
  említett kiadás.
- Lassú futtatás, mivel a scriptek végül MapReduce jobokra fordulnak le, és
  öröklik azok rezsijét.

## Kapocs

- [[concepts/bigdata/mapreduce]] — a Pig scriptek végső fordítási célja; a Pig
  Compiler ebbe alakítja a logikai tervet
- [[concepts/bigdata/hdfs]] — a Pig LOAD/DUMP műveletei innen olvasnak és ide
  írnak
- [[concepts/bigdata/hadoop-korlatai]] — a MapReduce-ra épülő eszközök (így a
  Pig) közös korlátai, mint a lassú futtatás
- [[concepts/bigdata/big-data-okoszisztema]] — a Hadoop-ökoszisztémán belüli
  elhelyezkedése
