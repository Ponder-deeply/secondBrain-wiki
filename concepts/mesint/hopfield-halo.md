---
tags: [concept]
sources: [12.neuronhalok.pdf]
derivation: source
kind: model
element: water
updated: 2026-10-12
---

# Hopfield-háló

Egyrétegű, teljesen összekötött, aszinkron működésű neuronháló $\pm 1$ állapotú neuronokkal; eredetileg asszociatív memóriának készült: a tárolt minták a háló stabil konfigurációi.

## Tartalom

### Topológia

Aszinkron működésű Hopfield-topológia: egyrétegű, teljesen összekötött hálózat $n$ darab $+1$ vagy $-1$ állapotú neuronnal. Minden neuron belső állapotú: $a_j = \operatorname{sgn}(\sum_i w_{ij} a_i - \theta_j)$, ahol a küszöb a konstans 1 bemenet $-\theta_j$ súlyával jelenik meg.

### Működés

1. **Kezdet** — a neuronok kívülről kapják értékül az állapotaikat. A neuronok által felvett állapot-együttest a háló *konfigurációjának* hívjuk; az összes konfiguráció a *konfigurációs tér*.
2. **Iteráció** — a neuronok aszinkron módon, többször is újraszámolják az állapotukat, folyamatosan változtatva a konfigurációt:
   $$a_j^{\text{új}} = \operatorname{sgn}\Big(\sum_{i=1}^{n} w_{ij} a_i - \theta_j\Big)$$
   ($a_i$ az $i$-edik neuron állapota, $w_{ij}$ az $i$-ből $j$-be vezető kapcsolat súlya, $\theta_j$ a $j$-edik neuron küszöbe).
3. **Vég** — amikor a háló *stabil konfigurációba* jut (az állapotok újraszámolásuk ellenére sem változnak tovább), a neuronok állapotait a háló kimenetének tekintjük.

### Használat: asszociatív memória

Egy-egy stabil konfiguráció egy eltárolt mintát ad (pl. egy kép pixelpontjait). Ha a minta zajos, torzított vagy hiányos változatát adjuk bemenetként, a háló addig változtatja az állapotát, amíg újra stabil konfigurációba nem kerül, azaz fel nem idézi az eredeti mintát (több minta esetén a leghasonlóbbat).

Vizsgálandó kérdések: hogyan lehet (felügyelet nélkül) betanítani, hogy a tárolt minták a stabil konfigurációk legyenek; konvergál-e a háló valamelyik stabil konfigurációhoz.

### Egyetlen minta tárolása

A tárolandó $p \in \{+1,-1\}^n$ minta legyen stabil konfiguráció: $p_j = \operatorname{sgn}(\sum_i w_{ij} p_i)$ (ha $\theta_j = 0$). Ez teljesül, ha $w_{ij} \cong p_i \cdot p_j$.

Az ilyen minta vonzáskörzettel bír: minden olyan $a$ konfigurációból, amelynek több mint a fele komponense azonos a mintáéval ($\sum_i p_i a_i > 0$), a háló véges lépésben a mintához konvergál. Ugyanis egy neuron újraszámolásakor azonnal a minta megfelelő komponensével válik azonossá:

$$a_j^{\text{új}} = \operatorname{sgn}\Big(\sum_i p_i p_j a_i\Big) = \operatorname{sgn}\Big(p_j \sum_i p_i a_i\Big) = p_j.$$

### Több minta tárolása

Legyen $d$ darab tárolandó minta: $p^k \in \{+1,-1\}^n$ ($k = 1..d$). A súlyok a minták szuperpozíciója:

$$w_{ij} = \frac{1}{n}\sum_k p_i^k p_j^k,$$

ami inkrementális tanulási szabályként is felírható: $\Delta w_{ij} = \frac{1}{n} p_i^k p_j^k$ (**Hebb-szabály**).

Véletlenszerűen választott (ortogonális) minták esetén annak, hogy a minták stabil konfigurációk legyenek, a legnagyobb a valószínűsége, ha $d \le n / \log n$.

### Konvergencia

Vegyük a hibafüggvényt: $E = -\frac12 \sum_{i,j} w_{ij} a_i a_j - \sum_i \theta_i a_i$. Belátható, hogy ha a súlymátrix szimmetrikus és a diagonális elemei nem negatívak, akkor egy konfigurációváltás során a függvény értékének csökkennie kell. Mivel a konfigurációk száma véges, a háló véges lépésben stabil konfigurációba jut.

## Kapocs

- [[concepts/bigdata/mesterseges-neuron]] — a küszöbös ($\operatorname{sgn}$) neuron
- [[concepts/mesint/neuronhalo-topologiak]] — a Hopfield-háló a visszacsatolt, teljesen összekötött topológia
- [[concepts/mesint/altalanositott-perceptron]] — a neuron számítási modellje
- [[concepts/mesint/delta-szabaly]] — felügyelt tanulási szabály, a Hebb-szabály ellenpontja
- [[concepts/mesint/hiba-visszaterjesztes]] — előrecsatolt hálók tanítása
- [[concepts/mesint/retegenkenti-aktivacios-fuggveny]] — rétegelt (MLP) modell, szemben az egyréteggel
