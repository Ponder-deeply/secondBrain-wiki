---
tags: [concept, esemalk/wpf-alapok]
sources: [elte_eva_ea06_wpf_basics.pdf]
derivation: source
updated: 2026-09-13
---

# WPF vezérlők megjelenése és felépítése

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

## Kapocs

- [[concepts/esemalk/wpf-transzformaciok]] — a transzformáció a megjelenés
  testreszabásának másik, geometriai eszköze
- [[concepts/esemalk/wpf-vezerlok-tartalmazasa]] — a `ContentControl`/
  `ItemsControl` megkülönböztetés a logikai fa egyik alapmintázata
