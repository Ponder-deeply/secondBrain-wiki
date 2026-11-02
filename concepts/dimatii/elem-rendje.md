---
tags: [concept]
sources: [Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf]
derivation: source
kind: definition
element: air
updated: 2026-10-21
---

# Csoport és elem rendje

A csoport rendje az elemszáma; egy elem rendje a legkisebb pozitív kitevő, amelyre a hatványa az egységelem.

## Tartalom

### Definíció

- A **csoport rendje** a csoport elemeiből álló halmaz számossága; jele $|G|$ vagy $O(G)$.
- A $g \in G$ **elem rendje** a legkisebb pozitív egész $n$, amelyre $g^n = e$; ha nincs ilyen $n$, akkor $\infty$.

### Példák

1. Az $(\mathbb{R}^*, \cdot)$ csoportban $+1$ és $-1$ végesrendű elemek ($1$ rendje 1, $-1$ rendje 2), a többi végtelen rendű.
2. A Prüfer-csoport ($Z(p^\infty)$: az összes $p^n$-edik egységgyök, $p$ rögzített prím, a művelet a szorzás): minden elem végesrendű, maga a csoport végtelen rendű.

Kapcsolat a ciklikus csoporttal: a véges rendű $g$ által generált csoport $n$ elemű, ahol $n$ a $g$ rendje, lásd [[concepts/dimatii/ciklikus-csoport]].

## Kapocs

- [[concepts/dimatii/ciklikus-csoport]] — $\langle g\rangle$ elemszáma $g$ rendje
- [[concepts/dimatii/reszcsoport]] — generátum
- [[concepts/dimatii/csoport]] — az alapfogalom
- [[concepts/dimatii/komplex-egysegiyokok-hatvanyai]] — egységgyökök mint példák
