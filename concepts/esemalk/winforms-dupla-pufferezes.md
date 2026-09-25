---
tags: [concept, esemalk/winforms-elemi-grafika]
sources: [elte_eva_ea03_winforms_dynamic.pdf]
derivation: source
updated: 2026-09-13
---

# Villogásmentes rajzolás (dupla pufferezés) WinForms-ban

Ha egy `Panel_Paint` kezelő sok alakzatot rajzol közvetlenül a képernyőre,
a felület sok alakzat esetén villoghat, mivel a rajzolás több lépésben,
láthatóan épül fel. A megoldás, hogy nem közvetlenül a képernyőre
rajzolunk, hanem egy, a memóriában lévő képre (`Bitmap`), és a kész képet
egy lépésben rajzoljuk ki.

## Tartalom

### Probléma és megoldás

- Feladat: módosítsuk a rajzolóprogramot úgy, hogy ne villogjon a
  képernyő sok alakzat esetén sem.
- A megoldás, hogy nem közvetlenül a képernyőre rajzolunk, hanem egy
  memóriabeli képre (`Bitmap`).
- A képet kezdetben olyan színűre színezzük, mint a vezérlő
  (`SystemColors.Control`).
- Minden alakzatot a képre rajzolunk, majd a képet egy lépésben
  kirajzoljuk a képernyőre (`DrawImage`), így az csak egyszer frissül.
- Mozgatás közben nem használjuk a frissítést, csupán egy lépésben
  kirajzoljuk a képet.

### Megvalósítás

```csharp
// DrawingForm.cs
private void Panel_Paint(...) {
    Bitmap bitmap = new Bitmap(_panel.Width,
        _panel.Height); // kép létrehozása
    Graphics graphics = Graphics.FromImage(bitmap);
        // rajzeszköz a képre
    graphics.Clear(SystemColors.Control);
        // a vezérlő színére festjük a képet
    foreach (Shape shape in _image.Shapes)
        DrawShape(graphics, shape);
        // alakzatok kirajzolása
    e.Graphics.DrawImage(bitmap, 0, 0);
        // kép kirajzolása a panelre
}
```

A `Panel_Paint` így két `Graphics` objektummal dolgozik: a köztes
`graphics` a memóriabeli `bitmap`-re rajzol (ide kerül minden alakzat), az
`e.Graphics` pedig csak egyetlen `DrawImage` hívással jeleníti meg a kész
képet a panelen.

## Kapocs

- [[concepts/esemalk/winforms-grafika-alapok]] — a `Graphics.FromImage`
  és `DrawImage` műveletek, amelyekre ez a technika épül
- [[concepts/esemalk/rajzolo-alkalmazas-tervezese]] — a rajzolóprogram
  példa, amelynek villogását ez a technika szünteti meg
