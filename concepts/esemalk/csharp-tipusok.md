---
tags: [concept, esemalk/csharp-nyelvi-alapok]
sources: [elte_eva_ea00_csharp.pdf]
derivation: source
updated: 2026-09-12
---

# Típusok (C#)

A C# nyelv szigorúan típusos: minden érték típusa fordítási időben ismert, és
a nyelv nem enged meg értékvesztést. Minden típus objektumorientáltan van
megvalósítva, és része a teljes származtatási hierarchiának.

## Tartalom

### Típuskategóriák

A nyelv három típuskategóriát különböztet meg:

- **érték** (`struct`): érték szerint kezelendő típusok, mindig másolódnak a
  memóriában, és a blokk végén törlődnek.
- **referencia** (`class`): biztonságos mutatókon keresztül kezelt típusok, a
  virtuális gép és a szemétgyűjtő felügyeli és törli őket.
- **mutató**: nem biztonságos mutatók, amelyek csak felügyeletmentes
  (`unsafe`) kódrészben használhatóak.

### Primitív típusok

A primitív típusok két névvel rendelkeznek: C# programozási nyelvi név és
.NET könyvtárbeli megfelelő típusnév.

| Kategória | C# nevek | .NET nevek |
|---|---|---|
| logikai | `bool` | `Boolean` |
| egész | `sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong` | `SByte`, `Byte`, `Int16`, `UInt16`, `Int32`, `UInt32`, `Int64`, `UInt64` |
| lebegőpontos | `float`, `double` | `Single`, `Double` |
| tizedestört | `decimal` | `Decimal` |
| karakter | `char` | `Char` |
| objektum (minden osztály őse) | `object` | `Object` |
| szöveg | `string` | `String` |

A primitív típusok is „intelligensek": számos műveletet és speciális
értéklekérdezést támogatnak, pl.:

- speciális értékek: `Int32.MaxValue`, `Double.NaN`, `Double.PositiveInfinity`,
  `String.Empty`
- konverziós műveletek: `Double.Parse(…)`
- karakterműveletek: `Char.ToLower(…)`
- szövegműveletek: `str.Length`, `str.Find(…)`, `str.Replace(…)`

A konstans literálok is intelligens objektumok, pl. `10.ToString()`,
`"Hello World".SubString(0, 5)`.

### Típuskezelés és típuskonverzió

Nagyobb halmazra implicit típuskonverzió, kompatibilis halmazra explicit
típuskonverzió használható, pl.:

```csharp
int x = 1; double y = 2; string z;
y = x;      // implicit típuskonverzió
x = (int)y; // explicit típuskonverzió
z = (string)y; // hiba, nem kompatibilisek
```

Primitív típusok konverziójához a `Convert` osztály, illetve egyéb metódusok
is rendelkezésre állnak, pl.:

```csharp
x = Convert.ToInt32(y);
z = Convert.ToString(y); // vagy y.ToString();
x = Convert.ToInt32(z);  // vagy Int32.Parse(z);
```

## Kapocs

- [[concepts/esemalk/csharp-osztalyok]] — a `class` és `struct` mint
  referencia-, illetve érték szerint kezelt osztály
- [[concepts/esemalk/csharp-valtozok-peldanyositas]] — típusok példányosítása
