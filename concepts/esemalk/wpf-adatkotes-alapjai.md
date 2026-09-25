---
tags: [concept, esemalk/wpf-architektura]
sources: [elte_eva_ea07_wpf_architecture.pdf]
derivation: source
updated: 2026-09-13
---

# WPF adatkötés (Binding) alapjai

Az *adatkötés* (*data binding*) segítségével egy WPF felületi vezérlő
tulajdonsága függővé tehető egy másik objektum (jellemzően a nézetmodell)
állapotától, anélkül hogy a vezérlőhöz közvetlen kódbeli hozzáférés kellene.

## Tartalom

### Cél és forrás

Az adatkötés során egy adott vezérlő valamilyen *függőségi tulajdonságát*
(**cél**) tesszük függővé valamilyen objektumtól vagy annak egy
tulajdonságától (**forrás**). Így közvetett módon — a konkrét vezérlőhöz való
hozzáférés nélkül — tudunk egy tulajdonságot beállítani. Példa: egy
szövegdobozban tárolt szöveg kiíratása egy címkére, ahol a címke a cél, a
szövegdoboz a forrás.

A kötést (`Binding`) a függőségi tulajdonság értékeként hozzuk létre, forrás
objektum (`Source`, `ElementName`) és tulajdonság útvonal (`Path`)
megadásával:

```xml
<TextBox Name="textBoxName" />
<!-- forrás (szövegdoboz) -->

<TextBlock Text="{Binding ElementName=textBoxName, Path=Text}" />
<!-- cél (címke), mindig azt a szöveget jeleníti meg, ami a szövegdobozban van -->
```

A forrás lehet egy teljes objektum, bármely tulajdonsága, vagy beágyazott
tulajdonság is, pl. `Path=Text.Length`. Névvel rendelkező felületi elemhez az
`ElementName`, más objektumokhoz, erőforrásokhoz a `Source` tulajdonsággal
adjuk meg a forrást. A forrás értéke implicit konvertálódik a cél tulajdonság
típusára, vagy az átalakítás módját az `IValueConverter` interfész
segítségével magunk adjuk meg.

### Paraméterezés

A kötés többféleképpen paraméterezhető:

- a kötés módja (`Mode`) lehet egyirányú (`OneWay`), kétirányú (`TwoWay`,
  ekkor mindkét objektum változása kihat a másikra), egyszeres (`OneTime`), …
- a cél frissítése (`UpdateSourceTrigger`) lehet változtatásra
  (`PropertyChanged`), fókuszváltásra (`LostFocus`), …

```xml
<TextBox Name="textAnotherName"
    Text="{Binding ElementName=textBoxName,
           Path=Text, Mode=OneWay,
           UpdateSourceTrigger=LostFocus}" />
<!-- egyirányú kötés fókuszváltásra -->
```

### Adatkötés objektumértékekhez

Az adatkötés a felületi vezérlők mellett tetszőleges objektumra kódban is
megadható: a cél `DataContext` tulajdonságának kell megadni a forrást.

A teljes forrás kötése esetén a felületi kódban egy üres kötést adunk meg, a
forrást pedig a háttérkódban:

```xml
<TextBox Name="textBox" Text="{Binding}" />
```
```csharp
textBox.DataContext = "Hello DataBinding!";
```

Tulajdonság kötése esetén meg kell adnunk az útvonalat is:

```csharp
class Person {
    public String FirstName { get; set; }
    public String LastName { get; set; }
}
…
Person person = new Person { … };
textBox.DataContext = person; // a forrás a teljes objektum lesz
```
```xml
<TextBox Name="textBox" Text="{Binding Path=FirstName}" />
<!-- röviden: {Binding FirstName} -->
```

### Tranzitivitás

Az adatkötés tranzitív az elemek közötti kapcsolatokat leíró *logikai fán* a
gyerek elemekre, így a tulajdonságok a beágyazott elemekben is elérhetőek: ha
egy szülő elem `DataContext`-jét beállítjuk, minden gyerek eleme örökli azt,
és mindegyikük hozzáférhet a forrás tulajdonságaihoz. A tranzitivitás
szűkíthető a tulajdonság megadásával.

```xml
<StackPanel Name="panelPersons">
    <TextBlock Text="{Binding FirstName}" />
    <TextBlock Text="{Binding LastName}" />
</StackPanel>
```
```csharp
panelPersons.DataContext = person; // az objektum két tulajdonsága jelenik meg
```

## Kapocs

- [[concepts/esemalk/wpf-mvvm-alapok]] — az MVVM architektúra, amelyben az
  adatkötés a nézet és a nézetmodell közötti fő kommunikációs eszköz
- [[concepts/esemalk/wpf-adatkotes-gyujtemenyek-teljesfelulet]] — az
  adatkötés gyűjteményekre, elemsablonokra és a teljes ablakra
- [[concepts/esemalk/wpf-mvvm-inotifypropertychanged]] — a kötött forrás
  változásának követése (`INotifyPropertyChanged`)
- [[concepts/esemalk/wpf-fuggosegi-tulajdonsagok]] — a függőségi
  tulajdonság (dependency property) fogalma, amelyre a kötés célja épül
- [[subjects/esemalk]]
