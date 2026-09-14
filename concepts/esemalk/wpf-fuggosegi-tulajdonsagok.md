---
tags: [concept]
sources: [elte_eva_ea06_wpf_basics.pdf]
derivation: source
updated: 2026-09-13
---

# WPF függőségi tulajdonságok (dependency property)

A WPF bevezette a tulajdonság egy speciális változatát, a függőségi
tulajdonságot (dependency property), amely a hagyományos C# tulajdonságoknál
rugalmasabb módon köthető a környezethez.

## Tartalom

- Lehetővé teszi, hogy egy adott objektum tulajdonságait más objektumon
  keresztül definiáljuk, és úgy szabjunk rá értéket, hogy az a
  környezettől függően változzon.
- A `DependencyObject` statikus `GetValue` és `SetValue` metódusaival
  kezelhetők a tulajdonság átadásával, amely statikus tulajdonságként
  (attached property) definiált.
- A legtöbb WPF-beli tulajdonság függőségi tulajdonság, és XAML-ben is
  kihasználható — például lehetőséget ad a szülőelemek tulajdonságainak
  elérésére és beállítására.

### Csatolt (attached) tulajdonságok panelekben

```csharp
Canvas myCanvas = new Canvas();
Label myLabel = new Label();
myLabel.SetValue(Canvas.LeftProperty, 100);
myLabel.SetValue(Canvas.TopProperty, 50);   // függőségi tulajdonságok beállítása
myCanvas.Children.Add(myLabel);              // elem felvétele gyerekelemként

Grid myGrid = new Grid();
myLabel.SetValue(Grid.RowProperty, 1);
myLabel.SetValue(Grid.ColumnProperty, 3);    // rácsban sort és oszlopot kell beállítanunk
myGrid.Children.Add(myLabel);
```

Ugyanez XAML-ben:

```xml
<Canvas Name="myCanvas">
    <Label Name="myLabel" Content="Hello!" Canvas.Left="100" Canvas.Top="50" />
</Canvas>

<Grid Name="myGrid">
    <Label Name="myLabel" Content="Hello!" Grid.Row="1" Grid.Column="3" />
</Grid>
```

## Kapocs

- [[concepts/esemalk/wpf-panelek]] — a `Canvas.Left`/`Top` és `Grid.Row`/
  `Column` csatolt tulajdonságok a panelek elrendezési logikáját vezérlik
- [[concepts/esemalk/wpf-transzformaciok]] — a transzformációk tulajdonságai
  (pl. `Angle`) is függőségi tulajdonságok
- [[concepts/esemalk/csharp-tulajdonsagok]] — a hagyományos C# tulajdonságok
  (`property`), amelyekhez képest a függőségi tulajdonság kiegészítő
  viselkedést ad
