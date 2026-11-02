---
tags: [concept]
sources: [08.evolucio.pdf]
derivation: source
kind: definition
element: air
updated: 2026-10-12
---

# Visszahelyezés

A visszahelyezés a populáció frissítése az utódokkal: kiválasztja a lecserélendő egyedeket, és azok helyére a kiválasztott utódokat teszi.

## Tartalom

A visszahelyezés (a generációváltás) két rátával jellemezhető:

- **utódképzési ráta**: $u = \dfrac{\text{utódok száma}}{\text{populáció száma}}$
- **visszahelyezési ráta**: $v = \dfrac{\text{lecserélendő egyedek száma}}{\text{populáció száma}}$

A folyamathoz két szelekció kell: az egyik a lecserélendő egyedeket, a másik (szükség esetén) a bekerülő utódokat választja ki — lásd [[concepts/mesint/szelekcio]].

Esetek:

- ha $u = v$, akkor feltétlen cseréről van szó (minden utód bekerül);
- ha $u < v$, akkor egy utód több példánya is bekerülhet (további szelekció a bekerülő utódok között);
- ha $u > v$, akkor az utódok közül szelektálni kell (további szelekció).

## Kapocs

- [[concepts/mesint/szelekcio]] — mind a szülők, mind a lecserélendők kiválasztása szelekció
- [[concepts/mesint/rekombinacio-es-keresztezes]] — az utódok előállítása
- [[concepts/mesint/mutacio]] — az utódok módosítása a visszahelyezés előtt
- [[concepts/mesint/evolucios-algoritmus]] — az algoritmus ciklusa
