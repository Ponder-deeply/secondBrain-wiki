---
tags: [concept]
sources: [07.md, szelmJegyzet.pdf]
derivation: source
updated: 2026-08-05
---

# Turing-gép (TG)

A Turing-gép az egyik legáltalánosabb algoritmusmodell: véges sok állapotú vezérlő, ami egy kétirányban végtelen, cellákra osztott szalagon dolgozik egy író-olvasó fejjel. A Church–Turing tézis szerint minden algoritmikusan megoldható probléma TG-vel megoldható.

## Definíció

A Turing-gép olyan $M = (Q, \Sigma, \Gamma, \delta, q_0, q_i, q_n)$ rendszer, ahol:

- $Q$ — az *állapotok* véges, nemüres halmaza
- $q_0, q_i, q_n \in Q$ — a *kezdő-*, az *elfogadó* és az *elutasító* állapot
- $\Sigma$ — a *bemenő jelek* ábécéje
- $\Gamma$ — a *szalagszimbólumok* ábécéje, $\Sigma \subseteq \Gamma$, és $\Gamma - \Sigma$ tartalmaz egy speciális *üres* szimbólumot ($\sqcup$)
- $\delta : (Q - \{q_i, q_n\}) \times \Gamma \to Q \times \Gamma \times \{L, R, S\}$ — az *átmenetfüggvény*

A fej egy lépésben olvas/ír egy cellát, és balra ($L$), jobbra ($R$) lép vagy helyben marad ($S$). Kezdetben a szalagon csak a bemenő szó van (cellánként egy betű), a többi cella $\sqcup$; a fej a bemenő szó első betűjén áll, a gép $q_0$-ban van.

## Konfiguráció és számítás

Egy $M$ *konfigurációja* olyan $uqav$ szó, ahol $q \in Q$, $a \in \Gamma$, $u, v \in \Gamma^*$ (a tényleges definícióban a fej alatti $a$ kiemelve). A szalag tartalma $uav$ (előtte és utána csak $\sqcup$), a gép $q$ állapotban van, a fej az $a$ betűn áll.

**Kezdőkonfiguráció:** $q_0 u \sqcup$, ahol $u$ csak $\Sigma$-beli betűket tartalmaz.

A *konfiguráció-átmenet* ($\vdash$) — legyen $uqav$ konfiguráció:
1. $\delta(q,a) = (r,b,S)$ esetén $uqav \vdash urbv$
2. $\delta(q,a) = (r,b,R)$ esetén $uqav \vdash ubrv'$, ahol $v' = v$ ha $v \ne \varepsilon$, különben $v' = \sqcup$
3. $\delta(q,a) = (r,b,L)$ esetén $u'cqav \vdash u'rcbv$, ahol $u'c = u$ ($c \in \Gamma$) ha $u \ne \varepsilon$, különben $u' = \varepsilon$, $c = \sqcup$

$\vdash^*$ a $\vdash$ reflexív, tranzitív lezártja. Ha $q \in \{q_i, q_n\}$, a konfiguráció *megállási konfiguráció* (elfogadó, ill. elutasító).

## Felismert nyelv

$$L(M) = \{u \in \Sigma^* \mid q_0 u \sqcup \vdash^* x q_i y \text{ valamely } x, y \in \Gamma^*, y \ne \varepsilon\}$$

Ha $M$ nem fogad el egy $u$ bemenetet, akkor vagy elutasítja (véges sok lépés után elutasító konfigurációba lép), **vagy nem áll meg** rajta.

- $L \subseteq \Sigma^*$ *Turing-felismerhető*, ha $L = L(M)$ valamely $M$ TG-re — ezek a **rekurzívan felsorolható** nyelvek, osztályuk **RE**.
- $L$ *eldönthető*, ha létezik olyan $M$ TG, ami felismeri $L$-et és **minden** bemeneten megáll — ezek a **rekurzív** nyelvek, osztályuk **R**.

## Időigény

- $M$ *időigénye az $u$ szón* $n$, ha $M$ a $q_0 u \sqcup$ kezdőkonfigurációból $n$ lépésben megállási konfigurációba jut (ha nincs ilyen, az időigény $u$-n végtelen).
- $M$ *$f(n)$ időkorlátos gép* ($f : \mathbb{N} \to \mathbb{N}$), ha minden $u$ input szóra $M$ időigénye legfeljebb $f(l(u))$, ahol $l(u)$ a szó hossza.
- Egy $L$ nyelv *$f(n)$ időben eldönthető*, ha eldönthető egy $f(n)$ időkorlátos (akár többszalagos) TG-vel.

## Church–Turing tézis

Minden intuitív értelemben vett algoritmus megvalósítható Turing-géppel. Nem bizonyítható tétel, hanem elfogadott azonosítás.

## Kapocs

- [[concepts/bvszam/kiszamithatosagelmelet-tortenete]] — Turing 1936-os modellje, a tézis háttere
- [[concepts/bvszam/r-re-nyelvek]] — R és RE osztályok, megállási probléma
- [[concepts/bvszam/nemdeterminisztikus-turing-gep]] — NTG, nemdeterminizmus
- [[concepts/bvszam/tobb-szalagos-turing-gep]] — $k$-szalagos általánosítás
- [[concepts/bvszam/turing-gep-egyiranyu-szalag]] — egyirányban végtelen szalagos változat
- [[concepts/bvszam/turing-gep-szimulacio]] — többszalagos ↔ egyszalagos szimulálás
- [[concepts/bvszam/turing-gep-kodolas]] — TG-k bináris kódolása
- [[concepts/bvszam/chomsky-hierarchia]] — $\mathcal{L}_0 = \text{RE}$ a hierarchia csúcsán
- [[concepts/bvszam/aszimptotikus-jeloles]] — időigény mérésének eszköztára
