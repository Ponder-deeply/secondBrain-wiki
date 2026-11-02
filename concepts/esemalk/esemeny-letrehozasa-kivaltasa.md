---
tags: [concept]
sources: [elte_eva_ea02_winforms_mv.pdf, elte_eva_gy03_munkafuzet.pdf]
derivation: source
kind: procedure
element: earth
updated: 2026-10-21
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
szokás védeni, általában külön metódusban. Az esemény csak a deklaráló
osztályon belül váltható ki (kívülről csak fel- és leiratkozni lehet rá),
ezért a kiváltó kód az `EventClass` egy metódusában áll:

```csharp
if (MyEvent != null)
    // ha van hozzárendelve eseménykezelő
    MyEvent(this, new MyEventArgs{ … });
    // kiváltjuk: a küldő az aktuális objektum,
    // az eseményargumentumokat megadjuk
```

A szintaxis egyszerűsíthető a *null-conditional operator* (`?.`)
használatával, amellyel egy objektum tagja csak akkor kerül kiértékelésre, ha
az objektum nem `null` érték volt:

```csharp
MyEvent?.Invoke(this, new MyEventArgs{ … });
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

### Push és pull stílusú események, őrfeltétel (3. gyakorlat)

- *Pull*: az esemény csak jelez (`EventArgs.Empty`), a nézet kiolvassa a modell tulajdonságát — egyszerű, sok összefüggő adatnál kényelmes.
- *Push*: egyedi `EventArgs` szállítja az adatot (csak olvasható tulajdonságok); a kezelő mindig érvényes adatot kap, nem kell a modellre hivatkoznia.
- Az állapotváltozást jelző esemény csak tényleges változáskor váltódjon ki (a setter `if (_value == value) return;`), különben a felesleges értesítések fölösleges frissítéseket okoznak.
- Haladást jelző esemény sok, gyors egymásutánban kiváltott eseményt jelent; ilyenkor ritkítani kell (pl. századonként). Részletek: [[concepts/esemalk/docustat-winforms-nezet-esemenyek]], [[concepts/esemalk/docustat-tobbfajlos-aszinkron-betoltes]].

## Kapocs

- [[concepts/esemalk/modell-nezet-architektura]] — a mintázat tipikus
  alkalmazási helye: a modell jelzése a nézet felé
- [[subjects/esemalk]]
