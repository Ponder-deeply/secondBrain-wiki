---
tags: [concept]
sources: [07.md, szelmJegyzet.pdf]
derivation: source
updated: 2026-08-05
---

# Többszalagos TG szimulálása egyszalagossal

Minden $k$-szalagos Turing-gép szimulálható egy ekvivalens egyszalagos TG-gel; a konstrukció legfeljebb négyzetes időköltség-növekedéssel jár.

## Tétel (2.7)

Minden $M$ $k$-szalagos TG-hez van vele ekvivalens egyszalagos $M'$ TG (azaz $L(M) = L(M')$). Ha $M$ legalább lineáris időigényű ($f(n) = \Omega(n)$), $M'$ az $O(f(n)^2)$ időkorláttal dolgozik.

## A szimuláció alapötlete

$M'$ egymás után tárolja egyetlen szalagján $M$ szalagjainak tartalmát, `#` elválasztóval:

$$\# \mid \underbrace{a_1 a_2 \ldots a_n}_{\text{1. szalag}} \mid \# \mid \underbrace{\sqcup}_{\text{2. szalag}} \mid \# \mid \cdots \mid \# \mid \underbrace{\sqcup}_{k\text{. szalag}} \#$$

Az aktuális fejpozíciót minden szalag-szegmensben egy `^`-pal megjelölt szimbólum (`â`) reprezentálja; $M'$ szalagábécéje így tartalmazza a `#`-et és $M$ szalagszimbólumainak `^`-jelölt változatait.

## A szimuláció menete

1. $M'$ kezdőkonfigurációja: az inputot az első szegmensbe másolja, a többi szegmens üres (`#`-ekkel elválasztva).
2. **Olvasófázis:** $M'$ végigpásztáz a szalagon, és az állapotában eltárolja minden szegmens dot-jelzett szimbólumát ($k$ db, összesen).
3. **Írófázis:** $M$ átmeneti függvénye alapján $M'$ visszajár, aktualizálja a dot-jelzett szimbólumokat és lépteti a dot-jelzéseket ($L$/$S$/$R$).
4. Ha a dot-jelzés kívülre kerülne a szegmensből, $M'$ a szalagon jobbra tolja a tartalmat, hogy helyet csináljon.

## Időköltség elemzése

- $M'$ szalagjának mérete kezdetben $\Theta(n)$; az $i$-edik lépés után $O(n + f(n))$, mivel lépésenként legfeljebb $k$ cellával nő.
- $M$ egy lépésének szimulálása $M'$-ben: kétszeri átpásztázás, azaz $O(n + f(n))$ lépés.
- $M$ összesen $f(n)$ lépést tesz, tehát $M'$ összesen $O(f(n) \cdot (n + f(n))) = O(f(n)^2)$ lépést tesz (ha $f(n) = \Omega(n)$).

## Kapocs

- [[concepts/bvszam/tobb-szalagos-turing-gep]] — a szimulált modell definíciója
- [[concepts/bvszam/turing-gep]] — az egyszalagos célmodell
- [[concepts/bvszam/aszimptotikus-jeloles]] — $O(f(n)^2)$ időkorlát értelmezéséhez
- [[concepts/bvszam/bonyolultsagelmeleti-osztalyok]] — a szimulációs overhead komplexitásosztályokat befolyásol
