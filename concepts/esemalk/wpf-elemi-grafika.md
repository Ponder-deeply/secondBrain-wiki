---
tags: [concept]
sources: [elte_eva_ea06_wpf_basics.pdf]
derivation: source
kind: procedure
element: earth
updated: 2026-09-30
---

# WPF képkezelés és elemi grafika

WPF-ben lehetőség van elemi alakzatok rajzolására egy rajzeszköz
(`DrawingContext`) segítségével, bár ez a mód nem az ajánlott megoldás.

## Tartalom

### Képkezelés (`BitmapImage`, `WriteableBitmap`)

A képek memóriabeli kezelését WPF-ben több osztály segíti, amelyek speciális
eszközöket biztosítanak.

- Alapvető képtípus a `BitmapImage`, amely felhasználható különböző felületi
  elemeken (pl. `Image` vezérlő, vagy `ImageBrush` ecset).
- Amennyiben pixelszintű manipulációra van szükség, a `WriteableBitmap`
  biztosít írási/olvasási lehetőségeket.
- WPF-ben minden elérési útvonal `Uri` segítségével van megfogalmazva, pl.:

```csharp
Uri iUri = new Uri(@"Images\smiley.png", UriKind.Relative);
BitmapImage bImage = new BitmapImage(iUri);
```

### Elemi rajzolás (`DrawingContext`)

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

- [[concepts/esemalk/winforms-grafika-alapok]] — a WinForms `Graphics`
  osztálya a hasonló szerepű, de más keretrendszerbeli rajzoló API
- [[concepts/esemalk/wpf-vezerlok-megjelenese]] — a betöltött kép (`ImageBrush`)
  transzformálására szolgáló példa
- [[concepts/esemalk/winforms-kepek-megjelenitese]] — a WinForms `Image`/
  `Bitmap`/`PictureBox` a hasonló szerepű, de más keretrendszerbeli megoldás
