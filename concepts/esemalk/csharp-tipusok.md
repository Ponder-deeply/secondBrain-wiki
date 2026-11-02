---
tags: [concept]
sources: [elte_eva_ea00_csharp.pdf]
derivation: source
kind: definition
element: earth
updated: 2026-09-30
---

# C# típusok, változók és példányosítás

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
- szövegműveletek: `str.Length`, `str.IndexOf(…)`, `str.Replace(…)`

A konstans literálok is intelligens objektumok, pl. `10.ToString()`,
`"Hello World".Substring(0, 5)`.

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

### Változók és példányosítás

Változókat bármely (nem névtér) blokkon belül létrehozhatunk a programkódban
típus, név és kezdőérték megadásával.

- Pl.: `Int32 myInt = 10;`
- Felhasználás előtt mindenképpen kezdőértéket kell kapnia a változónak.
- Összetett (referencia-) típusok esetén a `new` operátort használjuk, pl.:
  `Stack<Int32> s = new Stack<Int32>();`
- A típusnév feloldható fordítási időben is a `var` kulcsszóval, pl.:
  `var myInt = 10;`
- Típusok futási időben is feloldhatóak (`dynamic`), és manipulálhatóak
  (pl. `ExpandoObject`).
- Konstansokat a `const` kulcsszóval, konstruktorban értékül adható mezőket a
  `readonly` kulcsszóval adhatunk meg.

## Kapocs

- [[concepts/esemalk/csharp-osztaly-szerkezete]] — a `class` és `struct` mint
  referencia-, illetve érték szerint kezelt osztály
