---
tags: [concept]
sources: [elte_eva_ea10_avaloniaui_complex.pdf]
derivation: source
kind: procedure
element: earth
updated: 2026-09-30
---

# Avalonia UI eszközfüggő viselkedés (eszközkezelés)

Az Avalonia UI-alkalmazások táblagépes és mobil környezetben is futhatnak,
és mindkettőben megfelelő megjelenítést kell biztosítani. Az eszköz típusát
kódból és XAML-ből is lekérdezhetjük, és ez alapján eltérő értékeket vagy
viselkedést adhatunk meg.

## Tartalom

### Eszköztípus lekérdezése kódból

Az `OperatingSystem` típus segítségével kódból lekérhető az aktuális eszköz
típusa, és arra megfelelően reagálhatunk:

```csharp
if (OperatingSystem.IsAndroid() ||
    OperatingSystem.IsIOS()) {
    image.Source = new Bitmap(AssetLoader.Open(
        new Uri("avares://MyApp/Assets/small.jpg")));
} else {
    image.Source = new Bitmap(AssetLoader.Open(
        new Uri("avares://MyApp/Assets/large.jpg")));
}
// táblagépen nagyobb képet használunk
```

A diasoron itt a MAUI-s `ImageSource.FromFile(…)` szerepel, ami Avaloniában
nem létezik; ott a képet `Bitmap`-ként, az `AssetLoader` segítségével
töltjük be.

### Eszközfüggő értékek XAML-ből (`OnPlatform`)

A nézetből az `OnPlatform` jelölőnyelvi kiterjesztéssel (markup extension)
az eszköznek megfelelő értékeket adhatjuk át, az alapértelmezett és a
platformspecifikus értékek megadásával:

```xml
<Label FontSize="{OnPlatform 12, Windows=24}" />
```

A vezérlők bármely tulajdonsága, akár a tartalmuk is testreszabható ilyen
módon, elemi (nem attribútum) szintaxissal:

```xml
<StackPanel>
    <OnPlatform>
        <OnPlatform.Default>
            ...
        </OnPlatform.Default>
        <OnPlatform.Windows>
            ...
        </OnPlatform.Windows>
    </OnPlatform>
</StackPanel>
```

## Kapocs

- [[concepts/esemalk/avalonia-xaml-felulet]] — az `.axaml` felületleírás
  alapjai, amelyre az `OnPlatform` kiterjesztés épül
- [[concepts/esemalk/avalonia-projekt-felepites]] — a közös és
  platformspecifikus programegységek szerkezete, amelyhez az eszközfüggő
  viselkedés kapcsolódik
- [[concepts/esemalk/avalonia-meret-tajolas-kezeles]] — a méret- és
  tájolásfüggő viselkedés, amely gyakran az eszköztípussal együtt kezelendő
