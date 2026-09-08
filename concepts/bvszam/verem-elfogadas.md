---
tags: [concept]
sources: [6.-veremauto-és-környezetfüggetlen-nyelv.md]
derivation: source
updated: 2026-04-08
---

# Végállapottal vs. üres veremmel elfogadás

A veremautomata két, egymással ekvivalens elfogadási módja: végállapottal elfogadás ($L(A)$) és üres veremmel elfogadás ($N(A)$); mindkét módból a másikba konvertálható az automata.

## Tartalom

### Végállapottal elfogadás

$$L(A) = \{w \in T^* \mid z_0 q_0 w \Rightarrow_A^* up, \; u \in Z^*, p \in F\}$$

Az automata elfogadja $w$-t, ha valamely végállapotba ér (a veremben maradhat tartalom).

### Üres veremmel elfogadás

$$N(A) = \{w \in T^* \mid z_0 q_0 w \Rightarrow_A^* p, \; p \in Q\}$$

Az automata elfogadja $w$-t, ha a verem **kiürül** ($p \in Q$, nincs veremszimbólum). Az elfogadó állapothalmaz ($F$) ilyenkor irreleváns.

### Példa üres veremmel elfogadásra: $N(A) = \{a^n b^n \mid n \geq 1\}$

$$A = \langle \{\$, a\},\, \{q_0, q_1\},\, \{a, b\},\, \delta,\, \$,\, q_0,\, \emptyset \rangle$$

$M_\delta$ szabályai:
```
$q₀ a → $aq₀      (a beolvasása, push)
aq₀ a → aaq₀      (további a-k, push)
aq₀ b → q₁        (első b: pop és váltás q₁-be)
aq₁ b → q₁        (további b-k, pop)
$q₁  → q₁         (aljszimbólum eltávolítása)
```

Elfogadó futás $a^2b^2$-re:
$$\$q_0 aabb \Rightarrow \$aq_0 abb \Rightarrow \$aaq_0 bb \Rightarrow \$aq_1 b \Rightarrow \$q_1 \Rightarrow q_1$$

Elutasított futás $a^2b^3$-ra: a harmadik $b$-nél a verem már üres, de marad input — az automata blokkolódik, mielőtt elfogadna.

### $L(A) \to N(A')$

Minden $A$-hoz megadható $A'$ (új $z'_0, q'_0, q'_h$ szimbólumokkal), amelyre $N(A') = L(A)$:

- Új kezdőkonfiguráció: $\delta'(z'_0, q'_0, \varepsilon) = \{(z'_0 z_0, q_0)\}$ (a régi verem tartalmát egy új aljszimbólum alá tesszük).
- Valahányszor az eredeti $A$ elfogadó állapotba kerül: $A'$ a $q'_h$ állapotba lép és kipucolja a vermet.

### $N(A) \to L(A')$

Minden $A$-hoz megadható $A'$, amelyre $L(A') = N(A)$:

- Új $z'_0$ aljszimbólum és $q'_f$ elfogadó állapot.
- Ha a verem alján $z'_0$ kerül (az eredeti verem kiürült): $A'$ a $q'_f$ elfogadó állapotba lép.

## Kapocs

- [[concepts/bvszam/veremautomata]] — veremautomata definíciója
- [[concepts/bvszam/va-kf-ekvivalencia]] — az ekvivalencia-tétel
