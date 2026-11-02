---
tags: [concept]
sources: [12.neuronhalok.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-10-12
---

# Delta-szabály

A delta-szabály az egyetlen neuron felügyelt tanulási szabálya: minden példa után a súlyt a bemenet és a hiba (elvárt − számított kimenet) szorzatával, a tanulási rátával skálázva módosítjuk.

## Tartalom

### Szabály

$$\Delta w_i = \eta\cdot x_i\cdot (y - o),\qquad w_i := w_i + \Delta w_i$$

- $y$ — elvárt kimenet, $o$ — számított kimenet, $e = y-o$ a hiba,
- $\eta$ — tanulási ráta (a példában $0{,}1$),
- $x_0 = 1$ a bias bemenet.

Ha $e=0$, a súly nem változik. Egy teljes végigfutás a tanítóhalmazon egy epoch; a tanítás addig ismétlődik, amíg a hiba minden példára 0 nem lesz.

### Példa: AND tanítása

Egyetlen neuron, $x_1,x_2\in\{0,1\}$, kimenet $o=\text{step}(I)$, $I=w_0+w_1x_1+w_2x_2$, kezdősúly $w_0=w_1=w_2=0{,}08$, $\eta=0{,}1$.

| # | $x_1$ | $x_2$ | $y$ | $I$ | $o$ | $e$ | új $(w_0,w_1,w_2)$ |
|---|---|---|---|---|---|---|---|
| 1 | 1 | 0 | 0 | 0,16 | 1 | −1 | (−0,02; −0,02; 0,08) |
| 2 | 0 | 1 | 0 | 0,06 | 1 | −1 | (−0,12; −0,02; −0,02) |
| 3 | 1 | 1 | 1 | −0,16 | 0 | 1 | (−0,02; 0,08; 0,08) |
| 4 | 1 | 0 | 0 | 0,06 | 1 | −1 | (−0,12; −0,02; 0,08) |

Ezután a második epoch és további lépések következnek; a végén $\mathbf{w}=(-0{,}22;\,0{,}08;\,0{,}18)$, és mind a négy bemenetre helyes a kimenet (az (1,1)-re $I=0{,}04>0$, a többire $I\le0$).

### Mit tanultunk meg

A neuron azonos az $\text{AND}(x_1,x_2)$ függvénnyel, mert az $I$ előjele csak az $(1,1)$ bemenetre pozitív. Az $I(x_1,x_2)=w_0+w_1x_1+w_2x_2=0$ egyenes (itt $x_2=-0{,}44\,x_1+1{,}22$) két félsíkra osztja a bemenet-párokat: az azonos eredményűek egy oldalra kerülnek. Lásd [[concepts/mesint/linearis-szeparalhatosag]].

## Kapocs

- [[concepts/mesint/altalanositott-perceptron]] — a tanított neuron
- [[concepts/mesint/felugyelt-tanulas]] — az elvárt kimenetet használó tanulás
- [[concepts/mesint/hiba-visszaterjesztes]] — a delta-szabály általánosítása többrétegű hálóra (deriválható $g$)
- [[concepts/bigdata/perceptron]] — perceptron-tanulási szabály
