---
tags: [concept]
sources: [LTL_CTL.pdf]
derivation: source
updated: 2026-09-08
---

# Kripke-struktúra

A temporális logikák (LTL, CTL) modellje: egy állapotokból és állapotátmenetekből álló irányított gráf, amelynek állapotait atomi állítások címkézik.

## Tartalom

### Definíció

Legyen $AP$ egy címkehalmaz — atomi állítások (propozíciók) halmaza, például változók, konstansok és predikátumszimbólumok fölötti Boole-kifejezések.

Egy **Kripke-struktúra** egy négyes, $M = (S, I, R, L)$:

- $S$ — állapotok véges halmaza,
- $I \subseteq S$ — kezdőállapotok halmaza,
- $R \subseteq S \times S$ — átmeneti reláció, amelyre $\forall s \in S,\ \exists s' \in S$ úgy, hogy $(s, s') \in R$ (minden állapotnak van rákövetkezője — az átmeneti reláció nem akadhat el),
- $L : S \to 2^{AP}$ — címkéző függvény, amely minden állapothoz hozzárendeli az ott igaz atomi állítások halmazát.

### Példa

$S = \{s_0, s_1, s_2, s_3\}$, $I = \{s_0\}$,

$$R = \{(s_0,s_1), (s_0,s_2), (s_1,s_1), (s_1,s_3), (s_2,s_0), (s_2,s_3), (s_3,s_0)\}$$

$$L = \{(s_0,\{p\}), (s_1,\{p,q\}), (s_2,\{p,r\}), (s_3,\{v\})\}$$

Vagyis $s_0$-ban $p$ igaz, $s_1$-ben $p$ és $q$, $s_2$-ben $p$ és $r$, $s_3$-ban $v$.

### Utak (paths)

Az LTL és a CTL is kizárólag **végtelen utakkal** foglalkozik. Egy $\pi = (\pi_0, \pi_1, \pi_2, \dots)$ végtelen sorozat pontosan akkor út (útvonal, pálya) $M$-ben, ha tiszteletben tartja $M$ átmeneti relációját: $\forall i,\ (\pi_i, \pi_{i+1}) \in R$. Az átmeneti reláció fenti feltétele ($\forall s\ \exists s'$) garantálja, hogy minden állapotból indítható végtelen út.

$\pi^i$ jelöli $\pi$ $i$-edik **szuffixét**: $\pi^i = (\pi_i, \pi_{i+1}, \pi_{i+2}, \dots)$. Ebből $(\pi^i)^j = \pi^{i+j}$.

Az út fogalma az alapja az LTL szemantikájának (egy formula igazsága egy adott úton értelmezett), míg a CTL szemantikája állapotokhoz köti a kielégítést, és a köztük futó összes vagy legalább egy útra kvantifikál — lásd [[concepts/logika/ltl]] és [[concepts/logika/ctl]].

## Kapocs

- [[concepts/logika/ltl]] — a lineáris temporális logika, amelynek formulái egy Kripke-struktúra egyetlen útján értelmezettek
- [[concepts/logika/ctl]] — az elágazó idejű temporális logika, amelynek formulái egy Kripke-struktúra állapotain, az onnan induló utakra kvantifikálva értelmezettek
- [[concepts/logika/elsorendu-interpretacio]] — rokon fogalom: ott egy struktúra ad jelentést a nyelv szimbólumainak; itt egy Kripke-struktúra állapotai és címkéi adják a modellt, amelyen a temporális formulák kiértékelődnek
