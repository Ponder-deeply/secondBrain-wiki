---
tags: [concept]
sources: [elte_eva_ea03_winforms_dynamic.pdf]
derivation: source
updated: 2026-09-13
---

# WinForms elemi grafika — a `Graphics` osztály

A WinForms grafikus felülete lehetővé teszi 2D alakzatok (vonal, kör,
szöveg, ...) és képek közvetlen rajzolását bármely felületre az ablakon
belül, a `System.Drawing` névtér `Graphics` osztályának metódusaival.

## Tartalom

### Alapfogalmak

- Minden vezérlő (`Control`) és kép (`Image`) rajzolható.
- A rajzolás az adott vezérlő koordinátarendszerében, logikai koordináták
  szerint történik (élsimítással korrigálható).
- A rajzolásnál műveletenként adjuk meg a tulajdonságokat (nincs
  megőrzött "rajzolási állapot" a `Graphics` objektumon kívül).

### Rajzoló műveletek

- Körvonal rajzolása toll (`Pen`) segítségével: `DrawLine`,
  `DrawRectangle`, `DrawArc`, ...
- Kitöltés ecset (`Brush`) segítségével: `FillRectangle`, `FillEllipse`,
  `FillPath`, ...
- Szöveg rajzolása betűtípussal (`Font`) és tollal: `DrawString`.
- Kép rajzolása: `DrawImage`.
- A rajzfelület törlése: `Clear`.

### A rajzfelület megszerzése

A `Graphics` példány (a rajzfelület) többféleképpen szerezhető meg:

1. **`Panel` közvetlen rajzoláshoz.** A `Panel`-nek van egy `Paint`
   eseménye, amelynek eseményargumentumából (`PaintEventArgs.Graphics`)
   lekérdezhető a rajzobjektum. A panel `Refresh()` hívására újra kiváltódik
   a `Paint` esemény. Ugyanígy lekérhető az objektum a
   `CreateGraphics()` utasítással is.
2. **Bármely egyéb vezérlő** — a `Graphics.FromHwnd(control.Handle)`
   utasítással, amely paraméterben egy `Control` objektum `Handle`
   tulajdonságát kapja meg:
   ```csharp
   Graphics g = Graphics.FromHwnd(myButton.Handle);
   ```
3. **Kép (`Image`)** — háttérben végzett rajzoláshoz és kimentéshez a
   `Graphics.FromImage(image)` művelettel:
   ```csharp
   Panel myPanel = new Panel(); // rajzpanel
   ...
   myPanel.Paint += new PaintEventHandler(Panel_Paint);
   ...
   void Panel_Paint(object sender, PaintEventArgs e){
       Graphics gr = e.Graphics;
       // vagy myPanel.CreateGraphics();
       ...
   }
   ```

### Kapcsolódó példa

Egy teljes rajzolóprogram (rögzített alakzatok — téglalap, ellipszis,
háromszög — egérrel történő elhelyezése) tervezését és megvalósítását lásd:
[[concepts/esemalk/rajzolo-alkalmazas-tervezese]].

## Kapocs

- [[concepts/esemalk/winforms-szinek-ecsetek-tollak]] — a `Color`, `Pen`,
  `Brush` típusok, amelyekkel a rajzoló műveletek paraméterezhetők
- [[concepts/esemalk/winforms-rajzeszkoz-beallitasok]] — élsimítás,
  koordinátarendszer-transzformáció, állapotkezelés, vágás
- [[concepts/esemalk/winforms-eger-esemenyek]] — az egérrel vezérelt
  rajzolás eseményei
- [[concepts/esemalk/winforms-dupla-pufferezes]] — villogásmentes
  rajzolás `Bitmap` közbeiktatásával
- [[concepts/esemalk/winforms-vezerlok-alapjai]] — a `Control` osztály,
  amelynek rajzolása a `Graphics` osztályon keresztül történik
