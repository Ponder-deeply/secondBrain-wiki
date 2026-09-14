---
tags: [concept]
sources: [elte_eva_ea09_avaloniaui.pdf]
derivation: source
updated: 2026-09-13
---

# Avalonia MVVM architektúra és adatkötés

Az Avalonia UI támogatja az MVVM (modell/nézet/nézetmodell) architektúra
alapú fejlesztést; ennek eszköze a nézet oldali adatkötés (`Binding`).

## Tartalom

Az adatkötés (`Binding`) a nézet oldalon érhető el, amelynek megadhatunk
tetszőleges forrást a `DataContext` tulajdonság segítségével. Minden
vezérlőnek külön is megadható forrás a saját `DataContext` tulajdonságán
keresztül — az érték öröklődik a vizuális fában lefelé, amíg felül nem
írják.

Az elnevezett elemekre (`x:Name`) is hivatkozhatunk a kötésben
(`x:Reference`), például:

```xml
<TextBox x:Name="MyTextBox" />
<Label Text="{Binding #MyTextBox.Text.Length}" />
<!-- a címke a szövegdoboz tartalmának hosszát jelenítse meg -->
```

Ez az `x:Reference` / `#name` szintaxis lehetővé teszi, hogy a nézet egy
másik, elnevezett elemének tulajdonságához kössünk anélkül, hogy a
nézetmodellben külön tulajdonságot kellene létrehozni hozzá.

Az architektúra a WPF MVVM mintájával azonos elveken nyugszik (lásd
[[concepts/esemalk/wpf-mvvm-alapok]] és
[[concepts/esemalk/wpf-adatkotes-alapjai]]): a nézetmodellt az alapvető
eszközök (`ICommand`, `INotifyPropertyChange`, stb.) segítségével építjük
fel, és a nézetmodell réteg — megfelelő tervezés esetén — kompatibilis a
WPF és a MAUI alkalmazások nézetmodell rétegével. Az Avalonia projekt
sablon (Template Studio) létrehozásakor tervezési mintaként (*design
pattern*) választható például a *Community Toolkit*, amely a
[[concepts/esemalk/avalonia-mvvm-toolkit]] lapon tárgyalt MVVM Toolkit-nak
felel meg (illetve a WPF-es
[[concepts/esemalk/wpf-mvvm-tamogato-csomagok]] lapon tárgyalt megfelelője).

### Az alkalmazás vezérlése és a nézet kiválasztása

Az alkalmazás egészének vezérlését az `App` osztály látja el. A nézet
adatforrását (a nézetmodellt) a nézet `DataContext` tulajdonságán keresztül
adhatjuk meg — jellemzően az `App` osztályban, az alkalmazás indulásakor.

A nézet kiválasztása azonban már függ az alkalmazás életciklusától
(*application lifetime*):

- **asztali alkalmazásban** (`IClassicDesktopStyleApplicationLifetime`)
  tetszőlegesen sok ablakunk lehet, de egy fő ablakot kötelezően meg kell
  adnunk (`MainWindow`)
- **mobil alkalmazásban** (`ISingleViewApplicationLifetime`) egy nézet
  látszódik egyszerre; a felület megjelenítéséhez ezt a nézetet kell
  kicserélni (`MainView`)

## Kapocs

- [[concepts/esemalk/wpf-mvvm-alapok]] — a WPF MVVM architektúrája, amelynek
  elvei az Avaloniában is érvényesek
- [[concepts/esemalk/wpf-adatkotes-alapjai]] — az adatkötés (`Binding`)
  alapjai WPF-ben, `DataContext`, `Mode`
- [[concepts/esemalk/wpf-mvvm-inotifypropertychanged]] — a
  változáskövetés (`INotifyPropertyChange`) eszköze
- [[concepts/esemalk/wpf-mvvm-tamogato-csomagok]] — MVVM-et támogató
  programcsomagok, köztük a Community Toolkit megfelelője
- [[concepts/esemalk/avalonia-mvvm-toolkit]] — az MVVM Toolkit
  (`CommunityToolkit.Mvvm`) Avalonián belüli használata
- [[concepts/esemalk/avalonia-szamologep-pelda]] — MVVM-alapú Avalonia
  alkalmazás gyakorlati példája
- [[subjects/esemalk]]
