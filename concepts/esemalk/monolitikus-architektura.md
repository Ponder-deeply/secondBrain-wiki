---
tags: [concept]
sources: [elte_eva_ea02_winforms_mv.pdf]
derivation: source
updated: 2026-09-13
---

# Monolitikus architektúra

A monolitikus architektúra (*monolithic architecture*) a legegyszerűbb
felépítésű szoftver architektúra: nem különíti el egymástól az egyes
feladatköröket, például a megjelenítést, az eseménykezelést és az
adatelérést/adatkezelést — mindezek egyetlen, osztatlan "alkalmazás"
komponensben helyezkednek el, amellyel a felhasználó közvetlenül
kommunikál.

## Tartalom

Egyszerű alkalmazásoknál a monolitikus felépítés kényelmes, de összetettebb
programoknál korlátozza:

- az áttekinthetőséget és tesztelhetőséget (pl. nehezen látható át, hol
  tároljuk a számításokhoz szükséges adatokat),
- a módosíthatóságot és bővíthetőséget (pl. nehezen lehet a felület
  kinézetét módosítani),
- az újrafelhasználhatóságot (pl. komponens kiemelése és áthelyezése másik
  alkalmazásba).

Ez a felhalmozódó "technikai adósság" (*technical debt*) az az ár, amelyet a
kezdetben egyszerűbb, de rétegzetlen felépítésért fizetünk. A korlátok
feloldására szolgál a feladatkörök szétválasztása, aminek legegyszerűbb
formája a [[concepts/esemalk/modell-nezet-architektura]].

## Kapocs

- [[concepts/esemalk/modell-nezet-architektura]] — a monolitikus felépítés
  korlátait feloldó, rétegzett alternatíva
- [[concepts/esemalk/haromreteg-architektura]] — a modell/nézet felbontás
  továbbfejlesztése, amely a perzisztenciát is önálló rétegként kezeli
- [[subjects/esemalk]]
