---
tags: [concept, bigdata/gepi-tanulas-klaszterezes-es-dimenziocsokkentes]
sources: [BDAEM-2022-EA10.pptx]
references: [Andrew Ng, PCA lecture slides]
derivation: source
updated: 2026-09-12
---

# Principal Component Analysis (PCA)

A PCA (főkomponens-analízis) a legelterjedtebb dimenziócsökkentő módszer:
olyan új, egymásra merőleges bázisvektorokat (főkomponenseket) keres — az
adat középpontjából kiindulva, csak eltolással és forgatással —, amelyek
mentén vetítve a lehető legtöbb varianciát őrizzük meg.

## Tartalom

### Alapötlet

A PCA az adatpontok súlypontjából (centrumából) indul ki, és új bázisvektorokat
konstruál kizárólag eltolás és forgatás (nem torzítás) útján:

- **Első főtengely (first principal axis):** az az irány, amely mentén az
  adatpontok a legnagyobb varianciát mutatják.
- **Második főtengely:** erre merőleges, kevésbé fontos irány (kisebb
  variancia).

A PCA megmondja, hogy az egyes tengelyek (irányok) mennyire "fontosak", azaz
mekkora hányadát őrzik meg az adat teljes varianciájának.

### Feladat-megfogalmazás

- **2 dimenzióból 1 dimenzióba:** keressünk egy olyan irányt (vektort),
  amelyre vetítve az adatpontokat, a vetítési hiba minimális.
- **Általánosítva, $n$ dimenzióból $k$ dimenzióba:** keressünk $k$ darab
  (egymásra merőleges) vektort, amelyekre vetítve az adatpontokat a
  vetítési hiba minimális.

Ez ekvivalens azzal, hogy a megőrzött varianciát maximalizáljuk.

### Számítás: kovariancia és sajátvektorok

A PCA a bemeneti $D$ dimenziós $X$ adatot egy $K$ dimenziós $h(x)$
jellemzővektorral summázza egy ortonormált bázisvektor-halmaz segítségével.
A számítás menete:

1. Számítsuk ki az adat empirikus átlagát, és centráljuk vele az adatot.
2. Számítsuk ki az adat kovarianciamátrixát (lásd
   [[concepts/bigdata/kovariancia]]).
3. Határozzuk meg a kovarianciamátrix sajátvektorait és sajátértékeit (lásd
   [[concepts/bigdata/sajatvektor-sajatertek]]): $Ax = \lambda x$.
4. A legnagyobb sajátértékekhez tartozó sajátvektorok adják a
   főkomponenseket (az ortonormált bázist); a hozzájuk tartozó sajátérték
   mutatja, mekkora varianciát őriz meg az adott irány.
5. Az új, $h(x)$ reprezentáció az adatpontok vetülete erre a $K$ darab
   legfontosabb sajátvektorra kifeszített altérre.

### Alkalmazás: képtömörítés

Példa a PCA gyakorlati hatására: egy $372 \times 492$ pixeles képet
$12 \times 12$ pixeles foltokra (patch) osztva, mindegyik folt egy 144
dimenziós vektorként kezelhető. A PCA-val ez a 144 dimenzió jelentősen
csökkenthető (pl. 60, 16, 6 vagy akár 3 dimenzióra) úgy, hogy a kép
lényegében felismerhető marad — minél kevesebb főkomponenst tartunk meg,
annál nagyobb az információveszteség (és a tömörítés).

Érdekesség, hogy a legfontosabb sajátvektorok mintázata hasonlít a JPEG
tömörítés alapjául szolgáló diszkrét koszinusz-transzformáció (DCT)
bázisfüggvényeire.

## Kapocs

- [[concepts/bigdata/dimenziocsokkentes]] — a PCA a dimenziócsökkentés
  egyik konkrét módszere, a megőrzött varianciát maximalizáló vetítés
  szempontja szerint
- [[concepts/bigdata/kovariancia]] — a PCA a kovarianciamátrixot
  bontja fel sajátvektorokra/sajátértékekre
- [[concepts/bigdata/sajatvektor-sajatertek]] — a főkomponensek
  matematikai alapja: a kovarianciamátrix sajátvektorai és sajátértékei
- [[concepts/bigdata/dbscan]] — a PCA és a DBSCAN egyaránt felügyelet
  nélküli módszer, de más-más célra: a PCA dimenziót csökkent, a DBSCAN
  klasztereket keres
</content>
