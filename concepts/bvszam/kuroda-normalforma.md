---
tags: [concept]
sources: [6.-veremauto-és-környezetfüggetlen-nyelv.md]
derivation: source
updated: 2026-04-08
---

# Kuroda normálforma

A Kuroda normálforma a környezetfüggő (1-es típusú) grammatikák standardizált alakja, ahol a szabályok legfeljebb 2 nemterminálisból álló jobb oldalakra és speciális kontextus-átírásokra korlátozódnak.

## Tartalom

### Definíció

Egy $G = \langle N, T, P, S \rangle$ grammatika **Kuroda normálformájú**, ha minden szabálya:
- $S \to \varepsilon$ (és $S$ nem szerepel más szabály jobboldalán), vagy
- $A \to a$ ($A \in N$, $a \in T$), vagy
- $A \to BC$ ($A, B, C \in N$), vagy
- $AB \to AC$ ($A, B, C \in N$), vagy
- $BA \to CA$ ($A, B, C \in N$).

### Tétel

> Minden KF-ő grammatikához létezik vele ekvivalens Kuroda normálformájú grammatika.

### Átalakítás lépései (5 lépés)

1. **Álterminálisok bevezetése:** Terminálisok csak $A \to a$ szabályban.
2. **KF szabályok hosszredukciója:** Chomsky normálforma szerint ($A \to BC$ alakra).
3. **KF-ő láncmentesítés:** $H(A) = \{B \mid A \Rightarrow^* B\}$ segítségével.
4. **KF-ő szabályok hosszredukciója:** Minden $X_1 \cdots X_m \to Y_1 \cdots Y_n$ ($n \geq m \geq 2$) szabályt a következőképpen redukálunk. Ha $n = m = 2$: a következő lépésre halad. Egyébként új $Z_1, \ldots, Z_{n-2}$ nemterminálisokkal:
   ```
   X₁X₂ → Y₁Z₁
   Z₁X₃ → Y₂Z₂
   ⋮
   Zₘ₋₂Xₘ → Yₘ₋₁Zₘ₋₁    (ha n > m)
   Zₙ₋₂ → Yₙ₋₁Yₙ
   ```
5. **$AB \to CD$ ($A \neq C$, $B \neq D$) eliminálása:** Új $W$ nemterminálissal: $AB \to AW$, $AW \to CW$, $CW \to CD$. Ezáltal minden kontextuális szabály $AB \to AC$ vagy $BA \to CA$ alakú lesz.

## Kapocs

- [[concepts/bvszam/kornyezetfuggo-nyelvek]] — hossz-nemcsökkentő grammatikák, $\mathcal{L}_1$
- [[concepts/bvszam/chomsky-hierarchia]] — az 1-es típus
- [[concepts/bvszam/chomsky-normalforma]] — analóg normálalak 2-es típusra
