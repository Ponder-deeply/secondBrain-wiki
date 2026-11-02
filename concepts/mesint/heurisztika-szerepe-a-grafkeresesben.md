---
tags: [concept]
sources: [05-06.grafker.pdf]
derivation: source
kind: overview
element: water
updated: 2026-10-12
---

# A heurisztika szerepe a gráfkeresésben

A gráfkereső algoritmusok hatékonysága a heurisztikus függvényen múlik: jó heurisztika megengedhető, jól informált és lehetőleg monoton, rossz heurisztikánál pedig változó heurisztikák vagy a B/B' algoritmus segíthet.

## Tartalom

### Milyen a jó heurisztika?

- **Megengedhető**: $h(n)\le h^*(n)$ – ez az A\* optimalitásának feltétele. Bár nincs mindig szükség optimális megoldásra, ilyenkor a megengedhetőség erősebb, mint amit a feladat kíván.
- **Jól informált**: $h(n)\sim h^*(n)$, azaz közel van a valódi hátralévő költséghez – minél jobban megközelíti, annál kevesebb csúcsot kell kiterjeszteni.
- **Monoton megszorítás**: $h(n)-h(m)\le c(n,m)$ minden élre. Ilyenkor nem érdemes B algoritmust használni, mert az A\* ekkor sem terjeszt ki egy csúcsot többször.

### Változó heurisztikák

- $f=g+\phi\cdot h$, ahol $\phi\sim d$: a heurisztika súlya a $d$ értékétől függ (a dia nem részletezi; $d$ feltehetően a csúcs mélysége).
- [[concepts/mesint/b-vesszo-algoritmus]] — a $h$-t menet közben javítja.

### Árok-szemlélet

A kiterjesztések számának csökkentése: az árkon belüli sorrend megváltoztatásával (lásd [[concepts/mesint/b-algoritmus]]) a futási idő négyzetesre szorítható, az eredmény és a küszöbcsúcsok nem változnak.

## Kapocs

- [[concepts/mesint/heurisztika]] — a heurisztika fogalma általában
- [[concepts/mesint/heurisztikus-fuggveny-tulajdonsagai]] — megengedhetőség, monotonitás részletesen
- [[concepts/mesint/a-csillag-algoritmus]] — az optimalitás feltétele
- [[concepts/mesint/b-algoritmus]], [[concepts/mesint/b-vesszo-algoritmus]] — a futási időt csökkentő változatok
