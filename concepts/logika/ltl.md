---
tags: [concept, logika/temporalis-logika]
sources: [LTL_CTL.pdf]
derivation: source
updated: 2026-09-08
---

# LTL (Linear Temporal Logic)

A lineáris temporális logika: formulái egy Kripke-struktúra egyetlen (végtelen) útján, annak lineáris időbeli lefolyása mentén értelmezettek.

## Tartalom

### BNF szintaxis

Egy jólformált LTL-formula, $\varphi$, szerkezeti rekurzióval:

$$\varphi ::= \top \mid \bot \mid p \mid \neg\varphi \mid \varphi \wedge \varphi \mid \varphi \vee \varphi \mid X\varphi \mid F\varphi \mid G\varphi \mid \varphi U \varphi$$

ahol $p$ egy $AP$-beli atomi állítás (lásd [[concepts/logika/kripke-struktura]]). A négy temporális operátor:

- $X\varphi$ — *next time*: a következő időpillanatban $\varphi$
- $F\varphi$ — *eventually*: valamikor a jövőben $\varphi$
- $G\varphi$ — *always*: mindig (a jövőben, a jelent is beleértve) $\varphi$
- $\varphi U \psi$ — *until*: $\varphi$ addig tart, amíg $\psi$ be nem következik

### Szemantika

A kielégítési reláció, $\models$, egy $\langle M, \pi \rangle$ pár — egy Kripke-struktúra és egy útja — mellett értelmezett.

**Alapesetek:**
- $M,\pi \models \top$ mindig teljesül; $M,\pi \models \bot$ soha.
- $M,\pi \models p \iff p \in L(\pi_0)$ — az atomi állítás akkor teljesül, ha tagja az út első elemének címkéjének.

**Boole-kombinációk** (a szokásos matematikai jelentésükkel):
- $M,\pi \models \neg\varphi \iff M,\pi \not\models \varphi$
- $M,\pi \models \varphi \wedge \psi \iff (M,\pi \models \varphi) \wedge (M,\pi \models \psi)$
- $M,\pi \models \varphi \vee \psi \iff (M,\pi \models \varphi) \vee (M,\pi \models \psi)$

**Temporális operátorok:**
- $M,\pi \models X\varphi \iff M,\pi^1 \models \varphi$
- $M,\pi \models F\varphi \iff \exists i:\ M,\pi^i \models \varphi$
- $M,\pi \models G\varphi \iff \forall i:\ M,\pi^i \models \varphi$
- $M,\pi \models \varphi U \psi \iff \exists i$ úgy, hogy $(\forall j<i:\ M,\pi^j \models \varphi) \wedge (M,\pi^i \models \psi)$

Az itt szereplő $U$ az ún. *erős* (strong) until: megköveteli, hogy $\psi$ ténylegesen bekövetkezzen. Van egy *gyenge* (weak) until is: $\varphi U_w \psi \equiv (\varphi U \psi) \vee G\varphi$ — vagyis $\varphi$ akár örökké is tarthat, ha $\psi$ sosem következik be.

**Modellkielégítés és ekvivalencia:**
- $M \models_M \varphi \iff$ minden $\pi$ útra, amelyre $\pi_0 \in I$, $M,\pi \models \varphi$. Egy Kripke-struktúra (modell) akkor elégít ki egy LTL-formulát, ha minden útja kielégíti.
- $\varphi \equiv \psi \iff$ minden $M$-re $(M \models_M \varphi) \Leftrightarrow (M \models_M \psi)$. Két LTL-formula ekvivalens, ha ugyanazok a Kripke-struktúrák elégítik ki őket.

### LTL ekvivalenciák

$$X(\varphi \wedge \psi) \equiv X\varphi \wedge X\psi \qquad X(\varphi \vee \psi) \equiv X\varphi \vee X\psi$$
$$X(\varphi U \psi) \equiv (X\varphi) U (X\psi) \qquad \neg X\varphi \equiv X\neg\varphi$$
$$F(\varphi \vee \psi) \equiv F\varphi \vee F\psi \qquad G(\varphi \wedge \psi) \equiv G\varphi \wedge G\psi \qquad \neg F\varphi \equiv G\neg\varphi$$
$$(\varphi \wedge \psi) U \rho \equiv (\varphi U \rho) \wedge (\psi U \rho) \qquad \rho U (\varphi \vee \psi) \equiv (\rho U \varphi) \vee (\rho U \psi)$$
$$FF\varphi \equiv F\varphi \qquad GG\varphi \equiv G\varphi$$

A $\neg X\varphi \equiv X\neg\varphi$ és $\neg F\varphi \equiv G\neg\varphi$ ekvivalenciák bizonyítása a definíciók egyenes behelyettesítésével adódik: pl. $M,\pi \models X(\varphi \wedge \psi) \iff M,\pi^1 \models \varphi \wedge \psi \iff (M,\pi^1 \models \varphi) \wedge (M,\pi^1 \models \psi) \iff (M,\pi \models X\varphi) \wedge (M,\pi \models X\psi) \iff M,\pi \models X\varphi \wedge X\psi$.

## Kapocs

- [[concepts/logika/kripke-struktura]] — a modell, amelynek útjain az LTL-formulák értelmezettek
- [[concepts/logika/ctl]] — az elágazó idejű rokon logika, amely állapotokon és útkvantorokon értelmezett
- [[concepts/logika/ltl-ctl-osszehasonlitas]] — a két logika kifejezőereje, ekvivalenciái és bonyolultsága
