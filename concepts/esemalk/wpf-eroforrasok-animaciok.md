---
tags: [concept]
sources: [elte_eva_ea08_wpf_complex_resources.pdf]
derivation: source
updated: 2026-09-13
---

# WPF animációk

A WPF támogatja animációk végrehajtását, amely lényegében függőségi
tulajdonságok adott időn keresztül történő folyamatos módosítását jelenti.

## Tartalom

- Az animáció típusa megadja a módosítani szánt érték típusát, pl.
  `DoubleAnimation`, `ColorAnimation`, `ThicknessAnimation`.
- Az animációnál definiálni kell a kezdőállapotot (`From`), a végállapotot
  (`To`), valamint az időt (`Duration`).
- Az animáció rendelkezhet tetszőlegesen sok köztes állapottal (`KeyFrame`),
  amelyekre egyéni kritériumok és időkorlátok szabhatóak, valamint megadható
  az animáció módja (lineáris, diszkrét, spline).

### Forgatókönyvek (Storyboard)

Az animációkat forgatókönyvekbe (`Storyboard`) szervezzük:

- a forgatókönyvvel megadható a célobjektum (`Storyboard.Target`,
  `Storyboard.TargetName`), illetve a céltulajdonság
  (`Storyboard.TargetProperty`)
- a céltulajdonság tetszőlegesen összetett lehet, pl.: `Opacity`,
  `Canvas.Left`, `(Control.Foreground).(SolidColorBrush.Color)`,
  `(Control.RenderTransform).(TransformGroup.Children[0]).
  (ScaleTransform.ScaleX)`
- a forgatókönyvvel szabályozható a végrehajtás (`Start`, `Stop`), az
  ismétlődés (`RepeatBehavior`), gyorsulási és lassulási mérték, esetleg
  visszajátszás (`AutoReverse`)

Példa:

```xml
<Storyboard Storyboard.TargetName="myButton" Duration="0:00:04">
    <!-- forgatókönyv, amely 4 másodpercig fut a myButton vezérlőre -->
    <DoubleAnimation From="1" To="0"
        Storyboard.TargetProperty="Opacity" />
    <!-- áttetszővé tesszük -->
    <DoubleAnimation From="100" To="200"
        Storyboard.TargetProperty="Canvas.Left" />
    <!-- eltoljuk jobbra -->
    …
</Storyboard>
```

## Kapocs

- [[concepts/esemalk/wpf-fuggosegi-tulajdonsagok]] — az animáció mindig egy
  függőségi tulajdonságot módosít folyamatosan
- [[concepts/esemalk/wpf-transzformaciok]] — a `RenderTransform` altulajdonságai
  (pl. `ScaleTransform.ScaleX`) gyakori animációs célpontok, összetett
  céltulajdonság-útvonalon keresztül
- [[concepts/esemalk/wpf-stilus-triggerek]] — a forgatókönyvek végrehajtása
  triggerekhez köthető (`BeginStoryboard`)
- [[subjects/esemalk]]
