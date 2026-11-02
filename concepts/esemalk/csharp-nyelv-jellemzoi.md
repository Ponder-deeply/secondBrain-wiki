---
tags: [concept]
sources: [elte_eva_ea00_csharp.pdf]
derivation: source
kind: overview
element: air
updated: 2026-09-25
---

# C# nyelv jellemzői

A *C#* tisztán objektumorientált programozási nyelv, amely teljes mértékben a
[[concepts/esemalk/csharp-dotnet-platform]]ra támaszkodik. Ez a lap a nyelv
alapjellemzői mellett a névtereket és a vezérlési szerkezeteket is tárgyalja.

## Tartalom

### Alapjellemzők

- Szintaktikailag nagyrészt C++, megvalósításában (viselkedésében) Java.
- Egyszerűsített szerkezet, strukturált felépülés névterekkel.
- Tisztán objektumorientált, egyszeres öröklődéssel — minden típus egy .NET
  osztály, vagy annak leszármazottja.
- Támogatja a sablon- (generikus), eseményvezérelt és funkcionális
  programozást is.
- Forrásfájl kiterjesztése: `.cs`. Kódolás: Unicode 3.0.

### A „Hello, World!” program

```csharp
using System; // névtér használatba vétele

namespace Hello // névtér
{
    class HelloWorld // osztály
    {
        static void Main() // statikus főprogram
        {
            Console.WriteLine("Hello, World!");
            // kiírás konzol képernyőre (a Console
            // osztály statikus WriteLine metódusa)
        }
    }
}
```

A belépési pont egy statikus `Main` metódus, amely egy osztály tagja.

### Top level statements

A C# nyelv .NET 6-os verziója (nyelvi verzió 10.0) óta a belépési pontot
tartalmazó fájl procedurális szintaxissal is elkészíthető: valójában ilyenkor
is objektum-orientált program készül, a fordító kódgenerálása révén. Hasznos
lehet egyszerűbb programokhoz és kezdő programozóknak, pl.:

```csharp
using System;
Console.WriteLine("Hello, World!");
```

### Verziótörténet

| Verzió | Év | | Verzió | Év |
|---|---|---|---|---|
| C# 1.0 | 2002 | | C# 7.0 | 2017 |
| C# 2.0 | 2005 | | C# 8.0 | 2019 |
| C# 3.0 | 2007 | | C# 9.0 | 2020 |
| C# 4.0 | 2010 | | C# 10.0 | 2021 |
| C# 5.0 | 2012 | | C# 11.0 | 2022 |
| C# 6.0 | 2015 | | C# 12.0 | 2023 |

A Visual Studio 2022 alapértelmezett nyelvi verziói célplatformonként
eltérőek: .NET Framework esetén C# 7.3, .NET Core 3.1 esetén C# 8.0, .NET
Standard 2.1 esetén C# 8.0, .NET 8 esetén C# 12.0.

### Névterek

A névterek biztosítják a kód logikai felbontását: minden osztálynak névtérben
kell elhelyezkednie.

- Hierarchikusan egymásba ágyazhatóak, ponttal jelölve (pl. `System.Collections.Generic`).
- Van egy globális névtér is (`global`).
- Névtereket a `using <névtér>;` utasítással lehet használatba venni; az
  utasítás hatóköre a fájl. Pl.:

```csharp
using System;
using System.Collections.Generic;
```

- Az osztálynév elé is megadható a névtér (így nem szükséges `using`), pl.:

```csharp
System.Console.WriteLine("Hello, World!");
```

#### Névterek automatikus használata

.NET 6 óta lehetőség van a leggyakrabban használt névterek automatikus
betöltésére: az `<ImplicitUsings>enable</ImplicitUsings>` direktívát kell
elhelyezni a projektállományban (`.csproj`). Projekttípustól függően tölt be
automatikusan névtereket — konzolos alkalmazásoknál például:

```csharp
using System;
using System.IO;
using System.Collections.Generic;
using System.Linq;
using System.Net.Http;
using System.Threading;
using System.Threading.Tasks;
```

### Vezérlési szerkezetek

A C# nyelv vezérlési szerkezetei a szekvenciától a bejáró cikluson át
szokásos, C-szerű elemkészletet nyújtanak.

- **Szekvencia**: a `;` tagolja az utasításokat.
- **Programblokk**: `{ <utasítások> }`
- **Elágazás**: lehet kétágú (`if`), illetve többágú (`switch`); utóbbinál az
  ágakat le kell zárni (`break`, `goto`, `return`).
- **Ciklus**:
  - számláló (`for`), előtesztelő (`while`), utántesztelő (`do … while`)
  - bejáró (egy `IEnumerable` gyűjtemény elemein halad végig):

    ```csharp
    foreach (<deklaráció> in <gyűjtemény>)
        <utasítás>;
    ```

## Kapocs

- [[concepts/esemalk/csharp-dotnet-platform]] — a nyelv a .NET platform
  köztes nyelvére (IL) fordul, a CLR alatt fut
- [[concepts/esemalk/csharp-osztaly-szerkezete]] — az osztály mint minden típus alapja
- [[concepts/esemalk/csharp-tipusok]] — az `IEnumerable` gyűjtemény elemeinek
  típusa a bejáró ciklusban
