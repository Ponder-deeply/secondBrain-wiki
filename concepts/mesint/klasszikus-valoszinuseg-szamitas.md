---
tags: [concept]
sources: [10.bizonytalansag.pdf]
derivation: source
kind: definition
element: fire
updated: 2026-10-12
---

# Klasszikus valószínűségszámítás

A bizonytalan $B \to A$ szabály erősségét a feltételes valószínűséggel mérjük: mi az $A$ esemény bekövetkezésének valószínűsége, amikor $B$ bekövetkezik.

## Tartalom

### Feltételes valószínűség

$$p(A \mid B) = \frac{p(A \wedge B)}{p(B)}, \quad \text{ha } p(B) > 0$$

### Állítás = esemény

Az állítások mindig egy esemény bekövetkezéséről szólnak, ezért (diszkrét) valószínűségi változókkal fogalmazzuk meg őket: $X_i = x_i$, ahol $X_i$ a diszkrét valószínűségi változó, $x_i$ az értéke. Ha $X_i$ csak *igaz* vagy *hamis* lehet, akkor $X_i = igaz$ helyett $X_i$, $X_i = hamis$ helyett $\neg X_i$ jelölést használunk.

### Az együttes eloszlás problémája

Egy problémakör összes feltételes valószínűsége az események **együttes valószínűségi eloszlásából** könnyen kiszámolható. A gyakorlatban viszont az együttes eloszlás többnyire nem ismert explicit módon, és túl sok apriori adat tárolását igényelné (a memóriaigény exponenciálisan nő az elemi események számával). Ezért a feltételes valószínűség közvetlen kiszámításához különféle elkerülő technikákat alkalmazunk: [[concepts/mesint/bayes-tetel]], [[concepts/mesint/felteteles-fuggetlenseg]], normalizálás.

### Normalizálás

Ha egy esemény és ellentettje valószínűsége ugyanazzal az ismeretlen együtthatóval számolható:

$$p(A) = \alpha \cdot u, \qquad p(\neg A) = \alpha \cdot v,$$

akkor $1 = p(A) + p(\neg A) = \alpha\,[u+v]$, azaz $\alpha = 1/[u+v]$. Így a nevezőbeli (nehezen ismert) valószínűséget nem kell kiszámolni.

### A Bayes-féle modell értékelése

- Az apriori valószínűségekhez nehéz hozzájutni, és sokat kell tárolni.
- A következtetés ötletszerű, nehéz algoritmizálni.
- Matematikailag megalapozott, de számításigényes és magyarázatadásra nem alkalmas.
- Új ismeretekkel nehezen bővíthető: az új esemény mellett a korábbi valószínűségi értékeket is felül kell bírálni.

Ezek a hiányosságok motiválják a [[concepts/mesint/bayes-halo]] használatát.

## Kapocs

- [[concepts/mesint/bizonytalansagkezeles]] — az általános keret
- [[concepts/mesint/bayes-tetel]] — a feltételes valószínűség megfordítása
- [[concepts/mesint/felteteles-fuggetlenseg]] — az együttes eloszlás egyszerűsítése
- [[concepts/mesint/bayes-halo]] — a tömör reprezentáció
