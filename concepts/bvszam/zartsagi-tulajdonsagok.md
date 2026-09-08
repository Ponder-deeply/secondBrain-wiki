---
tags: [concept]
sources: [1.-bevezetés.md, "3.-automata,-det-&-nemdet.md"]
derivation: source
updated: 2026-04-08
---

# Zártsági tulajdonságok

A Chomsky-hierarchia minden szintje zárt a reguláris műveletekre (unió, konkatenáció, Kleene-lezárt); a magasabb szinteken további műveletek (pl. komplementer) is megőrzik a típust, míg 2-es típuson több művelet nem.

## Tartalom

### Reguláris műveletek: unió, konkatenáció, Kleene-lezárt

> **Tétel:** $\mathcal{L}_i$ zárt a reguláris műveletekre ($i = 0,1,2,3$).

Bizonyítás: grammatika-konstrukciókkal. Mindhárom műveletre $4$ típus = $12$ eset.

**Unió ($i = 0, 2, 3$):** Új $S_0$ kezdőszimbólummal, $S_0 \to S_1 \mid S_2$ szabállyal.

**Unió ($i = 1$):** A KES miatt az $\varepsilon$-szabályokat el kell távolítani, majd az $\varepsilon \in L_k$ eseteket külön kezelni.

**Konkatenáció ($i = 0, 2$):** $S_0 \to S_1 S_2$.

**Konkatenáció ($i = 3$):** Az $R_1$ lezáró szabályainak végéhez fűzzük $S_2$-t.

**Kleene-lezárt ($i = 2$):** $G^* = \langle N \cup \{S_0\}, T, S_0, R \cup \{S_0 \to S S_0 \mid \varepsilon\} \rangle$.

**Kleene-lezárt ($i = 3$):** A lezáró szabályok végéhez $S$-t írunk.

**Kleene-lezárt ($i = 0, 1$):** Speciális konstrukció szükséges. A naív $S_0 \to SS_0 \mid \varepsilon$ megoldás a 0-as típuson ugyan helyes, de 1-es típuson a KES (korlátozott $\varepsilon$-szabály) sérelmet okozhat, ha $S$ szerepel valamelyik szabály jobb oldalán. Ezenfelül $\mathcal{L}_1$ esetén gondoskodni kell arról, hogy az iterált lezárt csak valóban $L$-beli szavak iteráltjait generálhassa (a határok összekeveredése elkerülendő). A pontos konstrukció biztosítja a KES megőrzését és a típus megmaradását.

### $\mathcal{L}_3$ további zártsági tulajdonságai

> **Következmény:** $\mathcal{L}_3$ zárt a **komplementerre**, **metszetre** és **különbségre** is.

- **Komplementer:** Ha $A$ VDA felismeri $L$-t, az $A' = \langle Q, T, \delta, q_0, Q \setminus F \rangle$ felismeri $\bar{L}$-t.
- **Metszet:** $L_1 \cap L_2 = \overline{\bar{L}_1 \cup \bar{L}_2}$ (De Morgan).
- **Különbség:** $L_1 \setminus L_2 = L_1 \cap \bar{L}_2$.

### $\mathcal{L}_3$ tükrözésre való zártsága

Minden reguláris nyelvhez létezik azt felismerő bal-lineáris grammatika, és $\mathcal{L}_3$ zárt a tükrözés ($L \mapsto L^{-1}$) műveletre.

### $\mathcal{L}_2$ nem zárt bizonyos műveletekre

> **Következmény:** $\mathcal{L}_2$ **nem zárt** metszetre, komplementerre, különbségre és szimmetrikus differenciára.

Ellenpélda: $\{a^n b^n c^n\} = \{a^k b^n c^n\} \cap \{a^n b^n c^k\}$, ahol mindkét tényező KF, de a metszet nem az (Bar-Hillel lemmával).

## Kapocs

- [[concepts/bvszam/chomsky-hierarchia]] — a négy szint
- [[concepts/bvszam/formalis-nyelvek]] — műveletek definíciói
- [[concepts/bvszam/vda]] — komplementer-konstrukció véges automatával
- [[concepts/bvszam/bar-hillel-lemma]] — miért nem zárt $\mathcal{L}_2$ metszetre
