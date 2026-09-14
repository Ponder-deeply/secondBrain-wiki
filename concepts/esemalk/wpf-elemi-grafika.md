---
tags: [concept]
sources: [elte_eva_ea06_wpf_basics.pdf]
derivation: source
updated: 2026-09-13
---

# WPF elemi grafika (DrawingContext)

WPF-ben lehetőség van elemi alakzatok rajzolására egy rajzeszköz
(`DrawingContext`) segítségével, bár ez a mód nem az ajánlott megoldás.

## Tartalom

- A rajzoláshoz számtalan rajzolómetódus használható, pl. `DrawRectangle`,
  `DrawText`, `DrawImage`, `DrawVideo`.
- A rajzobjektumot egy kezelőre (`DrawingGroup`) kell ráállítani, azt pedig
  egy rajzfelületre (`DrawingImage`).
- A `DrawingContext` igazából nem rajzol azonnal, hanem utasításokat állít
  össze a (3D) rendereléshez; emellett lehetőség van állapotkezelésre is.

```csharp
Image myImage = new Image();               // képmegjelenítő
DrawingGroup drGroup = new DrawingGroup();  // rajzkezelő
using (DrawingContext dx = drGroup.Open())  // rajzeszköz létrehozása
{
    Pen myPen = new Pen(Brushes.Black, 2);  // toll
    dx.DrawRectangle(Brushes.Blue, myPen, new Rect(0, 0, 25, 25));
    // …
}
DrawingImage img = new DrawingImage(drGroup); // rajzfelület
myImage.Source = img;                          // kirajzolás
```

- Az elemi rajzolás használata **nem javasolt**, mivel a primitív alakzatok
  (`Rectangle`, `Ellipse`, …) már osztályként meg vannak valósítva a
  keretrendszerben, ezért a használatuk egyszerűbb és gyorsabb.

## Kapocs

- [[concepts/esemalk/wpf-kepkezeles]] — a `BitmapImage`/`WritableBitmap`
  raszteres képkezelés a vektoros `DrawingContext`-tel szemben
- [[concepts/esemalk/winforms-grafika-alapok]] — a WinForms `Graphics`
  osztálya a hasonló szerepű, de más keretrendszerbeli rajzoló API
