---
tags: [concept]
sources: [08.evolucio.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-10-12
---

# Mutáció

A mutáció egy egyed (utód) kis mértékű, véletlen megváltoztatása; kódolásfüggő operátor.

## Tartalom

A mutáció egy utódot kis mértékben, véletlenszerűen módosít. Megvalósítása a [[concepts/mesint/evolucios-kodolas]]-tól függ:

- **Valós tömbös kódolás**, kis $p$ valószínűséggel:
  $$\forall i = 1 \dots n:\; z_i = x_i \pm domain_i \cdot p$$
  ahol $domain_i$ az $i$-edik komponens értékkészletének mérete.
- **Bináris tömbös kódolás**, kis $p$ valószínűséggel:
  $$\forall i = 1 \dots n:\; z_i = 1 - x_i \text{, ha } random[0..1] < p$$
  vagyis minden bitet $p$ valószínűséggel átbillentünk.
- **Permutáció** esetén (a permutáció tulajdonság megmarad):
  - egy jelpár cseréje, vagy
  - egy kódszakaszon a jelek ciklikus léptetése, megfordítása vagy átrendezése.

## Kapocs

- [[concepts/mesint/rekombinacio-es-keresztezes]] — a másik változtató operátor
- [[concepts/mesint/evolucios-algoritmus]] — az algoritmus ciklusának lépése
- [[concepts/mesint/evolucios-kodolas]] — a mutáció formáját a kódolás szabja meg
- [[concepts/mesint/visszahelyezes]] — a mutált utódok bekerülése a populációba
