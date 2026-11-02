---
tags: [concept]
sources: [elte_eva_ea10_avaloniaui_complex.pdf]
derivation: source
kind: procedure
element: earth
updated: 2026-09-30
---

# Avalonia UI témák és stílusok

Az Avalonia UI-alkalmazás alapvető megjelenítését a beállított téma
határozza meg; a stílusok vezérlőkhöz csatolásakor pedig CSS-szerű
szelektorok használhatók, ami eltér a WPF stílusrendszerének
`TargetType`-alapú megközelítésétől.

## Tartalom

### Témák (themes)

A témát jellemzően az alkalmazás szintjén állítjuk be:

```xml
<Application.Styles>
    <FluentTheme />
</Application.Styles>
```

Két beépített téma áll rendelkezésre, illetve további NuGet csomagokból is
elérhetők:

- `SimpleTheme` — egyszerű, minimalista téma
- `FluentTheme` — a Microsoft Fluent Design alkalmazása
- `Material.Avalonia` — a Google Material Design alkalmazása (NuGet csomag)
- `Classic.Avalonia` — Windows 9x-re hasonlító retró téma (NuGet csomag)

### CSS-szerű szelektorok

A `Style.Selector` attribútumban a következő illesztési módok érhetők el:

- típus szerinti illesztés: `<Style Selector="Button">`
- név alapján konkrét vezérlőre illesztés: `<Style Selector="#MyButton">`
- osztállyal (`Classes`) rendelkező vezérlőkre illesztés:
  `<Style Selector="Button.large">`
- hierarchiának megfelelő (leszármazott) vezérlőkre illesztés:
  `<Style Selector="StackPanel Button">`
- tulajdonság alapján illesztés: `<Style Selector="Button[(Grid.Row)=0]">`

### Osztályok adatkötése

A vezérlők `Classes` gyűjteménye statikusan és adatkötéssel (`Binding`) is
megadható, logikai értékek formájában:

```xml
<!-- Classes="Large": nem kondícionális;
     Classes.IsActive: kondícionális osztály,
     adatkötéssel a nézetmodellre -->
<Button ...
    Classes="Large"
    Classes.IsActive="{Binding IsButtonActive}">
<Button.Styles>
    <Style Selector="Button.Large">...</Style>
    <Style Selector="Button.IsActive">...</Style>
</Button.Styles>
</Button>
```

A stílusok `UserControl` szintjén is megadhatók tranzitívan, vagy
`ResourceDictionary`-ben — hasonlóan a WPF-hez.

## Kapocs

- [[concepts/esemalk/wpf-stilusok-alapjai]] — a WPF `Style`/`Setter`,
  implicit és explicit stílusok, `TargetType`-alapú megközelítése, amelynek
  az Avalonia szelektoros rendszere az analógja
- [[concepts/esemalk/wpf-stilus-triggerek]] — a WPF triggerek (`DataTrigger`
  stb.), amelyekhez az Avalonia feltételes osztálykötése (`Classes.X`)
  hasonlítható
- [[concepts/esemalk/wpf-eroforrasok-alapjai]] — a `ResourceDictionary`
  megosztott stílus-/sablonkészletként való használata WPF-ben
- [[concepts/esemalk/avalonia-meret-tajolas-kezeles]] — a tájolásfüggő
  szelektor osztályok (`IsPortrait`/`IsLandscape`) gyakorlati alkalmazása
