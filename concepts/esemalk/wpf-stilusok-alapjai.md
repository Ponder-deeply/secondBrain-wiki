---
tags: [concept, esemalk/wpf-eroforrasok-es-stilusok]
sources: [elte_eva_ea08_wpf_complex_resources.pdf]
derivation: source
updated: 2026-09-13
---

# WPF stílusok (Style)

A stílusok (`Style`) megjelenési beállítás gyűjtemények, amelyekkel egyszerre
számos elem kinézetét lehet vezérelni, függetlenül az operációs rendszer
beállításaitól.

## Tartalom

### Motiváció: közvetlen tulajdonságbeállítás

A vezérlők megjelenése a függőségi tulajdonságok közvetlen állításával is
testre szabható, pl. háttér-átmenet (`LinearGradientBrush`) vagy hatás
(`DropShadowEffect`) megadásával egy adott elemen:

```xml
<Label Content="Hello World" FontSize="20">
  <Label.Background>
    <LinearGradientBrush> <!-- átmenetes -->
      <GradientStop Color="Green" Offset="0"/>
      <GradientStop Color="Red" Offset="1"/>
    </LinearGradientBrush>
  </Label.Background>
  <Label.Effect>
    <DropShadowEffect BlurRadius="40" Direction="50" Opacity="1"/>
  </Label.Effect>
  …
```

Ez elemenként ismétlendő, ezért nem skálázódik több, hasonló megjelenésű
vezérlő esetén — ezt a problémát oldja meg a `Style`.

### A `Style` elem

- a `FrameworkElement` leszármazottaira használhatóak a `Style` függőségi
  tulajdonságon keresztül
- lehetővé teszik, hogy vezérlők kinézetét egyszerre kezeljük
- megadhatóak **elemenként**:

```xml
<Button Content="Blue Button">
  <Button.Style>
    <Setter Target="Foreground" Value="Blue" />
  </Button.Style>
</Button>
```

- vagy megadhatóak **erőforrásként**:

```xml
<Style x:Key="buttonStyle" TargetType="Button">
  <!-- megadható a céltípus is -->
  <Setter Target="Foreground" Value="Blue" />
</Style>
…
<Button Style="{StaticResource buttonStyle}" />
```

### Implicit vs. explicit stílusok

- **implicit** — nincs megadva kulcs (`x:Key`), így a stílus az összes
  megadott típusú elemre érvényes lesz, nincs szükség `StaticResource`
  hivatkozásra
- **explicit** — a kulcs megadásával és a `Style` tulajdonság
  használatával definiáljuk a vezérlő stílusát

### `Setter`

A stílusokban a `Setter` elem segítségével adunk függőségi tulajdonságokra
(`Property`) a típusnak megfelelő értéket (`Value`):

```xml
<Style x:Key="buttonStyle" TargetType="Button">
  <Setter Property="Width" Value="400"/> <!-- egyszerű érték -->
  <Setter Property="Canvas.Left" Value="200" />
  <Setter Property="RenderTransform">
    <Setter.Value> <!-- összetett érték -->
      <TranslateTransform X="100" Y="50" />
    </Setter.Value>
  </Setter>
</Style>
```

Egy `Setter` értéke lehet egyszerű string, vagy — a `Setter.Value` elemen
keresztül — összetett objektum (pl. transzformáció).

## Kapocs

- [[concepts/esemalk/wpf-eroforrasok-alapjai]] — a stílus mint erőforrás,
  `x:Key` és `StaticResource`
- [[concepts/esemalk/wpf-fuggosegi-tulajdonsagok]] — a `Setter` által
  állított függőségi tulajdonságok
- [[concepts/esemalk/wpf-vezerlok-megjelenese]] — a `Style` mint a
  megjelenés testreszabásának egyik eszköze, a `ControlTemplate` mellett
- [[concepts/esemalk/wpf-transzformaciok]] — a `TranslateTransform` és
  társai, amelyek `Setter.Value`-ként is megadhatók
- [[concepts/esemalk/wpf-stilusok-dinamikus-felulet]] — stílusok
  alkalmazása dinamikusan generált vezérlőkre
- [[subjects/esemalk]]
