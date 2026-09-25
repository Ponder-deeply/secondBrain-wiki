---
tags: [concept, esemalk/wpf-alapok]
sources: [elte_eva_ea06_wpf_basics.pdf]
derivation: source
updated: 2026-09-13
---

# WPF vezérlő-transzformációk

A WPF-ben a vezérlőkre geometriai transzformációk alkalmazhatók a
`RenderTransform` tulajdonságon keresztül.

## Tartalom

Alaptípusok:

- `RotateTransform` — forgatás
- `ScaleTransform` — nagyítás/kicsinyítés
- `TranslateTransform` — eltolás
- `SkewTransform` — ferdítés

A transzformációk `TransformGroup`-ba csoportosíthatók, és a csoport egyben
adható a vezérlő `RenderTransform` tulajdonságának.

### Példa: kép transzformálása csúszkákkal

Feladat: egy képet (`ImageBrush`-sal egy `Rectangle`-be helyezve) csúszkák
(`Slider`) segítségével interaktívan transzformálni.

- a négyzetre (`Rectangle`) definiálunk egy `TransformGroup`-ot, amely a
  transzformáció-típusok egy-egy példányát tartalmazza (`_transformSkew`,
  `_transformRotate`, `_transformTranslate`, `_transformScale` mezők a
  `MainWindow` osztályban)
- a csoport elemeit a konstruktorban adjuk hozzá:
  `_transformGroup.Children.Add(_transformSkew)`, majd
  `_rectangleSmiley.RenderTransform = _transformGroup`
- a paramétereket csúszkák szabályozzák, közös eseménykezelővel
  (`Slider_ValueChanged`), amely a megfelelő transzformáció tulajdonságát
  állítja be, pl.: `_transformRotate.Angle = _sliderRotateAngle.Value`
- egy gomb (`ButtonDefault_Click`) az alapértelmezett értékek
  visszaállítására szolgál

## Kapocs

- [[concepts/esemalk/wpf-vezerlok-megjelenese]] — a transzformáció a vezérlő
  megjelenésének testreszabási eszközei közül az egyik
- [[concepts/esemalk/wpf-fuggosegi-tulajdonsagok]] — a `RenderTransform` és a
  transzformáció-tulajdonságok (pl. `Angle`) maguk is függőségi
  tulajdonságok, ezért köthetők adatkötéssel vagy csúszkával
