---
tags: [concept]
sources: [gyak3.pdf]
derivation: inferred
updated: 2026-09-12
---

# K legközelebbi szomszéd (K-NN)

A K-NN (K-Nearest Neighbors) egy egyszerű, "lusta tanulású" (lazy learning)
osztályozó módszer, amely egy új eset osztályát a hozzá — egy
távolságmérték szerint — legközelebb eső $K$ tanítópont többségi
osztálycímkéje alapján határozza meg.

## Tartalom

### Alapötlet

A K-NN nem épít explicit modellt tanítás közben (innen a "lusta tanulás"
elnevezés): a teljes tanítóadatot megőrzi, és a predikciót csak az új eset
osztályozásakor számítja ki. Egy új $x$ ponthoz:

1. kiszámítjuk a távolságát a tanítóadat minden pontjától (lásd
   [[concepts/bigdata/tavolsag-hasonlosag-meresek]]);
2. kiválasztjuk a $K$ legközelebbi tanítópontot;
3. az új pont osztálya a $K$ szomszéd közötti **többségi szavazással**
   dőlbe el (regresszió esetén az átlaguk adja az előrejelzést).

### A $K$ megválasztása

$K$ a modell egyik hiperparamétere: kis $K$ esetén a döntési felület
érzékenyebb a zajra (túltanulás felé hajlik), nagy $K$ esetén simább, de
kevésbé lokális döntést hoz (alultanulás felé hajlik). A megfelelő $K$
megválasztása jellemzően [[concepts/bigdata/modellertekeles-keresztvalidacio]]
segítségével, kipróbálás útján történik.

### Kapcsolódás a döntési felülethez

A K-NN döntési felülete nem explicit (nincs zárt alakja, mint pl. az SVM
hipersíkjának), hanem a tanítópontok elrendezéséből implicit módon adódik —
szemben a [[concepts/bigdata/gepi-tanulas-alapfogalmak]] lapon tárgyalt
explicit döntési felületet kereső módszerekkel.

## Kapocs

- [[concepts/bigdata/tavolsag-hasonlosag-meresek]] — a távolságmérték,
  amelyre a K-NN szomszédkeresése épül
- [[concepts/bigdata/gepi-tanulas-alapfogalmak]] — a felügyelt osztályozási
  feladat általános keretrendszere
- [[concepts/bigdata/modellertekeles-keresztvalidacio]] — a $K$
  hiperparaméter és a modell teljesítményének kiértékelése
- [[concepts/bigdata/logisztikus-regresszio]] — másik, a gyakorlaton
  közvetlenül ezután tárgyalt osztályozó módszer
