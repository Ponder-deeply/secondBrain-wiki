---
tags: [concept]
sources: [07.jatek.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-10-12
---

# Negamax algoritmus

A negamax a minimax egyszerűbben implementálható alakja: a MIN szintjeinek értékeit $-1$-gyel szorozva minden szinten ugyanazt a maximumképzést használjuk.

## Tartalom

### Eljárás

1. Kezdetben $(-1)$-gyel szorozzuk azon levélcsúcsok értékeit, amelyek az ellenfél (MIN) szintjein vannak.
2. Az értékek felfuttatásánál minden szinten a belső csúcsok értékét így számoljuk:

$$szülő := \max(-gyerek_1, \dots, -gyerek_k)$$

A minimaxszal azonos eredményt ad, de nincs külön MAX- és MIN-szabály.

### Példa

A dia fája (gyökér MAX, négy szint). A MIN-szint leveleinek eredeti értékei (pl. $-2, 7, 2, -4$ és $12, 23, 10$) mellé a $(-1)$-gyel szorzott értékek kerülnek ($2, -7, -2, 4$, illetve $-12, -23, -10$); a belső csúcsokban a fenti képlettel számolt értékek: $7$, $8$, $23$ (MAX csúcsok), $-7$, $-6$ (MIN csúcsok). A gyökérben $7$ adódik, a bal oldali lépéssel, vagyis ugyanaz, mint a minimaxnál.

## Kapocs

- [[concepts/mesint/minimax-algoritmus]] — az eredeti, két szabályos alak.
- [[concepts/mesint/alfa-beta-algoritmus]] — a vágás ugyanerre a fára.
- [[concepts/mesint/jatekot-jatszo-program]] — a programok negamax kiértékelést használnak.
