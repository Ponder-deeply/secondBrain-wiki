---
tags: [concept]
sources: [07.jatek.pdf]
derivation: source
kind: model
element: fire
updated: 2026-10-12
---

# Grundy mama játéka

Egy kis kétszemélyes játék (7 érmés kupac), amelyen a kurzus bemutatja az állapot-gráfot, a játékfát és a nyerő stratégia keresését.

## Tartalom

### A játék

Kezdetben egy kupac érme van (a példában 7). A játékosok felváltva lépnek: egy kupacot két **nem egyenlő** nagyságú, nem üres kupacra kell szétosztani. Aki nem tud lépni, veszít. (A szabályok a dia ábráiból olvashatók ki: a végállások `2,1,1,1,1,1`, `2,2,1,1,1`, `2,2,2,1`, ahol csak 1-es és 2-es kupac van, tehát nincs szabályos lépés.)

Kezdő játékos: $A$.

### Állapot-gráf

Az állapot a kupacméretek multihalmaza és a soron következő játékos, pl. `7; A`. A kezdőállásból három lépés lehetséges: `6,1; B`, `5,2; B`, `4,3; B`. Az állapot-gráfban a különböző úton elért azonos állások egy csúcsot alkotnak (pl. `4,2,1; A` három szülőből is elérhető). A végállapotok a diákon:

- `2,1,1,1,1,1; B` — $A$ nyer,
- `3,2,1,1; B` ágán `2,2,1,1,1; A` — $B$ nyer,
- `2,2,2,1; B` — $A$ nyer.

### Játékfa

A [[concepts/mesint/jatekfa]] a gráfot fává bontja: a gyökér `7` ($A$ szintje), alatta a `6,1`, `5,2`, `4,3` ($B$ szintje), és így tovább felváltva. Az ismétlődő állások külön csúcsok. A levelek közül csak két ág nyer $A$-nak: a `6,1 → 5,1,1 → 4,1,1,1 → 3,1,1,1,1 → 2,1,1,1,1,1` és a `5,2 → 3,2,2 → 2,2,2,1`; a többi $B$-nek kedvez.

### Megoldás

$B$ biztosan nyerhet: bármelyik $A$-lépésre van olyan válaszlépése, amely győzelemhez vezet. A `7 → 6,1` ágon is kell $B$-nek válasz minden $A$-lépésre (`5,1,1` után `3,2,1,1`, majd `2,2,1,1,1`). Egyetlen győztes játszma felmutatása nem elég; erről lásd [[concepts/mesint/nyero-strategia]].

## Kapocs

- [[concepts/mesint/ketszemelyes-jatekok]] — a játékosztály
- [[concepts/mesint/jatekfa]] — a fa fogalma
- [[concepts/mesint/nyero-strategia]] — a példa $B$ nyerő stratégiája
