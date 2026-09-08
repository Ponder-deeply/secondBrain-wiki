---
tags: [concept]
sources: [01_ea_an_ii_a_b_merged.pdf]
references: ["An II A/B 3. előadás"]
derivation: source
updated: 2026-09-04
---

# Inflexiós pont

Az inflexiós pont az a hely, ahol a függvény konvexitásának iránya megváltozik — azaz ahol a görbe „átfordul" konvexből konkávba vagy fordítva.

## Definíció

**Definíció.** Legyen $I$ nyílt intervallum, és t.f.h. $f \in D(I)$. Azt mondjuk, hogy a $c \in I$ pont az $f$ függvénynek **inflexiós pontja**, ha

$$\exists\,\delta > 0 : f \text{ konvex } (c-\delta, c]\text{-n és konkáv } [c, c+\delta)\text{-n,}$$

vagy fordítva.

**Példa.** Az $x^3$ ($x \in \mathbb{R}$) és a $-x^3$ ($x \in \mathbb{R}$) függvénynek a $c = 0$ pont inflexiós pontja.

## Szükséges és elégséges feltétel

**Tétel.** Legyen $I$ nyílt intervallum, és t.f.h. $f \in D^2(I)$. Annak, hogy $c \in I$-ben $f$-nek inflexiós pontja legyen:

1. **szükséges feltétele**, hogy $f''(c) = 0$ teljesüljön;
2. **elégséges feltétele**, hogy $f''$ előjelet váltva legyen $0$ a $c$ pontban.

**Megjegyzés.** A feltételek aszimmetriája ugyanolyan jellegű, mint a szélsőérték-keresésnél: az $f''(c) = 0$ szükséges, de nem elégséges (pl. $f(x) = x^4$-nek $c = 0$-ban $f''(0) = 0$, de nincs inflexiós pontja). Az $f''$ előjelváltása elégséges, de nem szükséges.

## Kapcsolat a konvexitással

Az inflexiós pont pontosan azokat a helyeket azonosítja, ahol a [[concepts/analii/konvex-konkav-fuggvenyek|konvexitás]] iránya megfordul. A [[concepts/analii/monotonitas|monotonitás]] és a derivált kapcsolatának analógiájára:

- ahol $f'' > 0$: $f$ (szigorúan) konvex,
- ahol $f'' < 0$: $f$ (szigorúan) konkáv,
- ahol $f''$ előjelet vált: inflexiós pont.

## Kapocs

- [[concepts/analii/konvex-konkav-fuggvenyek]] — a konvexitás/konkávitás definíciója és $f''$-vel való kapcsolata
- [[concepts/analii/lokalis-szelsertekek]] — analóg feltételrendszer szélsőértékekre ($f'$ előjelváltása)
- [[concepts/analii/magasabb-rendu-derivaltak]] — $f''$ mint a konvexitásvizsgálat fő eszköze
- [[concepts/analii/teljes-fuggvenyvizsgalat]] — inflexiós pontok keresése a szisztematikus vizsgálat része
