---
tags: [concept, esemalk/architektura-es-esemenykezeles]
sources: [elte_eva_ea04_winforms_architecture_testing.pdf]
derivation: source
updated: 2026-09-13
---

# Erőforrások felszabadítása (`IDisposable`, `using`)

A .NET-ben a referencia szerinti változók törlését a szemétgyűjtő (*garbage
collector*, GC) felügyeli, ez azonban nem garantálja az erőforrások
(fájlkezelők, hálózati kapcsolatok stb.) időben történő felszabadítását —
erre az `IDisposable` interfész és a `using` utasítás ad determinisztikus
megoldást.

## Tartalom

A szemétgyűjtő adott algoritmussal, adott időközönként pásztázza a
memóriát, és törli a felszabadult objektumokat. Sok, erőforrás-igényes
objektum példányosítása esetén azonban a GC nem mindig reagál időben,
így nőhet a memóriahasználat; a `GC` osztály segítségével
beavatkozhatunk a működésébe.

Manuális törlésre (destruktor futtatására) nincs lehetőség felügyelt
blokkban, de erőforrások felszabadítására igen, amennyiben az osztály
megvalósítja az `IDisposable` interfészt, és benne a `Dispose()`
metódust.

### A `using` utasítás

A C# nyelv tartalmaz egy blokk-kezelési technikát, amely garantálja a
`Dispose()` automatikus futtatását:

```csharp
using (<objektum példányosítása>)
{
    <objektum használata>
} // itt automatikusan meghívódik a Dispose()
```

Például:

```csharp
using (StreamReader reader = new StreamReader(…)){
    // a StreamReader is IDisposable
    …
}
// itt biztosan bezáródik a fájl, és
// felszabadulnak az erőforrások
```

A `using` használata megfeleltethető a következő `try`-`finally`
blokknak:

```csharp
StreamReader reader = new StreamReader(…);
try {
    // reader használata …
}
finally {
    if (reader != null)
        ((IDisposable)reader).Dispose();
}
```

## Kapocs

- [[concepts/esemalk/stream-alapu-fajlkezeles]] — a `StreamReader`/
  `StreamWriter`, amelyek `IDisposable`-ként tipikusan `using`-gal
  kerülnek lezárásra
- [[concepts/esemalk/csharp-kivetelkezeles]] — a `try`/`finally` szerkezet,
  amelynek a `using` egy speciális esete
- [[concepts/esemalk/tictactoe-haromreteg-pelda]] — a `TextFilePersistence`
  megvalósítása `using`-gal
- [[subjects/esemalk]]
