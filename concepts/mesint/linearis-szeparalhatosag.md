---
tags: [concept]
sources: [12.neuronhalok.pdf]
derivation: source
kind: theorem
element: water
updated: 2026-10-12
---

# Lineáris szeparálhatóság

Egyetlen perceptron csak olyan feladatot old meg, amelyben a különböző eredményű bemeneteket egy hipersík választja szét; az XOR nem ilyen, ezért több réteg kell.

## Tartalom

### Állítás

- Egyetlen perceptron $I(\mathbf{x})=\mathbf{w}^T\mathbf{x}=0$ hipersíkja két félterre osztja a bemeneti teret, az azonos kimenetű bemenetek egy oldalra kerülnek. Az ilyen feladat **lineárisan szeparálható** (pl. AND, OR).
- Az **XOR** lineárisan nem szeparálható: a $(0,1),(1,0)$ pontokat ($y=1$) nem választja el egyenes a $(0,0),(1,1)$ pontoktól ($y=0$). Egyetlen perceptronnal nem megvalósítható.

### Több réteg

Több rétegű hálóval összetettebb tartományok is leírhatók: az első réteg neuronjai egy-egy egyenest (hipersíkot) adnak, a következő réteg ezek metszeteit/uniójait képezi. A probléma: a step függvény nem deriválható, ezért egyszerű perceptronokkal nem sikerült megfelelő tanuló algoritmust találni. Ha a kimeneti függvényt deriválhatóra (pl. szigmoid) cseréljük, a háló taníthatóvá válik: [[concepts/mesint/hiba-visszaterjesztes]] (a tárgy példája az XOR két rejtett neuronnal és egy kimeneti neuronnal, szigmoid $f$, $\eta=1{,}0$, súlyok $\text{rand}(-0{,}1;0{,}1)$).

## Kapocs

- [[concepts/mesint/altalanositott-perceptron]] — az egyetlen neuron modellje
- [[concepts/mesint/delta-szabaly]] — AND tanítása, a szétválasztó egyenes
- [[concepts/mesint/neuronhalo-topologiak]] — többrétegű hálók
- [[concepts/bigdata/perceptron]] — a perceptron korlátai
