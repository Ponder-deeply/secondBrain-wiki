---
tags: [concept]
sources: [4.-myhill-nerode-és-minimál-automata.md]
derivation: source
updated: 2026-06-09
---

# Myhill–Nerode tétel és minimális automata

A Myhill–Nerode tétel karakterizálja a reguláris nyelveket a maradéknyelvek számossága alapján, és megadja a minimális (legkevesebb állapotú) véges determinisztikus automata elméleti alapját.

## Tartalom

### Maradéknyelvek

Az $L$ nyelv $p \in T^*$ szóra vonatkozó **maradéknyelve**:
$$L_p := \{v \mid pv \in L\}$$

Tulajdonságok: $(L_p)_q = L_{pq}$; $L_\varepsilon = L$; $\varepsilon \in L_p \iff p \in L$.

Az $A = \langle Q, T, \delta, q_0, F \rangle$ VDA $q$ állapotának maradéknyelve:
$$L(A, q) := \{v \mid \delta(q, v) \in F\}$$

Összefüggés: $L_u = L(A, \delta(q_0, u))$; az automata állapotai által generált maradéknyelvek lefedik a nyelv maradéknyelveit.

### Myhill–Nerode tétel

> **Tétel:** $L \in \mathcal{L}_3 \iff |\{L_p\}_{p \in T^*}| < \infty$

**$\Rightarrow$:** Ha $A$ véges automata felismeri $L$-t, akkor $\{L_u\} \subseteq \{L(A,q)\}$, ami véges.

**$\Leftarrow$:** A Myhill–Nerode automata:
$$A^{MN}_L = \langle \{L_p\}_{p \in T^*}, T, \delta, L_\varepsilon, F \rangle$$
ahol $\delta(L_p, t) = L_{pt}$ és $F = \{L_p \mid \varepsilon \in L_p\}$.

Ez a konstrukció helyes, véges (feltétel szerint) és elfogadja $L$-t.

### Minimális automata

> **Következmény:** $A^{MN}_L$ állapotszáma kisebb vagy egyenlő, mint bármely $L$-et felismerő VDA állapotszáma — tehát $A^{MN}_L$ az $L$ **minimális automatája**.

### Algoritmikus minimalizálás

Adott $A$ VDA minimális automatájának előállítása két lépésben:

**1. Összefüggővé alakítás:** elérhetetlen állapotok elhagyása (BFS/iteratív módszerrel).

**2. Redukálás (ekvivalens állapotok összevonása):**

Az $i$-megkülönböztethetőség ($\sim_i$): $q \sim_i q'$, ha minden $|u| \leq i$-re $\delta(q,u) \in F \iff \delta(q',u) \in F$.

- $q \sim_0 q'$: mindkettő elfogadó vagy mindkettő nem elfogadó.
- $q \sim_{i+1} q'$: $q \sim_i q'$ és minden $t \in T$-re $\delta(q,t) \sim_i \delta(q',t)$.
- A sorozat legkésőbb $|Q|-1$ lépésnél stabilizálódik: $\sim = \sim_{i_0}$.

**Faktorautomata** ($A/{\sim}$): az ekvivalenciaosztályok mint állapotok. Formálisan $A/{\sim} = \langle Q', T, \delta', q_0', F' \rangle$, ahol $Q'$ a $Q$ ekvivalenciaosztályait tartalmazza, $\delta'(q', t)$ a $\delta(r, t)$ ekvivalenciaosztálya (bármely $r \in q'$ reprezentánssal), $q_0'$ a $q_0$ osztálya, és $F' = \{q' \mid q' \subseteq F\}$.

> **Tétel:** Az $A/{\sim}$ faktorautomata ekvivalens $A$-val, redukált, és izomorfia erejéig az egyetlen ilyen összefüggő, redukált automata. Ezért az algoritmikusan kapott minimális automata izomorf $A^{MN}_L$-lel.

**A faktorautomata egyediségének bizonyítása:**

Legyenek $A$ és $A'$ összefüggő, redukált és egymással ekvivalens véges determinisztikus automaták ($L(A) = L(A')$). Definiáljuk:

$$\varphi(\delta(q_0, u)) := \delta'(q_0', u) \quad \text{minden } u \in T^*\text{-ra.}$$

