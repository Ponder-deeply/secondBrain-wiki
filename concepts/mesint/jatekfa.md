---
tags: [concept]
sources: [07.jatek.pdf]
derivation: source
kind: definition
element: air
updated: 2026-10-12
---

# Játékfa

A játékfa a kétszemélyes játék állapotgráfjának fává kiterített alakja: a fa ágai a lehetséges játszmák, a szintek a játékosok lépéseit váltogatják.

## Tartalom

### Megfeleltetés

| Játékfa | Játék |
|---|---|
| csúcs | állás (egy állás több csúcs is lehet) |
| szint | játékos (felváltva az $A$ és $B$ szintjei) |
| él | lépés (szintről szintre) |
| gyökér | kezdőállás (kezdő játékos) |
| levél | végállások |
| ág | játszma |

Mivel ugyanaz az állás több úton is elérhető, az állapot-gráfban egy csúcsba több él fut, a fában viszont az állás ismétlődhet több csúcsként ([[concepts/mesint/grundy-mama-jateka]] fája például több `4, 2, 1` és `3, 2, 1, 1` csúcsot tartalmaz).

### ÉS/VAGY fa nézet

A játék az egyik játékos szempontjából [[concepts/mesint/es-vagy-grafok]]ként, ÉS/VAGY fával ábrázolható:

- a saját szinten egy csúcs utódai között **VAGY** kapcsolat van (mi választunk lépést),
- az ellenfél szintjén egy csúcs utódai között **ÉS** kapcsolat van (bármelyik lépésre fel kell készülnünk).

Ezért a [[concepts/mesint/nyero-strategia]] keresése ÉS/VAGY fabeli hiper-út keresése ([[concepts/mesint/hiperut]]).

## Kapocs

- [[concepts/mesint/ketszemelyes-jatekok]] — a modellezett játékosztály
- [[concepts/mesint/grundy-mama-jateka]] — példa fa
- [[concepts/mesint/es-vagy-grafok]] — a fa mint ÉS/VAGY gráf
- [[concepts/mesint/nyero-strategia]] — a fában keresett hiper-út
- [[concepts/mesint/reszleges-jatekfa-kiertekeles]] — nagy fák kezelése
