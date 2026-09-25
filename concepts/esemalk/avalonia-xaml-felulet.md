---
tags: [concept, esemalk/avaloniaui-alapok]
sources: [elte_eva_ea09_avaloniaui.pdf]
derivation: source
updated: 2026-09-13
---

# Avalonia grafikus felület és XAML

Az Avalonia UI alkalmazások egységes, *Google Skia* alapú grafikus
felülettel rendelkeznek, amelyet — a WPF-hez hasonlóan — deklaratív módon,
XAML szintaxissal írhatunk le.

## Tartalom

### `.axaml` fájlok

A felületleíró fájlok kiterjesztése `.axaml`, de a `.xaml`-tól való
eltérésnek csak technikai (Visual Studio integrációs) oka van — nyelvtanilag
ugyanaz a XAML, mint a WPF-ben (lásd [[concepts/esemalk/wpf-xaml-nyelv]]).

A felület platformtól függően ablakokból (asztali alkalmazás, `Window`) vagy
nézetekből (mobil alkalmazás, `UserControl`) áll. Amennyiben egyszerre
asztali- és mobilplatformot is támogatunk, a felületet a nézetekben
(`UserControl`) valósítjuk meg, ezeket ágyazzuk közvetlenül az ablakokba
(`Window`) — így elkerülhető a kódredundancia a nézet rétegben.

Példa (`MainView.axaml`):

```xml
<UserControl xmlns=https://github.com/avaloniaui
             ...
             x:Class="MyApp.Views.MainView">

    <TextBlock Text="Hello Avalonia UI!"
               HorizontalAlignment="Center"
               VerticalAlignment="Center" />

</UserControl>
```

Ezt egy `Window` ágyazza be (`MainWindow.axaml`):

```xml
<Window xmlns="https://github.com/avaloniaui"
        ...
        xmlns:views="clr-namespace:MyApp.Views"
        x:Class="MyApp.Views.MainWindow">

        <views:MainView />

</Window>
```

### Vezérlők

Az Avalonia UI felületi vezérlői és lehetőségeik ismerősek lehetnek a WPF
keretrendszerből, de eltérések is adódnak. Széles körű beépített vezérlő áll
rendelkezésre az Avalonia dokumentációjában
(`docs.avaloniaui.net/docs/basics/user-interface/controls/builtin-controls`):

- **megjelenítők**: `TextBlock`, `Label`, `AutoCompleteBox`, stb.
- **nyomógombok**: `Button`, `ToggleButton`, `RadioButton`, stb.
- **csoportos megjelenítők**: `ListBox`, `ItemsControl`, stb.
- **beviteli vezérlők**: `TextBox`, `Slider`, `Calendar`, stb.
- **elrendezők**: `Canvas`, `Grid`, `StackPanel`, `WrapPanel`, stb.

Ez a vezérlőkészlet a WPF [[concepts/esemalk/wpf-panelek]] és
[[concepts/esemalk/wpf-vezerlok-tulajdonsagai]] lapokon leírt vezérlőkkel
mutat rokonságot, de az Avalonia saját, Skia-alapú rajzolási rétege miatt a
konkrét megjelenítés és néhány vezérlő viselkedése eltérhet.

## Kapocs

- [[concepts/esemalk/wpf-xaml-nyelv]] — a WPF XAML nyelve, amelynek az
  Avalonia `.axaml`-ja nyelvtanilag megfelel
- [[concepts/esemalk/wpf-panelek]] — a WPF elrendező vezérlői, összevetésül
- [[concepts/esemalk/wpf-vezerlok-tulajdonsagai]] — a WPF vezérlők közös
  tulajdonságai, összevetésül
- [[concepts/esemalk/avalonia-projekt-felepites]] — a nézet réteg helye a
  projekt szerkezetében
- [[concepts/esemalk/avalonia-mvvm-adatkotes]] — a nézet kötése a
  nézetmodellhez
- [[subjects/esemalk]]
