---
tags: [concept, bigdata/deep-learning-bevezetes]
sources: [BDAEM-2022-EA12.pdf]
references: ["https://hmkcode.com/ai/backpropagation-step-by-step/"]
derivation: source
updated: 2026-09-12
---

# Hibavisszaterjesztés (backpropagation)

A hibavisszaterjesztés a többrétegű ("második generációs", kb. 1985 óta
elterjedt) feedforward hálózatok tanítási módszere: a kimeneti hibából
számított érzékenységet rétegről rétegre visszafelé propagálva adja meg,
hogyan kell módosítani az egyes súlyokat.

## Tartalom

### Alapötlet

A hálózat egy bemeneti vektorból (input vector), rejtett rétegeken
(hidden layers) át jut el a kimeneti rétegig (outputs). A kimeneteket a
helyes válasszal összevetve hibajelet (error signal) kapunk, amelyet
visszafelé propagálva (back-propagate) számítjuk ki az egyes súlyok szerinti
deriváltakat — ez teszi lehetővé a gradiens alapú tanulást olyan
hálózatokban is, amelyek rejtett rétegeket tartalmaznak, ahol a hiba nem
közvetlenül megfigyelhető.

### A hibafüggvény

Egy adott tanítópéldára a kimeneti hiba:

$$E = \frac{1}{2}\sum_j (y_j - d_j)^2$$

ahol $y_j$ a $j$-edik kimeneti neuron aktivációja, $d_j$ pedig az elvárt
(helyes) érték.

### Hibaérzékenység a kimeneti rétegen

A $j$ kimeneti neuronra vonatkozó érzékenység:

$$\frac{\partial E}{\partial y_j} = y_j - d_j$$

### Hibaérzékenység visszaterjesztése rejtett neuronra

A $j$ kimeneti (vagy magasabb rétegbeli) neuronok felől az $i$ rejtett
neuronra a hibaérzékenységet a $w_{ji}$ súlyokkal és az aktivációs függvény
deriváltjával ($f'$) súlyozva összegezzük:

$$\frac{\partial E}{\partial y_i} = \sum_j \frac{\partial E}{\partial y_j}\, f'(x_j)\, w_{ji}$$

Ez a lépés — az érzékenység rétegenkénti visszafelé propagálása — adja a
módszer nevét, és épp az [[concepts/bigdata/aktivacios-fuggvenyek]] lapon
tárgyalt aktivációs függvény deriválhatóságát követeli meg (ezért nem
alkalmas rá közvetlenül a bináris lépcsőfüggvény, amelyet a
[[concepts/bigdata/perceptron]] használ).

### Súlyérzékenység és súlyfrissítés

A $w_{ji}$ élsúlyra vonatkozó érzékenység:

$$\frac{\partial E}{\partial w_{ji}} = \frac{\partial E}{\partial x_j}\, y_i$$

A súlyt ez alapján, egy $\epsilon$ tanulási rátával (learning rate) skálázva
frissítjük:

$$\Delta w_{ji} = -\epsilon \, \frac{\partial E}{\partial w_{ji}}$$

### Döntésihatár-perspektíva

A forrás egy kétosztályos, kétdimenziós ponthalmazon szemlélteti a tanulás
menetét: a kezdeti véletlen súlyokhoz tartozó, kaotikus döntési görbe
tanítópéldák egymás utáni bemutatásával és a súlyok apró módosításával
fokozatosan simul rá a valódi osztályhatárra ("eventually…" a görbe már
tisztán elválasztja a két osztályt).

### Nemlineáris vs. lineáris modellek

A nemlineáris aktivációjú hálózat komplex (görbe) döntési határt tud
rajzolni úgy, hogy az eredeti adatteret nem alakítja át; ezzel szemben a
kernel-módszerek (pl. SVM) egyenes határt húznak, de előbb transzformálják
az adatot úgy, hogy az lineárisan szeparálhatóvá váljon — lásd
[[concepts/bigdata/svm]].

### Univerzális approximációs tétel

Egyetlen rejtett réteggel rendelkező hálózat — elég nagy rétegméret mellett —
tetszőleges pontossággal képes bármely $F(x)$ függvényt reprezentálni.
Ez azonban nem jelenti azt, hogy az egyrétegű hálózat *hatékony*: sok
adathalmaz esetén egy mély (több rejtett rétegű) hálózat lényegesen
keskenyebb rétegekkel is képes ugyanazt az $F(x)$ függvényt reprezentálni.
Ez a megfigyelés indokolja a mély hálózatok (deep networks) használatát az
egyetlen széles rejtett réteg helyett.

## Kapocs

- [[concepts/bigdata/mesterseges-neuron]] — az a neuronmodell, amelynek
  súlyait a hibavisszaterjesztés tanítja
- [[concepts/bigdata/aktivacios-fuggvenyek]] — a hibavisszaterjesztéshez
  szükséges deriválható aktivációs függvények
- [[concepts/bigdata/perceptron]] — az egyrétegű, lineáris korlátokkal
  rendelkező elődmodell, amelynek korlátait a többrétegű, hibavisszaterjesz-
  téssel tanított hálózat oldja fel
- [[concepts/bigdata/svm]] — alternatív, nem gradiens alapú lineáris
  osztályozási megközelítés összevetésül
