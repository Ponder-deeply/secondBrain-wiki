---
tags: [concept, esemalk/winforms-elemi-grafika]
sources: [elte_eva_ea03_winforms_dynamic.pdf]
derivation: source
updated: 2026-09-13
---

# Színek, tollak és ecsetek WinForms grafikában

A `Graphics` osztály rajzoló műveletei (`DrawLine`, `FillRectangle`, ...)
színt, tollat vagy ecsetet vesznek paraméterül — ezeket a `Color`, `Pen` és
`Brush` típusok írják le.

## Tartalom

- **`Color`** — a színezést biztosítja alapértelmezett értékekkel (pl.
  `Color.Blue`), illetve tetszőleges, akár áttetsző szín létrehozásával
  (`Color.FromArgb(...)`). A `SystemColors` típus tartalmazza a
  rendszerszíneket (pl. `SystemColors.Control`, a vezérlők alapértelmezett
  háttérszíne).
- **`Pen` (toll)** — a színen felül vastagságot, stílust (pl. szaggatott,
  pöttyözött — `DashStyle`) és végpont típust (pl. lekerekített, nyíl) is
  definiál. A `Pens` osztály tartalmazza az egyszerű, előre elkészített
  tollakat (pl. `Pens.Green`, `Pens.Red`).
- **`Brush` (ecset)** — a szín mellett speciális átmenettel, textúrával
  tudja ellátni a felületet, ezért különböző ecsettípusok használhatók
  (`SolidColorBrush`, `TextureBrush`, `LinearGradientBrush`, ...). A
  `Brushes` osztály tartalmazza az egyszerű kitöltéseket (pl.
  `Brushes.Yellow`).

### Példa

```csharp
gr.FillRectangle(Brushes.Yellow, 0, 0, 200, 100);
    // sárga színű téglalap kitöltés
Pen myPen = new Pen(Color.Red, 2);
    // 2 vastag piros toll
myPen.DashStyle = DashStyle.Dot; // pontozott
gr.DrawRectangle(myPen, 0, 0, 200, 100);
    // szegély megrajzolása

Brush myBrush = new LinearGradientBrush(
    new Point(0, 0), new Point(100, 100),
    Color.LightBlue, Color.LightRed);
    // átmenetes ecset
gr.FillPolygon(myBrush, ...); // sokszög kitöltés
```

## Kapocs

- [[concepts/esemalk/winforms-grafika-alapok]] — a `Graphics` osztály és a
  rajzoló műveletek, amelyek a `Pen`/`Brush` paramétereket felhasználják
- [[concepts/esemalk/winforms-rajzeszkoz-beallitasok]] — további rajzeszköz
  beállítások (élsimítás, transzformáció)
