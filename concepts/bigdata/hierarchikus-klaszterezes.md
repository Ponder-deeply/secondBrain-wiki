---
tags: [concept, bigdata/gepi-tanulas-klaszterezes-es-dimenziocsokkentes]
sources: [BDAEM-2022-EA9.pptx]
references: ["Slides based on Eamonn Keogh's clustering lecture"]
derivation: source
updated: 2026-09-12
---

# Hierarchikus klaszterezés

A hierarchikus klaszterezés az objektumok egymásba ágyazott (beágyazott)
klaszterhierarchiáját építi fel — az eredmény egy **dendrogram** —, szemben
a [[concepts/bigdata/k-means]]-hez hasonló partícionáló módszerekkel,
amelyek egyetlen, rögzített számú klaszterre bontják az adatot.

## Tartalom

### Két klaszterezési család

A klaszterező algoritmusoknak két fő családja van:

- **Partícionáló algoritmusok**: különböző partíciókat állítanak elő, majd
  valamilyen kritérium alapján értékelik őket (pl.
  [[concepts/bigdata/k-means]]).
- **Hierarchikus algoritmusok**: az objektumhalmaz hierarchikus felbontását
  hozzák létre valamilyen kritérium mentén.

### Dendrogram

A dendrogram a hasonlósági mérések összegzésének eszköze: egy fastruktúra,
amelyben két objektum hasonlóságát az a (legalacsonyabb) belső csomópont
magassága fejezi ki, amelyet a két objektum közösen örököl — minél
alacsonyabban egyesül két ág, annál hasonlóbb a két objektum.

A dendrogramnak további gyakorlati haszna is van:

- segítségével megbecsülhető a "helyes" klaszterszám (ahol a fát elvágva
  értelmes csoportok adódnak);
- kiugró értékek (outlierek) detektálására is használható: egy elszigetelt,
  a többitől nagyon eltérő ág gyakran különálló, más objektumoktól
  jellegzetesen eltérő adatpontra utal.

Fontos óvatosságra intő példa: a hierarchikus klaszterezés néha jelentés
nélküli vagy véletlenszerű mintázatokat is mutathat (pl. országok
csoportosításánál egy triviálisan értelmezhető csoport — volt brit
gyarmatok — mellett megjelenhet egy teljesen véletlenszerű egyezés is), ezért
az eredmény értelmezése erősen szubjektív marad.

### Csak egy dendrogram létezik minden adathalmazra?

Adott $n$ objektumhoz tartozó lehetséges dendrogramok száma
$$\frac{(2n-3)!}{2^{(n-2)}(n-2)!}$$
— ez már $n=5$-re is 105, nagyobb $n$-re csillagászati (pl. $n=10$-re több
mint 34 millió). Mivel az összes lehetséges fát nem lehet kimerítően
letesztelni, a gyakorlatban heurisztikus kereséssel építjük fel a
hierarchiát, két fő irányban:

- **Alulról felfelé (agglomeratív)**: kezdetben minden objektum saját
  klaszterben van; minden lépésben megkeressük és összevonjuk a "legjobb"
  (legközelebbi) klaszterpárt, amíg egyetlen klaszter marad.
- **Felülről lefelé (divizív)**: kezdetben minden objektum egyetlen közös
  klaszterben van; minden lépésben megvizsgáljuk a klaszter lehetséges
  kettéosztásait, kiválasztjuk a legjobbat, és a két félen rekurzívan
  folytatjuk.

Az agglomeratív eljárás a gyakorlatban jóval elterjedtebb. A kiindulási
alap mindkét esetben egy **távolságmátrix**, amely minden objektumpár
közti [[concepts/bigdata/tavolsag-hasonlosag-meresek]] szerinti távolságot
tartalmazza.

### Linkage típusok — klaszterek közti távolság

Míg két objektum távolsága közvetlenül számítható, két *klaszter* (vagy egy
objektum és egy klaszter) közti távolság definíciója nem egyértelmű. Három
alapvető linkage-módszer:

- **Single linkage (legközelebbi szomszéd)**: két klaszter távolsága a két
  klaszterben lévő legközelebbi objektumpár távolsága.
- **Complete linkage (legtávolabbi szomszéd)**: két klaszter távolsága a
  két klaszterben lévő legtávolabbi objektumpár távolsága.
- **Group average linkage (csoportátlag)**: két klaszter távolsága a két
  klaszter összes objektumpárja közti távolságok átlaga.

(A forrás e három módszert nevezi meg explicit módon; a Ward-módszert és
egyéb linkage-variánsokat a diasor nem tárgyalja.) A single linkage a
láncszerű, megnyúlt klasztereket részesíti előnyben, míg a complete linkage
kompaktabb, gömbszerűbb klasztereket eredményez — ezt a különbséget a
forrás egy single vs. average linkage összehasonlító ábrával szemlélteti.

### Összegzés: erősségek és gyengeségek

**Erősségek:**

- nem kell előre megadni a klaszterek számát;
- a hierarchikus felépítés sok területen jól illeszkedik az emberi
  intuícióhoz.

**Gyengeségek:**

- rosszul skálázódik: az időbeli komplexitás legalább $O(n^2)$, ahol $n$ az
  objektumok száma;
- mint minden heurisztikus keresési algoritmus, hajlamos lokális optimumba
  ragadni;
- az eredmény értelmezése (erősen) szubjektív.

## Kapocs

- [[concepts/bigdata/tavolsag-hasonlosag-meresek]] — a klaszterek közti
  linkage-távolság alapját adó objektum-távolságmértékek
- [[concepts/bigdata/k-means]] — a hierarchikus módszerek partícionáló
  alternatívája, rögzített klaszterszámmal
- [[concepts/bigdata/ensemble-modszerek]] — a diasor másik fő témája
  (ugyanabból a forrásból), a klaszterezéstől független felügyelt tanulási
  technika
</content>
