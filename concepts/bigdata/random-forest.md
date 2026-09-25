---
tags: [concept, bigdata/gepi-tanulas-osztalyozas-es-regresszio]
sources: [gyak4.pdf]
derivation: inferred
updated: 2026-09-12
---

# Random Forest

A Random Forest egy homogén ensemble módszer: sok, egymástól független
döntési fát épít bootstrap-mintavételezéssel (bagging) és véletlenszerű
jellemző-részhalmazokkal, majd a fák döntéseit többségi szavazással
kombinálja.

## Tartalom

### A módszer

A Random Forest a [[concepts/bigdata/bagging]] alapötletét egészíti ki egy
további véletlenítési lépéssel:

1. a [[concepts/bigdata/bagging]]-hez hasonlóan $m$ darab bootstrap mintát
   készít (visszatevéses újramintavételezéssel) a tanítóadatból;
2. mindegyik bootstrap mintán egy-egy [[concepts/bigdata/dontesi-fa]]
   modellt épít, de minden egyes elágazásnál (split) a lehetséges
   jellemzőknek csak egy **véletlenszerűen kiválasztott részhalmazát**
   veszi figyelembe (nem az összes jellemzőt);
3. a végső döntés a fák **többségi szavazata** (osztályozás esetén),
   illetve átlaga (regresszió esetén).

### Miért jobb, mint egyetlen döntési fa vagy sima bagging?

A jellemzők véletlenszerű részhalmazolása csökkenti a fák közötti
korrelációt: bagging esetén, ha van egy különösen erős jellemző, szinte
minden bootstrap fa ugyanazt a jellemzőt választja a gyökér-elágazáshoz,
ami korrelált, hasonló hibát elkövető fákat eredményez. A jellemzők
véletlenszerű megszorítása miatt a Random Forest fái egymástól
diverzebbek, ami az [[concepts/bigdata/ensemble-modszerek]] lapon
tárgyalt elv szerint jobb, kisebb varianciájú végső modellhez vezet.

## Kapocs

- [[concepts/bigdata/dontesi-fa]] — az alapmodell, amelyet a Random Forest
  sok példányban, véletlenszerűen korlátozott jellemzőkészlettel épít fel
- [[concepts/bigdata/bagging]] — a bootstrap-mintavételezésen és többségi
  szavazáson alapuló ensemble elv, amelyre a Random Forest épül
- [[concepts/bigdata/ensemble-modszerek]] — az ensemble koncepció és a
  modelldiverzitás szerepe a végső döntés pontosságában
- [[concepts/bigdata/adaboost]] — másik homogén ensemble technika, amely
  újrasúlyozással (nem újramintavételezéssel) dolgozik
