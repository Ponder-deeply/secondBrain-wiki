---
tags: [concept, dimatii/algebrai-strukturak]
sources: [DimatIIEa04.pdf]
derivation: source
updated: 2026-09-08
---

# Csoport és Abel-csoport

Olyan egységelemes félcsoport, amelyben minden elemnek van inverze; ha a művelet ráadásul kommutatív, Abel-csoportról beszélünk.

## Tartalom

### Elem inverze

Legyen $(G; *)$ egységelemes félcsoport $e$ egységelemmel. A $g \in G$ elem **inverze** az a $g^{-1} \in G$ elem, amelyre

$$g * g^{-1} = g^{-1} * g = e.$$

Egy elemnek nem feltétlenül létezik inverze, de ha létezik, akkor **egyértelmű** — a bizonyításhoz a művelet asszociativitása kell.

### Csoport

Ha egy $(G; *)$ egységelemes félcsoportban minden $g \in G$ elemnek létezik inverze, akkor $(G; *)$ **csoport**.

### Abel-csoport

Ha egy $(G; *)$ csoportban a $*$ csoportművelet **kommutatív**, akkor $(G; *)$ **Abel-csoport**.

$\mathbb{Z}$ a legszűkebb olyan (Abel-)csoport, amely tartalmazza $\mathbb{N}$-et; $\mathbb{Z}$ meg is konstruálható $\mathbb{N}$-ből: az $(r, s) \sim (p, q)$ reláció, ha $r + q = p + s$, ekvivalenciareláció, és az osztályai épp az egész számok.

### Példák

- $(\mathbb{Q}; +)$ Abel-csoport $0$ egységelemmel.
- $(\mathbb{Q}^*; \cdot)$ Abel-csoport $1$ egységelemmel, ahol $\mathbb{Q}^* = \mathbb{Q} \setminus \{0\}$.
- $(\mathbb{Z}_m; +)$ Abel-csoport $\overline{0}$ egységelemmel.
- $(\mathbb{Z}_p^*; \cdot)$ Abel-csoport $\overline{1}$ egységelemmel ($p$ prím).
- $\{M \in \mathbb{C}^{k \times k} : \det M \ne 0\}$ a mátrixszorzással csoport az egységmátrixszal mint egységelemmel, de $k > 1$ esetén **nem** Abel.
- Az $X \to X$ bijektív függvények a kompozícióval csoportot alkotnak, egységeleme az $\mathrm{id}_X : x \mapsto x$ identikus leképezés.

A $(\mathbb{Z}_p^*; \cdot)$ csoport ciklikus is: a benne található generátor a [[concepts/dimatii/primitiv-gyok]] lapon szerepel.

## Kapocs

- [[concepts/dimatii/felcsoport-es-monoid]] — a kiindulási struktúra, amelyhez az inverzek hozzáadódnak
- [[concepts/dimatii/algebrai-struktura]] — a fogalmi keret
- [[concepts/dimatii/gyuru]] — a gyűrű additív része definíció szerint Abel-csoport
- [[concepts/dimatii/test]] — a nemnulla elemek a szorzásra csoportot alkotnak
- [[concepts/dimatii/primitiv-gyok]] — $\mathbb{Z}_p^*$ ciklikussága
