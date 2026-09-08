---
tags: [concept]
sources: [szelmJegyzet.pdf, 08.md]
derivation: source
updated: 2026-08-05
---

# Visszavezetés (many-one reducibility)

A visszavezetés ($L_1 \leq L_2$) azt fejezi ki, hogy $L_1$ nehézsége „belefér" $L_2$-be: ha $L_2$ (fel)ismerhető/eldönthető, akkor $L_1$ is az. A fogalom Emil Posttól származik; angol neve: *many-one reducibility*.

## Definíció

$L_1 \subseteq \Sigma^*$ **visszavezethető** $L_2 \subseteq \Delta^*$-ra ($L_1 \leq L_2$), ha létezik olyan kiszámítható $f : \Sigma^* \to \Delta^*$ szófüggvény, amelyre

$$w \in L_1 \iff f(w) \in L_2.$$

## Szimuláló konstrukció

Ha $M_f$ kiszámítja $f$-et és $M_2$ (fel)ismeri $L_2$-t, akkor az alábbi $M_1$ (fel)ismeri $L_1$-t:

$$w \xrightarrow{M_f} f(w) \xrightarrow{M_2} \begin{cases} q_i & \text{elfogad} \\ q_n & \text{elutasít} \end{cases}$$

## Következmények

| Feltétel | Következmény |
|----------|--------------|
| $L_1 \leq L_2$ és $L_2 \in \text{RE}$ | $L_1 \in \text{RE}$ |
| $L_1 \leq L_2$ és $L_2 \in \text{R}$ | $L_1 \in \text{R}$ |
| $L_1 \leq L_2$ és $L_1 \notin \text{RE}$ | $L_2 \notin \text{RE}$ |
| $L_1 \leq L_2$ és $L_1 \notin \text{R}$ | $L_2 \notin \text{R}$ |

## Alkalmazás: $L_u \leq L_h$

$$L_h = \{\langle M, w \rangle \mid M \text{ megáll } w\text{-n}\}$$

**Visszavezetési függvény:** Minden $M$ TG-re legyen $M'$ a következő TG:
1. Futtatja $M$-et $u$-n.
2. Ha $M$ elfogadó állapotba ($q_i$) lép, $M'$ is elfogad.
3. Ha $M$ elutasító állapotba ($q_n$) lép, $M'$ **végtelen ciklusba** kerül.

Ekkor $f(\langle M, w \rangle) = \langle M', w \rangle$ és

$$\langle M, w \rangle \in L_u \iff \langle M', w \rangle \in L_h.$$

Tehát $L_u \leq L_h$. Mivel $L_u \in \text{RE} \setminus \text{R}$, következik: $L_h \notin \text{R}$.

## RE nem zárt komplementerre

**Tétel:** Ha $L \in \text{RE}$ és $\bar{L} \in \text{RE}$, akkor $L \in \text{R}$.

**Bizonyítás:** Legyen $M_1$ az $L$-t, $M_2$ a $\bar{L}$-t felismerő TG. $M'$ felváltva szimulál egy-egy lépést — valamelyik véges lépésen belül elfogad, tehát $M'$ mindig megáll.

**Következmény:** $\text{RE}$ nem zárt komplementerre. Ha $\bar{L}_u \in \text{RE}$ lenne, akkor $L_u \in \text{R}$ következne — ellentmondás.

**R zárt komplementerre:** Ha $L \in \text{R}$ és $M$ eldönti, akkor $M'$ az elfogadó/elutasító állapotokat felcserélve eldönti $\bar{L}$-t.

## Polinom idejű változat

Ha az $f$ visszavezető függvénytől megköveteljük, hogy egy adott $v$ függvényosztályba essen, $L_1 \leq_v L_2$ jelölést használunk. A bonyolultságelméletben fontos a **polinom idejű visszavezetés** ($L_1 \leq_p L_2$), ahol $f$ polinom időben kiszámítható — ez az NP-teljesség alapfogalma.

## Kapocs

- [[concepts/bvszam/kiszamithato-szofuggveny]] — az $f$ visszavezetési függvény fogalma
- [[concepts/bvszam/r-re-nyelvek]] — R és RE osztályok, zártsági tulajdonságok
- [[concepts/bvszam/eldonthetetlen-problemak]] — PMP, Rice-tétel és további alkalmazások
- [[concepts/bvszam/megallasi-problema]] — $L_h$, az $L_u \leq L_h$ visszavezetés
- [[concepts/bvszam/univerzalis-turing-gep]] — $L_u$ mint kanonikus $\text{RE} \setminus \text{R}$ példa
- [[concepts/bvszam/np-teljesseg]] — polinom idejű visszavezetés ($\leq_p$), NP-teljesség
