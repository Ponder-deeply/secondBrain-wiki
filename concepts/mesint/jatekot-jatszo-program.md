---
tags: [concept]
sources: [07.jatek.pdf]
derivation: source
kind: overview
element: air
updated: 2026-10-12
---

# Kétszemélyes játékot játszó program

A játékprogram a kiértékelési technikákat keretprogramba, felhasználói felülettel és kiegészítő funkciókkal építi össze.

## Tartalom

- A program **váltakozó mélységű, szelektív, $(m,n)$ átlagoló, negamax alfa-béta kiértékelést** végez ([[concepts/mesint/jatekfa-kiertekelesi-valtozatok]], [[concepts/mesint/negamax-algoritmus]], [[concepts/mesint/alfa-beta-algoritmus]]).
- **Keretprogram**, amely váltakozva fogadja a felhasználó lépéseit, és generálja a számítógép lépéseit.
- **Kiegészítő funkciók**: beállítások, útmutató, segítség, korábbi lépések tárolása, mentés stb.
- **Felhasználói felület**, grafika.
- **Heurisztika megválasztása**: kiértékelő függvény, szelekció, kiértékelés sorrendje.

### Megjegyzés

Az algoritmust minden alkalommal megismételjük, amikor mi következünk, mert az ellenfél nem biztos, hogy a várt legerősebb lépéssel válaszol: eltérő mélységű részfával dolgozik, más kiértékelő függvényt használ, nem minimax eljárást alkalmaz, vagy hibázik.

## Kapocs

- [[concepts/mesint/ketszemelyes-jatekok]] — a modellezett játékosztály.
- [[concepts/mesint/reszleges-jatekfa-kiertekeles]] — a kiértékelés alapja.
- [[concepts/mesint/minimax-algoritmus]] — az alapeljárás.
