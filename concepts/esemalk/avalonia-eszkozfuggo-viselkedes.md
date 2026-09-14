---
tags: [concept]
sources: [elte_eva_ea10_avaloniaui_complex.pdf]
derivation: source
updated: 2026-09-13
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
    image.Source =
        ImageSource.FromFile("small.jpg");
} else {
    image.Source =
        ImageSource.FromFile("large.jpg");
}
// táblagépen nagyobb képet használunk
```

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
