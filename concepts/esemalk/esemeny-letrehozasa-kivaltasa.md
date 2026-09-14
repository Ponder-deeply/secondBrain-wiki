---
tags: [concept]
sources: [elte_eva_ea02_winforms_mv.pdf]
derivation: source
updated: 2026-09-12
---

# Esemény létrehozása és kiváltása C#-ban

Saját C# esemény (*event*) definiálásához és kiváltásához egyedi
eseményargumentum-típus, esemény-deklaráció és a kiváltást védő
null-ellenőrzés szükséges — ez teszi lehetővé, hogy egy komponens (pl. egy
[[concepts/esemalk/modell-nezet-architektura]] szerinti modell) jelezzen a
figyelői felé anélkül, hogy ismerné őket.

## Tartalom

### Egyedi eseményargumentum

Amennyiben adatokat szeretnénk továbbítani az eseménnyel, célszerű saját
argumentumtípust létrehozni az `EventArgs` típusból származtatva:

```csharp
class MyEventArgs : EventArgs {
    Object SomeData { get; set; }
}
```

A saját eseményargumentumot (vagy általánosabban bármilyen típust) sablon-
paraméterként rögzíthetjük az esemény delegáltjában:

```csharp
class EventClass {
    event EventHandler<MyEventArgs> MyEvent;
}
```

### Esemény kiváltása

Az esemény kiváltása az esemény meghívásával történik, ahol átadjuk a
megfelelő paramétereket. Esemény csak akkor váltható ki, ha van hozzárendelve
eseménykezelő — különben az esemény `null` értéknek felel meg, és ennek
meghívása kivételt dob. Emiatt a kiváltást explicit `null`-ellenőrzéssel
szokás védeni, általában külön metódusban:

```csharp
if (ec.MyEvent != null)
    // ha van hozzárendelve eseménykezelő
    ec.MyEvent(this, new MyEventArgs{ … });
    // kiváltjuk: a küldő az aktuális objektum,
    // az eseményargumentumokat megadjuk
```

A szintaxis egyszerűsíthető a *null-conditional operator* (`?.`)
használatával, amellyel egy objektum tagja csak akkor kerül kiértékelésre, ha
az objektum nem `null` érték volt:

```csharp
ec.MyEvent?.Invoke(this, new MyEventArgs{ … });
// kiváltjuk az eseményt,
// ha van hozzárendelve eseménykezelő
```

C# 8.0 vagy újabb verzió esetén, ha *nullable reference types* van
használatban, érdemes az esemény delegáltjának típusát ennek megfelelően
`nullable`-nek jelölni (`event EventHandler<MyEventArgs>? MyEvent;`) — így
fordítási időben figyelmeztetést kapunk, ha ellenőrizetlen módon váltanánk ki
egy eseményt.

### Példa

A forrás számológép-példájában a modell (`CalculatorModel`) egy
`CalculationPerformed` eseményt vált ki a számítás befejezésekor, egyedi
`CalculatorEventArgs` argumentummal (amely az eredményt és a szöveges
leírást hordozza), így a nézetnek (`CalculatorForm`) nem kell lekérdeznie a
számítás eredményét — automatikusan megkapja azt az eseményen keresztül.

## Kapocs

- [[concepts/esemalk/modell-nezet-architektura]] — a mintázat tipikus
  alkalmazási helye: a modell jelzése a nézet felé
- [[subjects/esemalk]]
