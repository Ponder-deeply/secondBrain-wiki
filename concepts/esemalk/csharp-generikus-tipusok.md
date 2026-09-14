---
tags: [concept]
sources: [elte_eva_ea00_csharp.pdf]
derivation: source
updated: 2026-09-12
---

# C# generikus típusok

Generikus programozásra futási időben feldolgozott sablon típusok
(*generic*-ek) segítségével van lehetőség: osztály, metódus és delegált lehet
sablonos, a sablon (típusparaméter) csak osztály lehet.

## Tartalom

A sablon fordításra kerül, és csak a futásidejű fordításkor helyettesítődik
be a konkrét értékre.

```csharp
struct Rational<T> {
    private T nom; // használható a T típusként
    ...
    public Rational(T n, T d) { ... }
    ...
}
...
Rational<SByte> r1 = new Rational<SByte>(10, 5);
Rational<Int64> r2 = new Rational<Int64>(10, 5);
// különböző értékkészletű racionálisok
```

A szigorú típuskezelés miatt a sablonra csak az `Object`-ben értelmezett
műveletek használhatóak; ezt a műveletkört megszorításokkal (`where`)
növelhetjük:

```csharp
class Rational<T> where T : struct, IComparable,
            IFormattable, IConvertible { ...
    // T elemi osztály, amire használható a fenti
    // interfészek összes művelete
}
```

## Kapocs

- [[concepts/esemalk/csharp-osztalyok]] — a generikus típus is osztály
  (vagy `struct`), csak típusparaméterezve
- [[concepts/esemalk/csharp-interfeszek]] — a `where` megszorítás
  interfészekre hivatkozva bővíti a sablonra alkalmazható műveletkört
- [[subjects/esemalk]] — a kurzus áttekintése
