---
tags: [concept]
sources: [BDAEM-2022-EA9.pptx]
references: ["Slides based on Eamonn Keogh's clustering lecture"]
derivation: source
updated: 2026-09-12
---

# K-Means klaszterezés

A K-means egy partícionáló (nem hierarchikus) klaszterező algoritmus,
amely az objektumokat $K$, előre megadott számú, nem átfedő klaszterbe
sorolja úgy, hogy iteratívan felváltva frissíti a klaszterek középpontjait
és az objektumok klaszter-hovatartozását.

## Tartalom

### A klaszterezés célja és kontextusa

A klaszterezés felügyelet nélküli tanulási feladat (nincs tanuló címke): a
cél olyan csoportokat találni az adatpontok között, ahol a **klaszteren
belüli hasonlóság maximális**, a **klaszterek közti hasonlóság minimális**.
Ehhez szükséges egy hasonlósági (távolság-) mérték definiálása az
objektumokon.

A klaszterező algoritmusok két fő családja: **hierarchikus** (a
klaszterek egymásba ágyazott hierarchiáját építik fel) és **partícionáló**
algoritmusok (egy adott, rögzített klaszterszámú felosztást állítanak elő
és értékelnek). A K-means az utóbbi családba tartozó, ún. *négyzetes hiba*
(*squared error*) célfüggvényt optimalizáló módszer.

### Az algoritmus lépései

1. Válasszunk egy $K$ értéket (a klaszterek számát).
2. Inicializáljuk a $K$ klaszterközéppontot (szükség esetén véletlenül).
3. Rendeljük az összes $N$ objektumot a hozzájuk legközelebbi
   klaszterközépponthoz (klaszter-hovatartozás meghatározása).
4. Becsüljük újra a $K$ klaszterközéppontot a most kapott
   klaszter-hovatartozások alapján (pl. az adott klaszterbe tartozó
   pontok átlagaként).
5. Ha egyetlen objektum klaszter-hovatartozása sem változott az utolsó
   iterációban, állj meg; egyébként ugorj vissza a 3. lépésre.

Az algoritmus tehát az objektum-hovatartozás és a klaszterközéppontok
frissítését váltogatja, amíg egy stabil (konvergens) felosztáshoz nem jut.
A leggyakrabban használt távolságmérték az euklideszi távolság.

### Erősségek és gyengeségek

**Erősségek:**

- viszonylag hatékony: futásideje $O(t \cdot k \cdot n)$, ahol $n$ az
  objektumok, $k$ a klaszterek, $t$ az iterációk száma — jellemzően
  $k, t \ll n$;
- jellemzően (lokális) optimumban áll meg.

**Gyengeségek:**

- csak akkor alkalmazható, ha az "átlag" fogalma értelmezhető az adaton —
  kategorikus (nem numerikus) adatra nem közvetlenül alkalmazható;
- előre meg kell adni $K$-t, a klaszterek számát;
- érzékeny a zajra és a kiugró (outlier) értékekre;
- nem alkalmas nem konvex alakú klaszterek felismerésére.

## Kapocs

- [[concepts/bigdata/gepi-tanulas-alapfogalmak]] — a felügyelt/felügyelet
  nélküli tanulás megkülönböztetése, amelynek a k-means a felügyelet
  nélküli (klaszterezési) oldalára a legfőbb példa
</content>
