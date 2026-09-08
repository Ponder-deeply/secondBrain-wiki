---
tags: [concept]
sources: [6.-veremauto-és-környezetfüggetlen-nyelv.md]
derivation: source
updated: 2026-09-04
---

# Veremautomata ↔ KF grammatika ekvivalencia

A nemdeterminisztikus veremautomata pontosan a környezetfüggetlen (2-es típusú) nyelveket ismeri fel; a determinisztikus veremautomata ereje kisebb, mint a nemdeterminisztikusé, de nagyobb, mint a véges automatáké.

## Tartalom

### Ekvivalencia tétel

> **Tétel:** Bármely $L$ nyelvre az alábbi állítások ekvivalensek:
> 1. $L$ **környezetfüggetlen** (2-es típusú grammatikával generálható).
> 2. $L$ **nemdeterminisztikus veremautomatával végállapottal** felismerhető.
> 3. $L$ **nemdeterminisztikus veremautomatával üres veremmel** felismerhető.

### KF grammatika → veremautomata

Legyen $G = \langle N, T, P, S \rangle$ CNF grammatika. Konstruálunk $A$ veremautomatát, amelynek $M_\delta$ szabályrendszere lényegében $G$ invertált szabályait tartalmazza:

- $z_0 q_0 \to z_0 q_S$ (ha $S \to \varepsilon \in P$)
- $z_0 q_0 a \to z_0 q_X$ (ha $X \to a \in P$)
- $Z q_Y a \to Z Y q_X$ ($\forall Z$, ha $X \to a \in P$)
- $Z q_Y \to q_X$ (ha $X \to ZY \in P$)
- $z_0 q_S \to q_h$ (befejezés)

A $w$ szó jobboldali levezetése $G$-ben megfelel $A$ redukcióinak.

### Veremautomata → KF grammatika

Legyen $A$ nemdeterminisztikus veremautomata. Konstruálunk $G$ KF grammatikát, amelynek nemterminálisai $[q, x, p]$ alakú hármasok ($q, p \in Q$, $x \in Z$):

- $S \to [q_0, z_0, p]$ minden $p \in Q$-ra.
- Ha $xqa \to y_1 \cdots y_m p_m \in M_\delta$: $[q, x, p_0] \to a\, [p_m, y_m, p_{m-1}] \cdots [p_1, y_1, p_0]$ minden $p_0, \ldots, p_{m-1} \in Q$-ra.
- Ha $m = 0$: $[q, x, p_0] \to a$.

Ezzel $L(G) = N(A)$.

### Determinisztikus vs. nemdeterminisztikus

- Létezik KF nyelv (pl. $\{ww^{-1} \mid w \in \{a,b\}^+\}$), amely **nem ismerhető fel determinisztikus** veremautomatával.
- A determinisztikus veremautomaták ereje: $\mathcal{L}_3 \subsetneq \text{DVA-k} \subsetneq \mathcal{L}_2$.

## Kapocs

- [[concepts/bvszam/veremautomata]] — a veremautomata definíciója
- [[concepts/bvszam/verem-elfogadas]] — kétféle elfogadási mód ekvivalenciája
- [[concepts/bvszam/kornyezetfuggetlen-grammatika]] — KF grammatika alapja
- [[concepts/bvszam/chomsky-normalforma]] — a CNF-alak szükséges a konstrukcióhoz
- [[concepts/bvszam/l0-re-ekvivalencia]] — ugyanez az automata–grammatika ekvivalencia a hierarchia felső szintjén
