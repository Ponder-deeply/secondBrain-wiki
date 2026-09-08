---
tags: [concept]
sources: [2.-lingram-és-regexp.md]
derivation: source
updated: 2026-04-08
---

# Reguláris (3-as típusú) grammatikák normálformája

Minden reguláris nyelv generálható olyan grammatikával, amelynek szabályai kizárólag $X \to aY$ vagy $X \to \varepsilon$ alakúak; ez az ún. normálalak, amelyből reguláris kifejezések és véges automaták könnyen felépíthetők.

## Tartalom

### A normálalak

> **Tétel:** Minden 3-as típusú grammatika ekvivalens egy olyan grammatikával, amelynek szabályai vagy $X \to aY$ ($X, Y \in N$, $a \in T$) vagy $X \to \varepsilon$ ($X \in N$) alakúak.

### Átalakítási lépések

#### 1. lépés: Hosszredukció

- $A \to uB$ ($|u| > 1$): $A \to a_1 Z_1, Z_1 \to a_2 Z_2, \ldots, Z_{n-1} \to a_n B$ — új $Z_i$ nemterminálisok.
- $A \to u$ ($|u| \geq 1$): hasonlóan, az utolsó tag $\ldots \to a_m E, E \to \varepsilon$.

#### 2. lépés: Láncmentesítés

Az $X \to Y$ alakú (**lánc-**) szabályokat eliminálni kell. Jelölje $R_0$ az összes láncszabályt.

**A $H(A)$ halmazok iteratív kiszámítása** (minden $A \in N$-re):

$$H_0(A) := \{A\}$$
$$H_{i+1}(A) := H_i(A) \cup \{B \in N \mid \exists C \in H_i(A) : C \to B \in R\}$$

Mivel $H_0(A) \subseteq H_1(A) \subseteq \cdots \subseteq N$ és $N$ véges, a sorozat véges sok lépésen belül stabilizálódik. Legyen:

$$k := \min\{i \geq 0 \mid H_i(A) = H_{i+1}(A)\}, \quad H(A) := H_k(A)$$

Így $H(A) = \{B \in N \mid A \Rightarrow^* B\}$ (az $A$-ból láncszabályokkal elérhető nemterminálisok).

Az ekvivalens, láncmentes $R'$:

$$R' := \{A \to w \mid \exists B \in H(A) : B \to w \in R \setminus R_0\}$$

Azaz: $A$ örökli azon $B$ lánckövető minden nem-lánc szabályát, amelyet $A$-ból láncút vezet $B$-be.

**Ellenőrző példa:**

Kiindulási grammatika: $S \to abS \mid B$, $B \to bB \mid V$, $V \to aa \mid b$.

Hosszredukció után a szabályrendszer: $S \to aZ_1$, $Z_1 \to bS$, $S \to B$, $B \to bB$, $B \to V$, $V \to aZ_2$, $Z_2 \to aE$, $E \to \varepsilon$, $V \to bE$.

A $H$ halmazok kiszámítása:
- $H(V) = \{V\}$, $H(Z_1) = \{Z_1\}$, $H(Z_2) = \{Z_2\}$, $H(E) = \{E\}$
- $H(B)$: $H_0 = \{B\}$, $H_1 = \{B, V\}$ (mert $B \to V \in R$), $H_2 = \{B, V\}$ — kész. $H(B) = \{B, V\}$
- $H(S)$: $H_0 = \{S\}$, $H_1 = \{S, B\}$ (mert $S \to B \in R$), $H_2 = \{S, B, V\}$, $H_3 = \{S, B, V\}$ — kész. $H(S) = \{S, B, V\}$

Láncmentesítés végeredménye:

$$S \to aZ_1,\ Z_1 \to bS,\ S \to bB,\ S \to aZ_2,\ S \to bE$$
$$B \to bB,\ B \to aZ_2,\ B \to bE$$
$$V \to aZ_2,\ Z_2 \to aE,\ V \to bE,\ E \to \varepsilon$$

## Kapocs

- [[concepts/bvszam/linearis-grammatika]] — jobb- és bal-lineáris grammatikák
- [[concepts/bvszam/chomsky-hierarchia]] — a 3-as típus helye
- [[concepts/bvszam/vda]] — ebből a normálalakból könnyen épül automata
- [[concepts/bvszam/regularis-kifejezesek]] — a másik leíróeszköz
