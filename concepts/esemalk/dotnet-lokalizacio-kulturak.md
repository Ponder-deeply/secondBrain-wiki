---
tags: [concept, esemalk/lokalizacio]
sources: [elte_eva_ea12_localization.pdf]
derivation: source
updated: 2026-09-13
---

# .NET alkalmazások lokalizációja

Az alkalmazás lokalizációja (*application localization*) azt jelenti, hogy az
alkalmazás a felhasználó nyelvén kommunikál, és annak megfelelő nyelvi
környezetet (számformátum, pénznem, dátumformátum stb.) használja. A .NET
platform ezt egységes módon, a `System.Globalization` névtérben kezeli.

## Tartalom

### Nyelvi környezet (`CultureInfo`)

Az alkalmazás nyelvi környezetét a `CultureInfo` típus reprezentálja, amely
bárhol elérhető és módosítható:

- `CultureInfo.CurrentCulture` — a formázási konvenciókat (naptár, dátum,
  szám, tizedesvessző) meghatározó kulturális beállítás
- `CultureInfo.CurrentUICulture` — a megjelenített (fordított) szövegeket
  meghatározó nyelvi beállítás

Az alkalmazás alapértelmezésben átveheti a rendszer nyelvi környezetét, de ez
felülírható is, pl.:

```csharp
CultureInfo info = new CultureInfo("en-US");
// amerikai lokalizáció betöltése
```

A kultúra kódja két részből áll: nyelv és terület (ország) szerint, pl.
`en-US` (angol, Egyesült Államok), `en-GB` (angol, Egyesült Királyság),
`hu-HU` (magyar, Magyarország). A beállított `CultureInfo`-n keresztül
érhetők el a lokális formázási információk is: `Calendar` (naptár),
`DateTimeFormat` (időformátum), `NumberFormat` (számformátum),
`NumberFormat.NumberDecimalSeparator` (tizedes elválasztó).

### Lokalizált erőforrások (`.resx`)

A megjelenített, nyelvfüggő tartalmakat (szöveg, kép) lokalizált
erőforrásfájlokból (*resource file*, `.resx`) lehet betölteni. Az
erőforrásfájlból generált osztály statikus tulajdonságaiként hivatkozhatók a
benne tárolt értékek — az erőforrásfájl neve lesz az osztály neve, a kulcs a
tulajdonság neve:

```csharp
nameLabel.Text = AppText.NameText;
// az AppText.resx fájl NameText kulcsú szövegének betöltése,
// és a címkére állítása
```

Egy erőforrásfájl több nyelvi változatban is elkészíthető úgy, hogy a
lokalizáció (kultúra) nevét hozzáillesztjük a fájlnévhez:

```
AppText.resx        // alapértelmezett szövegek
AppText.hu-HU.resx   // magyar környezetre
AppText.en-US.resx   // amerikai nyelvi környezetre
```

Futás közben a rendszer a beállított nyelvi környezetnek megfelelő
erőforrásfájl tartalmát tölti be. Ha a lokalizációnak megfelelő fájl nem
található, vagy nincs benne megadva a keresett kulcs, a lokalizáció nélküli
(alapértelmezett) erőforrásfájl tartalma töltődik be — ezért célszerű minden
esetben elkészíteni egy alapértelmezett `.resx` fájlt is a lokalizált
változatok mellé. Az erőforrások kezelésére (pl. dinamikus betöltésére)
további lehetőségeket a `ResourceManager` típus biztosít.

## Kapocs

- [[concepts/esemalk/dotnet-eroforraskezeles]] — az erőforrásfájlok (`.resx`)
  általános szerepe a projektben (content vs. embedded resource); ez a lap a
  kultúra-specifikus (lokalizációs) felhasználásukat mutatja be
- [[concepts/esemalk/xaml-lokalizacio-x-static]] — a lokalizált erőforrások
  megjelenítése WinForms tervezőfelületen, illetve WPF/Avalonia XAML-ban
- [[subjects/esemalk]] — a kurzus áttekintése
