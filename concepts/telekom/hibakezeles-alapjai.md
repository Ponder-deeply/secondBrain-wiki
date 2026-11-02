---
tags: [concept]
sources: [Laki_Lecture_3.pdf]
derivation: source
kind: definition
element: air
updated: 2026-09-25
---

# Hibakezelés alapjai: bithibák, redundancia, paritás

A fizikai világ eredendően zajos (interferencia a kábelek között, áthallás a rádiós átvitelek között, mikrosütő, napviharok), ezért az adatkapcsolati rétegnek fel kell ismernie, és esetleg javítania kell a bithibákat. Ehhez **redundancia** kell: az üzenethez ellenőrző biteket fűzünk, így nem minden bitsorozat lesz érvényes kódszó.

## Tartalom

### Hibatípusok

- **Egyszerű bithiba**: az adategység egy bitje 0-ról 1-re vagy 1-ről 0-ra változik. Példa: küldött `01100010`, vett `01101010`.
- **Csoportos hiba** (*burst error*): a fogadott bitek olyan folytonos sorozata, amelynek első és utolsó szimbóluma hibás, és a két szimbólummal határolt részsorozaton belül nincs olyan $m$ hosszú részsorozat, amelyet helyesen fogadtunk volna. Az $m$ paramétert **védelmi övezetnek** (*guard band*) nevezzük (Gilbert–Elliott modell). Példa $m=3$-ra: ha a hibás bitek között legfeljebb 2 helyes bit van, egyetlen, 5 illetve 7 hosszú burst-ről beszélünk.

### Naiv hibadetektálás

Ötlet: küldjünk minden keretből két példányt, és hasonlítsuk össze őket. Rossz ötlet: **túl magas az ára** (a hatékonyság felére esik), és **gyenge a hibavédelme** — kétszer annyi adat kétszer akkora eséllyel hibásodik meg, és ha mindkét példány ugyanott sérül, észre sem vesszük.

### Stratégiák és célok

| Stratégia | Működés | Mikor célszerű |
|---|---|---|
| **FEC** — *Forward Error Correction*, előre hibajavítás | hibajavító kódokkal a vevő maga javít | kevésbé megbízható csatornán (pl. vezeték nélküli) |
| **ARQ** — *Automatic Repeat Request* | hibadetektálás + újraküldés | megbízható csatornán olcsóbb |

A célok szerint:
- **hibadetektálás javítással** — FEC;
- **hibadetektálás javítás nélkül** — a keretet eldobjuk, majd utólagos javítás vagy a hibás keret újraküldése;
- **hibajavítás detektálás nélkül** — pl. hangátvitelnél, ahol egy kis hiba elfogadható.

### Redundancia és kódszó

Redundancia nélkül $m$ biten $2^m$ üzenet írható le, és mindegyik legális: minden hiba egy újabb legális üzenetet eredményez, a hiba felismerése lehetetlen.

Ezért egy keret felépítése:
- $m$ **adatbit** (az üzenet),
- $r$ **redundáns / ellenőrző bit** — az üzenetből számolt, új információt nem hordoz,
- a teljes hossz $n = m + r$; az így előálló $n$ bites sorozat az $n$ hosszú **kódszó**.

A kód tehát a $2^n$ lehetséges szó egy részhalmaza; csak kódszavakat küldünk. Példa: 3 biten 8 szó, a kód $\{000, 011, 101, 110\}$ (a kocka minden második csúcsa). Ha nem kódszó érkezik, hiba történt. A kódok erejét a [[concepts/telekom/hamming-tavolsag-es-korlat]] méri.

### Paritásbit

Egy extra bitet fűzünk a sorozathoz úgy, hogy az egyesek száma a kódszóban páros (vagy páratlan) legyen:

- **Even parity**: ha az egyesek száma páros, 0-t fűzünk, egyébként 1-et (az eredmény páros sok 1-es).
- **Odd parity**: ha az egyesek száma páratlan, 0-t fűzünk, egyébként 1-et (az eredmény páratlan sok 1-es).

Példa: az `1101011` üzenetben 5 egyes van → odd parity: `11010110`, even parity: `11010111`.

Tulajdonságok: az **1 bites hiba detektálható**, a **2 bites nem** (a paritás visszaáll), **burst hibákra nem megbízható**. A paritásbittel kapott kód Hamming-távolsága 2. Több paritásbit ügyes elhelyezésével javítás is lehetséges: [[concepts/telekom/hamming-kod-keretekben]].

**Vizsgaszempont:** FEC vs. ARQ; a burst-hiba definíciója a védelmi övezettel; paritásbit kiszámítása páros és páratlan paritásra.

## Kapocs

- [[concepts/telekom/hamming-tavolsag-es-korlat]] — felismerhető és javítható hibák száma
- [[concepts/telekom/hamming-kod-keretekben]] — paritásbitekkel javító kód
- [[concepts/telekom/crc]] — polinomiális ellenőrző összeg, burst hibákra is
- [[concepts/telekom/keretezes]] — keretenkénti hibaellenőrzés
