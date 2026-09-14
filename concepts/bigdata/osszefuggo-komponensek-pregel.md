---
tags: [concept]
sources: [EA4_spark_graphx.pdf]
derivation: source
updated: 2026-09-12
---

# Összefüggő komponensek keresése Pregellel

Az összefüggő komponensek (connected components) keresése a GraphX-ben a
[[concepts/bigdata/pregel-modell]] azon behelyettesítése, ahol minden csúcs a
saját komponensén belüli legkisebb azonosítót terjeszti szét, amíg minden
csúcs a komponense minimális id-jét fel nem veszi.

## Tartalom

### Pregel-paraméterezés

- `vprog: math.min(msg, id)` — egy csúcs a saját aktuális állapotát (kezdetben
  a saját `id`-ja) a beérkezett üzenet és a jelenlegi érték minimumára
  cseréli.
- `sendMsg: if n1.id < n2.id: n1 send n1.id` — egy csúcs csak akkor küldi el
  a saját azonosítóját egy szomszédjának, ha annál kisebb az azonosítója;
  így az információ csak "lefelé", a kisebb id irányába terjed.
- `aggrMsg: math.min(a, b)` — több beérkező üzenetet a minimumukkal aggregál.

### Végrehajtás

A forrás egy kis példagráfon mutatja be, hogy több superstepen keresztül
(a csúcsok kezdeti azonosítói 2, 3, 4, 5, 7) a komponensen belüli legkisebb
azonosító fokozatosan mindenhová eljut: az első körben a szomszédos csúcsok
között terjed a legkisebb szomszédos érték, majd a következő körökben ez
tovább minimalizálódik, amíg a komponens minden csúcsa ugyanazt a (globálisan
legkisebb) azonosítót veszi fel — ez az azonosító jelöli ki magát a
komponenst.

Ez a mechanizmus a Pregel superstep-modell klasszikus alkalmazása: az
algoritmus akkor áll meg, amikor egyetlen superstepben sem küld egyetlen
csúcs sem új (kisebb) üzenetet.

## Kapocs

- [[concepts/bigdata/pregel-modell]] — az általános superstep/üzenetküldés
  keretrendszer, amelynek ez az algoritmus egy konkrét behelyettesítése
- [[concepts/bigdata/pagerank-graphx]] — másik tipikus Pregel-instanciáció
  ugyanazon a modellen
</content>
