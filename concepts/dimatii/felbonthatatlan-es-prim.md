---
tags: [concept]
sources: [DimatIIEa01.pdf, DimatIIEa02.pdf]
derivation: source
updated: 2026-09-08
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

## Kapocs

- [[concepts/dimatii/egyseg-es-asszocialt]] — a triviális osztók, amelyekre a felbonthatatlanság definíciója épül
- [[concepts/dimatii/bovitett-euklideszi-algoritmus]] — a megfordítás bizonyításának eszköze
- [[concepts/dimatii/szamelmelet-alaptetele]] — a prímfelbontás egzisztenciája és egyértelműsége
- [[concepts/dimatii/primek-eloszlasa]] — hány prím van és hogyan keressük őket
- [[concepts/dimatii/oszthatosag]] — az alapreláció
