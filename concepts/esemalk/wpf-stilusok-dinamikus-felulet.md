---
tags: [concept]
sources: [elte_eva_ea08_wpf_complex_resources.pdf]
derivation: source
updated: 2026-09-13
---

# Stílusok dinamikus felületű WPF alkalmazásokban

Dinamikus (adatkötéssel generált) felhasználói felület esetén a stílusok
nem közvetlenül a vezérlőn, hanem az elemeket megjelenítő tárolón keresztül
alkalmazhatók.

## Tartalom

### `ItemsControl` sablonjai

Dinamikus felhasználói felületet `ItemsControl` vezérlő segítségével lehet
megjeleníteni:

- a megjelenítőt és az elemeket sablonok (`ItemsPanel`, `ItemTemplate`)
  segítségével adjuk meg
- az elemek tárolókba kerülnek (`ItemContainer`)
- speciális megjelenítő esetén (pl. `Grid`) az elemekre függőségi
  tulajdonságokat alkalmazhatunk az elhelyezésre vonatkozóan (pl.
  `Grid.Row`, `Grid.Column`)
- az `ItemsControl` az elemeket `ContentPresenter`-be csomagolja

```xml
<ItemsControl ItemsSource="{Binding Fields}">
  <ItemsControl.ItemsPanel>
    <ItemsPanelTemplate>
      <UniformGrid Rows="5" Columns="5" />
      <!-- egy 5x5-ös rácsot használunk -->
    </ItemsPanelTemplate>
  </ItemsControl.ItemsPanel>
  <ItemsControl.ItemTemplate>
    … <!-- a megjelenített elem -->
  </ItemsControl.ItemTemplate>
```

### `ItemContainerStyle`

A függőségi tulajdonságot (pl. az elhelyezést vezérlő `Grid.Row`/
`Grid.Column`) nem a dinamikus vezérlőn, hanem a tárolóban kell megadni,
stílus használatával — erre szolgál az `ItemContainerStyle` tulajdonság:

```xml
  <ItemsControl.ItemContainerStyle>
    <!-- az elemek elhelyezését stílus keretében adjuk meg -->
    <Style>
      <Setter Property="Grid.Row" Value="{Binding X}" />
      <Setter Property="Grid.Column" Value="{Binding Y}" />
    </Style>
  </ItemsControl.ItemContainerStyle>
</ItemsControl>
```

Ez a mintázat lehetővé teszi, hogy egy adatforrásból (`ItemsSource`)
generált, változó számú elem mindegyike a saját adatához kötött pozícióba
kerüljön a megjelenítő rácsban.

## Kapocs

- [[concepts/esemalk/wpf-stilusok-alapjai]] — a `Style`/`Setter`
  alapmechanizmus, amelyet az `ItemContainerStyle` egy tárolóra alkalmaz
- [[concepts/esemalk/wpf-adatkotes-gyujtemenyek-teljesfelulet]] — az
  `ItemsSource` és `ItemTemplate` adatkötés gyűjteményekre
- [[concepts/esemalk/wpf-vezerlok-tartalmazasa]] — az `ItemsControl` mint
  tartalmazó vezérlő
- [[concepts/esemalk/wpf-panelek]] — a `Grid`/`UniformGrid`, amelyeket
  `ItemsPanel`-ként gyakran használnak
- [[concepts/esemalk/wpf-itemscontrol-elrendezes-dinamikus-mezok]] — az `ItemsPanel`/`ItemContainerStyle` MVVM-specifikus, dinamikus mezőket generáló mintája, amely erre a lapra épül
- [[subjects/esemalk]]
