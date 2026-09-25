---
tags: [concept, esemalk/wpf-eroforrasok-es-stilusok]
sources: [elte_eva_ea08_wpf_complex_resources.pdf]
derivation: source
updated: 2026-09-13
---

# WPF triggerek stílusban és sablonban

A *triggerek* (`trigger`) valamilyen esemény vagy értékváltozás hatására
képesek animációt futtatni vagy tulajdonságot beállítani, akár stílusban,
vezérlőben vagy sablonban elhelyezve.

## Tartalom

- Animációk végrehajthatóak kódban, valamint a felületen triggerek
  segítségével.
- Kétféle trigger:
  - `EventTrigger` — valamilyen esemény (pl. `RoutedEvent="MouseEnter"`)
    hatására fut le
  - `DataTrigger` — értékváltozás (pl. adatkötött tulajdonság adott értéke)
    hatására fut le
- A trigger hatására animáció indítható (`BeginAnimation`,
  `BeginStoryboard`) vagy tulajdonság állítható be (`Setter`).
- Elhelyezhetőek stílusban (`Style.Triggers`), vezérlőben
  (`<Button.Triggers>`), sablonban is.

```xml
<Button.Triggers>
    <EventTrigger RoutedEvent="MouseEnter">
        <!-- MouseEnter eseményre fut le -->
        <BeginStoryboard Storyboard="…" />
        <!-- animáció futtatása -->
    </EventTrigger>
    …
</Button.Triggers>
```

Egy forgatókönyv ablak-erőforrásként (`Window.Resources`) is megadható, és
`StaticResource`-ként hivatkozható a triggerből:

```xml
<Window.Resources>
    <Storyboard x:Key="fieldSizeStoryboard" Duration="0:0:2" AutoReverse="True">
        <DoubleAnimation Storyboard.TargetProperty="Opacity" From="1" To="0"/>
        <DoubleAnimation
            Storyboard.TargetProperty="(Control.RenderTransform).
                (ScaleTransform.ScaleX)" From="1" To="0.5" />
        …
    </Storyboard>
</Window.Resources>
…
<Button.Triggers>
    <EventTrigger RoutedEvent="MouseEnter">
        <BeginStoryboard Storyboard="{StaticResource fieldSizeStoryboard}" />
    </EventTrigger>
</Button.Triggers>
```

### Megjelenítés befolyásolása nézetmodell-adat alapján

A triggerek akkor is hasznosak, ha a megjelenítést a nézetmodell adatai
alapján akarjuk szabályozni: a `DataTrigger` egy adatkötés (`Binding`) adott
értékére reagál, és `Setter`-rel állít be tulajdonságot, pl.:

```xml
<Style TargetType="Button">
    <Style.Triggers>
        <!-- a szín adatkötés hatására változik -->
        <DataTrigger Binding="{Binding FieldText}" Value="">
            <!-- ha nincs szöveg megadva -->
            <Setter Property="Background" Value="Gray" />
            <!-- a gomb szürke lesz -->
        </DataTrigger>
    </Style.Triggers>
</Style>
```

### Példa: háromszínű mezőkijelölés

Feladat: egy dinamikus, méretezhető tábla, amely három szín között (piros,
fehér, zöld) állítja a kattintott gombot, valamint a vele egy sorban és
oszlopban lévőket.

- a színt a nézet adja meg, így a nézetmodell nem adhat vissza konkrét
  színt, csak egy sorszámot (0 és 2 között), amely alapján a szín állítható
  (`ColorNumber`)
- a színt trigger segítségével állítjuk a nézetben, a gomb stílusában, amely
  az érték függvényében színezi a gombot (a gomb emellett animálódik, így
  `DataTrigger` és `EventTrigger` is hatni fog a vezérlőre)
- a triggereket az ablak erőforrásaként megadott stílusban hozzuk létre

```xml
<Style x:Key="buttonStyle" TargetType="Button">
    <Style.Triggers>
        <!-- a színezés a nézetmodellben lévő adat függvényében fog változni -->
        <DataTrigger Binding="{Binding ColorNumber}" Value="0">
            <Setter Property="Background" Value="Green" />
        </DataTrigger>
        …
    </Style.Triggers>
</Style>
```

## Kapocs

- [[concepts/esemalk/wpf-eroforrasok-animaciok]] — a triggerek gyakran
  forgatókönyv-alapú animációt indítanak (`BeginStoryboard`)
- [[concepts/esemalk/wpf-adatkotes-alapjai]] — a `DataTrigger` egy adatkötés
  (`Binding`) értékét figyeli
- [[concepts/esemalk/wpf-vezerlok-megjelenese]] — a `Style`/`ControlTemplate`
  keretrendszer, amelyben a triggerek elhelyezkednek
- [[concepts/esemalk/wpf-tictactoe-pelda]] — a Tic-Tac-Toe példa egy további
  változata `DataTrigger`-rel és egyedi `ControlTemplate`-tel jeleníti meg a
  játékosok jeleit
- [[subjects/esemalk]]
