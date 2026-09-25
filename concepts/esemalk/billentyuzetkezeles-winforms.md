---
tags: [concept, esemalk/architektura-es-esemenykezeles]
sources: [elte_eva_ea02_winforms_mv.pdf]
derivation: source
updated: 2026-09-12
---

# Billentyűzetkezelés WinForms alkalmazásokban

WinForms alkalmazásokban a billentyűzet lekezelésére a fókuszált vezérlőn van
alapesetben lehetőség, a `PreviewKeyDown`, `KeyDown`, `KeyUp` és `KeyPress`
eseményeken keresztül; az eseményargumentumban (`KeyEventArgs`) megkapjuk a
billentyűzet adatait (`KeyCode`, `KeyData`, `Modifiers`, …).

## Tartalom

A fókuszban lévő vezérlő helyett az ablak (a `Form`) is le tudja kezelni a
billentyű eseményeket:

- az ablaknál engedélyeznünk kell a kezelést a `KeyPreview` tulajdonság
  `true`-ra állításával, különben az ablak nem fogja el az eseményt;
- ha `KeyPreview` be van kapcsolva, az ablak *mellett* a fókuszban lévő
  vezérlő is megkapja az eseményt; ha ezt nem szeretnénk, a
  `KeyEventArgs.SuppressKeyPress = true` beállításával megakadályozható,
  hogy az esemény továbbjusson a vezérlőnek.

Példa (a forrásból):

```csharp
KeyPreview = true;
    // az ablak lekezeli a billentyűzetet
KeyDown += new KeyEventHandler(Form_KeyDown);
    // billentyű lenyomásának eseménye

void Form_KeyDown(object? sender, KeyEventArgs e) {
    if (e.KeyCode == Keys.Enter) // Enter hatására
    {
        … // tevékenység elvégzése
        e.SuppressKeyPress = true;
            // a vezérlő nem kapja meg az eseményt
    }
}
```

A forrás számológép-példájában ez a mintázat szolgál arra, hogy az ablak
szintjén fogott billentyűkódok (pl. `Keys.Add`) közvetlenül a
[[concepts/esemalk/modell-nezet-architektura]] szerinti nézet
(`CalculatorForm`) műveletvégrehajtó alprogramját (`PerformCalculation`)
hívják meg.

## Kapocs

- [[concepts/esemalk/modell-nezet-architektura]] — a nézet komponens, ahol ez
  az eseménykezelés elhelyezkedik
- [[subjects/esemalk]]
