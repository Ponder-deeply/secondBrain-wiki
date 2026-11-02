---
tags: [concept]
sources: ["2026_27_1 ESATL8-IP-18KVIBDAG - Big Data architektúrák és elemző módszerek Gy_ 2. Gyakorlat _ ELTE Moodle.md"]
references: ["spark.apache.org/docs/latest/api/python/reference/pyspark.html#rdd-apis"]
derivation: source
kind: comparison
element: earth
updated: 2026-10-07
---

# Spark kulcs-érték műveletek és gyakorlati feladatminták

A `(kulcs, érték)` párokból álló RDD-k kulcs szerinti aggregálása és összekapcsolása; a leggyakoribb vizsgapont a `reduceByKey` és a `groupByKey` különbsége.

## Tartalom

### reduceByKey és groupByKey

- `reduceByKey(f)` — kulcsonként összevonja az értékeket; a shuffle előtt a partíción belül **elő-összesítést** (combiner) végez, kevés adat kerül a hálózatra.
- `groupByKey()` — kulcsonként összegyűjti az összes értéket; nincs elő-összesítés, minden érték átmegy a hálózaton, ezért nagy adatnál drága és memóriaigényes. Aggregációra általában `reduceByKey`-t kell használni.
- `mapValues(f)` — csak az értéken dolgozik, a kulcs és a partícionálás megmarad.

**Átlag kulcsonként** (az átlag nem asszociatív, ezért `(összeg, darab)` párt redukálunk):

```python
r.mapValues(lambda x: (x, 1)) \
 .reduceByKey(lambda a, b: (a[0]+b[0], a[1]+b[1])) \
 .mapValues(lambda x: x[0]/x[1])
```

A `groupByKey().mapValues(lambda v: sum(v)/len(list(v)))` ugyanazt adja, de elő-összesítés nélkül.

### Join változatok

| Művelet | Eredmény |
|---|---|
| `join` | csak a mindkét oldalon szereplő kulcsok |
| `leftOuterJoin` | a bal oldal összes kulcsa (hiányzó jobb érték: `None`) |
| `rightOuterJoin` | a jobb oldal összes kulcsa |
| `fullOuterJoin` | mindkét oldal összes kulcsa |

Példa: bal `{x:10, y:30, y:20, x:10}`, jobb `{x:15, z:15}` — a `join` csak az `x` kulcsot adja, a `fullOuterJoin` `x`, `y`, `z`-t.

### Feladatminták (szenzoradat, JSON-sorok)

1. **Kategóriánként hány különböző nap** (Airport, temperature): `textFile → map(json.loads) → filter(location, sensor_type) → map(→ (kategória, dátum)) → distinct() → mapValues(→1) → reduceByKey(+)`. Kategóriák: `<10`, `10-20`, `20-30`, `>30`; a dátum a `timestamp` `T` előtti része. A `distinct` biztosítja, hogy egy nap kategóriánként egyszer számít.
2. **Legmelegebb nap:** `(dátum, érték)` párok, majd `reduce` a maximumra (`a if a[1]>b[1] else b`) vagy `sortBy` csökkenő érték szerint és `first`; kimenet a dátum és a hőmérséklet.
3. **Napi átlaghőmérséklet:** `map → (dátum, (érték, 1)) → reduceByKey(összeg, darab) → mapValues(összeg/darab)`; opcionálisan rendezés dátum szerint, a legmelegebb/leghidegebb napi átlag `min`/`max`-szal.

### Paraméterek

*Dokumentáció alapján, nem a gyakorlati forrásból.*

- `reduceByKey(func, numPartitions=None)`
  - `func`: (V, V) → V, asszociatív és kommutatív függvény. Az átlag ilyen függvényként nem számolható, ezért kell az (összeg, darab) pár.
  - `numPartitions`: az eredmény partíciószáma.
- `groupByKey()` — `(K, ResultIterable)` párokat ad; ez lusta bejáró, ezért kell a `list(...)`.
- `mapValues(f)` — megtartja a partícionálást, így egy utána következő kulcs szerinti művelet nem shuffle-öl újra. A kulcsot is érintő `map` ezt elveszíti.
- `join(other)` — `(K, (V, W))` párokat ad; outer joinnál a hiányzó oldal `None`. Ismétlődő kulcsnál minden párosítás megjelenik.
- `sortBy(keyfunc, ascending=True)` — csökkenő sorrendhez `ascending=False`.

## Kapocs

- [[concepts/bigdata/spark-transzformaciok-es-akciok]] — az alapműveletek (`map`, `reduce`, `aggregate`...)
- [[concepts/bigdata/rdd]] — a pár-RDD alapja
- [[concepts/bigdata/spark-particionalas]] — a shuffle és a partíciók
- [[concepts/bigdata/mapreduce]] — a reduce-fázis és combiner analógiája
