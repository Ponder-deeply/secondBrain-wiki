---
tags: [concept, esemalk/csharp-nyelvi-alapok]
sources: [elte_eva_ea00_csharp.pdf]
derivation: source
updated: 2026-09-12
---

# Osztályok (C#)

A .NET platform és a C# programozási nyelv tisztán objektumorientált, ezért
minden érték objektum, és minden típus egy osztály.

## Tartalom

- Az osztály lehet érték szerint (`struct`), vagy referencia szerint kezelt
  (`class`); utóbbi élettartama független a blokktól.
- Az osztály tagjai lehetnek mezők, metódusok, események, tulajdonságok
  (*property*), illetve más (beágyazott) osztályok.
  - A tulajdonság lényegében a lekérdező (`get`) és beállító (`set`)
    műveletek absztrakciója.
- Minden tagnak, és az osztálynak is jelöljük a láthatóságát (`public`,
  `private`, `protected`, `internal`); minden tag a `.` operátorral érhető el.

## Kapocs

- [[concepts/esemalk/csharp-tipusok]] — a `class`/`struct` mint a referencia-
  illetve érték szerinti típuskategória megvalósítása
- [[concepts/esemalk/csharp-valtozok-peldanyositas]] — osztálypéldányok
  létrehozása a `new` operátorral
