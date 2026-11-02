---
tags: [concept]
sources: [02.modellek.pdf]
derivation: source
kind: model
element: earth
updated: 2026-10-12
---

# Tologató játék (8-as, 15-ös)

A tologató játék az [[concepts/mesint/allapotter-modell]] példája: számozott lapkákat tologatunk egy rács üres helye felé; az állapot a kirakó egy konfigurációja.

## Tartalom

- **Kezdőállapot**: tetszőleges. **Célállapot**: szokásos (rendezett) kirakás.
- **Állapottér** (8-as játék): $AT = rec(mátrix:\{0..8\}^{3\times3},\ üres:\{1..3\}\times\{1..3\})$.
- **Invariáns**: az állapot mátrixának sorfolytonos kiterítése a $0..8$ számok egy permutációja; az `üres` hely a $0$ elem mátrixbeli sor- és oszlopindexe.
- **Művelet**: `Tol(irány): AT → AT`.
  - HA $irány\in\{(0,-1),(-1,0),(0,1),(1,0)\}$ és $(1,1)\le this.üres+irány\le(3,3)$ (koordinátánkénti összeadás),
  - AKKOR `this.mátrix[this.üres] ↔ this.mátrix[this.üres+irány]` és `this.üres := this.üres + irány`.
- **Állapot-gráf**: a start és a cél között többféle út van; a gráfban körök vannak, a lépések visszafordíthatók (a műveletek inverzei is műveletek, ezért az élek kétirányúak).

## Kapocs

- [[concepts/mesint/allapotter-modell]] — az általános modell
- [[concepts/mesint/hanoi-tornyai]] — másik mintapélda
- [[concepts/mesint/n-kiralyno-problema]] — másik mintapélda
- [[concepts/mesint/visszafele-halado-keresesi-modell]] — a célból induló keresés (a következő téma)
