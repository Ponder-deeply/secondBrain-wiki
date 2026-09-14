---
tags: [concept]
sources: [BDAEM-2022-EA9.pptx]
derivation: source
updated: 2026-09-12
---

# Boosting és AdaBoost

A boosting a bagginggel szemben nem a tanuló adatot mintavételezi újra,
hanem iteratívan **átsúlyozza**: minden körben nagyobb hangsúlyt kap az
előző körben rosszul osztályozott adat. Az AdaBoost (*Adaptive Boosting*) a
technika legismertebb konkrét algoritmusa.

## Tartalom

### Boosting — az alapelv

A boosting egy iteratív eljárás, amely körről körre módosítja a tanuló adat
elemeinek súlyát:

- kezdetben minden rekord egyenlő súlyt kap;
- minden kör (klasszifikátor) után a **hibásan osztályozott** rekordok
  súlya **nő**, a **helyesen osztályozottaké csökken**;
- így a következő kör tanulója kényszerítetten jobban odafigyel a nehezen
  osztályozható esetekre.

Ez homogén ensemble a bagginggel közös értelemben (lásd
[[concepts/bigdata/ensemble-modszerek]]): ugyanaz a tanuló algoritmus fut
le egymás után, de minden körben más súlyeloszláson.

### Az AdaBoost algoritmus

Az AdaBoost $T$ darab bázisklasszifikátort ($C_1, C_2, \dots, C_T$) épít
egymás után:

- minden $C_t$ klasszifikátorhoz kiszámítja annak **hibaarányát** (*error
  rate*) a soron következő súlyozott tanuló adaton;
- ebből származtatja a klasszifikátor **fontosságát** (*importance*/*alpha*
  súly) — minél kisebb egy klasszifikátor hibája, annál nagyobb súllyal
  esik latba a végső döntésben;
- ez alapján frissíti a tanuló rekordok súlyait a következő körre (a
  rosszul osztályozottakét növelve, a jólét csökkentve);
- a végső osztályozás a bázisklasszifikátorok **súlyozott szavazata**
  (ellentétben a bagging egyenlő súlyú többségi szavazásával, lásd
  [[concepts/bigdata/bagging]]), ahol a súlyokat éppen az egyes
  klasszifikátorok fontossága adja.

### Viselkedés — miért erős az AdaBoost?

Két empirikus/elméleti megfigyelés indokolja a módszer erejét:

- a **tanuló halmazon mért hiba** exponenciálisan csökken az iterációk
  ($T$) számával — elméletileg tetszőlegesen kicsivé tehető több iterációval;
- az **általánosítási hiba** (a tényleges eloszláson mért hiba) a tanuló
  adat méretének négyzetgyökével csökken — ez a tanuló adat növelésével
  tehető tetszőlegesen kicsivé.

Ebből adódik az AdaBoost egyik ismert gyengéje is: elegendően sok
iterációval a tanuló hiba a zajos/kiugró rekordokra is túltanulhat, ha a
tanuló adat mérete nem nő ezzel arányosan.

### GradientBoostingTree — rövid kitekintés

A GradientBoostingTree hasonló elven működik, mint az AdaBoost: iteratívan
épít újabb és újabb (jellemzően fa alapú) modelleket, amelyek az előző
körök hibáját (rezidumát) próbálják korrigálni.

## Kapocs

- [[concepts/bigdata/ensemble-modszerek]] — az ensemble koncepció és a
  homogén/heterogén megkülönböztetés
- [[concepts/bigdata/bagging]] — a másik fő homogén ensemble technika,
  amely újramintavételezéssel és egyenlő súlyú szavazással dolgozik
</content>
