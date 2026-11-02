---
tags: [concept]
sources: [DimatIIEa01.pdf, DimatIIEa02.pdf, Lehman-Leighton-Meyer-Mathematics-for-Computer-Science.pdf, Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf, dm2gy06_2020_Algebra.pdf]
derivation: source
kind: comparison
element: water
updated: 2026-10-21
---

# Felbonthatatlan és prím

Két különböző fogalom, amely az egész számok körében egybeesik: a felbonthatatlanság a szám osztóiról, a prímtulajdonság a szám osztási viselkedéséről szól.

## Tartalom

### A két definíció

**Definíció (felbonthatatlan).** Ha egy nem nulla, nem egység számnak a triviális osztóin kívül nincs más osztója, akkor **felbonthatatlannak** (*irreducibilisnek*) nevezzük. Ekvivalensen: $t$ felbonthatatlan, ha $t = ab \Rightarrow a$ vagy $b$ egység.

**Definíció (prím).** Egy nem nulla, nem egység $p$ számot **prímszámnak** nevezünk, ha
$$p \mid ab \;\Rightarrow\; p \mid a \ \text{ vagy } \ p \mid b.$$

**Példák.** $2, -2, 3, 5, -5$ felbonthatatlanok és prímek is. $6$ egyik sem: nem felbonthatatlan, mert $6 = 2\cdot 3$; és nem prím, mert $6 \mid 2 \cdot 3$, de $6 \nmid 2$ és $6 \nmid 3$.

### Minden prím felbonthatatlan

**Állítás.** Minden prímszám felbonthatatlan.

**Bizonyítás.** Legyen $p$ prím és $p = ab$ egy felbontás. Mivel $p = ab$, így $p \mid ab$, ahonnan például $p \mid a$. Ekkor $a = pk = a(bk)$, azaz $bk = 1$, tehát $b$ (és $k$) egység. $\square$

Ez az irány minden integritási tartományban igaz.

### A megfordítás $\mathbb{Z}$-ben

A fordított irány **nem** általánosan igaz: $\mathbb{Z}$-ben igen, de például $\{a + bi\sqrt{5} \,:\, a, b \in \mathbb{Z}\}$-ben nem.

**Tétel.** Minden felbonthatatlan egész szám prímszám.

**Bizonyítás.** Legyen $p$ felbonthatatlan, és legyen $p \mid ab$. Tegyük fel, hogy $p \nmid b$. Ekkor $p$ és $b$ relatív prímek, így a [[concepts/dimatii/bovitett-euklideszi-algoritmus]] szolgáltat olyan $x, y$ egészeket, melyekre $px + by = 1$. Innen $pax + aby = a$. Mivel $p$ osztója a bal oldal mindkét tagjának ($p \mid p a x$ és $p \mid ab \mid aby$), így osztja a jobb oldalt is: $p \mid a$. $\square$

A két fogalom egybeesése az, ami a [[concepts/dimatii/szamelmelet-alaptetele]] egyértelműségi részét lehetővé teszi.

### Euklidész-lemma a legnagyobb közös osztóval (Lehman–Leighton–Meyer 9.4.1)

Az $\mathbb{Z}$-beli bizonyítás röviden: ha $p$ prím és $p \mid ab$, akkor vagy $(a,p) = p$ ($p \mid a$), vagy $(a,p) = 1$, és $1 = sa + tp$ alapján $b = s(ab) + (tb)p$ osztható $p$-vel. A bizonyítás a lnko lineáris kombináció-tulajdonságát használja, ezért nem hivatkozhat a prímfelbontás egyértelműségére.

### Általános integritási tartományban (előadásdiák)

*(Farkas Gábor előadásdiái.)* Legyen $R$ tetszőleges egységelemes integritási tartomány, $a \in R^* \setminus U(R)$.

- $a$ **felbonthatatlan** (irreducibilis), ha $a = bc \Rightarrow b$ **vagy** $c$ egység (a „vagy” kizáró értelmű); $\mathbb{N}$-ben ez a törzsszám.
- $a$ **prím**, ha $a \mid bc \Rightarrow a \mid b \vee a \mid c$.
- $a$ **összetett**, ha nem csak triviális osztója van.

**Tétel.** $R$-ben minden prím felbonthatatlan. *Bizonyítás.* Legyen $p$ prím, $p = bc$. Ekkor $p \mid bc$, így (mondjuk) $p \mid b$, $b = pq$. Innen $b = pq = b(cq)$, tehát $cq = 1$ (egyszerűsítés integritási tartományban), azaz $c, q$ egységek és $p, b$ asszociáltak. $\square$

**Tétel.** $\mathbb{Z}$-ben $p$ akkor és csak akkor prím, ha felbonthatatlan. A fordított irány az előadásdiák szerint: legyen $p$ felbonthatatlan, $p \mid bc$. Ha $p \mid b$, kész. Ha $p \nmid b$, akkor $(p,b) = 1$, így $1 = px + by$ és $c = pcx + bcy \equiv 0 \pmod p$, azaz $p \mid c$.

**Észrevétel.** $(a,b) = 1 \wedge a \mid bc \Rightarrow a \mid c$ (ugyanezzel az érveléssel, Bézout-azonosságból).

### Euklideszi gyűrűben

*(Farkas Gábor előadásdiái, 8.2.33.)* Euklideszi gyűrűben a megfordítás is igaz: egy elem pontosan akkor felbonthatatlan, ha prím — a bizonyítás ugyanaz a bővített euklideszi algoritmus-os érv; részletek: [[concepts/dimatii/euklideszi-gyuru-egyertelmu-felbontas]].

### Feladattípusok és módszerek: $\bar5$ a $\mathbb{Z}_{10}$-ben (gyakorlati feladatsor, 2020 ősz, 6. sor)

A $\mathbb{Z}_{10}$ nem integritási tartomány, ezért a két fogalom szétválik. $\bar5$ nem egység, nem nulla.

- **Nem felbonthatatlan:** $\bar5=\bar5\cdot\bar5$ ($25\equiv5$), és $\bar5$ nem egység. (Más felbontás: $\bar3\cdot\bar5=\bar5$, de $\bar3$ egység.)
- **Prím:** $\bar5 \mid ab$ azt jelenti, hogy $ab\in\{\bar0,\bar5\}$. Ha $ab=\bar5$, mindkét tényező páratlan, és $\bar5$-tel osztható valamelyik (egységek szorzata egység lenne); ha $ab=\bar0$, valamelyik tényező $5$ többszöröse. Tehát $\bar5\mid a$ vagy $\bar5\mid b$ (ellenőrizhető az összes $a,b$ párra).

Tanulság: nullosztómentes gyűrűben minden prím felbonthatatlan, de nullosztós gyűrűben egy prím lehet felbontható.

## Kapocs

- [[concepts/dimatii/egyseg-es-asszocialt]] — a triviális osztók, amelyekre a felbonthatatlanság definíciója épül
- [[concepts/dimatii/bovitett-euklideszi-algoritmus]] — a megfordítás bizonyításának eszköze
- [[concepts/dimatii/szamelmelet-alaptetele]] — a prímfelbontás egzisztenciája és egyértelműsége
- [[concepts/dimatii/primek-eloszlasa]] — hány prím van és hogyan keressük őket
- [[concepts/dimatii/oszthatosag]] — az alapreláció
