---
tags: [concept]
sources: [10.md]
derivation: source
updated: 2026-09-04
---

# $\mathcal{L}_0$ és RE ekvivalenciája; $\mathcal{L}_1$ és R kapcsolata

A Chomsky-hierarchia felső szintjeinek automatás megfelelői: $\mathcal{L}_0 = \text{RE}$ és $\mathcal{L}_1 \subsetneq \text{R}$.

## $\mathcal{L}_0 = \text{RE}$

**Tétel:** $L \in \mathcal{L}_0 \iff L \in \text{RE}$.

**Bizonyítás ($\mathcal{L}_0 \subseteq \text{RE}$):** Minden $G$ grammatikához megadható $L(G)$-t felismerő NTG:
1. Az NTG szalagára felírja az inputot.
2. Nemdeterminisztikusan alkalmaz grammatikai szabályokat (bal → jobb irányban, az aktuális sentenciális formán).
3. Ha az $\varepsilon^*$-ból levezetett szó egyenlő az inputtal, elfogad.

(Részletesen: 3 szalagos TG — bemenet, sentenciális forma, szabályok.)

**Bizonyítás ($\text{RE} \subseteq \mathcal{L}_0$):** Minden $M$ DTG-hez megkonstruálható $G$ grammatika, amely kódolt konfigurációk sorozatát generálja; a generált szó pontosan $L(M)$.

## $\mathcal{L}_1$ és R kapcsolata

**Tétel:** Ha $A$ LKA (lineárisan korlátolt automata), akkor $L(A)$ eldönthető ($L(A) \in \text{R}$).

**Bizonyítás:** Az LKA lehetséges konfigurációinak száma $u$ bemenetre legfeljebb $m(u) = |Q| \cdot |u| \cdot |\Gamma|^{|u|}$. Ha van elfogadó számítás, van legfeljebb $m(u)$ hosszú elfogadó számítás. Egy $M$ TG szimulálhatja $A$-t pontosan $m(u)$ lépésig, majd leáll — tehát $L(A) \in \text{R}$.

**Következmény:** $\mathcal{L}_1 \subseteq \text{R}$.

**Tétel:** $\mathcal{L}_1 \subsetneq \text{R}$ (a tartalmazás valódi).

**Bizonyítás:** Legyen $L_{\text{LKA-átló}} = \{\langle M \rangle \mid M \text{ LKA és } \langle M \rangle \notin L(M)\}$.
- Diagonalizáció: $L_{\text{LKA-átló}} \in \text{R}$ (az univerzális TG $m(w)$ lépés után leállítható).
- $L_{\text{LKA-átló}}$ nem ismerhető fel LKA-val (önhivatkozásos ellentmondás).
- Tehát $L_{\text{LKA-átló}} \in \text{R} \setminus \mathcal{L}_1$.

## Összefoglaló táblázat (Chomsky-hierarchia)

| Osztály | Grammatika | Automata |
|---------|-----------|---------|
| $\mathcal{L}_3$ | 3-típusú (reguláris) | VDA, VNDA, reguláris kifejezés, determinisztikus VA |
| $\mathcal{L}_2$ | 2-típusú (KF) | (nemdeterminisztikus) veremautomata |
| $\mathcal{L}_1$ | 1-típusú (KF-ő) | lineárisan korlátolt automata (LKA) |
| R | — | minden inputra megálló TG |
| RE $= \mathcal{L}_0$ | 0-típusú | Turing gép / NTG |

## 0-típusú normálforma

> **Tétel:** Bármely $G = \langle N, T, P, S \rangle$ 0-típusú grammatikához megadható egy vele ekvivalens $G'$ grammatika, amelynek minden szabálya az alábbi alakok egyike:
> - $S \to \varepsilon$ (és $S$ nem szerepel más szabály jobboldalán)
> - $A \to a$ ($A \in N$, $a \in T$)
> - $A \to B$ ($A, B \in N$)
> - $A \to BC$ ($A, B, C \in N$)
> - $AB \to B$ ($A, B \in N$)
> - $AB \to AC$ ($A, B, C \in N$)
> - $BA \to CA$ ($A, B, C \in N$)

Ez az alak analóg a [[concepts/bvszam/kuroda-normalforma|Kuroda normálformával]], de $A \to B$ láncszabályokat és $AB \to B$ rövidítő szabályokat is megenged (amelyek a 0-típusban lehetségesek).

## Kapocs

- [[concepts/bvszam/turing-gep]] — DTG
- [[concepts/bvszam/nemdeterminisztikus-turing-gep]] — NTG
- [[concepts/bvszam/linearis-korlatolt-automata]] — LKA részletes definíciója
- [[concepts/bvszam/chomsky-hierarchia]] — az osztályok hierarchiája
- [[concepts/bvszam/kornyezetfuggo-nyelvek]] — $\mathcal{L}_1$ grammatikák
- [[concepts/bvszam/va-kf-ekvivalencia]] — ugyanez az automata–grammatika ekvivalencia a KF szinten
