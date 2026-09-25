---
tags: [concept, logika/temporalis-logika]
sources: [LTL_CTL.pdf]
derivation: source
updated: 2026-09-08
---

# CTL (Computation Tree Logic)

Az elágazó idejű temporális logika: formulái egy Kripke-struktúra egy adott **állapotán** (nem egy útján) értelmezettek, és a temporális operátorokat mindig egy útkvantor ($A$ vagy $E$) előzi meg.

## Tartalom

### BNF szintaxis

$$\varphi ::= \top \mid \bot \mid p \mid \neg\varphi \mid \varphi \wedge \varphi \mid \varphi \vee \varphi \mid AX\varphi \mid AF\varphi \mid AG\varphi \mid \varphi AU \varphi \mid EX\varphi \mid EF\varphi \mid EG\varphi \mid \varphi EU \psi$$

Fontos: $AX$, $AF$, $AG$, $AU$, $EX$, $EF$, $EG$, $EU$ mindegyike **egyetlen, oszthatatlan szimbólum** — nem egy útkvantor és egy önálló temporális operátor kombinációja. A CTL-ben temporális operátor önmagában (útkvantor nélkül) nem fordulhat elő.

Az útkvantorok jelentése:
- $A$ — *for all paths*: az adott állapotból induló **minden** útra
- $E$ — *there exists a path*: az adott állapotból induló **legalább egy** útra

### Szemantika

A kielégítési reláció egy $\langle M, s \rangle$ pár — egy Kripke-struktúra és egy állapota — mellett értelmezett. Ez a váltás (út helyett állapot) gyökeresen más logikát eredményez, mint az LTL.

**Alapesetek és Boole-kombinációk** — az LTL-hez hasonlóan, csak $\pi$ helyett $s$-re:
- $M,s \models \top$; $M,s \not\models \bot$
- $M,s \models p \iff p \in L(s)$
- $M,s \models \neg\varphi \iff M,s \not\models \varphi$; hasonlóan $\wedge$, $\vee$ a szokásos módon

**Az $A$ csapat** (minden $s$-ből induló $\pi$ útra, $\pi_0 = s$):
- $M,s \models AX\varphi \iff \forall \pi\ (\pi_0=s):\ M,\pi^1 \models \varphi$
- $M,s \models AF\varphi \iff \forall \pi\ (\pi_0=s)\ \exists i:\ M,\pi^i \models \varphi$
- $M,s \models AG\varphi \iff \forall \pi\ (\pi_0=s)\ \forall i:\ M,\pi^i \models \varphi$
- $M,s \models \varphi AU \psi \iff \forall \pi\ (\pi_0=s)\ \exists i$ úgy, hogy $(\forall j<i:\ M,\pi^j\models\varphi) \wedge (M,\pi^i\models\psi)$

**Az $E$ csapat** (legalább egy $s$-ből induló $\pi$ útra):
- $M,s \models EX\varphi \iff \exists \pi\ (\pi_0=s):\ M,\pi^1 \models \varphi$
- $M,s \models EF\varphi \iff \exists \pi\ (\pi_0=s)\ \exists i:\ M,\pi^i \models \varphi$
- $M,s \models EG\varphi \iff \exists \pi\ (\pi_0=s)\ \forall i:\ M,\pi^i \models \varphi$
- $M,s \models \varphi EU \psi \iff \exists \pi\ (\pi_0=s)\ \exists i$ úgy, hogy $(\forall j<i:\ M,\pi^j\models\varphi) \wedge (M,\pi^i\models\psi)$

**Modellkielégítés és ekvivalencia:**
- $M \models_M \varphi \iff \forall s \in I:\ M,s \models \varphi$. A modell akkor elégít ki egy CTL-formulát, ha minden kezdőállapota kielégíti.
- $\varphi \equiv \psi \iff$ minden $M$-re $(M \models_M \varphi) \Leftrightarrow (M \models_M \psi)$.

### CTL ekvivalenciák

$$AX(\varphi \wedge \psi) \equiv AX\varphi \wedge AX\psi \qquad EX(\varphi \vee \psi) \equiv EX\varphi \vee EX\psi \qquad \neg AX\varphi \equiv EX\neg\varphi$$
$$EF(\varphi \vee \psi) \equiv EF\varphi \vee EF\psi \qquad AG(\varphi \wedge \psi) \equiv AG\varphi \wedge AG\psi$$
$$\neg AF\varphi \equiv EG\neg\varphi \qquad \neg EF\varphi \equiv AG\neg\varphi$$
$$AFAF\varphi \equiv AF\varphi \qquad EFEF\varphi \equiv EF\varphi \qquad AGAG\varphi \equiv AG\varphi \qquad EGEG\varphi \equiv EG\varphi$$

A $\neg AX\varphi \equiv EX\neg\varphi$ pár mutatja az útkvantorok De Morgan-szerű dualitását: "nem igaz, hogy minden útra $\varphi$" ekvivalens azzal, hogy "van olyan út, amelyre nem $\varphi$" — ugyanez a mintázat ismétlődik $\neg AF\varphi \equiv EG\neg\varphi$-ben és $\neg EF\varphi \equiv AG\neg\varphi$-ben.

## Kapocs

- [[concepts/logika/kripke-struktura]] — a modell, amelynek állapotain a CTL-formulák értelmezettek
- [[concepts/logika/ltl]] — a lineáris rokon logika, amelynek formulái útra (nem állapotra) vonatkoznak, és nincs útkvantora
- [[concepts/logika/ltl-ctl-osszehasonlitas]] — a két logika kifejezőereje, nevezetes nem-ekvivalenciái és bonyolultsága
