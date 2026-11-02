---
tags: [concept]
sources: [12.neuronhalok.pdf]
derivation: source
kind: model
element: fire
updated: 2026-10-12
---

# Általánosított perceptron

Az általánosított perceptron a mesterséges neuron Gregorics-féle modellje: a bemenetek súlyozott összegét (bias-szal kiegészítve) egy tetszőleges kimeneti függvényen vezeti át; a súlyok tanulhatók.

## Tartalom

### Felépítés

A neuronnak $x_1,\dots,x_n$ bemenete és $w_1,\dots,w_n$ súlya van, továbbá egy aktiváló bemenet (bias) $x_0 \neq 0$ (a példákban $x_0=1$) a $w_0$ súllyal.

- Összegzett bemenet: $I=\sum_{i=0}^{n} w_i x_i = \mathbf{w}^T\mathbf{x}$
- Kimenet: $o = g(I) = g\big(\sum_{i=1}^{n} w_i x_i + \underbrace{w_0 x_0}_{b}\big)$, ahol $g$ a kimeneti (aktivizációs) függvény.

A $b = w_0 x_0$ tag a kimeneti függvényt a vízszintes tengely mentén eltolja (a küszöb $-b$ helyre kerül).

### Kimeneti függvények (a tárgy áttekintése)

| függvény | alak |
|---|---|
| step | 0, ha $I\le 0$; 1, ha $I>0$ |
| sgn | $-1$ / $+1$ |
| linear$_{a,b}$ | $a$ alatt 0, $b$ fölött 1, közte lineáris |
| relu | $\max(0,x)$ |
| sigmoid | $\frac{1}{1+e^{-x}}$ |
| tanh | $\frac{1-e^{-x}}{1+e^{-x}}$ |
| sin$_{-1,+1}$ | $-1$ és $+1$ közé vágott szinusz |
| softmax | $\frac{e^{x_j}}{\sum_k e^{x_k}}$ |

A step nem deriválható, ezért a [[concepts/mesint/hiba-visszaterjesztes]] módszerhez deriválható függvény (pl. szigmoid) kell; lásd még [[concepts/bigdata/aktivacios-fuggvenyek]].

### Tanulás

A neuron számítási képletét a $\mathbf{w}$ súlyok határozzák meg. A súlyok implicit módon a topológiát is kijelölik: nulla súlyú él az él elhagyását jelenti. Tanulás közben a súlyokat fokozatosan módosítjuk: $\mathbf{w} := \mathbf{w} + \Delta\mathbf{w}$, ahol $\Delta\mathbf{w}$ a neuron bemeneteitől és kiszámított kimenetétől függ.

- felügyelt tanulásnál az elvárt kimenetet is felhasználjuk ([[concepts/mesint/delta-szabaly]], [[concepts/mesint/felugyelt-tanulas]]),
- felügyelet nélküli tanulásnál nincs szükség elvárt kimenetre.

## Kapocs

- [[concepts/bigdata/mesterseges-neuron]] — a neuron általános (nem a tárgyhoz kötött) tárgyalása
- [[concepts/bigdata/perceptron]] — step kimenetű változat, Rosenblatt
- [[concepts/mesint/neuronhalo-topologiak]] — a neuronokból épített hálózatok
- [[concepts/mesint/linearis-szeparalhatosag]] — mit képes egyetlen perceptron
- [[concepts/mesint/retegenkenti-aktivacios-fuggveny]] — rétegenként eltérő $g$
