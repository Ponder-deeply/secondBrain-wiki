---
tags: [concept, esemalk/csharp-nyelvi-alapok]
sources: [elte_eva_ea00_csharp.pdf]
derivation: source
updated: 2026-09-12
---

# C# megjegyzések

A C# kétféle megjegyzést különböztet meg: az egyszerű megjegyzések fordításkor
törlődnek, a *dokumentációs megjegyzések* viszont fordításra kerülnek, és
utólag előhívhatóak a lefordított tartalomból.

## Tartalom

**Egyszerű megjegyzések.** Sor végéig tartó (`// megjegyzés`), vagy
tetszőleges határok között (`/* megjegyzés */`).

**Dokumentációs megjegyzések.** Osztályok és tagjaik deklarációjánál
használhatók; céljuk az automatikus dokumentálás elősegítése és a
fejlesztőkörnyezetben azonnali segítség megjelenítése. A `///` jeltől a sor
végéig tart, belül XML blokkok adhatók meg, amelyek meghatározzák az
információ jelentését (pl. `<summary>`, `<remarks>`, `<param>`).

```csharp
/// <summary>
/// Racionális szám típusa.
/// </summary>
/// <remarks>Két egész szám hányadosa.</remarks>
struct Rational {
    ...
    /// <summary>
    /// Racionális szám példányosítása.
    /// </summary>
    /// <param name="n">Számláló.</param>
    /// <param name="d">Nevező.</param>
    public Rational(Int32 n, Int32 d) { ... }
    ...
}
```

## Kapocs

- [[concepts/esemalk/csharp-eloforditasi-direktivak]] — a régiókhoz
  hasonlóan a megjegyzések sem befolyásolják a lefordított kódot
- [[concepts/esemalk/csharp-osztaly-szerkezete]] — dokumentációs
  megjegyzések osztályok és tagjaik deklarációjánál
- [[subjects/esemalk]] — a kurzus áttekintése
