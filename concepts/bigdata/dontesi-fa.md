---
tags: [concept, bigdata/gepi-tanulas-osztalyozas-es-regresszio]
sources: [BDAEM-2022-EA7.pptx]
derivation: source
updated: 2026-09-12
---

# Döntési fa (Decision Tree)

Felügyelt osztályozó modell, amely az osztályozási döntést egymás után
feltett, egy-egy jellemzőre vonatkozó lineáris kérdések (elágazások)
sorozataként építi fel; az elágazási pontok kiválasztásához az entrópia
(vagy GINI-index) alapú tisztaságmérték szolgál.

## Tartalom

### Alapötlet

A döntési fa több, egymás utáni lineáris kérdést tesz fel az adat
jellemzőire (pl. "Fast?", majd "Soaring?"), és a válaszok (yes/no) mentén
ágazik szét, amíg el nem éri a végső osztálycímkét. Kétdimenziós példán
(tempó/intenzitás) ez geometriailag azt jelenti, hogy a döntési felületet
tengelyekkel párhuzamos szakaszokkal (pl. $X < 3$, majd $Y < 4$) közelíti,
szemben az egyetlen egyenessel elválasztható (lineárisan szeparálható)
esettel — lásd [[concepts/bigdata/gepi-tanulas-alapfogalmak]].

### Fa építése — tisztaság (impurity) mérése

A fa építésekor minden elágazásnál el kell dönteni, melyik jellemző mentén
érdemes osztani az adatot. Ehhez egy tisztaságmértékre (impurity measure)
van szükség, amely megmondja, mennyire "kevert" osztályösszetételű egy adott
adathalmaz-részlet. A következő split-et mindig a magasabb tisztaságot
(alacsonyabb impurity-t) eredményező jellemző mentén választjuk.

#### Entrópia

Az entrópia egy adathalmaz-részlet kevertségének (impurity) mértéke:

- ha minden példa ugyanabba az osztályba tartozik: entrópia = 0,
- ha a példák egyenletesen oszlanak meg az osztályok között: entrópia = 1.0.

Az entrópia definíciója (osztályonkénti $p_i$ arányokkal, minden osztályra
összegezve):

$$H = -\sum_i p_i \log_2 p_i$$

ahol $p_i$ az $i$-edik osztályba tartozó példák aránya az adott
részhalmazban.

#### Információnyereség (Information Gain)

Az információnyereség azt méri, mennyivel csökken az entrópia egy adott
jellemző mentén történő felosztás után: a szülő csomópont entrópiájából
kivonjuk a gyermek csomópontok entrópiáinak (a részhalmaz méretével súlyozott)
átlagát. A forrás egy konkrét példán mutatja be a számítást (szülő entrópia
1.0, majd a "Fast"/"Relaxed" szerinti felosztás után a gyermek csomópontok
entrópiája 0.0 és 0.92, ami 0.31 információnyereséget eredményez). Minél
nagyobb az információnyereség, annál jobb az adott jellemző az elágazáshoz.

#### GINI-index

A GINI-index az entrópia alternatívája ugyanarra a célra (tisztaság mérése az
elágazás kiválasztásához); számításigénye alacsonyabb, mint az entrópiáé.

### A fa mint modell

A döntési fa tanítás (training) végén egy olyan modell áll elő, amely új
esetekre alkalmazva a fa gyökerétől a levelekig haladva, az egyes
csomópontokon feltett kérdésekre adott válaszok mentén jut el a végső
osztálycímkéhez.

## Kapocs

- [[concepts/bigdata/gepi-tanulas-alapfogalmak]] — a felügyelt osztályozási
  feladat általános felépítése, amelynek a döntési fa egy konkrét
  megvalósítása
- [[concepts/bigdata/modellertekeles-keresztvalidacio]] — a betanított
  döntési fa (és más osztályozók) kiértékelésének módszerei
- [[concepts/bigdata/random-forest]] — sok döntési fát kombináló ensemble
  módszer, amely a döntési fát alapmodellként használja
