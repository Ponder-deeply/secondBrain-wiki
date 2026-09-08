---
tags: [concept]
sources: ["3.-automata,-det-&-nemdet.md"]
derivation: source
updated: 2026-04-07
---

# Véges determinisztikus automata (VDA)

A VDA egy diszkrét állapotú felismerő eszköz, amely egy szó betűit egyenként olvassa és állapotot vált; pontosan a reguláris (3-as típusú) nyelveket ismeri fel.

## Tartalom

### Definíció

$$A = \langle Q, T, \delta, q_0, F \rangle$$

- $Q$: állapotok véges, nemüres halmaza
- $T$: inputábécé
- $\delta : Q \times T \to Q$: **átmenetfüggvény** (minden $(q,a)$ párra pontosan egy következő állapot)
- $q_0 \in Q$: kezdőállapot
- $F \subseteq Q$: elfogadó állapotok

### Kiterjesztett átmenetfüggvény

$$\hat{\delta}(q, \varepsilon) := q \qquad \hat{\delta}(q, xa) := \delta(\hat{\delta}(q, x), a)$$

Az $u$ szót $A$ **elfogadja**, ha $\hat{\delta}(q_0, u) \in F$.

### Elfogadott nyelv

$$L(A) = \{u \in T^* \mid \hat{\delta}(q_0, u) \in F\}$$

### Konfiguráció és redukció

A $q \in Q$ állapotot és a maradék inputot $u \in T^*$-t az $M_\delta = \{qa \to p \mid p = \delta(q,a)\}$ szabályrendszer segítségével definiálva: $qu \Rightarrow_A pu'$ ha $qa \to p \in M_\delta$ és $u = au'$.

### Zártsági következmény

$\mathcal{L}_3$ zárt komplementerre: ha $A$ felismeri $L$-t, az $A' = \langle Q, T, \delta, q_0, Q \setminus F \rangle$ felismeri $\bar{L}$-t.

### Ekvivalencia a 3-as típusú grammatikákkal

Minden VDA-ból 3-as típusú grammatika, és megfordítva VNDA épül — lásd [[concepts/bvszam/vnda|vnda]].

## Kapocs

- [[concepts/bvszam/vnda]] — nemdeterminisztikus változat és determinizálás
- [[concepts/bvszam/myhill-nerode]] — minimális VDA jellemzése
- [[concepts/bvszam/regularis-kifejezesek]] — VDA ↔ reguláris kifejezés
- [[concepts/bvszam/regularis-normalforma]] — grammatika → VDA konstrukció
