---
tags: [concept]
sources: [BDAEM-2022-EA12.pdf]
derivation: source
updated: 2026-09-12
---
 
# Mesterséges neuron és feedforward hálózat

A mesterséges neuron a biológiai idegsejt (dendritek, sejttest, axon)
egyszerűsített számítási modellje: bemenetek súlyozott összegét egy
nemlineáris aktivációs függvényen vezeti át; ezekből a neuronokból épülnek
fel a rétegenként előrecsatolt (feedforward) hálózatok.

## Tartalom

### A biológiai analógia

A dia a biológiai neuron felépítését (dendritek, sejttest, axon, a szinapszis
terminális elágazásai) állítja párhuzamba a mesterséges modellel: a bemeneti
jelek ($x_1, \dots, x_n$) a dendriteknek, a súlyok ($w_1, \dots, w_n$) a
szinaptikus erősségnek, az összegzés ($\Sigma$) a sejttestnek, az aktivációs
függvény pedig az axon tüzelési küszöbének felel meg.

### A mesterséges neuron formális modellje

Egy neuron egy $\mathbf{x} = (x_1, \dots, x_n)$ bemeneti vektorhoz és egy
hozzá tartozó $\mathbf{w} = (w_0, w_1, \dots, w_n)$ súlyvektorhoz az alábbi
kimenetet rendeli:

$$y = f(\mathbf{w}^\top \mathbf{x}) = f\left(w_0 + \sum_{i=1}^n w_i x_i\right)$$

ahol:

- $x_1, \dots, x_n$ — a bemenetek,
- $w_1, \dots, w_n$ — a hozzájuk tartozó súlyok,
- $w_0$ — a **bias** (eltolás), amelyet egy állandó $1$ értékű bemenethez
  ("bias node") rendelt súlyként modelleznek, hogy a $\mathbf{w}^\top
  \mathbf{x}$ jelölésbe belefeledjen a bemeneti vektor kibővítése nélkül is
  szükséges legyen,
- a **summation** (összegzés) lépés adja a neuron nettó bemenetét,
- $f(\cdot)$ a **nemlineáris aktivációs függvény**, kimenete a neuron
  aktivációja — lásd [[concepts/bigdata/aktivacios-fuggvenyek]].

### Feedforward hálózatok

Több neuron egymás után kapcsolt rétegekbe rendezve alkotja a feedforward
(előrecsatolt) hálózatot: a bemeneti réteg jelei rétegről rétegre haladnak
előre a kimeneti rétegig, visszacsatolás nélkül. A forrás ezt a
függvényapproximációs és osztályozási feladatokra alkalmazott architektúrát
vezeti be, és három konkrét típust különböztet meg:

- **feedforward hálózatok** (általános, teljesen összekötött rétegek),
- **deep tensor networks** (mélyebb, tenzorműveletekre épülő változat — a
  forrás csak megnevezi, tartalmát nem részletezi),
- **ConvNets** (konvolúciós hálózatok) — lásd
  [[concepts/bigdata/konvolucios-halozat]].

### Mit tanul meg egy neurális hálózat?

A forrás a kézzel írott számjegyeket felismerő (MNIST-szerű) példán mutatja
be, hogy a betanított hálózat rejtett rétegének egységei **önszerveződő
jellemződetektorokká** (self-organized feature detectors) válnak: egy adott
rejtett egység súlyai — erős pozitív vagy közel nulla — azt kódolják, mely
bemeneti pixelmintázatra ad erős választ (pl. egy egység a bal felső sarokban
lévő sötét területre, egy másik a kép tetején húzódó vízszintes vonalra
érzékeny). Ez a megfigyelés a rejtett rétegek reprezentációtanulási
szerepének kulcsa: a hálózat nem előre megadott jellemzőket kap, hanem a
tanítás során maga alakítja ki azokat.

## Kapocs

- [[concepts/bigdata/aktivacios-fuggvenyek]] — a neuron kimenetét adó
  nemlineáris függvények
- [[concepts/bigdata/perceptron]] — a mesterséges neuron legegyszerűbb,
  bináris osztályozó alkalmazása
- [[concepts/bigdata/hibavisszaterjesztes]] — a feedforward hálózat súlyainak
  tanítása gradiens alapon
- [[concepts/bigdata/konvolucios-halozat]] — a feedforward hálózat
  specializált, képfeldolgozásra optimalizált változata
- [[concepts/bigdata/gepi-tanulas-alapfogalmak]] — a felügyelt osztályozási
  feladat általános kerete, amelybe a neurális hálózatok is illeszkednek
