---
tags: [concept]
sources: ["5.-környezetfüggetlen-gramm,-cnf,-cyk-pumpálási-lemma.md"]
derivation: source
updated: 2026-04-08
---

# CYK algoritmus

A Cocke–Younger–Kasami (CYK) algoritmus KF grammatika szóproblémáját oldja meg $O(n^3)$ lépésben (ahol $n$ a szó hossza), feltéve, hogy a grammatika Chomsky normálformában van.

## Tartalom

### Bemenet és kimenet

**Input:** $G = \langle T, N, P, S \rangle$ Chomsky normálformájú grammatika és $u = t_1 \cdots t_n \in T^*$.

**Output:** $u \in L(G)$?

### Az algoritmus

Dinamikus programozással: töltsük ki alulról felfelé az $n \times n$-es $H$ táblázatot.

$$H_{i,i} := \{A_k \mid \beta_k = t_i\}$$

$$H_{i,j} := \bigcup_{h=i}^{j-1} \{A_k \mid \beta_k \in H_{i,h} \cdot H_{h+1,j}\} \quad (i < j)$$

ahol $A_k \to \beta_k$ szabályokra: $A_k \in H_{i,j}$ azt jelenti, hogy $A_k \Rightarrow^* t_i \cdots t_j$.

**Eredmény:** $u \in L(G) \iff S \in H_{1,n}$.

### A tábla felépítése

```
H_{1,n}
H_{1,n-1}   H_{2,n}
    ...
H_{1,2}  H_{2,3}  ...  H_{n-1,n}
H_{1,1}  H_{2,2}  ...  H_{n,n}
  t_1      t_2    ...    t_n
```

### Helyesség

**Állítás:** $H_{i,j} = \{X \in N \mid X \Rightarrow^*_G t_i \cdots t_j\}$.

Bizonyítás $j-i$-re vonatkozó teljes indukcióval. Az indukciós lépésben: $X \Rightarrow YZ$ első lépéssel, majd $Y \Rightarrow^* t_i \cdots t_h$ és $Z \Rightarrow^* t_{h+1} \cdots t_j$ valamilyen $h$-ra.

### Kidolgozott példa

**Grammatika** (CNF, $S$ a kezdőszimbólum):
```
S → AB | BC
A → XA | a        X → a
B → UV | VW | XS  U → XX,  W → YY | XS,  V → ZZ,  Z → b
C → YC | c        Y → c
```

**Szó:** `aabbcc` ($n = 6$, tehát $t_1 \ldots t_6 = a, a, b, b, c, c$)

**Átlós cellák ($H_{i,i}$):**

| $i$ | $t_i$ | $H_{i,i}$ |
|---|---|---|
| 1 | $a$ | $\{A, X\}$ |
| 2 | $a$ | $\{A, X\}$ |
| 3 | $b$ | $\{Z\}$ |
| 4 | $b$ | $\{Z\}$ |
| 5 | $c$ | $\{Y, C\}$ |
| 6 | $c$ | $\{Y, C\}$ |

**Teljes tábla** (releváns cellák):

| $i \backslash j$ | 1 | 2 | 3 | 4 | 5 | 6 |
|---|---|---|---|---|---|---|
| **1** | {A,X} | {A,U} | {} | {} | {} | **{S}** |
| **2** | – | {A,X} | {} | {V} | {} | {S} |
| **3** | – | – | {Z} | {} | {} | {} |
| **4** | – | – | – | {Z} | {} | {} |
| **5** | – | – | – | – | {Y,C} | {C,W} |
| **6** | – | – | – | – | – | {Y,C} |

$S \in H_{1,6}$, tehát `aabbcc` $\in L(G)$.

Visszafejtett levezetés: $S \Rightarrow AB \Rightarrow XAB \Rightarrow XAVW \Rightarrow XAZZW \Rightarrow XAZZYY \Rightarrow^* aabbcc$.

### Hatékonyság

- Összesen $O(n^2)$ cella, mindegyik kiszámítása $O(n)$ lépés → **összesen $O(n^3)$**.
- Általános KF grammatikából CNF-re hozás $O(|G|^2)$, így az összhatékonyság $O(|G|^2 n^3)$.

## Kapocs

- [[concepts/bvszam/chomsky-normalforma]] — a CYK CNF-et igényel
- [[concepts/bvszam/kornyezetfuggetlen-grammatika]] — KF grammatika szóproblémája
- [[concepts/bvszam/levezetes-fa]] — a CYK implicit levezetési fát épít
