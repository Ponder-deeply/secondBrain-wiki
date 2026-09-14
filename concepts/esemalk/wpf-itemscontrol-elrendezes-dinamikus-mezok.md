---
tags: [concept]
sources: [elte_eva_ea08_wpf_complex_resources.pdf]
derivation: source
updated: 2026-09-13
---

# ItemsControl elrendezésének testreszabása és a dinamikus mezők mintája MVVM-ben

MVVM architektúrában a vezérlők futásidejű létrehozása speciális
megközelítést igényel: a nézetmodell nem hozhat létre vezérlőket, ezért a
nézet egy `ItemsControl`-lal generálja őket, amelynek elrendezését az
`ItemsPanel` tulajdonsággal, köthető adatait pedig egy dedikált
nézetmodellbeli osztállyal szabjuk testre.

## Tartalom

### Dinamikus felület MVVM-ben

Bár a WPF is lehetőséget ad vezérlők dinamikus létrehozására (lásd az
analóg [[concepts/esemalk/winforms-dinamikus-vezerlok|WinForms-os mintát]]),
az MVVM architektúra miatt ez speciális megközelítést igényel: a
nézetmodellben nem hozhatunk létre vezérlőket, mivel a vezérlők megadása a
nézet feladata. A nézetben adjuk meg a generálandó vezérlőket egy
gyűjteményben:

- a gyűjteményt az `ItemsControl` vezérlő biztosítja, amely a megadott
  típusú elemeket (`Item`) tetszőleges tartalmazó vezérlőbe (`ItemsPanel`)
  helyezi el megadott módon (`ItemContainer`)
- az elemek típusát is a nézetben adjuk meg (pl. gomb, kép, de lehet
  egyedi osztály is)
- az adatforrást az `ItemsSource` tulajdonságon keresztül kötjük, az
  elemek megjelenítési módját az `ItemTemplate`/`DataTemplate` írja le

Az `ItemsSource`/`ItemTemplate`/`DataTemplate` kötés alapjait lásd
[[concepts/esemalk/wpf-adatkotes-gyujtemenyek-teljesfelulet]] — ez a lap
azokra épülve mutatja be az elrendezés testreszabását és a dinamikusan
generált vezérlők köthető tulajdonságainak mintáját.

### A tartalmazó panel testreszabása: `ItemsPanel`/`ItemsPanelTemplate`

Az `ItemsControl` elemeinek sorrendje alapesetben oszlopfolytonos, azaz
egymás alatt helyezkednek el (mint egy `WrapPanel`-ben). Ez az
`ItemsPanel` tulajdonságban felüldefiniálható; bármilyen
[[concepts/esemalk/wpf-panelek|panel]] megadható (pl. `Grid`,
`UniformGrid`, `Canvas`, `StackPanel`, …):

```xml
<ItemsControl ItemsSource="{Binding Fields}">
    <ItemsControl.ItemsPanel>
        <ItemsPanelTemplate>
            <!-- tartalmazó vezérlő megadása -->
            <StackPanel Orientation="Horizontal" />
            <!-- vízszintes tájolású elrendezés -->
        </ItemsPanelTemplate>
    </ItemsControl.ItemsPanel>
</ItemsControl>
```

### A dinamikus mezők mintája

A nézetmodellbeli osztály feladata egy vezérlő összes köthető
tulajdonságának (pl. parancs, tartalom) egy helyen történő kezelése. Egy
ilyen segédosztály (pl. `DynamicField`) a generált vezérlőhöz tartozó
összes köthető tulajdonságot tartalmazza:

```csharp
class DynamicField {
    // a dinamikus vezérlő megjelenése a nézetmodellben
    public ICommand FieldCommand { get; set; }
    public String FieldText { get; set; }
    public Int32 X { get; set; }
    public Int32 Y { get; set; }
    … // megadjuk a köthető tulajdonságokat
}
```

A nézetmodell ezeket egy típusba (amennyiben szükséges) csoportosítja,
majd egy felügyelt gyűjteménybe (`ObservableCollection<DynamicField>`)
teszi, amit a nézet `ItemsControl`-ja `ItemsSource`-ként köt be a
`DataContext`-en keresztül; a `DynamicField` a
[[concepts/esemalk/wpf-mvvm-inotifypropertychanged|`INotifyPropertyChanged`]]
interfészt valósítja meg, hogy a nézet kövesse a változásait.

## Kapocs

- [[concepts/esemalk/wpf-adatkotes-gyujtemenyek-teljesfelulet]] — az
  `ItemsSource`/`ItemTemplate`/`DataTemplate` kötés alapjai, amelyekre ez a
  lap épül
- [[concepts/esemalk/wpf-vezerlok-tartalmazasa]] — a `ContentControl` vs.
  `ItemsControl` tartalmazás, amelyre az `ItemsControl` épül
- [[concepts/esemalk/wpf-panelek]] — az `ItemsPanel`-ben megadható panelek
  (`Grid`, `UniformGrid`, `Canvas`, `StackPanel`, …)
- [[concepts/esemalk/wpf-mvvm-inotifypropertychanged]] — a `DynamicField`
  változáskövetése
- [[concepts/esemalk/wpf-mvvm-parancsok-icommand]] — a `FieldCommand`
  (`ICommand`) mint köthető tulajdonság
- [[concepts/esemalk/wpf-vezerlok-megjelenese]] — a vezérlők megjelenésének
  és sablonjának (`Style`/`ControlTemplate`) bevezető szintű tárgyalása,
  amelyet ez a lap MVVM-specifikus mintával egészít ki
- [[concepts/esemalk/winforms-dinamikus-vezerlok]] — az analóg dinamikus
  vezérlő-létrehozási minta WinForms-ban
- [[concepts/esemalk/wpf-stilusok-dinamikus-felulet]] — az `ItemsControl` sablonozásának és stílusozásának általános alapjai, amelyre ez a minta épül
- [[subjects/esemalk]]
