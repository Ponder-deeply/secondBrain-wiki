---
tags: [concept]
sources: [12.neuronhalok.pdf]
derivation: source
kind: model
element: water
updated: 2026-10-12
---

# Rétegenként eltérő aktivizációs függvény

Az inhomogén MLP háló számítási modellje: a rétegek kimeneti függvényei egymásba ágyazott kompozíciót alkotnak, és mindegyik réteg saját (eltérő) aktivizációs függvényt használhat.

## Tartalom

Az inhomogén MLP háló számítási modellje egy $f: P \times X \to Y$ függvény:

$$f(\Theta, x) = g_r(w^{[r]}, g_{r-1}(\dots g_2(w^{[2]}, g_1(w^{[1]}, x))\dots))$$

- $\Theta = \{w^{[1]}, \dots, w^{[r]}\}$ — a paraméterek, azaz a súlyok.
- $g_s: P \times X^{s-1} \to X^s$ — az $s$-edik réteg kimeneti függvénye ($X = X^0$, $Y = X^r$). Mivel rétegenként más-más aktivizációs függvény használható, a hálózat „inhomogén".

### Tanítás: a gradiens számítása

A gradiens elméleti kiszámítása nehéz, ezért numerikus módszereket használnak (Keras, TensorFlow). A gradiens a [[concepts/mesint/hiba-visszaterjesztes]] módszerrel áll elő rétegről rétegre.

### További problémák

- A tanítóminták kiválasztása nehéz (homogén minták, overfitting).
- A hiper-paraméterek ($N$, $\eta$) megtanulásának kérdése.
- A lokális minimumok, illetve a nyeregpontok problémája (a hibafelületen a gradiens-módszer ezekben megakadhat).

## Kapocs

- [[concepts/bigdata/aktivacios-fuggvenyek]] — az aktivizációs függvények általános elmélete
- [[concepts/bigdata/mesterseges-neuron]] — az egyes neuron számítása
- [[concepts/mesint/neuronhalo-topologiak]] — a rétegek elrendezése
- [[concepts/mesint/hiba-visszaterjesztes]] — a súlyok tanítása a kompozíció gradiensével
- [[concepts/mesint/delta-szabaly]] — az egyrétegű tanulási szabály
