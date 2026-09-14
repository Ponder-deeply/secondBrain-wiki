---
tags: [concept]
sources: [elte_eva_ea07_wpf_architecture.pdf]
derivation: source
updated: 2026-09-13
---

# WPF adatkötés gyűjteményekre és a teljes felületre

A WPF [[concepts/esemalk/wpf-adatkotes-alapjai|adatkötése]] egyetlen
tulajdonságon túl egész gyűjteményekre, azok elemeinek megjelenítési
sablonjára, sőt egy teljes ablakra is kiterjeszthető.

## Tartalom

### Adatkötés gyűjteményekre

Az adatkötés gyűjteményekre is elvégezhető, ehhez olyan vezérlő szükséges,
amely adatsorozatot tud megjeleníteni (pl. `ItemsControl`, `ListBox`,
`GridView`, …). A vezérlők `ItemsSource` tulajdonságát kell kötnünk egy
gyűjteményre (`IEnumerable`):

```xml
<ComboBox Name="comboPersons" ItemsSource="{Binding}" />
```
```csharp
List<String> persons = new List<String> { … };
comboPersons.DataContext = persons;
// a teljes lista megjelenik a legördülő menüben
```

### Elemsablonok (adatkötés öröklődése)

Gyűjtemények esetén megadhatjuk az egyes elemek megjelenését is: ehhez az
adatok megjelenítési módját a vezérlőben az elemsablon (`ItemTemplate`)
módosításával kell megváltoztatni, amely egy adatsablont (`DataTemplate`)
fogad. Mind a teljes vezérlőre, mind az egyes elemek vezérlőire meg kell adni
a kötést; az adatsablon bármilyen összetett vezérlőt tartalmazhat.

```xml
<ComboBox Name="comboPersons" ItemsSource="{Binding}">
    <ComboBox.ItemTemplate>
        <!-- megadjuk az elemek megjelenítésének módját -->
        <DataTemplate>
            <TextBlock Text="{Binding FirstName}"/>
            <!-- minden elemnek a FirstName tulajdonsága jelenik meg -->
        </DataTemplate>
    </ComboBox.ItemTemplate>
</ComboBox>
```
```csharp
List<Person> persons = new List<Person> { … };
comboPersons.DataContext = persons; // az elemek már összetett objektumok
```

### Adatkötés a teljes felületre

Az adatkötés egy teljes ablakra (`Window`) is elvégezhető. Mivel az
adatkötést kódban adjuk meg, az ablakot is kódban kell példányosítanunk és
megjelenítenünk:

```csharp
MainWindow window = new MainWindow();
window.DataContext = …; // adatkötés az ablakra
window.Show(); // ablak megjelenítése
```

Az alkalmazás (`App`) indulásakor (`Startup`) kell végrehajtanunk a
tevékenységeket:

```csharp
public App() { // konstruktor
    Startup += new StartupEventHandler(App_Startup);
    // lekezeljük a Startup eseményt
}
```

## Kapocs

- [[concepts/esemalk/wpf-adatkotes-alapjai]] — az adatkötés alapfogalmai:
  cél, forrás, `Mode`, `UpdateSourceTrigger`, `DataContext`
- [[concepts/esemalk/wpf-mvvm-alapok]] — az MVVM architektúra, amelyben a
  nézetmodell `ObservableCollection`-jeit jellemzik ezek a kötések
- [[concepts/esemalk/wpf-vezerlok-tartalmazasa]] — `ContentControl` vs.
  `ItemsControl` tartalmazás, amelyre a gyűjtemény-kötés épül
- [[subjects/esemalk]]
