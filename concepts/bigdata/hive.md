---
tags: [concept, bigdata/hadoop-okoszisztema]
sources: [EA2_hadoop.pdf]
derivation: source
updated: 2026-09-12
---

# Hive

Apache Hadoopra épülő adattárház-réteg, amely SQL-szerű nyelvet (HiveQL)
biztosít nagy adathalmazok ad-hoc lekérdezésére és összegzésére, a lekérdezéseket
a háttérben MapReduce jobokra fordítva.

> Megjegyzés a forrásról: az `EA2_hadoop.pdf` 75. diájától kezdve a Hive-ról
> szóló diák láblécében "Korszerű adatbázisok" felirat szerepel (a Big Data
> kurzus többi diáján nincs ilyen felirat), és a tartalom is jóval mélyebb
> HiveQL/DDL részletekbe megy (bucketing, external table-ök, custom
> map/reduce transzformációk), mint amit egyetlen összefoglaló dia indokolna.
> Ez arra utal, hogy ezek a diák egy másik (adatbázis-) kurzus anyagából lettek
> újrafelhasználva, nem a Big Data kurzushoz készültek eredetileg. A Hive maga
> ettől még releváns a Big Data / Hadoop-ökoszisztéma szempontjából, ezért a
> tartalom itt kerül rögzítésre, de a forrás heterogenitása dokumentálva van.

## Tartalom

### Célja

- A Facebookhoz kötődik eredetileg.
- Apache Hadoopra épülő adattárház (data warehouse).
- Egyszerű adatösszegzésre, ad-hoc lekérdezésre és nagy adatok kezelésére lett
  tervezve.
- Támogatja az SQL nyelvet (HiveQL).
- **Ami nem Hive**: OLTP (online tranzakciófeldolgozás) — pl. banki
  tranzakciók, rendelések kezelése; ezekre nem alkalmas.

### Hive Metastore

Központi metatároló a Hive táblákhoz: itt vannak nyilvántartva a séma- és
elhelyezkedés-információk. Külső eszközök (pl. Spark, Presto, Hudi) is hozzá
tudnak férni, hogy megállapítsák, a HDFS-en (vagy más tárolón, pl. Amazon S3,
GCS, Kafka) hol találhatók a hozzá tartozó fájlok.

### Architektúra

Rétegek alulról fölfelé:

1. **Distributed Storage**: [[concepts/bigdata/hdfs]].
2. **Processing and Resource management**: MapReduce v1, illetve MapReduce v2
   / Tez a [[concepts/bigdata/yarn]] felett.
3. **Hive Services**: Hive Driver, Hive Server, Metastore (alapesetben Apache
   Derby DB-vel), CLI, Hive Web Interface.
4. **Hive Client**: Thrift/JDBC/ODBC alkalmazások, amelyek a megfelelő
   drivereken (Hive Thrift Client, Hive JDBC Driver, Hive ODBC Driver)
   keresztül a Hive Serverhez csatlakoznak.

**Adatfolyam egy lekérdezés végrehajtásakor**: a UI elküldi a lekérdezést a
Drivernek (`executeQuery`) → a Driver tervet kér a Compilertől (`getPlan`) →
a Compiler metaadatot kér a Metastore-tól (`getMetadata`/`sendMetadata`) →
a Compiler visszaküldi a tervet a Drivernek (`sendPlan`) → a Driver a tervet
végrehajtásra átadja az Execution Engine-nek (`executePlan`) → az Execution
Engine metaadat-műveleteket végezhet a Metastore-on, majd a tényleges
futtatást a Hadoop rétegre (MapReduce + HDFS) delegálja → az eredmény
visszajut az Execution Engine-en és a Driveren át a UI-hoz
(`sendResults`/`fetchResults`).

### Adatmodell (Hive felépítése)

- **Adatbázis** → **Táblák** → **Partíciók** → **Bucketek (klaszterek)**.
- A táblák rendelkezhetnek egy vagy több particionáló kulccsal, amely
  meghatározza, hogyan tároljuk az adatot; a particionált oszlop virtuális,
  nem része a tényleges adatnak.
- Egy partíciót tovább oszthatunk buckets-ekbe egy hash függvény segítségével.
- A particionálás és a bucket-elés nem kötelező, de gyorsítja a
  lekérdezéseket.
- Fizikailag: a particionált tábla adatai partíció-mappákban vannak tárolva
  (pl. `.../zipcodes/state=AL`, `.../state=AZ`, ...), a bucketek pedig ezen
  belül számozott azonosítófájlok.

### Típusok

- **Egyszerű típusok**: `tinyint`, `smallint`, `int`, `bigint`, `boolean`,
  `float`, `double`, `decimal`, `string`, `varchar` (max hosszal), `char`
  (fix hosszal), `date`, `timestamp`, `binary`. Implicit konverzió létezik,
  explicit konverzióhoz a `CAST` parancs használható.
- **Komplex típusok**:
  - `Struct` — struktúra tárolására, mezők pont (`.`) jelöléssel érhetők el:
    `c STRUCT {a INT; b INT}` → `c.a`.
  - `Map` (kulcs-érték) — pl. `M['group']`.
  - `Tömb` (indexelhető lista, azonos típusú elemekkel) — pl. `A = ['a','b','c']`,
    `A[1]` eredménye `'b'`.

