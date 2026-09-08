---
tags: [concept]
sources: [6.-veremauto-és-környezetfüggetlen-nyelv.md]
derivation: source
updated: 2026-04-08
---

# Veremautomata (VA)

A veremautomata a véges automata általánosítása végtelen veremmel kiegészítve; nemdeterminisztikus változata pontosan a környezetfüggetlen (KF) nyelveket ismeri fel.

## Tartalom

### Definíció

$$A = \langle Z, Q, T, \delta, z_0, q_0, F \rangle$$

| Komponens                                                                                          | Leírás                    |
| -------------------------------------------------------------------------------------------------- | ------------------------- |
| $Z$                                                                                                | Veremábécé (véges halmaz) |
| $Q$                                                                                                | Állapotok (véges)         |
| $T$                                                                                                | Inputábécé                |
| $\delta : Z \times Q \times (T \cup \{\varepsilon\}) \to \mathcal{P}_{\text{véges}}(Z^* \times Q)$ | Átmenetfüggvény           |
| $z_0 \in Z$                                                                                        | Kezdő veremszimbólum      |
| $q_0 \in Q$                                                                                        | Kezdőállapot              |
| $F \subseteq Q$                                                                                    | Elfogadó állapotok        |

### Konfiguráció

$zqw$ ahol $z \in Z^*$ a verem tartalma (utolsó betűje a tetőn), $q \in Q$ az aktuális állapot, $w \in T^*$ a maradék input.

**Kezdőkonfiguráció:** $z_0 q_0 w$.

### Alapvető veremműveletek

| Átmenet | Hatás |
|---|---|
| $(\varepsilon, r) \in \delta(z, q, t)$ | POP (tetőelem kivétele) |
| $(z, r) \in \delta(z, q, t)$ | Verem változatlan |
| $(z', r) \in \delta(z, q, t)$ | Csere ($z' \in Z$) |
| $(zz', r) \in \delta(z, q, t)$ | PUSH ($z'$ a tetőre) |
| $(w, r) \in \delta(z, q, t)$ | $z$ helyére $w \in Z^*$ kerül ($w$ utolsó betűje lesz a tetőn) |

### ε-átmenet

Ha $\delta(z, q, \varepsilon) \neq \emptyset$, az automata anélkül hajthat végre lépést, hogy szimbólumot olvasna.

### Determinisztikus veremautomata

$A$ **determinisztikus**, ha minden $(z, q, a) \in Z \times Q \times T$ esetén:
$$|\delta(z, q, a)| + |\delta(z, q, \varepsilon)| = 1$$

### Egylépéses redukció

$\alpha \Rightarrow_A \beta$, ha $\alpha = rzqaw$, $\beta = rupw$ és $(u,p) \in \delta(z,q,a)$.

### Elfogadott nyelv

$$L(A) = \{w \in T^* \mid z_0 q_0 w \Rightarrow_A^* up, \; u \in Z^*, p \in F\}$$

### Alternatív reprezentációk

Az átmeneti függvény megadható **átírási szabályok** ($M_\delta$) formájában:
$$zqa \to up \in M_\delta \iff (u, p) \in \delta(z, q, a)$$
$$zq \to up \in M_\delta \iff (u, p) \in \delta(z, q, \varepsilon)$$

Az **átmenetdiagram** jelölése:
$$q \xrightarrow{a;\, z \to u} p \iff (u, p) \in \delta(z, q, a)$$

ahol végállapotokat duplán karikázzuk, kezdőállapotot nyíl jelöli.

### Kidolgozott példák

#### 1. Determinisztikus eset: $L_1 = \{wcw^{-1} \mid w \in \{a,b\}^+\}$

A $w$ előtagot a verembe toljuk, a `c` elválasztójelre váltunk olvasó módba, majd ellenőrizzük, hogy a bemenet megfordítva egyezik-e a veremmel.

$$A = \langle \{q_0, q_1, q_2, q_3\},\, \{a,b,c\},\, \{\#, a, b\},\, \delta,\, q_0,\, \#,\, \{q_3\} \rangle$$

Főbb átmenetek:
- $(\#t, q_1) \in \delta(\#, q_0, t)$ — első szimbólum beolvasása ($t \in \{a,b\}$)
- $(zt, q_1) \in \delta(z, q_1, t)$ — további szimbólumok verembe ($z,t \in \{a,b\}$)
- $(z, q_2) \in \delta(z, q_1, c)$ — `c` beolvasásakor átváltás ellenőrzésre
- $(\varepsilon, q_2) \in \delta(t, q_2, t)$ — egyezés esetén POP ($t \in \{a,b\}$)
- $(\#, q_3) \in \delta(\#, q_2, \varepsilon)$ — elfogadás, ha a verem kiürült

#### 2. Nemdeterminisztikus eset: $L_2 = \{ww^{-1} \mid w \in \{a,b\}^+\}$

Az elválasztó szimbólum hiánya miatt az automata $\varepsilon$-átmenettel „találgatja", hol az átfordulás pontja: $q_1$-ből $q_2$-be ε-átmenettel lép (nem `c` alapján).

> **Fontos különbség:** $L_1$ felismerhető determinisztikus veremautomatával, $L_2$ **nem**. Ez szemlélteti, hogy a determinisztikus VA ereje valóban szűkebb.

## Kapocs

- [[concepts/bvszam/verem-elfogadas]] — végállapottal vs. üres veremmel elfogadás
- [[concepts/bvszam/va-kf-ekvivalencia]] — VA ↔ KF grammatika ekvivalencia
- [[concepts/bvszam/kornyezetfuggetlen-grammatika]] — a KF grammatikák
- [[concepts/bvszam/vda]] — véges automata (verem nélküli eset)
