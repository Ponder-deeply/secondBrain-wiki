---
tags: [concept]
sources: [11.gepi_tanulas.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-10-12
---

# K legközelebbi szomszéd

Felügyelt tanulási módszer: egy $x \in X$ bemenethez a kimenetet a hozzá legközelebb eső $K$ tanító minta kimenetéből számoljuk (átlagolással vagy többségi szavazással).

## Tartalom

### Működés

Egy $x$ bemenethez annak a $K$ mintának az outputja alapján számolunk kimenetet, amely minták inputja a legközelebb esik $x$-hez. Osztályozásnál többségi szavazás, folytonos kimenetnél átlagolás.

Jelölés: $sort(x, P, K)$ a $P = \{x_n \mid n = 1..N\}$ tanító minták bemeneteiből képzett, az $x$-től vett távolság szerint növekvő sorozat első $K$ eleme.

- Átlagolás:
$$f(\Theta, x) = \sum_{n=1..N} \frac{\mathbb{I}(x_n \in sort(x, P, K))}{K} \cdot y_n$$
ahol $\mathbb{I}$ az indikátor: igaz állításra 1, különben 0.
- Többségi szavazás:
$$f(\Theta, x) = \arg\max_{n=1..N} \sum_{x_i \in sort(x,P,K),\ \varphi(x_i) = y_n} 1$$

A $\Theta$ paraméter a minták és a $K \in \mathbb{N}$ szám együttese. A legközelebbi szomszédokat az $\lVert x_n - x \rVert_2^2$ távolságok sorba rendezésével választjuk ki.

### Értékelés

- **Előny:** egyszerű leprogramozni, a „tanulás" gyors (csak tárolás).
- **Hátrány:** ha $N$ nagy, a tárolás költséges; az $f$ kiszámítása, azaz a minták sorba rendezése erőforrás-igényes.

Ez a felügyelt tanulás szempontjából fordított arány: a tanulás olcsó, a kiértékelés drága (lásd [[concepts/mesint/felugyelt-tanulas]], ahol a gyors $f$-számítás volt a kívánalom).

## Kapocs

- [[concepts/mesint/felugyelt-tanulas]] — az általános keret
- [[concepts/bigdata/k-legkozelebbi-szomszed]] — a big data-s tárgyalás ugyanerről a módszerről
- [[concepts/mesint/dontesi-fa-epitese]] — alternatív felügyelt módszer
