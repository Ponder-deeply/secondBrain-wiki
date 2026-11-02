---
tags: [concept]
sources: [elte_eva_ea06_wpf_basics.pdf]
derivation: source
kind: procedure
element: earth
updated: 2026-09-25
---

# WPF vezérlők megjelenése, felépítése és transzformációi

A WPF vezérlők megjelenő formája számos módon testre szabható, és a
felépítésüket két, egymást kiegészítő fastruktúra írja le.

## Tartalom

### Megjelenés testreszabása

- a legtöbb vezérlőnél külön kezelhető a határvonal (`Border`/`Stroke`) és a
  kitöltés (`Background`/`Fill`), valamint különböző hatások (`Effect`)
  alkalmazhatók
- a színekhez különböző ecsetek használhatók, pl. `SolidColorBrush`,
  `LinearGradientBrush`
- a megjelenítés stílusba (`Style`) foglalható

### Logikai fa és vizuális fa

A megjelenő vezérlők összetettek, több elemből állnak; az egyes elemek
különböző tulajdonságokat szolgáltatnak a teljes vezérlő számára.

- a **logikai fa** (logical tree) írja le az elemek közötti (XAML-ben
  deklarált) kapcsolatokat
- a **vizuális fa** (visual tree) írja le a logikai elemek összes
  alkotóelemének kapcsolatát (pl. elhelyezés, áttetszőség, engedélyezettség
  szempontjából) — ez sokkal részletesebb, mint a logikai fa

Például egy `<Window><Grid><Label/><Button/></Grid></Window>` logikai
struktúra mögött a vizuális fában a `Window` ténylegesen egy `Border` →
`AdornerDecorator` → (`ContentPresenter` → `Grid` → `Label`/`Button`, illetve
egy másik `Border`) láncon keresztül épül fel; a `Label` és a `Button` maga is
`Border` → `ContentPresenter` → `TextBlock` elemekből áll.

A vezérlő felépítése a **sablonnal** (`ControlTemplate`) szabályozható.

### Transzformációk (`RenderTransform`)

A WPF-ben a vezérlőkre geometriai transzformációk alkalmazhatók a
`RenderTransform` tulajdonságon keresztül.

Alaptípusok:

- `RotateTransform` — forgatás
- `ScaleTransform` — nagyítás/kicsinyítés
- `TranslateTransform` — eltolás
- `SkewTransform` — ferdítés

A transzformációk `TransformGroup`-ba csoportosíthatók, és a csoport egyben
adható a vezérlő `RenderTransform` tulajdonságának.

#### Példa: kép transzformálása csúszkákkal

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

- [[concepts/esemalk/wpf-vezerlok-tulajdonsagai]] — a `ContentControl`/
  `ItemsControl` megkülönböztetés a logikai fa egyik alapmintázata
- [[concepts/esemalk/wpf-fuggosegi-tulajdonsagok]] — a `RenderTransform` és a
  transzformáció-tulajdonságok (pl. `Angle`) maguk is függőségi
  tulajdonságok, ezért köthetők adatkötéssel vagy csúszkával
