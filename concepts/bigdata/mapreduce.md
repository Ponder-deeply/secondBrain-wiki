---
tags: [concept]
sources: [EA2_hadoop.pdf]
derivation: source
updated: 2026-09-12
---

# MapReduce

Batch-feldolgozási paradigma nagy mennyiségű, klaszteren elosztva tárolt adat
párhuzamos feldolgozására: a feladatot egy **map**, egy köztes **shuffle**, és
egy **reduce** fázisra bontja.

## Tartalom

### A paradigma

- **Map**: egy master node szétbontja a problémát kisebb feladatokra, és
  kiosztja ezeket a worker node-oknak.
- **Reduce**: a master node összegyűjti a részproblémák eredményét, és
  összegzi a részeredményeket.

A map és a reduce folyamatok egyaránt képesek párhuzamosan futni a klaszter
több node-ján.

### Alap adattípusok

A MapReduce kulcs-érték párokkal és listákkal dolgozik:

| Fázis  | Input           | Output            |
|--------|-----------------|--------------------|
| map    | `<k1, v1>`      | `list(<k2, v2>)`   |
| reduce | `<k2, list(v2)>`| `list(<k3, v3>)`   |

### Egyszerű adatfolyam példa

Egy `[A, B, B, C, D]` bemeneti listán:

1. **input → map**: minden elem `<offset, érték>` párrá alakul, pl. `(0, A)`,
   `(1, B)`, `(2, B)`, `(3, C)`, `(4, D)`.
2. **map → shuffle**: a mapper `<kulcs, 1>` párokat generál minden elemre,
   pl. `(A, 1)`, `(B, 1)`, `(B, 1)`, `(C, 1)`, `(D, 1)`.
3. **shuffle → reduce**: a shuffle fázis kulcs szerint csoportosítja az
   értékeket: `(A, [1])`, `(B, [1, 1])`, `(C, [1])`, `(D, [1])`.
4. **reduce → output**: a reducer összegzi az egyes kulcsokhoz tartozó
   értékeket: `A,1`, `B,2`, `C,1`, `D,1`.

### Map fázis

A mapperek kis programok, amelyek a klaszteren elosztva, lokális adaton
futnak — minden mapper az input fájlnak csak egy kis részén dolgozik. Minden
mapper értelmezi, szűri vagy átalakítja a bemenetet, és `<kulcs, érték>`
párokat hoz létre.

### Shuffle fázis

A shuffle fázis mozgatja az adatot a klaszteren belül: minden mapper kimenete
előbb lokálisan csoportosításra kerül kulcs alapján, majd minden egyes
kulcshoz kiválasztásra kerül egy célnode. Az elosztást a **Partitioner
osztály** végzi, alapértelmezés szerint hash alapon, de ez felüldefiniálható.
A reducer bármelyik node-on futhat — a mapperek és a reducerek száma
egymástól függetlenül is beállítható.

### Reduce fázis

A reducerek kis programok, amelyek a hozzájuk rendelt kulcshoz tartozó
értékeket aggregálják. Minden reducer a saját kimenetét külön fájlba írja, és
az eredmény a HDFS-re kerül visszaírásra (alapértelmezésben egy fájl
reducerenként).

### Combiner (opcionális)

A combiner egy opcionális, a shuffle fázis *előtt* futó, map-oldali előzetes
redukálás: mielőtt az adat eljutna a reducer node-hoz, a map oldalon már
elvégzünk egy aggregációt, hogy csökkentsük a hálózaton átküldött adat
mennyiségét. Gyorsítja a futást, de nem kötelező.

### Partitioner

A partitioner felelős a kulcsok szétosztásáért a reducerek között. Alap
beállítása hash-alapú, de felüldefiniálható egyedi partícionálási logikával.
A teljes adatfolyam sorrendje: `map → combine → partition → shuffle and sort
(kulcs szerinti aggregálás) → reduce`.

### Data locality és a topológiafüggő futtatás

Vezérlési szabály: az adat a teljes klaszterben szét van szórva tárolva, ezért
**a programot kell mozgatni az adathoz, nem az adatot a programhoz**
(data locality elve). A futtatás topológiafüggő prioritási sorrendben
történik:

1. azon a node-on, ahol az adat (blokk) fizikailag van,
2. ha ez nem lehetséges, abban a rackben, ahol az adat van,
3. ha ez sem lehetséges, bármelyik rackben.

### Speculative execution

Mivel egyes node-ok lassabbak lehetnek, és ugyanaz az adat (a HDFS
replikáció miatt) több node-on is elérhető, a MapReduce ugyanazt a feladatot
egyszerre több node-on is elindíthatja. A leggyorsabban végző node
eredményét fogadja el, a többit elveti.

### InputFormat, InputSplit, RecordReader

