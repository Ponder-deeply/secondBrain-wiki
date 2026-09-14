---
tags: [concept]
sources: [elte_eva_ea02_winforms_mv.pdf]
derivation: source
updated: 2026-09-13
---

# Modell/nézet architektúra

A modell/nézet (MV, *model-view*) architektúra a legegyszerűbb felbontás, amely
leválasztja a felhasználói felület megjelenítését a háttérbeli
tevékenységektől, ezzel oldva a [[concepts/esemalk/monolitikus-architektura]]
korlátait.

## Tartalom

Összetettebb alkalmazásoknál az egyrétegű (monolitikus) felépítés korlátozza a
program áttekinthetőségét és tesztelését, módosíthatóságát és
bővíthetőségét, valamint újrafelhasználhatóságát. A szoftver architektúra
megválasztása a fejlesztés során meghozott elsődleges tervezési döntés,
amely kihat a rendszer felépítésére, viselkedésére, kommunikációjára,
nem funkcionális jellemzőire és megvalósítására — későbbi megváltoztatása a
szoftver jelentős újratervezését vonná maga után.

A modell/nézet architektúrában:

- a **modell** tartalmazza a háttérben futó logikát: a tevékenységek
  végrehajtását, az állapotkezelést és az adatkezelést. Ezt nevezzük
  *alkalmazáslogikának* vagy *üzleti logikának*.
- a **nézet** tartalmazza a grafikus felhasználói felület megvalósítását,
  beleértve a vezérlőket és eseménykezelőket.
- a felhasználó a nézettel kommunikál; a modell és a nézet egymással
  kommunikál.
- a modell nem függ a nézettől: függetlenül, önmagában is felhasználható,
  ezért könnyen átvihető másik alkalmazásba, és más felülettel is
  üzemképes.

### Példa: számológép

A forrás egy egyszerű számológép architektúráját mutatja be MV felbontásban:

- `CalculatorModel` — a modell, amely végrehajtja a műveletet (`Calculate`),
  tárolja az eredményt (`Result`) és a művelet szöveges leírását
  (`CalculationString`).
- `CalculatorForm` — a nézet, amely a modellt példányosítja és használja; a
  gombok eseménykezelése mellett a billentyűzetet is kezeli, a tevékenység
  végrehajtását külön alprogramba (`PerformCalculation`) helyezve.

Egy továbbfejlesztett változatban a modell saját eseményt (`CalculationPerformed`)
vált ki a számítás befejezésekor egy egyedi eseményargumentum-típussal
(`CalculatorEventArgs`, amely az eredményt és a szöveges leírást hordozza) —
így a nézetnek nem kell lekérdeznie a számítás eredményét, hanem
automatikusan megkapja. Lásd
[[concepts/esemalk/esemeny-letrehozasa-kivaltasa]] az esemény
létrehozásának és kiváltásának technikájáról.

Az itt bemutatott kétrétegű felbontás továbbfejleszthető úgy, hogy a
perzisztens adattárolást is leválasztjuk a modellről — ez a
[[concepts/esemalk/haromreteg-architektura]].

## Kapocs

- [[concepts/esemalk/monolitikus-architektura]] — az MV architektúra által
  kiváltott, egyszerűbb, de kevésbé karbantartható felépítés
- [[concepts/esemalk/haromreteg-architektura]] — a perzisztencia réteg
  leválasztásával kapott, továbbfejlesztett architektúra
- [[concepts/esemalk/esemeny-letrehozasa-kivaltasa]] — hogyan jelez a modell a
  nézet felé saját esemény segítségével
- [[concepts/esemalk/billentyuzetkezeles-winforms]] — a nézet oldali
  eseménykezelés egyik formája a példában
- [[subjects/esemalk]]
