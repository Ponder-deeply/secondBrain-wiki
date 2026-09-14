---
tags: [concept]
sources: [elte_eva_ea10_avaloniaui_complex.pdf]
derivation: source
updated: 2026-09-13
---

# Avalonia UI méret- és tájolás-kezelés

A mobil eszközök képernyőmérete és tájolása (portré/tájkép) jelentősen
eltérhet, ezért az Avalonia UI alkalmazásnak alkalmazkodnia kell a teljes
képernyős megjelenítéshez: relatív elrendezőkkel és pozícionálással, illetve
a vezérlő átméretezésének explicit kezelésével.

## Tartalom

### Méret kezelése

Relatív elrendezőket és pozícionálást célszerű használni, hogy a felület
tetszőleges méretű képernyőn helyesen jelenjen meg. A vezérlő
átméretezésekor lefutó eseményt a nézet háttérkódjában az `OnSizeChanged`
metódus felüldefiniálásával lehet elkapni:

```csharp
protected override void OnSizeChanged(…) {
    base.OnSizeChanged(e);

    Double height = e.NewSize.Height;
    Double width = e.NewSize.Width;
    // ...
}
```

### Tájolás kezelése

A mobil eszközök többféle tájolásban (jellemzően portré/álló és tájkép/fekvő)
helyezkedhetnek el; a támogatott tájolásokat platformspecifikusan is lehet
korlátozni (Android esetén pl. a főtevékenység, `MainActivity`,
`ScreenOrientation` jellemzőjével).

Célszerű az eszköz tájolását és az alkalmazás képernyőjének méretét egyszerre
szabályozni, ugyanazon `OnSizeChanged` felüldefiniálásban: a szélesség és a
magasság összevetéséből következtetünk az aktuális tájolásra.

```csharp
protected override void OnSizeChanged(
    SizeChangedEventArgs e)
    // megkapjuk az aktuális
    // szélességet/magasságot az argumentumban
{
    base.OnSizeChanged(e);

    // orientáció meghatározása
    if (e.NewSize.Width > e.NewSize.Height)
        … // tájkép
    else
        … // portré
}
```

Egy konkrét alkalmazásban (pl. a számológép mobilra alakításánál) a
nézetmodellek ősosztályát (`ViewModelBase`) is kiegészíthetjük a tájolás
kezelésével (`IsPortrait`, `IsLandscape` tulajdonságok), így szelektor
osztályok segítségével a stílusréteg is tud reagálni az elforgatásokra — ehhez
a nézet `OnSizeChanged` metódusát kell felüldefiniálni, és onnan frissíteni a
nézetmodell állapotát.

## Kapocs

- [[concepts/esemalk/avalonia-szamologep-pelda]] — a számológép példa mobil
  környezetre alakítása, amely a tájolásfüggő szelektor osztályokat is
  bevezeti
- [[concepts/esemalk/avalonia-temak-stilusok]] — a szelektor osztályok (pl.
  `IsPortrait`/`IsLandscape` alapján) a stílusrendszer eszközei
- [[concepts/esemalk/avalonia-kezmozdulat-kezeles]] — a mobil környezet másik
  jellemző alkalmazkodási igénye
- [[concepts/esemalk/wpf-elrendezes-tulajdonsagok]] — a relatív elrendezés
  WPF oldali megfelelője
