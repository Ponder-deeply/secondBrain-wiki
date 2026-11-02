---
tags: [concept]
sources: [12.neuronhalok.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-10-12
---

# Hiba-visszaterjesztés (error backpropagation)

A hiba-visszaterjesztés a többrétegű, deriválható kimeneti függvényű háló tanítása gradiens módszerrel: a kimeneti réteg hibáját rétegenként visszafelé terjesztve számoljuk ki a súlyok módosítását.

## Tartalom

### Hibafüggvény és gradiens módszer

A modell hibafüggvénye ($y_j$ az elvárt, $o^{[r]}_j$ a számított kimenet):

$$L(\Theta)=\tfrac12\sum_{j=1}^{n^{[r]}}\big(y_j-o^{[r]}_j\big)^2$$

$L$ a $w^{[s]}_{ij}$ súlyoktól függő többváltozós függvény; a minimumát gradiens módszerrel keressük, a súlyokat lépésenként kis mértékben, a megfelelő irányban módosítva. Az $I^{[s]}_j=\sum_i w^{[s]}_{ij} o^{[s-1]}_i$ összegzett bemenettel (láncszabály):

$$\Delta w^{[s]}_{ij}=\eta\frac{\partial L}{\partial w^{[s]}_{ij}}=\eta\frac{\partial L}{\partial I^{[s]}_j}\cdot\frac{\partial I^{[s]}_j}{\partial w^{[s]}_{ij}}=\eta\, e^{[s]}_j\, o^{[s-1]}_i$$

ahol $e^{[s]}_j$ a számítási hibának az $s$-edik réteg $j$-edik neuronjára jutó hányada, $e^{[s]}_j=-\partial E/\partial I^{[s]}_j$. (A diák a $\Delta w$-t a $w:=w-\Delta w$ és a $w:=w+\Delta w$ alakban is használja; az $e$ előjel-konvenciója a $-\partial E/\partial I$ definícióval konzisztens a $+$ alakkal.)

### Visszavetített hiba (szigmoid $g$ esetén)

- Kimeneti réteg ($s=r$): $e^{[r]}_j=o^{[r]}_j\,(1-o^{[r]}_j)\,(t_j-o^{[r]}_j)$
- Belső réteg ($s<r$): $e^{[s]}_j=o^{[s]}_j\,(1-o^{[s]}_j)\sum_{k=1}^{n^{[s+1]}} e^{[s+1]}_k\, w^{[s+1]}_{jk}$

($t_j$ a célérték; a $o(1-o)$ tag a szigmoid deriváltja.) Rekurzív szabályt kapunk: a $[s+1]$ réteg hibájából számolható az $[s]$ rétegé.

### Algoritmus

1. A bemeneti $\mathbf{x}$ vektorból indulva rétegenként kiszámoljuk a neuronok kimenetét $o^{[s]}_j$, a kimeneti rétegét is (előre menet).
2. A kimeneti réteg minden neuronjára kiszámoljuk a lokális hibát $e^{[r]}_j$.
3. Rétegenként hátulról előre haladva kiszámoljuk a belső neuronok hibáit $e^{[s]}_j$.
4. Módosítjuk a súlyokat: $w^{[s]}_{ij}:=w^{[s]}_{ij}+\Delta w^{[s]}_{ij}$, $\Delta w^{[s]}_{ij}=\eta\, e^{[s]}_j\, o^{[s-1]}_i$.

### Megjegyzések

- A step nem deriválható, ezért a módszer deriválható $g$-t (pl. szigmoid) igényel; lásd [[concepts/mesint/linearis-szeparalhatosag]].
- A diák indexelése a belső hibánál nem teljesen egységes ($w_{ik}$ a 18., $w_{jk}$ a 19. dián); a logika: az $[s]$ réteg $j$-edik neuronjának kimenete a következő réteg $k$-adik neuronjának $w^{[s+1]}_{jk}$ súlyával jut tovább.

## Kapocs

- [[concepts/bigdata/hibavisszaterjesztes]] — az általános (nem a tárgyhoz kötött) tárgyalás
- [[concepts/mesint/delta-szabaly]] — az egyneuronos előd
- [[concepts/mesint/neuronhalo-topologiak]] — a tanított MLP felépítése
- [[concepts/mesint/altalanositott-perceptron]] — neuron és kimeneti függvények
- [[concepts/mesint/retegenkenti-aktivacios-fuggveny]] — rétegenként eltérő $g$ a levezetésben
