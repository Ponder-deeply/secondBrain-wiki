---
tags: [concept]
sources: [elte_eva_ea08_wpf_complex_resources.pdf]
derivation: source
updated: 2026-09-13
---

# WPF erőforrások alapjai

A WPF általánosítja az *erőforrás* fogalmát: nem csak képek és hangok, hanem
bármely külső fájl, sőt bármely osztály példánya erőforrásként kezelhető.

## Tartalom

### Erőforrás-fogalom a WinForms-hoz képest

- a Windows Forms-ban az erőforrások azok a képek, hangok stb., amelyeket az
  egyes felületi osztályokhoz csatolunk
- a WPF-ben erőforrás lehet bármely külső fájl, sőt bármely osztály
  példánya; elsősorban:
  - **stílusok** (`Style`) — a felületi elemek egységes megjelenését
    definiálják
  - **sablonok** (`Template`) — a vezérlők felépülését és adatkötéseit
    definiálják
  - **forgatókönyvek** (`StoryBoard`) — animációk végrehajtását biztosítják

### Erőforrások deklarálása a felületi kódban

Bármely felületi elem (`UIElement`) tartalmazhat erőforrásokat a
`Resources` tulajdonság segítségével:

```xml
<Window …>
  <Window.Resources>
    … <!-- erőforrások az egész ablakra -->
  </Window.Resources>
  <Grid Name="LayoutRoot">
    <Grid.Resources>
      … <!-- rácson belüli erőforrások -->
    </Grid.Resources>
    …
  </Grid>
</Window>
```

Az erőforrás abban a részfában érhető el, amelyben deklarálva lett (az
adott elemtől lefelé).

### Erőforrások elérése: `StaticResource`

Minden erőforrás kulccsal (`x:Key`) rendelkezik, amely alapján
lekérdezhető a `StaticResource` jelölésmódú hivatkozással:

```xml
<Grid Name="grid">
  <Grid.Resources>
    <Style x:Key="buttonStyle"> … </Style>
    <!-- megadtuk az erőforrás célját -->
  </Grid.Resources>
  …
  <Button Style="{StaticResource buttonStyle}">
```

Maga a `Resources` tulajdonság egy kulcs szerint indexelt asszociatív tömb,
amely felületi kódból is elérhető:

```csharp
Style myButtonStyle = (grid.Resources["buttonStyle"] as Style);
```

## Kapocs

- [[concepts/esemalk/wpf-eroforrasok-fajlok]] — több elem közötti
  erőforrás-megosztás erőforrásfájlokkal (`ResourceDictionary`)
- [[concepts/esemalk/wpf-stilusok-alapjai]] — a `Style` mint a leggyakoribb
  erőforrástípus
- [[concepts/esemalk/wpf-vezerlok-tulajdonsagai]] — a `Resources` mint a
  vezérlők egyik közös tulajdonsága
- [[concepts/esemalk/dotnet-eroforraskezeles]] — a WinForms-beli erőforrás
  (content/embedded resource) fogalma, amelyet a WPF általánosít
- [[subjects/esemalk]]
