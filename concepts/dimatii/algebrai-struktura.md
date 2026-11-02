---
tags: [concept]
sources: [DimatIIEa03.pdf, DimatIIEa04.pdf, Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf, dm2gy06_2020_Algebra.pdf]
derivation: source
kind: definition
element: air
updated: 2026-10-21
---

# Algebrai struktúra és grupoid

Egy halmaz a rajta értelmezett műveletekkel együtt; ha a műveletek halmaza egyetlen bináris műveletből áll, grupoidról beszélünk. Ez a struktúrahierarchia legalsó szintje.

## Tartalom

### Algebrai struktúra

A $(H; M)$ pár **algebrai struktúra**, ha $H$ egy halmaz, $M$ pedig $H$-n értelmezett műveletek halmaza. A $(H; \{*, +, \circ\})$ jelölés helyett a $(H; *, +, \circ)$ írásmódot is használhatjuk.

### Grupoid

Ha az $M$ művelethalmaz **egyetlen** műveletet tartalmaz, és ez egy **bináris** művelet, akkor a $(H; M)$ struktúrát **grupoidnak** nevezzük.

### Példák

- $(\mathbb{N}; +)$ algebrai struktúra, mert természetes számok összege természetes szám, és grupoid is.
- $(\mathbb{N}; -)$ **nem** algebrai struktúra, mert például $0 - 1 = -1 \notin \mathbb{N}$ — a kivonás nem művelet $\mathbb{N}$-en.
- $(\mathbb{Z}; +, \cdot)$ algebrai struktúra, mert egész számok összege és szorzata is egész szám, de **nem** grupoid, mert két művelete van.
- $(\mathbb{Z}_m; +, \cdot)$ algebrai struktúra, de szintén nem grupoid, mert két művelet szerepel benne.

### Típus

Ha $\Omega$ a $n_0, n_1, \dots$ változós műveletek halmaza (nullér, unér, ...), akkor $(n_0, n_1, \dots)$ az $(A, \Omega)$ struktúra **típusa**; $A$ a **tartóhalmaz** (alapháza). A $(0,0,1,0,\dots)$ vagyis egyetlen bináris műveletes típus a grupoid, a $(0,0,2,0,\dots)$ típusúak (két bináris művelet) például a gyűrűk.

### Helye a hierarchiában

A grupoidra rárakott további feltételek adják a szokásos struktúrákat: asszociativitás $\Rightarrow$ félcsoport, egységelem $\Rightarrow$ monoid, inverzek $\Rightarrow$ csoport. Két művelet esetén a disztributivitás vezet a gyűrű, majd a test fogalmához.

### Feladattípusok és módszerek: melyik struktúra? (gyakorlati feladatsor, 2020 ősz, 6. sor)

A „milyen struktúra ez?” típusú feladatokat egy létrán kell végigmenni, és mindig az első elbukó lépést kell megnevezni:

1. **művelet** (mindenütt értelmezett, nem vezet ki) — [[concepts/dimatii/muvelet]]
2. **félcsoport** (asszociatív) → **monoid** (egységelem) → **csoport** (inverz) — [[concepts/dimatii/felcsoport-es-monoid]], [[concepts/dimatii/csoport]]
3. két műveletnél: **gyűrű** ($(R,+)$ Abel-csoport, $(R,\cdot)$ félcsoport, disztributivitás) → egységelemes / kommutatív → **nullosztómentes** → **integritási tartomány** → **test** (minden nemnulla elem invertálható) — [[concepts/dimatii/gyuru]], [[concepts/dimatii/test]]

## Kapocs

- [[concepts/dimatii/muvelet]] — a struktúrát alkotó műveletek fogalma
- [[concepts/dimatii/felcsoport-es-monoid]] — asszociatív, illetve egységelemes grupoid
- [[concepts/dimatii/csoport]] — a grupoidok legerősebb egyműveletes esete
- [[concepts/dimatii/gyuru]] — kétműveletes struktúra disztributivitással
- [[concepts/dimatii/homomorfizmus-es-izomorfizmus]] — struktúrák izomorfiája
- [[concepts/dimatii/muvelettarto-lekepezes]] — struktúrák összehasonlításának eszköze
