---
tags: [concept, logika/gentzen-stilusu-kalkulusok]
sources: [Szekventkalkulus.pdf]
derivation: source
updated: 2026-09-08
---

# Szekvent

A **szekvent** egy $(\Gamma, \Delta)$ pár, ahol $\Gamma$ és $\Delta$ véges, nem rendezett formulasorozatok (formulahalmazok); jelölése $\Gamma \to \Delta$. A szekvent a szekventkalkulus alapobjektuma, amelyre a [[concepts/logika/szekventkalkulus]] levezetési szabályai épülnek.

## Tartalom

### Szintaxis

Egy szekvent $\Gamma \to \Delta$ alakú, ahol $\Gamma$ a szekvent **baloldala** (a hagyományos elnevezéssel **antecedens**), $\Delta$ pedig a **jobboldala** (**szukcedens**). Mindkét oldal lehet üres:

- ha $\Gamma$ üres, $\emptyset \to \Delta$ helyett $\to \Delta$-t írunk;
- ha $\Delta$ üres, $\Gamma \to \emptyset$ helyett $\Gamma \to$-t írunk;
- ha mindkettő üres, a szekvent egyszerűen $\to$.

Ha $\Gamma = \{A_1, A_2, \dots, A_n\}$ és $\Delta = \{B_1, B_2, \dots, B_m\}$, és $A$, $B$ (ítéletlogikai vagy elsőrendű) formulák, akkor az $A, \Gamma \to \Delta, B$ jelölés az $A, A_1, A_2, \dots, A_n \to B_1, B_2, \dots, B_m, B$ szekventet jelenti — a formula egyszerűen a megfelelő oldal elé, illetve mögé kerül a felsorolásban. Elsőrendben a szintaxis értelemszerűen ugyanez.

**Fontos jelölési figyelmeztetés:** a $\to$ jel itt **nem** ugyanaz, mint a [[concepts/logika/iteletlogikai-formula]] lapon bevezetett $\supset$ implikációjel. A $\supset$ az ítéletlogikai *nyelv* egy művelete, formulán belül szerepel. A $\to$ ezzel szemben a **szekventek szintaxisának** jele: két formulasorozatot választ el, és — bár szándéka szerint egyfajta implikációt reprezentál — soha nem áll formulán belül. A két jel keverése az egyik leggyakoribb hibaforrás a szekventkalkulus tanulásakor.

### Szemantika

Legyen $I$ egy interpretáció, $B_I$ pedig az $I$-beli Boole-értékelés. A $B_I(\Gamma \to \Delta)$ szekvent igazságértékét úgy definiáljuk, hogy $B_I(\Gamma \to \Delta) = i$ pontosan akkor, ha van olyan $A_k \in \Gamma$, hogy $B_I(A_k) = h$, **vagy** van olyan $B_r \in \Delta$, hogy $B_I(B_r) = i$. Egyébként $B_I(\Gamma \to \Delta) = h$.

Ebből a definícióból következnek a peremesetek és a formulaszámra vonatkozó általános alak:

$$
\begin{aligned}
B_I(\to) &= h,\\
B_I(\to B) &= B_I(B),\\
B_I(A \to) &= B_I(\neg A),\\
B_I(A \to B) &= B_I(A \supset B),\\
B_I(A_1, A_2 \to B_1, B_2) &= B_I(A_1 \wedge A_2 \supset B_1 \vee B_2),\\
&\;\;\vdots
\end{aligned}
$$

Általánosan:

$$
B_I(\Gamma \to \Delta) = B_I(A_1 \wedge A_2 \wedge \dots \wedge A_n \supset B_1 \vee B_2 \vee \dots \vee B_m),
$$

ahol a baloldal $\top$ (tautologikusan igaz), ha $\Gamma$ üres, a jobboldal pedig $\bot$ (azonosan hamis), ha $\Delta$ üres. A szemantika elsőrendben értelemszerűen ugyanígy működik.

### A szekvent teljesülése

Azt mondjuk, hogy egy szekvent **teljesül**, ha valahányszor a $\to$ baloldalán (az antecedensben) lévő minden formula igaz, a jobboldalán (a szukcedensben) lévő formulák legalább egyike is igaz. Ez pontosan a fenti szemantikai definíció $B_I(\Gamma \to \Delta) = i$ esete — vagyis a szekvent az általa reprezentált $A_1 \wedge \dots \wedge A_n \supset B_1 \vee \dots \vee B_m$ formula igazságával azonosítható. A szekventek **bizonyíthatóságát** — a szintaktikus, kalkulusbeli megfelelőjét — a [[concepts/logika/szekvent-levezetesfa]] lap tárgyalja.

## Kapocs

- [[concepts/logika/szekventkalkulus]] — a levezetési szabályrendszerek (G- és C-kalkulus), amelyek szekventeken dolgoznak
- [[concepts/logika/szekvent-levezetesfa]] — a szekvent bizonyíthatóságának fogalma egy adott kalkulusban
- [[concepts/logika/iteletlogikai-formula]] — a formulanyelv, amelynek elemeiből $\Gamma$ és $\Delta$ épül; itt vezetjük be a $\supset$ jelet, amellyel a szekvent $\to$ jele nem összekeverendő
- [[concepts/bvszam/itelet-kalkulus]] — az ítéletkalkulus rokon, axiómasémás bizonyításelméleti tárgyalása
- [[concepts/bvszam/elsorendu-logika]] — az elsőrendű logika, amelyre a szekvent szintaxisa és szemantikája értelemszerűen kiterjed
</content>
