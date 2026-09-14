---
tags: [concept]
sources: [elte_eva_ea06_wpf_basics.pdf]
derivation: source
updated: 2026-09-13
---

# XAML nyelv

Az *eXtensible Application Markup Language* (XAML) a WPF felület deklaratív
leírására szolgáló, XML alapú nyelv.

## Tartalom

### A nyelv

A XAML lehetőséget ad 2D/3D elemek, transzformációk, animációk, valamint
további effektek leírására. Attribútumokkal, illetve tartalmazással írja le a
tulajdonságokat és a magukban foglalt elemeket:

```xml
<Canvas Name="myCanvas"> <!-- vászon -->
    <Label Name="myLabel" BorderBrush="Red">
        <!-- címke a vászonban -->
        Hello World! <!-- címke tartalma (nem csak szöveg lehet) -->
    </Label> <!-- címke vége -->
</Canvas> <!-- vászon vége -->
```

Beágyazott elemekre (nem csak attribútumokra) is épülhet a leírás, pl. egy
rács sor-/oszlopdefiníciói:

```xml
<Grid> <!-- elemek tároló rács -->
    <Grid.RowDefinitions> <!-- rács felépítés -->
        <RowDefinition Height="Auto" />
    </Grid.RowDefinitions>
    <Grid.ColumnDefinitions>
        ...
    </Grid.ColumnDefinitions>
    <Label Content="Enter Name: " Grid.Row="0" Grid.Column="0" />
    <TextBox Grid.Row="0" Grid.Column="1" MinWidth="50"/>
</Grid> <!-- rács vége -->
```

### Megfeleltetés kódnak

Minden XAML elemtípus megfeleltethető egy .NET osztálynak, és a deklaratív
leírás imperatív kódnak — így minden, amit XAML-ben leírunk, leírható kóddal
is, és dinamikusan is létrehozhatunk vezérlőket:

```csharp
Canvas myCanvas = new Canvas(); // vászon
Label myLabel = new Label(); // címke
myLabel.Content = "Hello World!"; // tartalom
myLabel.BorderBrush = Brushes.Red; // szegély
myCanvas.Children.Add(myLabel); // behelyezés
```

### Fordítás

A XAML kód fordítás során *BAML* (*Binary XAML*) formátumra alakul, amely
erőforrásként csatolható a felügyelt kódhoz:

1. a XAML kódot a XAML fordító feldolgozza, XAML C# kódra és BAML erőforrásra
   bontva
2. a (kézzel írt) C# kód és a XAML C# kód együtt kerül a C# fordítóba, amely
   köztes nyelvű (IL) kódot állít elő
3. a BAML erőforrás a végeredményhez csatolva kerül a felügyelt kódhoz

## Kapocs

- [[concepts/esemalk/wpf-bevezetes]] — a WPF áttekintése, amelynek a XAML a
  deklaratív felületleíró nyelve
- [[concepts/esemalk/wpf-ablakok-alkalmazasok]] — a `Window` és `Application`
  osztályok XAML-beli és háttérkód-beli leírása
- [[subjects/esemalk]]
