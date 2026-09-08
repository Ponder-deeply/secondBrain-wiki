---
tags: [concept]
sources: [szelmJegyzet.pdf]
derivation: source
updated: 2026-08-05
---

# A kiszámíthatóságelmélet rövid története

Az algoritmus matematikailag precíz fogalma a 20. század első felében alakult ki, miután kiderült, hogy léteznek algoritmikusan eldönthetetlen problémák, és ez megdöntötte Hilbert programját.

## Hilbert programja

1900-ban David Hilbert 23 megválaszolatlan kérdést tűzött ki a kor matematikusainak; ezek közül néhány nagy hatással volt a 20. századi matematikára, különösen a kiszámíthatóságelmélet fejlődésére.

- **Hilbert 10. problémája:** adott egy $p$ egész együtthatós többváltozós polinom; eldöntendő, lehet-e $p$ változóiba olyan egész számokat helyettesíteni, hogy $p$ értéke $0$ legyen. Hilbert olyan algoritmust keresett, ami tetszőleges polinom esetén helyes választ ad. Hilbert úgy gondolta, nincsenek megoldhatatlan problémák, és ilyen algoritmus is létezik.
- Az 1920-as években Hilbert meghirdette nagy programját: formalizálni és axiomatizálni szerette volna a matematika teljes elméletét egy véges, teljes és konzisztens axiómarendszerrel. A program része volt egy **Mindent Megoldó Algoritmus (MMA)** megadása, amely a matematika minden állításáról képes eldönteni, hogy igaz vagy hamis.

## A program cáfolata

- **Kurt Gödel** (első nemteljességi tétel) megmutatta, hogy minden olyan effektíven kiszámítható elmélet, ami tartalmazza a természetes számok elméletét, nem lehet egyszerre helyes és teljes — tehát Hilbert programja alapvetően megvalósíthatatlan. Az MMA cáfolatához viszont az algoritmus pontos definíciójára volt szükség.
- **1934:** Gödel definiálta a *rekurzív függvényeket*.
- **1930-as évek:** Alonzo Church és tanítványai megalkották a *$\lambda$-kalkulust*.
- **1936:** Alan Turing definiálta a *Turing-gépeket*.

Később kiderült, hogy ezek az eszközök mind ugyanazon függvényosztályt számítják ki; több más formális rendszer is azonos számítási erővel bír.

## Church–Turing tézis

> A kiszámíthatóság különböző matematikai modelljei mind az effektíven kiszámítható függvények osztályát definiálják.

Ez nem bizonyítható tétel, hanem széles körben elfogadott azonosítás az intuitív algoritmusfogalom és a formális modellek között.

## Eldönthetetlen problémák megjelenése

- **Turing** megmutatta, hogy nincs olyan effektíven kiszámítható módszer, ami két $\lambda$-kalkulusbeli kifejezésről eldönti, hogy ekvivalensek-e. Ehhez először megmutatta, hogy nincs módszer a Turing-gépek *megállási problémájának* eldöntésére, majd a problémát matematikai állításként fogalmazta meg — ebből következett, hogy nem létezhet a Mindent Megoldó Algoritmus.
- **1970:** Jurij Matijaszevics — korábbi eredményekre építve — megmutatta, hogy Hilbert 10. problémája is algoritmikusan eldönthetetlen.

## Kapocs

- [[concepts/bvszam/turing-gep]] — Turing 1936-os algoritmusmodellje
- [[concepts/bvszam/problemak-mint-formalis-nyelvek]] — a problémák matematikai megfogalmazása
- [[concepts/bvszam/r-re-nyelvek]] — eldönthető és felismerhető problémák osztályai
- [[concepts/bvszam/eldonthetetlen-problemak]] — a megállási probléma és társai
