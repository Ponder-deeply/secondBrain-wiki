---
tags: [concept]
sources: [07.jatek.pdf]
derivation: source
kind: definition
element: air
updated: 2026-10-12
---

# Kétszemélyes játékok

A kétszemélyes, teljes információjú, véges, determinisztikus, zéró összegű játékok a játékkeresés alapmodellje: két játékos felváltva lép, a végállapotban az egyik nyer, a másik veszít.

## Tartalom

### A játékosztály jellemzői

- Két játékos lép felváltva adott szabályok szerint, amíg a játszma véget nem ér.
- **Teljes információ:** mindkét játékos ismeri a maga és az ellenfele összes múltbeli és jövőbeli lépését, lépési lehetőségét és azok következményeit.
- **Véges, determinisztikus:** minden lépés véges számú lehetőség közül választható, minden játszma véges lépésben véget ér; a véletlennek nincs szerepe.
- **Zéró összegű:** amennyit a játszma végén az egyik játékos nyer, annyit veszít a másik. Legegyszerűbb változatban kétesélyes (egyik nyer, másik veszít), vagy háromesélyes (döntetlen is megengedett).

### Állapottér-modell

A játék a [[concepts/mesint/allapotter-modell]] szerint írható le:

| Elem | Jelentés |
|---|---|
| állapot | állás + soron következő játékos |
| művelet | lépés |
| kezdő állapot | kezdőállás + kezdő játékos |
| végállapot | végállás + játékos |

**Payoff függvény:** $p_A, p_B$: végállapot $\to \mathbb{R}$ (a játékosok $A$ és $B$). Zéró összegű kétszemélyes játékban $p_A(t) + p_B(t) = 0$ minden $t$ végállapotra.

A továbbiakban a speciális esetet feltételezzük: $p_A(t) = +1$, ha $A$ nyer; $-1$, ha $A$ veszít; $0$, ha döntetlen.

Szemléltető példa: [[concepts/mesint/grundy-mama-jateka]]. A játék lehetséges lefolyásait a [[concepts/mesint/jatekfa]] írja le.

## Kapocs

- [[concepts/mesint/jatekfa]] — a játék állapotgráfjának fává kiterített alakja
- [[concepts/mesint/nyero-strategia]] — a játék megoldásának fogalma
- [[concepts/mesint/allapotter-modell]] — a játék ennek a modellnek az esete
- [[concepts/mesint/grundy-mama-jateka]] — alappélda
