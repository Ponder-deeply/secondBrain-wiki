---
tags: [concept]
sources: [03.lokalker.pdf]
derivation: source
kind: model
element: water
updated: 2026-10-12
---

# Gráfszínezés

Egy véges egyszerű gráf csúcsait a lehető legkevesebb színnel kell kiszínezni úgy, hogy a szomszédos csúcsok eltérő színűek legyenek; a deck ezt állapottér-modellel írja fel, és lokális keresésre példaként használja.

## Tartalom

### Feladat és cél

- **Feladat:** adott egy véges egyszerű gráf; a csúcsait a lehető legkevesebb szín felhasználásával úgy kell kiszínezni, hogy szomszédos csúcsok eltérő színűek legyenek.
- **Cél:** a csúcsok olyan minimális osztályból álló osztályozását keressük, ahol egy osztályba tartozó csúcsok között nem vezet él. Az egy osztályba sorolt csúcsok azonos színűek lehetnek, a felhasznált színek száma az osztályok száma.

### Állapottér-modell

- **Állapot:** a csúcsok egy „gyengített" osztályozása: egy osztályhoz tartozó csúcsok között lehetnek élek; a gráf maximális fokszámánál több osztály van, de lehet egy osztály üres is.
- **Művelet:** egy osztályból egy csúcsot egy másik osztályba helyez át.
- **Kezdő állapot:** tetszőleges.
- **Célállapot:** a legjobb osztályozás (minél kevesebb első néhány osztályban legyenek csak csúcsok, amelyek között nincs él).
- **Állapot-gráf:** exponenciális méretű az eredeti gráf csúcsszámához mérve.

Az exponenciális állapotgráf miatt a feladat tipikus lokális keresési probléma: a gráfot nem építjük fel, csak az aktuális osztályozás környezetét vizsgáljuk.

## Kapocs

- [[concepts/mesint/allapotter-modell]] — az állapottér-modell általános fogalma
- [[concepts/mesint/hegymaszo-modszer]] — lokális keresési módszer a feladat megoldására
- [[concepts/mesint/szimulalt-hutes]] — véletlenített lokális keresés
