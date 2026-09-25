---
tags: [concept, esemalk/csharp-nyelvi-alapok]
sources: [elte_eva_ea00_csharp.pdf]
derivation: source
updated: 2026-09-12
---

# C# nullable típusok

A C# három típuskategóriát különböztet meg — érték, referencia és mutató
szerinti típusokat —, és ehhez kapcsolódik a null-képesség kérdése mindkét fő
kategóriában.

## Tartalom

**A három típuskategória.**

- **érték**: érték szerint kezelendő típusok, mindig másolódnak a
  memóriában, és a blokk végén törlődnek,
- **referencia**: biztonságos mutatókon keresztül kezelt típusok, a
  virtuális gép és a szemétgyűjtő felügyeli és törli őket,
- **mutató**: nem biztonságos mutatók, amelyek csak felügyeletmentes
  (`unsafe`) kódrészben használhatóak.

Az érték szerinti típusok nem vehetnek fel `null` értéket, míg a referencia
szerinti típusok igen.

**Nullable érték szerinti típusok.** A nyelvbe korán (C# 2.0, 2005) bekerült
a *nullable value types* fogalma, a `?` operátorral: az `int` nullable
típusa `int?`, teljes nevén `Nullable<int>`. Az ilyen típusok a megszokott
értékeiken túl a `null` értéket is felvehetik (pl. `bool?` esetén `true`,
`false` vagy `null`), és a nullable értékek default értéke mindig `null`.

A tárolt értéket a `Value` tulajdonság adja meg, a meglétét a `HasValue`
jelzi:

```csharp
if (x.HasValue) // x típusa int?
    int y = x.Value; // x.Value típusa int
```

**Nullable referencia szerinti típusok.** Újabban (C# 8.0, 2019, .NET Core
3) a *nullable reference types* fogalma is elérhető a nyelvben — ez az
elnevezés elsőre félrevezető lehet, hiszen a referencia típusok eddig is
felvehettek `null` értéket. A probléma az, hogy ha nem kezeltük, hogy egy
referencia `null` értéket is felvehet, és mégis dereferáltuk (kiértékeltük,
metódust hívtunk rajta stb.), az `NullReferenceException`-t eredményezett —
ez az egyik legelterjedtebb futásidejű hibatípussá vált az elmúlt években. A
*nullable reference types* funkció ebben hivatott segíteni.

Projekt szinten engedélyezhető, ekkor megkülönböztetjük a `T` és a `T?`
típusokat. Engedélyezni a `.csproj` fájlban lehet; Visual Studio 2022 és
.NET 6 esetén már ez az alapértelmezett:

```xml
<Nullable>enable</Nullable>
```

Ha `null` értéket adunk egy `T` típusú változónak, fordítási idejű
figyelmeztetést kapunk:

```csharp
string str = null; // fordítási idejű hiba
```

Kivétel a *null-forgiving* operátor használata: `string str = null!;`. Ha
elmulasztjuk a `null` ellenőrzést egy `T?` típusú érték dereferálása előtt,
az is fordítási idejű figyelmeztetést eredményez.

## Kapocs

- [[concepts/esemalk/csharp-ertek-referencia-osztalyok]] — az érték és referencia szerinti típusok alapmegkülönböztetése
- [[subjects/esemalk]] — a kurzus áttekintése
