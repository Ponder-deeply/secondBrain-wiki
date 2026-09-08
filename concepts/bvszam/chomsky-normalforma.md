---
tags: [concept]
sources: ["5.-környezetfüggetlen-gramm,-cnf,-cyk-pumpálási-lemma.md"]
derivation: source
updated: 2026-04-08
---

# Chomsky normálforma (CNF)

A Chomsky normálforma a KF grammatikák standardizált alakja, ahol minden szabály $A \to BC$ vagy $A \to a$ alakú (esetleg $S \to \varepsilon$); belőle egyszerűen elvégezhetők a levezetési fa és a CYK algoritmus.

## Tartalom

### Definíció

Egy $G = \langle N, T, P, S \rangle$ grammatika **Chomsky normálformájú (CNF)**, ha minden szabálya:
- $S \to \varepsilon$ (és ekkor $S$ nem szerepel más szabály jobboldalán), vagy
- $A \to BC$ ($A, B, C \in N$; $B, C \neq S$ ha $S \to \varepsilon \in P$), vagy
- $A \to a$ ($A \in N$, $a \in T$).

### Átalakítás CNF-re (4 lépés)

#### 1. Álterminálisok bevezetése
Minden $a \in T$ terminálishoz $\bar{a}$ új nemterminális; minden $A \to \cdots a \cdots$ szabályban (ahol a jobb oldal hossza $\geq 2$) $a$-t $\bar{a}$-ra cseréljük, és hozzávesszük az $\bar{a} \to a$ szabályt.

#### 2. Hosszredukció
$X \to Y_1 Y_2 \cdots Y_k$ ($k \geq 3$) helyett:
$$X \to Y_1 Z_1, \quad Z_1 \to Y_2 Z_2, \quad \ldots, \quad Z_{k-2} \to Y_{k-1} Y_k$$
új $Z_i$ nemterminálisokkal.

#### 3. ε-mentesítés
Meghatározzuk az **ε-generáló** nemterminálisokat:
$$U_1 = \{X \mid X \to \varepsilon \in P\}, \quad U_{i+1} = U_i \cup \{X \mid X \to u \in P, u \in U_i^*\}$$

Az $\varepsilon$-szabályokat törölve, de azok hatását minden $A \to BC$ szabálynál szimulálva (ha $B \in U$: adjuk hozzá $A \to C$-t; ha $C \in U$: adjuk hozzá $A \to B$-t; stb.).

Ha $S \in U$: új $S'$ kezdőszimbólum, $S' \to S \mid \varepsilon$.

#### 4. Láncmentesítés
Az $X \to Y$ (**lánc-**) szabályok eliminálása az $H(A)$ elérhető nemterminálisok halmazával:
$$P_1 = \{A \to w \mid \exists B \in H(A) : B \to w \in P\} \setminus \{X \to Y \mid X,Y \in N\}$$

### Teljes kidolgozott példa

**Eredeti grammatika:**
```
S → AB
A → aAa | C
B → bBb | C
C → Cabc | b | ε
```

**1. lépés — Álterminálisok** ($D \to a$, $E \to b$, $F \to c$):
```
S → AB
A → DAD | C
B → EBE | C
C → CDEF | b | ε
```

**2. lépés — Hosszredukció** (új $Z_1, Z_2, Z_3, Z_4$):
```
A → DZ₁        Z₁ → AD
B → EZ₂        Z₂ → BE
C → CZ₃        Z₃ → DZ₄,   Z₄ → EF
```

**3. lépés — ε-mentesítés:**

$U_0 = \{C\}$, $U_1 = \{C, A, B\}$ ($A \to C$, $B \to C$), $U_2 = U_3 = \{S, A, B, C\}$.

Az $\varepsilon$-szabályok törlése után az opcionális komponenseket minden érintett szabályban szimulálni kell. Mivel $S \in U$ de $S$ nem szerepel más szabály jobboldalán, elegendő $S \to \varepsilon$ megtartása (nem kell új kezdőszimbólum).

Például $S \to AB$-ből (mivel $A, B \in U$) keletkeznek: $S \to AB \mid A \mid B \mid \varepsilon$.

**4. lépés — Láncmentesítés:**

$H(S) = \{S, A, B, C, Z_3\}$, $H(A) = \{A, C, Z_3\}$, $H(B) = \{B, C, Z_3\}$, $H(C) = \{C, Z_3\}$, $H(Z_1) = \{Z_1, D\}$, $H(Z_2) = \{Z_2, E\}$.

**Végeredmény (CNF):**
```
S → AB | DZ₁ | CZ₃ | b | DZ₄ | EZ₂ | ε
A → DZ₁ | CZ₃ | b | DZ₄
B → EZ₂ | CZ₃ | b | DZ₄
C → CZ₃ | b | DZ₄
D → a,  E → b,  F → c
Z₁ → AD | a
Z₂ → BE | b
Z₃ → DZ₄
Z₄ → EF
```

### Levezetési fa CNF-ben

CNF grammatikánál a levezetési fa **bináris fa** (minden belső csúcsnak pontosan 2 gyereke van, kivéve az $A \to a$ leveleket). Az $n$ betűből álló szó levezetési fájában pontosan $2n-1$ belső csúcs van.

## Kapocs

- [[concepts/bvszam/kornyezetfuggetlen-grammatika]] — KF grammatika alapfogalmai
- [[concepts/bvszam/levezetes-fa]] — levezetési fa, egyértelmű grammatika
- [[concepts/bvszam/cyk-algoritmus]] — a CNF-en alapuló $O(n^3)$ algoritmus
- [[concepts/bvszam/bar-hillel-lemma]] — a pumpálási lemma CNF-et igényel
