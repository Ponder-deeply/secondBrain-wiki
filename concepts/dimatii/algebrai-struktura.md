---
tags: [concept]
sources: [DimatIIEa03.pdf, DimatIIEa04.pdf]
derivation: source
updated: 2026-09-08
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

### Helye a hierarchiában

A grupoidra rárakott további feltételek adják a szokásos struktúrákat: asszociativitás $\Rightarrow$ félcsoport, egységelem $\Rightarrow$ monoid, inverzek $\Rightarrow$ csoport. Két művelet esetén a disztributivitás vezet a gyűrű, majd a test fogalmához.

## Kapocs

- [[concepts/dimatii/muvelet]] — a struktúrát alkotó műveletek fogalma
- [[concepts/dimatii/felcsoport-es-monoid]] — asszociatív, illetve egységelemes grupoid
- [[concepts/dimatii/csoport]] — a grupoidok legerősebb egyműveletes esete
- [[concepts/dimatii/gyuru]] — kétműveletes struktúra disztributivitással
- [[concepts/dimatii/muvelettarto-lekepezes]] — struktúrák összehasonlításának eszköze
