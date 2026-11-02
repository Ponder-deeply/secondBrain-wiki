---
tags: [concept]
sources: [05-06.grafker.pdf]
derivation: source
kind: definition
element: air
updated: 2026-10-12
---

# Heurisztikus függvény és tulajdonságai

A heurisztikus függvény ($h: N \to \mathbb{R}$) egy csúcsnál megbecsüli a csúcsból a célba vezető ("hátralévő") optimális út költségét. Három nevezetes tulajdonsága a nem-negativitás, a megengedhetőség és a monoton megszorítás.

## Tartalom

### Definíció

$h(n) \approx h^*(n)$, ahol $h^*: N \to \mathbb{R}$ többnyire nem ismert, csak elméletben létező költségfüggvény:

- hátralévő optimális költség $n$-ből a célcsúcsok ($T$) valamelyikébe: $h^*(n) = c^*(n,T)$;
- $M$-be vezető optimális költség: $c^*(n,M) := \min_{m \in M} c^*(n,m)$;
- $n$-ből $m$-be vezető optimális költség: $c^*(n,m) := \min_{\alpha \in \{n \to m\}} c^{\alpha}(n,m)$.

Példák: a 8-kirakónál $W$ (rossz helyen lévő lapkák száma) és $P$ (lapkák célhelyüktől mért távolságainak összege); a $0$ (zéró) függvény is heurisztika.

### Nevezetes tulajdonságok

| Tulajdonság | Feltétel |
|---|---|
| **nem-negatív** | $h(n) \ge 0 \quad \forall n \in N$ |
| **megengedhető** (admissible) | $h(n) \le h^*(n) \quad \forall n \in N$ |
| **monoton megszorítás** (következetes) | $h(n) - h(m) \le c(n,m) \quad \forall (n,m) \in A$ |

Megjegyzések:

- a 8-kirakó $W$ és $P$ heurisztikája mindhárom tulajdonsággal bír;
- $h$ monoton + $h$ célban nulla $\Rightarrow$ $h$ megengedhető;
- a zéró függvény mindhárom tulajdonsággal bír.

### A 8-kirakó példa a diákon

Az azonos kezdőállásból ($W=4$, $P=5$) indított keresések összehasonlítása:

- $f = W$ (mohó): a kiterjesztés a $W$ értéke szerint halad: a diagram a 4. kiterjesztés után a megoldásig még 6 lépést jelöl;
- $f = g + W$ és $f = g + P$ ($A$ illetve $A^*$/$A^c$ jellegű keresés): a $g+P$ keresés az útvonal mentén 5 értéket tart (konstans $f$ az optimális úton), és kevesebb csúcsot terjeszt ki (5 kiterjesztés a $g+W$ 6 kiterjesztésével szemben).

Ez a dia alapján látható összehasonlítás: a pontosabb (nagyobb, de még megengedhető) $h$ szűkebb keresőgráfot eredményez. A $P$ definíciója a diákon nem szerepel kimondva; a Manhattan-távolság-összeg az ábrán látható értékekből ($P(start)=5$) következik.

## Kapocs

- [[concepts/mesint/heurisztika]] — a heurisztika általános fogalma a tárgyban
- [[concepts/mesint/tologato-jatek]] — a 8-kirakó mint heurisztika-példa
- [[concepts/mesint/nevezetes-grafkereso-algoritmusok]] — melyik algoritmus melyik tulajdonságot igényli
- [[concepts/mesint/a-csillag-algoritmus]] — a megengedhetőség szerepe az optimalitásban
- [[concepts/mesint/heurisztika-szerepe-a-grafkeresesben]] — a heurisztika hatása a keresésre
- [[subjects/mesint]] — tárgyi hub
