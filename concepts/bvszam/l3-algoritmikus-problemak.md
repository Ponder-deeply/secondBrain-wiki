---
tags: [concept]
sources: [4.-myhill-nerode-és-minimál-automata.md]
derivation: source
updated: 2026-06-09
---

# $\mathcal{L}_3$ algoritmikus problémák

A reguláris nyelvek osztályán minden fontos eldöntési probléma (üresség, egyenlőség, tartalmazás, szóprobléma) megoldható, és a szóprobléma lineáris időben is elvégezhető.

## Tartalom

### Eldönthető problémák

| Probléma | Megoldás |
|---|---|
| $L(G) = \emptyset$? | VDA-ba konvertálás; végállapot elérhető-e? |
| $L_1 \cap L_2 = \emptyset$? | $L_1 \cap L_2 \in \mathcal{L}_3$, üresség eldönthető |
| $L_1 = L_2$? | $L_1 \triangle L_2 = \emptyset$ (szimmetrikus differencia reguláris) |
| $L_1 \subseteq L_2$? | $L_1 \setminus L_2 = \emptyset$ ($= L_1 \cap \bar{L}_2$, reguláris) |
| $u \in L(G)$? | Lineáris algoritmus (ld. alább) |

### Szóprobléma — lineáris algoritmus

Legyen $G = \langle N, T, P, S \rangle$ normálformájú reguláris grammatika, $u = t_1 \cdots t_n$.

$$H_0 = \{S\}, \quad H_{i+1} = \{A \in N \mid \exists B \in H_i : B \to t_{i+1} A \in P\}$$

$$u \in L(G) \iff H_n \cap F \neq \emptyset, \quad F = \{A \mid A \to \varepsilon \in P\}$$

Ez lényegében a grammatikából épített VNDA determinizáltja $\mathcal{P}(N)$ állapothalmazzal. Futásidő: $O(n \cdot |G|)$.

## Kapocs

- [[concepts/bvszam/myhill-nerode]] — minimális automata, összefüggő, redukált automaták
- [[concepts/bvszam/vda]] — VDA mint algoritmikus eszköz
- [[concepts/bvszam/zartsagi-tulajdonsagok]] — komplementer, metszet, különbség
