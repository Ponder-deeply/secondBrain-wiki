---
tags: [concept, bigdata/gepi-tanulas-osztalyozas-es-regresszio]
sources: [BDAEM-2022-EA9.pptx]
derivation: source
updated: 2026-09-12
---

# Ensemble módszerek

Az ensemble tanulás alapötlete, hogy több modellt építünk (eltérő tanuló
adaton és/vagy eltérő tanuló algoritmussal), majd ezek döntéseit
kombináljuk egyetlen végső döntéssé — jellemzően (súlyozott) szavazással.

## Tartalom

### Az ensemble koncepció

Az architektúra sematikusan: a rendelkezésre álló tanuló adatot ($Data_1,
Data_2, \dots, Data_m$) feldaraboljuk vagy újramintavételezzük, mindegyik
részhalmazon egy-egy tanuló algoritmus ($Learner_1, \dots, Learner_m$) épít
egy modellt ($Model_1, \dots, Model_m$), végül egy modell-kombináló
(*model combiner*) állítja elő a végső modellt, tipikusan súlyozott
szavazással (*weighted voting*).

### Miért működik?

Az alapötlet, hogy több független, egymástól eltérő, de a véletlen
találgatásnál jobb döntést kombinálva:

- a véletlenszerű hibák kioltják egymást,
- a helyes döntések felerősödnek.

Hétköznapi analógiák: egy üveg gombóc/cukorka darabszámának becslésekor a
csoport átlaga jellemzően pontosabb, mint egy-egy egyéni becslés; a "Legyen
Ön is milliomos" show-ban a közönségszavazás gyakran pontosabb, mint egyetlen
szakértő barát tanácsa.

### Homogén és heterogén ensemble

Két fő eset különböztethető meg aszerint, hogy a tagmodellek azonos vagy
különböző tanuló algoritmusból származnak:

- **Homogén eset**: egyetlen tanuló algoritmus fut le több, egymástól eltérő
  tanuló adathalmazon ($Learner_1 = Learner_2 = \dots = Learner_m$, de
  $Data_1 \neq Data_2 \neq \dots \neq Data_m$). A tanuló adat módosítására a
  leggyakoribb technikák:
  - **bagging** — a tanuló adat véletlen újramintavételezése
    (*resampling*), lásd [[concepts/bigdata/bagging]];
  - **boosting** — a tanuló adat elemeinek súlyozásának módosítása
    (*reweighting*), a korábban rosszul osztályozott elemekre helyezve
    nagyobb hangsúlyt, lásd [[concepts/bigdata/adaboost]];
  - **decorate** — mesterségesen generált tanuló adat hozzáadása.
- **Heterogén eset**: a modelleket egymástól eltérő tanuló algoritmusokkal
  építjük ugyanazon (vagy hasonló) adaton; a diverzitás forrása ekkor az
  algoritmusok különbözősége, nem az adaté.

### Modellkombinálás — (súlyozott) szavazás

A tagmodellek döntéseinek egyesítésére a legegyszerűbb módszer a **többségi
szavazás** (*majority voting*): minden tagmodell leadja a saját döntését, és
a végső döntés a legtöbb szavazatot kapó osztály lesz. Ez az elv áll a
bagging modellkombinálása mögött is (lásd
[[concepts/bigdata/bagging]]). Kifinomultabb változatokban a szavazatok
súlyozottak — ez a boosting-alapú módszerek (pl. AdaBoost) esetén a
tagmodellek megbízhatóságától (fontosságától) függ, lásd
[[concepts/bigdata/adaboost]].

## Kapocs

- [[concepts/bigdata/bagging]] — homogén ensemble újramintavételezéssel és
  többségi szavazással
- [[concepts/bigdata/adaboost]] — homogén ensemble iteratív
  újrasúlyozással (boosting)
- [[concepts/bigdata/gepi-tanulas-alapfogalmak]] — a felügyelt tanulás és
  az osztályozási feladat alapfogalmai, amelyekre az ensemble módszerek
  épülnek
</content>
