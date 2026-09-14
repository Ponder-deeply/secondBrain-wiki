---
tags: [concept]
sources: [elte_eva_ea00_csharp.pdf]
derivation: source
updated: 2026-09-12
---

# C# interfészek

Az *interfész* (`interface`) egy tisztán absztrakt osztály: deklarációk
halmaza, amelyet osztályok implementálnak — a többszörös öröklődés
kiküszöbölésére szükséges, mivel [[concepts/esemalk/csharp-oroklodes]] C#-ban
csak egyszeres lehet.

## Tartalom

Az interfész csak láthatóságot és tagok szignatúráját tartalmazza, törzs
nélkül; egy osztály (vagy `struct`) tetszőleges számú interfészt
implementálhat, miközben legfeljebb egy ősosztálya lehet.

```csharp
interface IDoubleCompatible {
    Double ToDouble(); // láthatóság, törzs nélkül
}
...
struct Rational : IDoubleCompatible {
    ...
    // interfész megvalósítása:
    public Double ToDouble() { ... }
}
```

Mivel az interfész tisztán absztrakt, önmagában nem példányosítható —
ugyanúgy, ahogy egy absztrakt osztály sem —, csak azt implementáló
konkrét típuson keresztül érhető el a funkcionalitása.

## Kapocs

- [[concepts/esemalk/csharp-oroklodes]] — az interfész a többszörös
  öröklődés hiányát pótolja, egyszeres osztályöröklődés mellett
  implementálható tetszőleges számban
- [[concepts/esemalk/csharp-ertek-referencia-osztalyok]] — `struct` és
  `class` egyaránt implementálhat interfészt
- [[subjects/esemalk]] — a kurzus áttekintése