Az **InputFormat** írja le a MapReduce job bemeneti formátumát. Alaptípusai:

- **FileInputFormat**: egy vagy több fájl elérési útját adja meg.
- **TextInputFormat**: alapbeállítás — egy vagy több fájlból sorokat készít
  (offset a fájl elejétől + az adott sor).
- **KeyValueTextInputFormat**: a TextInputFormathoz hasonló, de a sorokat
  tabulátor (`\t`) mentén kulcs-érték párra bontja.
- **SequenceFileInputFormat**: bináris fájlok olvasása, a kulcs-érték
  típusokat a felhasználónak kell megadnia.
- **SequenceFileAsTextInputFormat**: hasonló az előbbihez, de a kulcsból és
  az értékből `toString()`-gel Text típust képez.
- **NlineInputFormat**: olyan TextInputFormat, ahol minden map task N sort
  kap meg.

Az **InputSplit** az InputFormat logikai megfelelője: egy adott map taskhoz
tartozó bemenetet készíti elő, a fájl blokkméretének megfelelően darabolva.
A **RecordReader** az InputSplit kimenetéből állítja elő a tényleges
kulcs-érték párokat.

### Mapper/Reducer objektumok és az élettartam-API

Egy Mapper és egy Reducer objektum minden taskhoz egyszer példányosodik, és a
következő életciklus-metódusokkal rendelkezik: `configure` (API
inicializálása) → `map`/`reduce` (minden bemeneti kulcs-értékre, illetve
minden kulcsra egyszer hívódik meg) → `close` (API megszüntetése).

Minimális Java API vázlat (WordCount példa):

```java
public class WCMapper extends Mapper<LongWritable, Text, Text, IntWritable> {
    public void map(LongWritable key, Text value, Context context) {
        for (String s : value.toString().split(" "))
            context.write(new Text(s), new IntWritable(1));
    }
}

public class WCReducer extends Reducer<Text, IntWritable, Text, IntWritable> {
    public void reduce(Text key, Iterable<IntWritable> values, Context context) {
        int sum = 0;
        for (IntWritable val : values) sum += val.get();
        context.write(key, new IntWritable(sum));
    }
}
```

A **Driver** osztály állítja össze és indítja a jobot (Mapper/Reducer
osztályok beállítása, ki- és bemeneti útvonalak megadása,
`job.waitForCompletion(true)`).

**Map-only MapReduce**: ha nincs szükség reduce fázisra,
`job.setNumreduceTasks(0)` hívással a job kizárólag a map fázist futtatja le,
és annak eredményét írja ki közvetlenül.

### Writeable típusok

A Hadoop Java API a natív típusok helyett szerializálható `Writeable`
csomagolókat használ, pl. `boolean → BooleanWriteable`, `int → IntWriteable`,
`long → LongWriteable`, `float → FloatWriteable`, `double → DoubleWriteable`,
`String → Text`.

### Optimalizálási lehetőségek

1. LZO tömörítés használata (`mapred.compress.map.output = true`).
2. A map/reduce taskok számának és a blokkméreteknek a hangolása.
3. Combiner használata a hálózati forgalom csökkentésére.
4. A Writeable objektumok újrafelhasználása új példányok létrehozása
   helyett (kevesebb GC-terhelés).

### Word Count példa

A klasszikus MapReduce-bemutató példa: egy állatneveket tartalmazó fájlt a
MapReduce automatikusan sortörések mentén két részre darabol, és két node-on
tárolja. A feladat: megszámolni, hányszor fordul elő az egyes nagymacska
nevek — SQL-ben ez egy `SELECT COUNT(name) ... GROUP BY name` lekérdezésnek
felelne meg. A map fázis kiszűri a nem releváns neveket és
`<Text(name), Integer(1)>` párokat készít; a shuffle fázis a Partitioner
(hash-elosztás) alapján a megfelelő reducer node-okhoz mozgatja az azonos
kulcsú párokat; a reduce fázis összegzi az egyes nevekhez tartozó
előfordulásokat, és az eredményt a HDFS-re írja.

## Kapocs

- [[concepts/bigdata/hdfs]] — a réteg, amelyen a MapReduce bemenete tárolódik,
  és amelynek blokk-elhelyezése meghatározza a data locality-t
- [[concepts/bigdata/yarn]] — az erőforrás-kezelő és ütemező, amely a
  MapReduce jobok futtatási környezetét biztosítja (illetve elődje, a Hadoop
  1.x JobTracker/TaskTracker architektúra)
- [[concepts/bigdata/mapreduce-hibatures]] — a MapReduce v1 és a YARN-alapú
  MapReduce hibakezelési mechanizmusai
- [[concepts/bigdata/hadoop-korlatai]] — a MapReduce-alapú batch-feldolgozás
  korlátai
