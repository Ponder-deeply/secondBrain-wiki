---
tags: [concept]
sources: [6.-veremauto-és-környezetfüggetlen-nyelv.md]
derivation: source
updated: 2026-04-08
---

# Környezetfüggő nyelvek

Az 1-es típusú (környezetfüggő, KF-ő) grammatikák szabályai $u_1 A u_2 \to u_1 v u_2$ alakúak; ekvivalensek a hossz-nemcsökkentő grammatikákkal, és $\mathcal{L}_2 \subsetneq \mathcal{L}_1$.

## Tartalom

### Hossz-nemcsökkentő grammatika

> **Definíció:** A $G = \langle N, T, P, S \rangle$ grammatika **hossz-nemcsökkentő**, ha minden szabályára $|u| \leq |v|$ (kivéve az $S \to \varepsilon$ szabályt, ha $S$ nem szerepel más szabály jobboldalán).

> **Tétel:** Minden hossz-nemcsökkentő grammatika KF-ő nyelvet generál, és viszont (minden KF-ő grammatika átalakítható hossz-nemcsökkentővé).

### Átalakítás 1-es típusú grammatikává

1. **Álterminálisok bevezetése** (terminálisok csak $A \to a$ alakban).
2. Minden $X_1 X_2 \cdots X_n \to Y_1 Y_2 \cdots Y_m$ ($m \geq n$) hossz-nemcsökkentő szabályt új $Z_1, \ldots, Z_n$ nemterminálisokkal az alábbi 1-es típusú (kontextuális) szabálysorozattal szimulálunk:

```
X₁X₂⋯Xₙ      → Z₁X₂⋯Xₙ
Z₁X₂⋯Xₙ      → Z₁Z₂X₃⋯Xₙ
⋮
Z₁⋯Zₙ₋₁Xₙ   → Z₁⋯ZₙYₙ₊₁⋯Yₘ
Z₁⋯ZₙYₙ₊₁⋯Yₘ → Y₁Z₂⋯ZₙYₙ₊₁⋯Yₘ
⋮
Y₁⋯Yₙ₋₁ZₙYₙ₊₁⋯Yₘ → Y₁Y₂⋯Yₘ
```

Minden egyes szabály itt egy-egy nemterminálison cserél (a bal oldalon levő kontextus megőrzi, hogy a csere a helyes pozícióban történik).

### $\mathcal{L}_2 \subsetneq \mathcal{L}_1$

- $\{a^n b^n c^n \mid n \in \mathbb{N}\} \notin \mathcal{L}_2$ (Bar-Hillel lemma)
- $\{a^n b^n c^n\} \in \mathcal{L}_1$: generálja a $P = \{S \to abc, S \to aAbc, Ab \to bA, Ac \to Bbcc, bB \to Bb, aB \to aaA, aB \to aa\}$ grammatika.

### Szóprobléma eldönthetősége

> **Állítás:** Eldönthető, hogy $u \in L(G)$ egy hossz-nemcsökkentő grammatikánál.

Mivel a grammatika hossz-nemcsökkentő, a levezetések nem tartalmaznak $|u|$-nál hosszabb mondatformát. A legfeljebb $r = \sum_{i=1}^{|u|} |N \cup T|^i$ hosszú levezetések algoritmikusan felsorolhatók.

## Kapocs

- [[concepts/bvszam/chomsky-hierarchia]] — a négy szint, $\mathcal{L}_1$ helye
- [[concepts/bvszam/kuroda-normalforma]] — KF-ő grammatikák normálalakja
- [[concepts/bvszam/bar-hillel-lemma]] — $\{a^n b^n c^n\} \notin \mathcal{L}_2$
- [[concepts/bvszam/kornyezetfuggetlen-grammatika]] — az alattuk lévő szint
