---
tags: [concept, bigdata/deep-learning-bevezetes]
sources: [BDAEM-2022-EA12.pdf]
derivation: source
updated: 2026-09-12
---

# Perceptron (Rosenblatt, 1957)

A perceptron a mesterséges neuron legelső, bináris lépcsőfüggvényt használó
osztályozó modellje, amely csak lineárisan szeparálható osztályok esetén
képes tökéletes döntési határt tanulni.

## Tartalom

### A modell

A perceptron egy [[concepts/bigdata/mesterseges-neuron]], amelynek
aktivációs függvénye bináris lépcsőfüggvény (binary step):

$$f(\mathbf{x}) = \begin{cases} 1 & \text{ha } \mathbf{w} \cdot \mathbf{x} > 0 \\ 0 & \text{egyébként} \end{cases}$$

A forrás megjegyzi, hogy bináris osztályozóként a perceptron ekvivalens a
support vector machine-nel (SVM) — lásd [[concepts/bigdata/svm]] — abban az
értelemben, hogy mindkettő lineáris döntési határt (hipersíkot) tanul; a
tanítási eljárásuk azonban különbözik.

### Tanítási szabály

A súlyokat egy $D = \{(\mathbf{x}_1, d_1), \dots, (\mathbf{x}_S, d_S)\}$
tanítóhalmazon, iteratív hibajavítással tanítja:

1. a $\mathbf{w}$ súlyvektor véletlen kezdőértékkel indul,
2. minden $(\mathbf{x}_j, d_j)$ példára:
   - kiszámítja a kimenetet: $y_j = f(\mathbf{w}^\top \mathbf{x}_j)$,
   - frissíti a súlyokat: $\mathbf{w} \leftarrow \mathbf{w} + (d_j - y_j)\,\mathbf{x}_j$,
3. a 2. lépést konvergenciáig ismétli.

A frissítés csak akkor módosít, ha a modell tévedett ($d_j \neq y_j$); helyes
osztályozás esetén a súlyok változatlanok maradnak.

### Lineáris szeparálhatóság korlátja

A forrás az AND, OR és XOR logikai függvényeken szemlélteti a perceptron
alapvető korlátját: egyetlen lineáris döntési határral (egyenessel) az AND és
OR függvény szeparálható, az **XOR nem** — XOR esetén "no separation is
possible" egyetlen lineáris egységgel. A megoldás két rétegnyi lineáris
küszöbegység (2-layer LTU) összekapcsolása, amellyel XOR is szeparálhatóvá
válik. Ez a korlát vezetett a többrétegű (feedforward) hálózatok és a
[[concepts/bigdata/hibavisszaterjesztes]] tanítási módszer bevezetéséhez a
"második generációs" hálózatokban.

## Kapocs

- [[concepts/bigdata/mesterseges-neuron]] — az általános neuronmodell,
  amelynek a perceptron egy speciális, lépcsőfüggvényes esete
- [[concepts/bigdata/aktivacios-fuggvenyek]] — a perceptron bináris
  lépcsőfüggvénye a lehetséges aktivációs függvények egyike
- [[concepts/bigdata/svm]] — a perceptronnal ekvivalens, más elven (margin-
  maximalizálás) tanított lineáris osztályozó
- [[concepts/bigdata/hibavisszaterjesztes]] — a perceptron lineáris
  korlátját feloldó többrétegű hálózatok tanítási módszere
