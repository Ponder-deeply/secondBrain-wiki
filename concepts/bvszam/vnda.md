---
tags: [concept]
sources: ["3.-automata,-det-&-nemdet.md"]
derivation: source
updated: 2026-04-08
---

# Véges nemdeterminisztikus automata (VNDA)

A VNDA a VDA általánosítása: egy állapotból egy inputszimbólumra több lehetséges következő állapot adható; a szót elfogadja, ha **van** legalább egy elfogadó állapotig vezető számítás.

## Tartalom

### Definíció

$$A = \langle Q, T, \delta, Q_0, F \rangle$$

- $Q$: állapotok véges, nemüres halmaza
- $T$: inputábécé
- $\delta : Q \times T \to \mathcal{P}(Q)$: átmenetfüggvény (halmazértékű)
- $Q_0 \subseteq Q$: kezdőállapotok halmaza
- $F \subseteq Q$: elfogadó állapotok

A VDA speciális eset: $|\delta(q,a)| = 1$ és $|Q_0| = 1$ minden $(q,a)$-ra.

### Elfogadott nyelv

$$L(A) = \{u \in T^* \mid \exists q_0 \in Q_0, p \in F : q_0 u \Rightarrow_A^* p\}$$

$\varepsilon \in L(A) \iff Q_0 \cap F \neq \emptyset$.

### Elakadás

Ha $\delta(q, a) = \emptyset$, a számítás **elakad** — ez elutasítást jelent arra a számítási ágra nézve.

### VNDA → 3-as típusú grammatika

Minden VNDA-hoz adható 3-as típusú grammatika: az átmenetszabályok bal-lineáris grammatikát alkotnak, amelynek ekvivalens jobb-lineáris változata közvetlenül felírható.

Formálisan legyen $G = \langle N, T, P, S \rangle$, ahol $N = Q \cup \{S\}$ ($S \notin Q$). A $P$ szabályrendszer:

1. $p \to a \in P \iff q_0 a \to p \in M_\delta$ valamely $q_0 \in Q_0$-ra
2. $p \to qa \in P \iff qa \to p \in M_\delta$
3. $S \to p \in P \iff p \in F$
4. $S \to \varepsilon \in P \iff Q_0 \cap F \neq \emptyset$

Az átmenet-szabályok hossz-csökkentők; a redukció egy bal-lineáris grammatikabeli levezetés fordítottjának felel meg.

### 3-as típusú grammatika → VNDA

Chomsky-normálformájú ($X \to aY$ és $X \to \varepsilon$ szabályok) reguláris grammatikából:

$$Q = N, \quad Q_0 = \{S\}, \quad F = \{Z \mid Z \to \varepsilon \in P\}, \quad Xa \to Y \in M_\delta \iff X \to aY \in P$$

### Megfeleltetési táblázat (VNDA $\leftrightarrow$ grammatika)

Az alábbi táblázat mutatja, hogy a VNDA elemei hogyan felelnek meg az $M_\delta$ szabályrendszer szabályainak, ill. a jobb-lineáris grammatika produkcióinak:

| VNDA | $M_\delta$ (bal-lineáris irány) | Jobb-lineáris grammatika |
|---|---|---|
| $q_0 \in Q_0$ (kezdőállapot) | — | $S$ (új kezdőszimbólum) |
| $p \in \delta(q_0, a)$, $q_0 \in Q_0$ | $q_0 a \to p$ | $p \to a$; $S \to ap$ |
| $p \in \delta(q, a)$, $q \notin Q_0$ | $qa \to p$ | $p \to qa$; $q \to ap$ |
| $p \in F$ (elfogadó állapot) | — | $S \to p$; $p \to \varepsilon$ |
| $Q_0 \cap F \neq \emptyset$ | — | $S \to \varepsilon$ |

A táblázat két irányt fog össze: az első három sor mutatja, hogyan fordítható le egy VNDA grammatikává (VNDA → grammatika irány), az utolsó két sor az elfogadó állapotok kezelését, a teljes táblázat visszafelé olvasva pedig a grammatika → VNDA irányt adja.

### Determinizálás (hatványhalmaz-konstrukció)

> **Tétel:** Minden VNDA-hoz megkonstruálható ekvivalens VDA.

$$Q' = \mathcal{P}(Q), \quad q_0' = Q_0, \quad F' = \{q' \in Q' \mid q' \cap F \neq \emptyset\}, \quad \delta'(q', a) = \bigcup_{q \in q'} \delta(q,a)$$

A konstruált VDA állapotainak száma legfeljebb $2^{|Q|}$; a gyakorlatban csak az elérhető részhalmazokat kell felvenni.

**Helyesség:** Két segédlemmával (lépésszám szerinti indukcióval) igazolható, hogy $L(A) = L(A')$.

## Kapocs

- [[concepts/bvszam/vda]] — determinisztikus eset
- [[concepts/bvszam/regularis-normalforma]] — grammatika → VNDA konstrukció
- [[concepts/bvszam/myhill-nerode]] — minimalizálás
- [[concepts/bvszam/regularis-kifejezesek]] — ε-VNDA felépítése reguláris kifejezésből
