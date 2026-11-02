---
tags: [concept]
sources: [elte_eva_ea03_winforms_dynamic.pdf]
derivation: source
kind: procedure
element: earth
updated: 2026-09-25
---

# Képek és erőforrások WinFormsban

Képek kezelését a `System.Drawing` és `System.Drawing.Imaging` névterek
biztosítják; a megjelenítéshez alapvetően a `PictureBox` vezérlő szolgál.

## Tartalom

Az `Image` osztály biztosítja az alapvető funkciókat: megnyitás
(`Image.FromFile(…)`, `Image.FromStream(…)`), mentés (`Save(…)`), egyszerű
manipulációk (`RotateFlip(…)`), miniatűrkép lekérdezés
(`GetThumbnailImage(…)`), valamint dimenziók lekérdezése (`Width`, `Height`,
`PixelFormat`, `Palette`, …). Támogatott képformátumok: BMP, GIF, JPEG, PNG,
TIFF.

Ennél bővebb funkcionalitást biztosít a `Bitmap` osztály, amely lehetővé teszi
a pixelszintű lekérdezést és írást (`GetPixel(…)`, `SetPixel(…)`), valamint
kép létrehozását méret, fájlnév, illetve másik kép alapján (átméretezéssel
is).

A képek több vezérlőn is megjeleníthetők, például egyszerű címkén
(`Label.Image`):

```csharp
Label myLabel = new Label();
Bitmap myBitmap = new Bitmap(…);  // kép betöltése
myLabel.Size = new Size(myBitmap.Width, myBitmap.Height); // címke átméretezése
myLabel.Image = myBitmap;         // kép beállítása
```

Alapvetően a képek megjelenítésére azonban a `PictureBox` vezérlő szolgál,
amely számos kényelmi funkciót biztosít:

- méretezés módja (`SizeMode`)
- kép betöltése lokális vagy távoli útvonalról (`ImageLocation`)
- hibakép megadása (`ErrorImage`)

```csharp
PictureBox myBox = new PictureBox();
…
myBox.Image = myBitmap;             // kép beállítása
myBox.SizeMode = PictureBoxSizeMode.StretchImage; // kép elnyújtása a vezérlő méreteinek megfelelően
```

Egy kidolgozott példa mozgókép-megjelenítő alkalmazást mutat be, amely egy
könyvtárból (`FolderBrowserDialog`-gal kiválasztva) betöltött képsorozatot
(`_images`) generált `PictureBox`-okon (`_pictureBoxes`) jelenít meg
animációként, egy `Timer` segítségével periodikusan cserélve a látható
képkockákat, és lehetővé téve az animáció sebességének szabályozását.

### Erőforrások kezelése (content, embedded resource, `.resx`)

A programban felhasznált erőforrásokat (képek, hangok, …) célszerű a
projekthez rögzíteni, ahelyett hogy futás közben, elszórt fájlokból töltenénk
be őket.

Bármilyen fájl hozzáadható a projekthez, két módon:

- **tartalomként** (*content*) — a fájl átmásolható a kimeneti könyvtárba, az
  elem tulajdonságainak megfelelő beállításával
- **beágyazott erőforrásként** (*embedded resource*) — a fájl az
  alkalmazásba (a végrehajtható fájlba) épül be

Az erőforrásfájlok (*resource file*, `.resx`) lehetővé teszik az erőforrások
(szöveg, kép, ikon) csoportos kezelését és programkódban történő elérését; az
így hozzáadott erőforrások is beágyazottan helyezkednek el az alkalmazásban.
Például egy `MyResource.resx` fájl hozzáadásával a tartalmak a
`MyResource.ResourceManager` útvonalon érhetők el a kódból.

## Kapocs

- [[concepts/esemalk/winforms-vezerlok-alapjai]] — a `Control` osztály, amelynek
  a `PictureBox` és a `Label` is leszármazottja
- [[concepts/esemalk/winforms-dinamikus-vezerlok]] — a `PictureBox`-ok
  dinamikus (kódból történő) létrehozása és elrendezése
- [[concepts/esemalk/stream-alapu-fajlkezeles]] — futásidőben, a
  fájlrendszerből (nem a projektbe ágyazva) betöltött fájlok kezelése
- [[concepts/esemalk/dotnet-lokalizacio-kulturak]] — az erőforrásfájlok
  kultúra-specifikus (lokalizációs) felhasználása
