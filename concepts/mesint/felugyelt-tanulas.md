---
tags: [concept]
sources: [11.gepi_tanulas.pdf]
derivation: source
kind: definition
element: water
updated: 2026-10-12
---

# Felügyelt tanulás

Paraméteres tanulás: a $\varphi : X \to Y$ leképezést közelítő $f : P \times X \to Y$ függvény $\Theta$ paraméterét a tanító minták $(x_n, y_n)$ párjai alapján keressük úgy, hogy az átlagos hiba kicsi legyen.

## Tartalom

### Hibafüggvény és veszteség

Adottak az $(x_n, y_n)$, $n = 1..N$ tanító minták, ahol $y_n = \varphi(x_n)$. Olyan $\Theta \in P$-t keresünk, amelyre az

$$L(\Theta) = \frac{1}{N} \sum_{n=1}^{N} \ell\bigl(f(\Theta, x_n),\, y_n\bigr)$$

hiba elég kicsi (ettől reméljük, hogy $f(\Theta, x) \approx \varphi(x)$). Itt $t_n = f(\Theta, x_n)$ a *számított kimenet*, $y_n$ az *elvárt kimenet*, $\ell : Y \times Y \to \mathbb{R}$ a *hibafüggvény* ($Y$ $m$ dimenziós).

Példák $\ell(t_n, y_n)$-re:

- $\lVert t_n - y_n \rVert_1$,
- $\lVert t_n - y_n \rVert_2^2$,
- $-\sum_{j=1..m} y_{nj} \cdot \log t_{nj}$ (keresztentrópia).

### Megjegyzések

- Fontos, hogy $f(\Theta, x)$ **kiszámítása gyors** legyen; nem baj, ha a megfelelő $\Theta$ megtalálása lassú, mert ezt a tanító mintákkal előre számoljuk ki.
- A $\Theta$ megtanulása akkor működik jól, ha
  - $N$ elég nagy (de a mintákat drága összegyűjteni, a $\varphi(x_n)$-eket költséges kiszámolni),
  - $f$ és $\ell$ megfelelőek (tapasztalat, sok próbálkozás kell),
  - $\Theta$ közel esik a paraméter globális optimumához.
- $\Theta$ megtalálása **nem-konvex optimalizálási feladat**; a globális optimum megtalálása NP-teljes. Szerencsére ez nem is cél: túl mohó módszert kapnánk (**túltanulás**), amely a tanító mintákra tökéletes, egyébként nem.

### Példák a kurzusban

Nem-paraméteres jellegű: [[concepts/mesint/legkozelebbi-szomszed-modszer]]; szimbolikus modell: [[concepts/mesint/dontesi-fa-epitese]]; paraméteres, hibafüggvényt minimalizáló: neuronhálók ([[concepts/mesint/hiba-visszaterjesztes]]).

## Kapocs

- [[concepts/mesint/tanulas-fogalma-es-modelljei]] — a tanulási módok áttekintése
- [[concepts/mesint/legkozelebbi-szomszed-modszer]] — a $\Theta$ itt maguk a minták és $K$
- [[concepts/mesint/dontesi-fa-epitese]] — felügyelt tanulás döntési fával
- [[concepts/mesint/delta-szabaly]] — hibafüggvény minimalizálása neuronnál
- [[concepts/bigdata/gepi-tanulas-alapfogalmak]] — általános big data-s megközelítés
