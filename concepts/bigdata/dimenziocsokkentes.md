---
tags: [concept, bigdata/gepi-tanulas-klaszterezes-es-dimenziocsokkentes]
sources: [BDAEM-2022-EA10.pptx]
derivation: source
updated: 2026-09-12
---

# Dimenziócsökkentés

A dimenziócsökkentés a felügyelet nélküli tanulás egyik fő ága: cél egy
magas dimenziós, valós értékű adatpontot egy alacsonyabb dimenziós, valós
értékű vektorral helyettesíteni úgy, hogy a lényegi információ minél kevésbé
vesszen el.

## Tartalom

### Motiváció

A felügyelet nélküli tanulásban nincs tanító címke — a cél a struktúra és az
összefüggések megtanulása magából az adatból. Ennek két fő útja van:

- **Klaszterezés:** egy komplex, valós értékű adatpontot egyetlen
  kategorikus változóval (klaszter-azonosítóval) összegez.
- **Dimenziócsökkentés:** ugyanezt egy alacsonyabb dimenziós, valós értékű
  vektorral teszi: adott $d$ dimenziós adatpontokból $r < d$ dimenziós
  pontokat állít elő, minimális információveszteséggel.

### Mérhető és látens jellemzők

A dimenziócsökkentés mögötti alapfeltevés, hogy egy jelenséget sok, közvetlenül
mérhető jellemző ír le, miközben a mintázatot valójában kevesebb, közvetlenül
nem megfigyelhető ("látens") jellemző mozgatja. Példa: egy ház árát olyan
mérhető jellemzők írják le, mint az alapterület, a szobák száma, az iskolai
körzet minősítése és a szomszédság biztonsága — ezek mögött azonban kevesebb
látens jellemző (pl. "méret", "szomszédság minősége") húzódhat.

A cél tehát egy **kompozit jellemző** (pl. főkomponens) létrehozása, amely
közvetlenebbül ragadja meg a mögöttes jelenséget, és ezáltal tömöríti az
adatot információvesztés minimalizálása mellett.

### Módszerek

Több technika létezik a dimenziócsökkentésre, eltérő optimalizálási
kritériummal:

- **PCA (Principal Component Analysis):** azt a vetítést keresi, amely
  maximalizálja a megőrzött varianciát.
- **ICA (Independent Component Analysis):** a PCA-hoz hasonló, de
  nem-Gauss eloszlású jellemzőket feltételez.
- **Multidimensional Scaling (MDS):** azt a vetítést keresi, amely a
  legjobban megőrzi a pontok közti páronkénti távolságokat.
- **LDA (Linear Discriminant Analysis):** olyan komponens-tengelyeket
  keres, amelyek maximalizálják az osztályok közti szeparációt (tehát
  felügyelt jellegű, osztálycímkéket használ).

Ezek közül a legrészletesebben tárgyalt módszer a PCA.

## Kapocs

- [[concepts/bigdata/pca]] — a legfontosabb dimenziócsökkentő módszer,
  amely a megőrzött varianciát maximalizáló vetítést keresi
- [[concepts/bigdata/gepi-tanulas-alapfogalmak]] — a felügyelt és
  felügyelet nélküli tanulás megkülönböztetése
- [[concepts/bigdata/k-means]] — a felügyelet nélküli tanulás másik fő ága
  (klaszterezés), amely kategorikus címkével összegzi az adatpontokat
</content>