### Hive vs. RDBMS

| Hive | RDBMS |
|---|---|
| Petabyte-os adatméret | Terabyte-os adatméret |
| "Egyszer írjuk, többször olvassuk" elv | Sokszori írás és olvasás elv |
| Támogatja az SQL nyelvet, de nem adatbázis — adattárház | Relációs adatmodell alapú |
| Könnyen skálázódik | Nehezen skálázódik |

### HiveQL — alapvető képességek

- Sorok szűrése `WHERE`, oszlopok kiválasztása `SELECT` kifejezéssel.
- Táblák összekapcsolása `JOIN`-nal, csoportosítás `GROUP BY`-jal.
- Az eredmény eltárolható új táblában, letölthető lokális mappába, vagy
  visszaírható HDFS háttértárra.
- Táblák és partíciók kezelése (`CREATE`, `DROP`, `ALTER`).
- Saját scriptek írhatók külső nyelven map/reduce jobokhoz (lásd alább).

Alapparancsok: `SHOW TABLES;`, `SHOW TABLES 'page.*';`, `SHOW PARTITIONS
page_view;`, `DESCRIBE page_view;`, `DESCRIBE EXTENDED page_view;`,
`DESCRIBE EXTENDED page_view PARTITION (ds='2008-08-08');`.

### Adatbetöltés

- **HDFS-ről**: pl. `hadoop dfs -put /tmp/pv_2008-06-08.txt
  /user/data/staging/page_view`, majd `INSERT OVERWRITE TABLE ... PARTITION(...)
  SELECT ... WHERE ...` egy staging táblából a célpartícióba.
- **Fájlrendszerről**: `LOAD DATA LOCAL INPATH ... INTO TABLE ... PARTITION(...)`
  (a `LOCAL` kulcsszó nélkül a HDFS-en lévő inputfájlt a Hive **törli**
  betöltés után).

### Tábla létrehozása

```sql
CREATE TABLE page_view(viewTime INT, userid BIGINT
        page_url STRING, referrer_url STRING,
        friends ARRAY<BIGINT>, properties MAP<STRING, STRING>
        ip STRING COMMENT 'IP Address of the User')
  COMMENT 'This is the page view table'
  PARTITIONED BY(date STRING, country STRING)
  CLUSTERED BY(userid) SORTED BY(viewTime) INTO 32 BUCKETS
  ROW FORMAT DELIMITED
    FIELDS TERMINATED BY ','
    COLLECTION ITEMS TERMINATED BY '$'
    MAP KEYS TERMINATED BY ';'
  STORED AS SEQUENCEFILE;
```

Itt a tábla `date` és `country` szerint particionált, 32 bucket-re van osztva
`userid` alapján (hash), és `viewTime` szerint rendezve tárolódik bucketenként.

**Külső (`EXTERNAL`) tábla**: a `CREATE EXTERNAL TABLE ... LOCATION '...'`
formával létrehozott táblát a Hive nem kezeli a szokásos módon — ha törlünk
egy ilyen táblát, a mögötte lévő adat megmarad a fájlrendszeren.

### Lekérdezések — példák

- Egyszerű szűrés: `SELECT user.* FROM user WHERE user.active = 1;`, illetve
  ennek eredménye insertálható is későbbi feldolgozáshoz:
  `INSERT OVERWRITE TABLE user_active SELECT user.* FROM user WHERE
  user.active = 1;`.
- Particionált lekérdezés: a `WHERE` feltételben a particionáló oszlopokra
  (pl. `date`, `country`) szűrve a Hive csak a releváns partíció-mappákat
  olvassa be.
- Komplex típusok elérése: tömbindexelés (`pv.friends[2]`), tömbméret
  (`size(pv.friends)`), map-elérés (`pv.properties['page type']`).
- **Custom Map/Reduce**: a `MAP ... USING 'map_script' AS ...` és a
  `REDUCE ... USING 'reduce_script' AS ...`, illetve a rövidebb
  `SELECT TRANSFORM(...) USING '...' AS (...)` szintaxis lehetővé teszi saját,
  külső nyelven (pl. Python) írt map/reduce scriptek beillesztését a HiveQL
  lekérdezésbe.

## Kapocs

- [[concepts/bigdata/hdfs]] — a Hive táblák adatai fizikailag itt tárolódnak,
  partíció- és bucket-mappák formájában
- [[concepts/bigdata/mapreduce]] — a HiveQL lekérdezések a háttérben ilyen
  jobokra fordulnak (illetve YARN felett Tez-re)
- [[concepts/bigdata/yarn]] — a Hive által futtatott jobok erőforrás-kezelője
- [[concepts/bigdata/apache-pig]] — a Hadoop-ökoszisztémán belüli másik, a
  MapReduce-ot magas szintű nyelvvel elfedő eszköz, hasonló motivációval, de
  eljárási (Pig Latin), nem deklaratív SQL-szerű nyelvvel
- [[concepts/bigdata/big-data-okoszisztema]] — a Hadoop-ökoszisztémán belüli
  elhelyezkedése
