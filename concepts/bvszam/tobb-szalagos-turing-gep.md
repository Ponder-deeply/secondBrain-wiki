---
tags: [concept]
sources: [07.md, szelmJegyzet.pdf]
derivation: source
updated: 2026-08-05
---

# Többszalagos Turing-gép ($k$-szalagos TG)

A $k$-szalagos Turing-gép ($k \ge 1$) az egyszalagos modell általánosítása: $k$ darab független szalaggal és szalagonként egy-egy író-olvasó fejjel rendelkezik. Ekvivalens számítási erejű az egyszalagos TG-gel, de időbonyolultsági szempontból hatékonyabb lehet.

## Definíció

$$M = (Q, \Sigma, \Gamma, \delta, q_0, q_i, q_n)$$

A komponensek a $\delta$ kivételével megegyeznek az egyszalagos TG komponenseivel; az átmenetfüggvény:
$$\delta : (Q \setminus \{q_i, q_n\}) \times \Gamma^k \to Q \times \Gamma^k \times \{L, R, S\}^k$$

Ha $\delta(q, a_1, \ldots, a_k) = (p, b_1, \ldots, b_k, D_1, \ldots, D_k)$, akkor $q$ állapotban, ha a szalagjain rendre az $a_1, \ldots, a_k$ betűket olvassa, a gép át tud menni $p$ állapotba, miközben $a_1, \ldots, a_k$-t a $b_1, \ldots, b_k$ betűkre átírja, és a fejeket a $D_1, \ldots, D_k$ irányokba mozgatja.

A konfiguráció, a konfiguráció-átmenet, valamint a felismert és eldöntött nyelv az egyszalagos eset értelemszerű általánosítása. Az időigény is az egyszalagoshoz hasonlóan van definiálva.

> Egy $L$ nyelv *$f(n)$ időben eldönthető*, ha eldönthető egy $f(n)$ időkorlátos (akár többszalagos) TG-vel.

## Átmenetdiagram

$$q \xrightarrow{a_1, \ldots, a_k /\; b_1, \ldots, b_k,\; D_1, \ldots, D_k} p$$

## Példa: $L = \{ww^{-1} \mid w \in \{a,b\}^*\}$, $k=2$

A 2-szalagos TG az inputot olvassa, miközben a második szalagra másolja; ha a másolás $q_1$-ben (páratlan hossz) ér véget, $q_n$-be lép. Egyébként a második szalagon visszamegy a szó elejére, majd az első szalagon balra, a másodikon jobbra lépkedve karakterenként összehasonlítja a betűket. Időigénye egy $n$ hosszú szón legfeljebb $3n + 3$, tehát $L$ egy $O(n)$, azaz **lineáris időben eldönthető** nyelv — szemben az egyszalagos $O(n^2)$-es megoldással.

## Kapocs

- [[concepts/bvszam/turing-gep]] — az egyszalagos alap modell
- [[concepts/bvszam/turing-gep-szimulacio]] — $k$-szalagos TG szimulálása egyszalagossal $O(f(n)^2)$ időben
- [[concepts/bvszam/turing-gep-egyiranyu-szalag]] — egyirányban végtelen szalagos változat
- [[concepts/bvszam/nemdeterminisztikus-turing-gep]] — másik általánosítás
- [[concepts/bvszam/aszimptotikus-jeloles]] — az időigény mérőeszköze
