---
tags: [concept]
sources: [07.jatek.pdf]
derivation: source
kind: procedure
element: air
updated: 2026-10-12
---

# Részleges játékfa-kiértékelés

Nagyobb játékfánál a nyerő stratégia keresése reménytelen, ezért az optimális lépés helyett a soron következő jó lépést keressük: a fát csak néhány szintig építjük fel, és a leveleit heurisztikával értékeljük.

## Tartalom

### Alapötlet

- A nyerő vagy nem-vesztő stratégia megkeresése nagyobb játékfánál reménytelen ([[concepts/mesint/nyero-strategia]]).
- A bennünket képviselő játékos neve mostantól **MAX**, az ellenfélé **MIN**.
- Az aktuális állapotból indulva:
  1. néhány szintjét felépíteni a [[concepts/mesint/jatekfa]]nak,
  2. a részfa leveleinek hasznosságát megbecsülni,
  3. majd a soron következő lépést meghatározni (lásd [[concepts/mesint/minimax-algoritmus]]).

### Kiértékelő függvény

Minden esetben szükség van egy [[concepts/mesint/heurisztika]]ra, amely a mi szempontunkból becsüli meg egy állás hasznosságát: $f$: Állások $\to [-1000, 1000]$.

Példák:

- **Sakk** (a fehérnek): $f(s) = $ (fehér királynő száma) $-$ (fekete királynő száma).
- **Tic-tac-toe:** $f(s) = M(s) - O(s)$, ahol $M(s)$ a saját lehetséges győztes vonalaink száma, $O(s)$ az ellenfél lehetséges győztes vonalainak száma. A dia ábráján 6 és 5 az értékek két állásra.

## Kapocs

- [[concepts/mesint/minimax-algoritmus]] — a kiértékelés értékeinek felfuttatása
- [[concepts/mesint/heurisztika]] — a kiértékelő függvény heurisztika
- [[concepts/mesint/jatekfa-kiertekelesi-valtozatok]] — átlagoló és más változatok
- [[concepts/mesint/jatekot-jatszo-program]] — a teljes játékprogram