Megmutatjuk, hogy $\varphi$ jól definiált bijekció és izomorfizmus:

- **Jól definiáltság és injektivitás:** Tetszőleges $u, v \in T^*$-ra:
$$\delta(q_0, u) = \delta(q_0, v) \iff L(A, \delta(q_0,u)) = L(A, \delta(q_0,v)) \iff L(A', \delta'(q_0',u)) = L(A', \delta'(q_0',v)) \iff \delta'(q_0', u) = \delta'(q_0', v)$$
ahol az első és utolsó ekvivalencia az $A$ ill. $A'$ redukáltságából, a középső az $A \sim A'$ ekvivalenciájából következik. Ezért $\varphi$ jól definiált és injektív.
- **Szürjektivitás:** $A'$ összefüggősége miatt minden $A'$-állapot elérhető $q_0'$-ból valamely $u \in T^*$-on át, azaz $\varphi$ szürjektív.
- **Izomorfizmus-tulajdonság:** $\varphi(q_0) = q_0'$; $\varphi(F) = F'$ (mivel $q \in F \iff \varepsilon \in L(A,q) \iff \varepsilon \in L(A', \varphi(q)) \iff \varphi(q) \in F'$); és minden $q \in Q$, $t \in T$-re $\varphi(\delta(q,t)) = \delta'(\varphi(q), t)$. $\square$

### Konkrét redukciós példa (9-állapotú automata)

A következő példa szemlélteti, hogyan finomodik a $\sim_i$ partíció, míg el nem éri a fixpontját.

Adott 9-állapotú, $\{a,b\}$ ábécé feletti determinisztikus automata esetén:

**$\sim_0$ partíció** (elfogadó vs. nem elfogadó állapotok):

$$\{1,2,3,6,7,8,9\} \mid \{4,5\}$$

**$\sim_1$ partíció** (az $a$- és $b$-utódok $\sim_0$-osztályát is figyelembe véve):

$$\{1,2,3\} \mid \{4,5\} \mid \{6,7,8\} \mid \{9\}$$

**$\sim_2$ partíció** (az $a$- és $b$-utódok $\sim_1$-osztályát figyelembe véve):

$$\{1,2,3\} \mid \{4,5\} \mid \{6,7\} \mid \{8\} \mid \{9\}$$

**Fixpont:** $\sim_2 = \sim_3$, tehát $\sim\ =\ \sim_2$, és a minimális automata 5 állapotú. Az ekvivalenciaosztályok lesznek az új állapotok; az átmeneteket és az elfogadó állapotokat tetszőleges reprezentáns alapján határozzuk meg; az eredeti kezdőállapotot tartalmazó osztály lesz az új kezdőállapot.

### Algoritmikus problémák ($\mathcal{L}_3$)

- **Üresség:** $L(G) = \emptyset$ $\iff$ egyetlen végállapot sem érhető el a kezdőállapotból (eldönthető).
- **Diszjunktság:** $L_1 \cap L_2 = \emptyset$ — mindkettő reguláris, a metszet is reguláris, az üresség eldönthető.
- **Egyenlőség:** $L_1 = L_2 \iff (L_1 \triangle L_2) = \emptyset$ (szimmetrikus differencia reguláris).
- **Tartalmazás:** $L_1 \subseteq L_2 \iff L_1 \setminus L_2 = \emptyset$.

### Szóprobléma: lineáris algoritmus

Adott $G$ reguláris grammatika normálformában és $u = t_1 \cdots t_n$:
$$H_0 = \{S\}, \quad H_{i+1} = \{A \mid \exists B \in H_i : B \to t_{i+1} A \in P\}$$
$$u \in L(G) \iff H_n \cap F \neq \emptyset, \quad F = \{A \mid A \to \varepsilon \in P\}$$

Az algoritmus $O(n \cdot |G|)$ lépésben fut; ez lényegében a VNDA determinizáltja ($\mathcal{P}(N)$ állapothalmazzal).

## Kapocs

- [[concepts/bvszam/vda]] — a minimalizálás alapja
- [[concepts/bvszam/vnda]] — VNDA determinizálása
- [[concepts/bvszam/regularis-kifejezesek]] — egyenértékű leíróeszköz
- [[concepts/bvszam/l3-algoritmikus-problemak]] — algoritmikus eldönthetőségi tételek
