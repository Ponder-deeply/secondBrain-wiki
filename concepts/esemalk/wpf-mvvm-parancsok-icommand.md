---
tags: [concept]
sources: [elte_eva_ea07_wpf_architecture.pdf]
derivation: source
updated: 2026-09-13
---

# Parancsok az MVVM architektúrában (`ICommand`)

Az MVVM architektúrában a hagyományos eseménykezelők nem használhatók,
mivel közvetlenül összekötnék a felületet a modellel; helyettük a
nézetmodellben elhelyezett **parancsokat** (`ICommand`) alkalmazzuk.

## Tartalom

A hagyományos eseménykezelők a felület (`View`) és a modell közötti
közvetlen kódkapcsolatot jelentenének, ami sérti az MVVM rétegek
függetlenségét. Az eseménykezelők helyettesítésére a nézetmodellben
**parancsokat** (`ICommand`) használunk, amelyek:

- adattársítással kapcsolhatók egy vezérlőhöz, annak `Command`
  tulajdonságán keresztül,
- megadják a végrehajtás tevékenységét (`Execute`), valamint a
  végrehajthatóság engedélyezettségét (`CanExecute`),
- jelzik a végrehajthatóság változását is (`CanExecuteChanged` esemény).

A parancsnak adható végrehajtási paraméter is, a vezérlő
`CommandParameter` tulajdonságával.

### Egyedi parancsosztály

```csharp
public class MyCommand : ICommand {
    public void Execute(object? parameter){
        // tevékenység végrehajtása (paraméterrel)
        MessageBox.Show(parameter);
    }
    public Boolean CanExecute(object? parameter){
        // tevékenység végrehajthatósága
        return parameter != null;
    }

    public event EventHandler? CanExecuteChanged;
        // kiválthatóság változásának eseménye
}
```

A nézetmodellben a parancs egy tulajdonságként jelenik meg, a felületen
pedig a `Command` és (opcionálisan) a `CommandParameter` tulajdonsággal
kötjük hozzá egy vezérlőhöz:

```csharp
public class MyViewModel { // nézetmodell
    // parancs elhelyezése a nézetmodellben
    public MyCommand ClickCommand { get; set; }
}
```

```xml
<Button Content="Click Me"
        Command="{Binding ClickCommand}"
        CommandParameter="Hello, world!" />
<!-- parancs megadása adatkötéssel, valamint paraméterrel -->
```

### Példa: új hallgató felvétele

A hallgatói adatok szerkesztő alkalmazás (lásd
[[concepts/esemalk/wpf-mvvm-inotifypropertychanged]]) kibővíthető úgy, hogy
lehessen felvenni új hallgatót:

- a felületen három szövegdobozban megadhatók az új hallgató adatai, majd
  egy gomb segítségével felvehető az alkalmazásba,
- ehhez létrejön egy új parancsosztály, amely a hallgató felvételét végzi
  (`StudentAddCommand`), és a végrehajtáskor felveszi a listába az új
  hallgatót — a parancsot tulajdonságként vesszük fel a nézetmodellben,
- magát az új hallgatót (`NewStudent`) is felvesszük a nézetmodellben, hogy
  legyen mihez kötni a felületi adatokat.

```csharp
class StudentAddCommand : ICommand // parancs objektum
{
    private StudentsViewModel _viewModel;

    public void Execute(Object? parameter) {
        _viewModel.AddNewStudent();
        // új hallgató felvétele
    }
    …
}
```

```xml
<StackPanel DataContext="{Binding NewStudent}"
    Orientation="Horizontal" Grid.Row="1">
    …
    <TextBox Text="{Binding StudentCode}" Width="100" Margin="5"/>
</StackPanel>
<Button Content="Add student"
    Command="{Binding AddCommand}" Margin="5"
    Grid.Row="2" />
<!-- parancs hozzákötése -->
```

A gomb megnyomása (`Click`) a parancs `Execute` metódusát váltja ki, amely a
nézetmodell `AddNewStudent` metódusán keresztül módosítja a
`Students` gyűjteményt; az `ObservableCollection` a bővülést
(`OnCollectionChanged`) és az érintett tulajdonságok változását
(`OnPropertyChanged`) automatikusan jelzi a felület felé.

## Kapocs

- [[concepts/esemalk/wpf-mvvm-inotifypropertychanged]] — a nézetmodell
  változáskövetése, amely a parancsok végrehajtása után a felületet
  frissíti
- [[concepts/esemalk/wpf-mvvm-delegatecommand]] — a saját parancsosztályok
  helyett használható, általános célú parancs
- [[concepts/esemalk/modell-nezet-architektura]] — az MV architektúra, amely
  az MVVM alapja
- [[subjects/esemalk]]
