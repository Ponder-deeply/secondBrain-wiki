---
tags: [concept, esemalk/csharp-nyelvi-alapok]
sources: [elte_eva_ea00_csharp.pdf]
derivation: source
updated: 2026-09-12
---

# Névterek (C#)

A névterek biztosítják a kód logikai felbontását: minden osztálynak névtérben
kell elhelyezkednie.

## Tartalom

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

### Névterek automatikus használata

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

## Kapocs

- [[concepts/esemalk/csharp-nyelv-jellemzoi]] — a Hello World példa névtér-
  használata
