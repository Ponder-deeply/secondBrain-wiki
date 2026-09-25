---
tags: [concept, bigdata/spark-graphx]
sources: [EA4_spark_graphx.pdf]
derivation: source
updated: 2026-09-12
---

# Háromszögszámlálás (Triangle Count) GraphX-ben

A háromszögszámlálás minden csúcsra meghatározza, hány háromszögben vesz
részt a gráfban — tipikus alkalmazása társasági/közösségi csoportok
(klikkek) feltárása —, és a GraphX-ben szomszédsági halmazok élenkénti
összevetésével számítható ki.

## Tartalom

### Az algoritmus lépései

1. **Szomszédok halmazának kiszámítása**: minden csúcshoz eltároljuk a
   közvetlen szomszédai azonosítóinak halmazát (pl. a `2` csúcs
   szomszédhalmaza `{3, 5, 7}`).
2. **Metszetképzés élenként**: minden élen (mindkét végpontján) megnézzük,
   hány közös szomszéd van a két végpont szomszédsági halmazának
   metszetében — ez adja meg, hány háromszögben szerepel az adott él.
3. **Üzenetküldés mindkét irányba**: minden élen mindkét irányba elküldjük a
   metszet méretét jelző üzenetet, majd csúcsonként összegezzük a beérkező
   értékeket.
4. **Duplikáció korrekciója**: mivel minden háromszöget két él (és mindkét
   irányban) számol, a végeredményt csúcsonként el kell osztani 2-vel. Az
   eredmény megmondja, hogy egy adott csúcs hány háromszögben szerepel.

### Kapcsolat a Pregel-mintával

Bár a forrás ezt a lépéssorozatot nem explicit `vprog`/`sendMsg`/`aggrMsg`
hármasként adja meg (szemben a
[[concepts/bigdata/pagerank-graphx]] és
[[concepts/bigdata/osszefuggo-komponensek-pregel]] példáival), a
szomszédsági halmazok szétküldése és élenkénti összevetése ugyanazt az
üzenetküldés + aggregálás mintát követi, mint a
[[concepts/bigdata/pregel-modell]] általános kerete: a csúcsok üzenetekben
osztják meg lokális állapotukat (szomszédsági halmazukat) a szomszédaikkal,
majd az élek mentén aggregálják az eredményt.

## Kapocs

- [[concepts/bigdata/pregel-modell]] — az üzenetküldés/aggregálás elve, amit
  ez az algoritmus élenkénti metszetképzésre alkalmaz
- [[concepts/bigdata/osszefuggo-komponensek-pregel]] — másik, csúcs-központú
  gráfalgoritmus GraphX-ben
</content>
