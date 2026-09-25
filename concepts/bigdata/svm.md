---
tags: [concept, bigdata/gepi-tanulas-osztalyozas-es-regresszio]
sources: [BDAEM-2022-EA8.pptx]
derivation: source
updated: 2026-09-12
---

# Support Vector Machine (SVM)

Osztályozó módszer, amely a döntési felületet úgy választja meg, hogy a két
osztály legközelebbi pontjaitól mért távolságát (a **margint**) maximalizálja.

## Tartalom

### Margin-maximalizálás

Szemben egy tetszőleges elválasztó egyenessel, amely csupán helyesen osztályoz,
az SVM azt az elválasztó felületet keresi, amely a legtávolabb esik mindkét
osztály legközelebbi pontjaitól. Ezt a legkisebb távolságot nevezzük
**marginnak**; az SVM ezt maximalizálja.

> **Forráshiány:** a forrásdiák (3–8. dia) a fenti elvet szórásdiagramokon
> (tempó/intenzitás tengelyeken ábrázolt zeneszámok, pl. „soaring”, „light”,
> „relaxed”, „fast” osztályok) szemléltették, konkrét pontkoordinátákkal és
> berajzolt döntési egyenesekkel. A `_md/` konverzió a diagramokat elvesztette
> (üres képaláírások maradtak), ezért a pontos ábrák és számértékek nem
> rekonstruálhatók a szövegből — az elv fent leírt lényege azonban egyértelműen
> következik a diák szövegéből és a diasorrendből (a diák egymás után mutatják
> be, hogy több lehetséges elválasztó egyenes közül melyik maximalizálja a
   margint, majd hogy kiugró értékek — outlierek — hogyan befolyásolják ezt).

### Nem lineárisan szeparálható esetek és a kernel trükk

Ha az adat az eredeti térben nem választható szét lineárisan (pl. egy belső és
egy külső csoport egy 2D síkon), egy **kernel** transzformáció az adatot egy
magasabb dimenziós térbe képezi, ahol már lineárisan szeparálhatóvá válik.
Példa a forrásból: az $(X, Y)$ síkon nem szeparálható pontokat egy $Z = X^2 +
Y^2$ harmadik koordinátával kiegészítve (azaz $(X, Y, Z)$ térbe emelve) már
lineáris felülettel el lehet választani.

Ez a **kernel trükk** lényege: a bemenetet egy magasabb dimenziós,
szeparálható reprezentációba transzformáljuk, majd ott alkalmazzuk a lineáris
SVM-et.

### Paraméterezés (`sklearn.svm.SVC`)

Az SVM néhány, a modell illesztése *előtt* rögzített paraméterrel hangolható
(hasonlóan a döntési fák max. mélységéhez vagy minimális mintaszámához):

- **kernel** — a használt kernelfüggvény; előre definiált kernelek mellett
  saját kernel is megadható.
- **C** — büntetőparaméter: a sima (nagy margójú) döntési határ és a
  tanítópontok helyes osztályozása közötti kompromisszumot szabályozza. Nagy
  $C$ esetén több tanítópont kerül helyesen osztályozásra, a döntési határ
  árán (kisebb margó, „szorosabb illeszkedés” a tanítóadatra).
- **gamma** — egyes kernelek esetén a kernel-együttható.

A $C$ és $gamma$ helyes megválasztása kritikus a modell teljesítményéhez;
rossz paraméterezés (kernel, gamma, C bármelyike) **túltanuláshoz**
(overfitting) vezethet.

## Kapocs

- [[concepts/bigdata/naive-bayes]] — másik, a forrásban közvetlenül ezután
  tárgyalt osztályozó módszer
