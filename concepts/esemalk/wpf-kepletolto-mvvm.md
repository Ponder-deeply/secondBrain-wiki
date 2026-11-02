---
tags: [concept]
sources: [elte_eva_gy08_munkafuzet.pdf]
derivation: source
kind: procedure
element: earth
updated: 2026-10-21
---

# WPF képletöltő MVVM architektúrában

A 8. gyakorlat az előző gyakorlat képletöltő alkalmazását refaktorálja kétrétegű modell-nézetből MVVM-re: a **modell réteg változatlan marad**, a megjelenítési logika a nézetmodellbe kerül, és ez a nézetmodell később Avalonia UI-ban is újrahasználható.

## Tartalom

### Alaposztályok

- `ViewModelBase` (absztrakt): `INotifyPropertyChanged`, `OnPropertyChanged([CallerMemberName] string? propertyName = null)` — a fordító a hívó függvény nevét tölti be.
- `DelegateCommand : ICommand`: konstruktorban `Action<object?> execute` és `Predicate<object?>? canExecute`; `CanExecute`, `Execute` (letiltott parancsnál `InvalidOperationException`), `RaiseCanExecuteChanged`. Lásd [[concepts/esemalk/wpf-mvvm-delegatecommand]], [[concepts/esemalk/wpf-mvvm-inotifypropertychanged]].

### `MainViewModel`

Tulajdonságok: `IsDownloading` (bool), `Progress`, `Images` (`ObservableCollection` — a kollekció változásáról az `INotifyCollectionChanged` gondoskodik, nem kell kézzel értesíteni), `DownloadCommand`. A publikus getter a privát mezőt adja, a setter privát és az érték beállítása után `OnPropertyChanged()`-et hív (az `IsDownloading` setter a `DownloadCommand.RaiseCanExecuteChanged()`-et is). Az adatkötés a publikus tulajdonságokra történik; kétirányú kötéshez a tulajdonság publikusan írható is legyen.

- Konstruktor: `Images` példányosítása; `DownloadCommand`: feltétel — nem zajlik letöltés; akció — `LoadAsync` hívása és megvárása.
- `LoadAsync(Uri)`: `IsDownloading = true`, `Images` törlése, új `WebPage` a `_model`-be, feliratkozás, `await LoadImagesAsync()`, `IsDownloading = false`.
- `OnImageLoaded`: a `WebImage`-ből `BitmapImage`, hozzáadás az `Images`-hez; `OnLoadProgress`: `Progress` beállítása.

### Nézet (`MainWindow.xaml`)

- A `.xaml.cs` kiürül (csak osztály és konstruktor); a legtöbb vezérlőnek a `Name` elhagyható (csak az `urlTextBox`-nak kell).
- `Click` helyett `Command="{Binding DownloadCommand}"`, `CommandParameter="{Binding ElementName=urlTextBox, Path=Text}"`.
- A képszámláló az `Images.Count`-hoz, a `ProgressBar.Value` a `Progress`-hez (`Mode=OneWay`) kötve.
- Konverter típuseltérésnél: az `IsDownloading` (bool) és a `Visibility` (enum) között `BooleanToVisibilityConverter` (`<Window.Resources>` `x:Key="VisibilityConverter"`, `Converter={StaticResource VisibilityConverter}`).
- A `WrapPanel` helyett `ItemsControl`: `ItemsSource` = `Images`, `ItemsPanel` = `WrapPanel`, `ItemTemplate` = `Image`. Lásd [[concepts/esemalk/wpf-adatkotes-gyujtemenyek-teljesfelulet]].

### Vezérlés (`App`)

A `StartupUri` sor törölve; az `App` konstruktorában a `Startup` eseményre `OnStartup`: új `MainWindow`, `DataContext` = új `MainViewModel`, `Show()`. Lásd [[concepts/esemalk/wpf-kornyezet-fuggosegkezeles]].

### Képek megjelenítése és mentése

- `MainViewModel`: `ImageSelected` esemény (argumentuma a kiválasztott kép) és `ImageSelectedCommand` (akciója az eseményt váltja ki).
- Az `ItemTemplate`-ben a `Border` helyett `Button` (keretre és képre közvetlenül nem alkalmazható parancskötés). Az `ItemTemplate` `DataContext`-je az aktuális elem (`BitmapImage`), ezért a parancs kötése sikertelen; megoldás: `Command="{Binding DataContext.ImageSelectedCommand, RelativeSource={RelativeSource AncestorType=Window}}"`, `CommandParameter="{Binding}"`.
- `ImageViewModel : ViewModelBase`: `Image` (`BitmapImage`), `SaveImageCommand`, `SaveImage` esemény; az `ImageWindow.xaml` a parancsra és az `Image` tulajdonságra kötve.
- **Új ablak megjelenítése nem a nézetmodell dolga** (nem lenne újrahasználható Avalonia UI-ban): az `App.OnStartup` iratkozik fel a `MainViewModel.ImageSelected`-re, létrehozza az `ImageViewModel`-t és az `ImageWindow`-t (`Show`), és a `SaveImage` eseményre feliratkozva a mentés logikáját is ő tartalmazza.

### Megszakíthatóság

`MainViewModel.CancelLoad()` (a modell `CancelLoad`-ját hívja, ha zajlik letöltés); a `DownloadCommand` letöltés közben a `CancelLoad`-ot hívja, különben `LoadAsync`-ot (a feltétel elhagyható, a gomb mindig aktív). A gomb felirata a `DownloadButtonLabel` tulajdonságból jön (az `_isDownloading` alapján), az `IsDownloading` változásakor `OnPropertyChanged(nameof(DownloadButtonLabel))` — a `nameof` átnevezéskor fordítási hibát ad, a beégetett string nem.

## Kapocs

- [[concepts/esemalk/wpf-kepletolto-modell-nezet]] — az MVVM-re átírt kétrétegű változat
- [[concepts/esemalk/wpf-mvvm-alapok]] — az MVVM architektúra
- [[concepts/esemalk/wpf-mvvm-parancsok-icommand]] — parancsok és `CommandParameter`
- [[concepts/esemalk/wpf-tobbablakos-mvvm-pelda]] — nézetmodell két ablakkal, hasonló mintával
- [[concepts/esemalk/avalonia-mvvm-adatkotes]] — a nézetmodell újrahasználata Avalonia UI-ban
- [[subjects/esemalk]]
