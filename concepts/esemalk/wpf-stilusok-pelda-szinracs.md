---
tags: [concept]
sources: [elte_eva_ea08_wpf_complex_resources.pdf]
derivation: source
updated: 2026-09-13
---

# Példa: dinamikus méretezhető színrács

Egy dinamikus méretezhető táblát megvalósító MVVM-példa, amely az
`ItemsControl`/`ItemContainerStyle` mintázatot alkalmazza: véletlenszerű
színre állítja a kattintott gombot, valamint a vele egy sorban és
oszlopban lévőket.

## Tartalom

### Feladat

Készítsünk egy dinamikus méretezhető táblát, amely véletlenszerű színre
állítja a kattintott gombot, valamint a vele egy sorban és oszlopban
lévőket.

- a felületen egy `ItemsControl` vezérlőben helyezzük el az elemeket,
  amely egy `UniformGrid` segítségével jelenít meg gombokat (`Button`)
- a nézetmodell megadja a mező típusát (`ColorFieldViewModel`), amely
  tárolja a sor (`Row`), oszlop (`Column`), szín (`Color`) értékeket,
  valamint a végrehajtandó utasítást (`FieldChangeCommand`), amely
  paraméterben az egész mezőt megkapja, így a nézetmodell könnyen tudja
  módosítani a megfelelő elemeket

### Tervezés

```
App ──▶ View::MainWindow

ViewModel::ColorGridViewModel (ViewModelBase)
  - _rowCount: Int32
  - _columnCount: Int32
  - _random: Random
  + ColorGridViewModel()
  - GenerateFields(): void
  - FieldChange(ColorFieldViewModel): void
  «property»
  + RowCount(): Int32
  + ColumnCount(): Int32
  + Fields(): ObservableCollection<ColorField>
  + ChangeSizeCommand(): DelegateCommand
    ◇── * ViewModel::ColorFieldViewModel (ViewModelBase)
          - _color: Color
          «property»
          + Row(): Int32
          + Column(): Int32
          + Color(): Color
          + FieldChangeCommand(): DelegateCommand
```

### Megvalósítás (`MainWindow.xaml`, részlet)

Méretváltás vezérlők (`RowCount`/`ColumnCount` kétirányú kötése, illetve a
méretváltás parancsa):

```xml
<GroupBox Margin="2" Header="Méret:" …>
  <StackPanel Orientation="Horizontal">
    <TextBlock Text="Sorok:" Margin="5" />
    <TextBox Text="{Binding RowCount}" … />
    <TextBlock Text="Oszlopok:" Margin="5" />
    <TextBox Text="{Binding ColumnCount}" … />
    <Button Name="_ChangeSizeButton"
        Command="{Binding ChangeSizeCommand}"
        Content="Méretváltás" Width="80" … />
  </StackPanel>
</GroupBox>
```

A mezők megjelenítése `DataTemplate`-tel, a szín kötésével és a
mezőváltás-parancs kiváltásával:

```xml
<ItemsControl.ItemTemplate>
  <DataTemplate> <!-- megadjuk, milyenek legyenek az elemek -->
    <Button CommandParameter="{Binding}"
        Command="{Binding FieldChangeCommand}">
      <Button.Background>
        <SolidColorBrush Color="{Binding Color}" />
      </Button.Background>
    </Button>
  </DataTemplate>
</ItemsControl.ItemTemplate>
```

*(A forrás következő szakaszában a `ColorGridViewModel`/
`ColorFieldViewModel` C# megvalósítása és az `ItemContainerStyle`
felhasználása folytatódik.)*

## Kapocs

- [[concepts/esemalk/wpf-stilusok-dinamikus-felulet]] — az
  `ItemsControl`/`ItemContainerStyle` mintázat, amelyet ez a példa
  alkalmaz
- [[concepts/esemalk/wpf-mvvm-delegatecommand]] — a `DelegateCommand`,
  amelyet a `FieldChangeCommand` és a `ChangeSizeCommand` is használ
- [[concepts/esemalk/wpf-mvvm-szamologep-pelda]] — hasonló felépítésű,
  korábbi MVVM-példa
- [[concepts/esemalk/wpf-panelek]] — a `UniformGrid`, amelyet az
  `ItemsPanel` használ
- [[subjects/esemalk]]
