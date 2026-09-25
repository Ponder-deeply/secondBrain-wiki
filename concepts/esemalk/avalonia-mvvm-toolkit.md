---
tags: [concept, esemalk/avaloniaui-alapok]
sources: [elte_eva_ea09_avaloniaui.pdf]
derivation: source
updated: 2026-09-13
---

# Avalonia MVVM Toolkit

Az MVVM Toolkit (`CommunityToolkit.Mvvm` NuGet csomag) egy népszerű, MVVM
alapú fejlesztést segítő, forráskód-generátorra épülő könyvtár, amely
Avalonia UI és WPF projektekben egyaránt használható.

## Tartalom

Az MVVM Toolkit alapértelmezetten a projekthez adásra kerül, ha az Avalonia
projekt létrehozásakor ezt a tervezési mintát választottuk (lásd
[[concepts/esemalk/avalonia-telepites-projekt-letrehozas]]). A csomag
gyakran használt őstípusokat és az MVVM alapú fejlesztést segítő
kódgenerátor attribútumokat tartalmaz.

### Alaptípusok

A korábban (WPF-ből, lásd [[concepts/esemalk/wpf-mvvm-tamogato-csomagok]])
megismert típusok itt más néven szerepelnek:

- a `ViewModelBase` megfelelője itt `ObservableObject` — nézetmodell
  osztályunkat továbbra is ebből származtathatjuk, további közös
  funkcionalitást biztosítva
- a `DelegateCommand` megfelelője itt `RelayCommand`, elérhető generikus
  formában is (`RelayCommand<T>`), pl.:

  ```csharp
  public RelayCommand<int> MyCommand { get; set; }
  ```

### Kódgenerátor attribútumok

Az MVVM Toolkit kódgenerátorral is használható: attribútumokkal ellátott
mezőkből/metódusokból fordítási időben generálja a szokásos MVVM
boilerplate kódot. Ehhez a nézetmodell osztálynak `partial`-nak kell
lennie, hogy a generált kód mellé illeszthető legyen.

**Parancs generálása metódusból** (`[RelayCommand]`):

```csharp
[RelayCommand] // SomethingCommand parancs
private void Something() { /* ... */ }
```

A generált kód egy `RelayCommand` mezőt és egy `IRelayCommand` típusú,
lusta módon inicializált tulajdonságot hoz létre:

```csharp
private RelayCommand? somethingCommand;
public IRelayCommand SomethingCommand =>
    somethingCommand ??= new RelayCommand(Something);
```

**Tulajdonság generálása mezőből** (`[ObservableProperty]`): az attribútum
adattag (mező) attribútumaként alkalmazható, és a `SetProperty()` metódust
(az `OnPropertyChanged()` korábbi megfelelőjét) használó tulajdonságot
generál. A `SetProperty(ref name, value)` beállítja a mezőt, majd kiváltja
rá a `PropertyChanged` eseményt.

```csharp
[ObservableProperty] // Data property
private string _data { /* ... */ }
```

```csharp
// generált kód
public string? Data {
    get => name;
    set => SetProperty(ref _data, value);
}
```

## Kapocs

- [[concepts/esemalk/wpf-mvvm-tamogato-csomagok]] — az MVVM Toolkit WPF-es
  megfelelője (`ViewModelBase`, `DelegateCommand`)
- [[concepts/esemalk/wpf-mvvm-inotifypropertychanged]] — a
  változáskövetés (`INotifyPropertyChanged`) alapja, amelyet az
  `ObservableObject`/`[ObservableProperty]` kivált
- [[concepts/esemalk/wpf-mvvm-delegatecommand]] — a `DelegateCommand`
  mintája, amelynek a `RelayCommand` felel meg
- [[concepts/esemalk/avalonia-mvvm-adatkotes]] — az Avalonia MVVM
  architektúrája és adatkötése, amelybe az MVVM Toolkit illeszkedik
- [[concepts/esemalk/avalonia-szamologep-pelda]] — a számológép példa MVVM
  Toolkit alapú nézetmodellje
- [[subjects/esemalk]]
