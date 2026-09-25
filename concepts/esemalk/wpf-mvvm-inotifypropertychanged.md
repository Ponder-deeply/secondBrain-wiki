---
tags: [concept, esemalk/wpf-architektura]
sources: [elte_eva_ea07_wpf_architecture.pdf]
derivation: source
updated: 2026-09-13
---

# Adatkötés változáskövetéssel (`INotifyPropertyChanged`)

WPF-ben az adatkötés akkor tud automatikusan frissülni, ha a kötött objektum
jelzi a tulajdonságai változását — ezt az `INotifyPropertyChanged` interfész
teszi lehetővé.

## Tartalom

Az egyszerű adatkötés (`{Binding ...}`) önmagában csak a kezdeti értéket
olvassa ki; ha a kötött objektum tulajdonsága a felület életciklusa alatt
megváltozik, a felület ezt alapesetben nem érzékeli. A **változáskövetéssel
ellátott adatkötéshez** a modellosztálynak meg kell valósítania az
`INotifyPropertyChanged` interfészt:

```csharp
class Person : INotifyPropertyChanged {
    private String _firstName;

    public String FirstName {
        get { return _firstName; }
        set {
            if (_firstName != value) {
                _firstName = value;
                OnPropertyChanged("FirstName"); // jelezzük a változást
            }
        }
    }

    public event PropertyChangedEventHandler? PropertyChanged;

    public void OnPropertyChanged([CallerMemberName] String? name = null)
        // ha paraméter nélkül hívták meg, a hívó nevét helyettesíti be
    {
        if (PropertyChanged != null) {
            PropertyChanged(this, new PropertyChangedEventArgs(name));
        } // eseménykiváltás
    }
}
```

A `[CallerMemberName]` attribútum lehetővé teszi, hogy az `OnPropertyChanged`
metódust paraméter nélkül hívva a fordító automatikusan behelyettesítse a
hívó tag (jelen esetben a `set` blokk tulajdonságának) nevét — ezzel egy
tulajdonság módosulása több másik, tőle függő tulajdonság
(`OnPropertyChanged`-hívást) is kiválthat, például egy `FullName` a
`FirstName` és `LastName` változásakor.

### Gyűjtemények változáskövetése

A változáskövetés teljes **gyűjteményekre** is alkalmazható, amennyiben a
gyűjtemény megvalósítja az `INotifyCollectionChanged` interfészt. Az
`ObservableCollection<T>` típus már tartalmazza ennek megvalósítását, ezért
alkalmas változó tartalmú gyűjtemények követésére:

```csharp
ObservableCollection<Person> persons =
    new ObservableCollection<Person> { … };
comboPersons.DataContext = persons;
    // amennyiben a gyűjtemény, vagy bármely
    // tagjának tulajdonsága változik, azonnal
    // megjelenik a változás
```

### Példa: hallgatói adatok szerkesztése

A forrás egy hallgatói adatokat megjelenítő és szerkesztő alkalmazáson
mutatja be a mintát:

- `Student` — a modell osztály, amely megvalósítja az
  `INotifyPropertyChanged` interfészt (`FirstName`, `LastName`,
  `StudentCode`, származtatott `FullName` tulajdonsággal).
- `StudentsViewModel` — a nézetmodell, amely egy `ObservableCollection<Student>`
  tulajdonságban (`Students`) tárolja a változásfigyelt gyűjteményt.
- `MainWindow` — a nézet, amely `ItemsControl`-lal és `DataTemplate`-tel
  jeleníti meg a gyűjtemény elemeit:

```xml
<ItemsControl ItemsSource="{Binding Students}">
    <!-- megadjuk az adatforrást -->
    <ItemsControl.ItemTemplate><DataTemplate>
        <!-- megadjuk az adatok reprezentációját -->
        <StackPanel Orientation="Horizontal">
            <TextBox Text="{Binding FirstName}" Width="100" Margin="5"/>
            <!-- adatkötés a tulajdonságokhoz -->
        </StackPanel>
    </ItemsControl.ItemTemplate></DataTemplate>
</ItemsControl>
```

- `App` — az alkalmazás belépési pontja, amely az `App_Startup`
  eseménykezelőben létrehozza a nézetet és a nézetmodellt, majd összeköti
  őket a `DataContext` tulajdonságon keresztül:

```csharp
private void App_Startup(…) {
    MainWindow window = new MainWindow(); // nézet létrehozása
    StudentViewModel viewModel = new StudentViewModel(); // nézetmodell létrehozása
    window.DataContext = viewModel; // nézetmodell és modell társítása
    window.Show();
}
```

A tulajdonság módosulásakor a `set` ágban lefutó `OnPropertyChanged` hívás
azonnal érvényre juttatja a változást a felületen — a `Binding` mechanizmus
feliratkozik a `PropertyChanged` eseményre, és újraolvassa az érintett
tulajdonságot.

## Kapocs

- [[concepts/esemalk/wpf-mvvm-parancsok-icommand]] — az eseménykezelők
  MVVM-kompatibilis megfelelője, a parancsok
- [[concepts/esemalk/modell-nezet-architektura]] — az általános modell/nézet
  felbontás, amelynek a nézet–nézetmodell–modell (MVVM) réteghármas
  továbbfejlesztése
- [[concepts/esemalk/wpf-bevezetes]] — a WPF áttekintése, benne az MVVM
  architektúra említése
- [[concepts/esemalk/wpf-adatkotes-alapjai]] — az adatkötés alapfogalmai,
  amelyekre a változáskövetés épül
- [[concepts/esemalk/wpf-adatkotes-gyujtemenyek-teljesfelulet]] — gyűjtemény-
  és teljes felület kötés, ahol az elemek szintén megvalósíthatják ezt az
  interfészt
- [[subjects/esemalk]]
