---
tags: [concept]
sources: [szelmJegyzet.pdf, 08.md, 08.md]
derivation: source
updated: 2026-08-05
---

# Megállási probléma

A megállási probléma azt kérdezi, hogy egy adott $M$ Turing-gép megáll-e egy adott $w$ bemeneten; ez a kérdés algoritmikusan eldönthetetlen, bár felismerhető.

## Definíció

$$L_h = \{\langle M, w \rangle \mid M \text{ megáll a } w \text{ bemeneten}\}$$

azon $\langle M, w \rangle$ kódolt párok nyelve, amelyekre az $M$ gép megáll (elfogadó vagy elutasító állapotban) a $w$ bemeneten. A Church–Turing tézis miatt ez azt is jelenti, hogy nem tudjuk eldönteni tetszőleges programról (C++, Pascal stb.), hogy megáll-e adott bemeneten.

## Tétel: $L_h \in \mathrm{RE} \setminus \mathrm{R}$

### $L_h \notin \mathrm{R}$ — visszavezetés $L_u \leq L_h$

Adott $\langle M, w \rangle$ párhoz konstruáljuk meg az $M'$ gépet, amely a $w$ bemeneten:

1. Futtatja $M$-et $w$-n (meghívja az $U$ univerzális Turing-gépet az $\langle M, w \rangle$ szóra).
2. Ha $M$ elfogadja $w$-t, akkor $M'$ is elfogadja.
3. Ha $M$ elutasítja $w$-t, akkor $M'$ olyan állapotba lép, ahol végtelen ciklusban lépteti a fejet jobbra — tehát **soha nem áll meg**.

Az $\langle M, w \rangle \mapsto \langle M', w \rangle$ leképezés kiszámítható, és
$$\langle M, w \rangle \in L_u \iff \langle M', w \rangle \in L_h.$$
Mivel $L_u \notin \mathrm{R}$, a [[concepts/bvszam/visszavezetes|2.19. tétel]] alapján $L_h \notin \mathrm{R}$.

### $L_h \in \mathrm{RE}$ — visszavezetés $L_h \leq L_u$

Tetszőleges $\langle M, w \rangle$ párhoz legyen $\langle M', w \rangle$, ahol $M'$-t úgy kapjuk $M$-ből, hogy minden $q_n$-be (elutasító) vezető átmenetét $q_i$-be (elfogadó) irányítjuk. Ekkor $M$ megáll $w$-n pontosan akkor, ha $M'$ elfogadja $w$-t, azaz $\langle M, w \rangle \in L_h \iff \langle M', w \rangle \in L_u$. Mivel $L_u \in \mathrm{RE}$, a 2.19. tétel 2. pontja alapján $L_h \in \mathrm{RE}$.

## Kapocs

- [[concepts/bvszam/univerzalis-turing-gep]] — $L_u$, a visszavezetések kiindulópontja
- [[concepts/bvszam/visszavezetes]] — many-one visszavezetés, a 2.19. tétel
- [[concepts/bvszam/r-re-nyelvek]] — R és RE osztályok
- [[concepts/bvszam/eldonthetetlen-problemak]] — további eldönthetetlen problémák
