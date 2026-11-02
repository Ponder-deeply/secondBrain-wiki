---
tags: [concept]
sources: [07.jatek.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-10-12
---

# Minimax algoritmus

A minimax algoritmus a részleges játékfa leveleinek kiértékelt értékeit felfuttatja a fában: saját (MAX) szinten maximumot, az ellenfél (MIN) szintjén minimumot vesz, és a legnagyobb értékű gyerek felé lép.

## Tartalom

### Lépések

1. A játékfának az adott állás csúcsából leágazó részfáját felépítjük néhány szintig.
2. A részfa leveleit kiértékeljük a kiértékelő függvény segítségével ([[concepts/mesint/reszleges-jatekfa-kiertekeles]]).
3. Az értékeket felfuttatjuk a fában:
   - MAX szintek csúcsaihoz a gyerekeinek maximuma: $szülő := \max(gyerek_1, \dots, gyerek_k)$,
   - MIN szintek csúcsaihoz a gyerekeinek minimuma: $szülő := \min(gyerek_1, \dots, gyerek_k)$.
4. Soron következő lépésünk ahhoz az álláshoz vezet, ahonnan a gyökérhez felkerült a legnagyobb érték.

### Példa

A dia fája (MAX, MIN, MAX, MIN szintek): a levelek balról `-2 7 2 -4 | 8 -1 -2 | 6 5 6 | 12 23 10`. A legalsó MAX-szint értékei: $7, 8, 6, 23$. A MIN szinten: $\min(7, 8) = 7$ és $\min(6, 23) = 6$. A gyökérben $\max(7, 6) = 7$, tehát a bal oldali lépést választjuk.

### Megjegyzés: ismétlés

Az algoritmust minden alkalommal megismételjük, valahányszor mi következünk, mert az ellenfél nem biztos, hogy a várt legerősebb lépéssel válaszol: eltérő mélységű részfával dolgozik, más kiértékelő függvényt használ, nem minimax eljárást alkalmaz, vagy hibázik.

## Kapocs

- [[concepts/mesint/reszleges-jatekfa-kiertekeles]] — a fa felépítése és a kiértékelő függvény
- [[concepts/mesint/jatekfa-kiertekelesi-valtozatok]] — átlagoló kiértékelés stb.
- [[concepts/mesint/negamax-algoritmus]] — egyszerűsített írásmód
- [[concepts/mesint/alfa-beta-algoritmus]] — a minimax gyorsítása vágással
- [[concepts/mesint/jatekot-jatszo-program]] — a lépésismétlés a programban
