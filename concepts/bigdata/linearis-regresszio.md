---
tags: [concept]
sources: [gyak3.pdf]
derivation: inferred
updated: 2026-09-12
---

# Lineáris regresszió

A lineáris regresszió egy előrejelző (nem osztályozó) módszer, amely egy
folytonos célváltozót a jellemzők **lineáris kombinációjaként** modellez,
és a paramétereket a becslési hiba (jellemzően a négyzetes hiba)
minimalizálásával illeszti a tanítóadatra.

## Tartalom

### A modell

Egy $y$ folytonos célváltozót a jellemzők ($x_1, \dots, x_k$) súlyozott
összegeként közelít:

$$\hat{y} = w_0 + w_1 x_1 + w_2 x_2 + \dots + w_k x_k$$

ahol a $w_i$ együtthatókat a tanítóadatra illesztve úgy választjuk meg, hogy
minimalizáljuk a becsült és a valós célérték eltérését.

### Tanítás — legkisebb négyzetek módszere

A leggyakoribb illesztési kritérium a **négyzetes hiba** (squared error)
minimalizálása a tanítópontokon:

$$\min_{w} \sum_i (y_i - \hat{y}_i)^2$$

Ez a **legkisebb négyzetek módszere** (least squares), amely zárt alakban
vagy gradiens alapú optimalizálással is megoldható.

### Viszonya a logisztikus regresszióhoz

A lineáris regresszió **előrejelzésre** (folytonos célérték becslésére)
szolgál, szemben a [[concepts/bigdata/logisztikus-regresszio]] által végzett
**osztályozással** (diszkrét osztálycímke becslése); a logisztikus
regresszió a lineáris regresszió alapötletét egy sigmoid transzformációval
egészíti ki, hogy valószínűséget, majd osztálycímkét kapjon.

## Kapocs

- [[concepts/bigdata/logisztikus-regresszio]] — a rokon osztályozó módszer,
  amely a lineáris kombinációt sigmoid transzformáción keresztül
  valószínűségre képezi
- [[concepts/bigdata/gepi-tanulas-alapfogalmak]] — a felügyelt tanulás
  keretrendszere, amelyben az előrejelzés (regresszió) az osztályozás
  mellett a másik fő feladattípus
- [[concepts/bigdata/modellertekeles-keresztvalidacio]] — a betanított
  előrejelző modell kiértékelésének módszerei
