---
tags: [concept]
sources: [elte_eva_ea06_wpf_basics.pdf]
derivation: source
updated: 2026-09-13
---

# WPF képkezelés

A képek memóriabeli kezelését WPF-ben több osztály segíti, amelyek speciális
eszközöket biztosítanak.

## Tartalom

- Alapvető képtípus a `BitmapImage`, amely felhasználható különböző felületi
  elemeken (pl. `Image` vezérlő, vagy `ImageBrush` ecset).
- Amennyiben pixelszintű manipulációra van szükség, a `WritableBitmap`
  biztosít írási/olvasási lehetőségeket.
- WPF-ben minden elérési útvonal `Uri` segítségével van megfogalmazva, pl.:

```csharp
Uri iUri = new Uri(@"Images\smiley.png", UriKind.Relative);
BitmapImage bImage = new BitmapImage(iUri);
```

## Kapocs

- [[concepts/esemalk/wpf-elemi-grafika]] — a `DrawingContext`-tel végzett
  elemi rajzolás a képkezeléstől független, vektoros megjelenítési mód
- [[concepts/esemalk/wpf-transzformaciok]] — a betöltött kép (`ImageBrush`)
  transzformálására szolgáló példa
- [[concepts/esemalk/winforms-kepek-megjelenitese]] — a WinForms `Image`/
  `Bitmap`/`PictureBox` a hasonló szerepű, de más keretrendszerbeli megoldás
