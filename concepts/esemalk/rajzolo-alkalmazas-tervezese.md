---
tags: [concept]
sources: [elte_eva_ea03_winforms_dynamic.pdf]
derivation: source
updated: 2026-09-13
---

# Rajzolóalkalmazás tervezése modell/nézet architektúrában

Egy egyszerű rajzolóprogram — amellyel rögzített típusú alakzatokat (zöld
téglalap, piros ellipszis, sárga háromszög) lehet egérrel egy felületre
rajzolni, törölni, betölteni és menteni — tankönyvi példa arra, hogyan
épül fel egy elemi grafikát használó WinForms alkalmazás a modell/nézet
architektúra szerint.

## Tartalom

### Feladat

- Az alakzatok rögzítettek (zöld téglalap, piros ellipszis, egyenlő szárú
  sárga háromszög), a típust rádiógombokkal lehet kiválasztani.
- A rajz törölhető (gombbal vagy a *Delete* billentyűvel), betölthető és
  menthető.
- A rajzolás a bal egérgomb lenyomására indul, ekkor kék kerettel jelöli
  ki az alakzatot a program, majd felengedéskor helyezi el a vásznon.

### Tervezés

- Minden alakzat leírható egy befoglaló téglalappal, ezért egy típusban
  (`Model::Shape`) modellezzük őket, megadva az alakzattípust
  (`Model::ShapeType`: `Rectangle`, `Ellipse`, `Triangle`) és a
  téglalap koordinátáit/méretét (`StartX`, `StartY`, `Width`,
  `Height`).
- Az alakzatokat egy képbe (`Model::VectorImage`) helyezzük, amely
  lehetőséget ad szöveges fájlból történő betöltésre, mentésre,
  hozzáadásra és törlésre (`AddShape`, `Clear`, `Save`, `Load`), illetve
  eseménnyel (`ImageChanged`) jelzi, ha változott a kép.
- A nézetben (`View::DrawingForm`, egy `Form`) feldolgozzuk a panel
  egéreseményeit (`Panel_MouseDown/Move/Up`), valamint az ablak
  billentyűzet eseményét; minden változáskor frissítjük a panelt, és
  újrarajzoljuk az elemeket (`Panel_Paint`).
- A `DrawingForm` az `Image_ImageChanged` kezelőben hívja a panel
  `Refresh()`-ét, ami kiváltja a `Panel_Paint` eseményt.

Ez a felépítés a korábban tárgyalt modell/nézet architektúra
([[concepts/esemalk/modell-nezet-architektura]]) konkrét alkalmazása: a
`Model::Shape`/`Model::VectorImage` a modell, a `View::DrawingForm` a
nézet, a köztük lévő kapcsolatot az `ImageChanged` esemény tartja fenn.

### Megvalósítás

```csharp
// DrawingForm.cs
private void Panel_Paint(object sender, PaintEventArgs e){
    Graphics graphics = e.Graphics;
    // rajzeszköz az eseményargumentumból
    foreach (Shape shape in _image.Shapes)
        DrawShape(graphics, shape);
        // alakzatok kirajzolása
}
...
private void Image_ImageChanged(...){
    _panel.Refresh();
}

private void DrawShape(Graphics graphics, Shape shape){
    switch (shape.Type) {
        case ShapeType.Rectangle:
            graphics.FillRectangle(
                Brushes.LightGreen,
                shape.StartX, shape.StartY,
                shape.Width, shape.Height);
                // kitöltés
            graphics.DrawRectangle(Pens.Green, ...);
                // keret
            break;
        ...
    }
}
```

A `DrawShape` egy `switch`-csel az alakzat típusa (`shape.Type`) szerint
választja ki a megfelelő kitöltő ecsetet és tollat, majd a megfelelő
`Fill*`/`Draw*` párost hívja.

### Interakció sorrendje

A tervezési (szekvencia-)diagram szerint az egérműveletek sorrendje:
`MouseDown` → `Panel_MouseDown` → `DrawShape` (előnézet); `MouseMove` →
`Panel_MouseMove` → `DrawShape` (előnézet frissítése); `MouseUp` →
`Panel_MouseUp` → `AddShape` a modellen → `ImageChanged` → `Refresh` a
panelen.

## Kapocs

- [[concepts/esemalk/modell-nezet-architektura]] — az általános
  modell/nézet architektúra, amelynek ez konkrét megvalósítása
- [[concepts/esemalk/winforms-grafika-alapok]] — a `Graphics` osztály és a
  rajzoló műveletek, amelyeket a `DrawShape` metódus használ
- [[concepts/esemalk/winforms-szinek-ecsetek-tollak]] — a `Brushes`/`Pens`
  osztályok, amelyekkel az alakzatokat rajzoljuk
- [[concepts/esemalk/winforms-eger-esemenyek]] — a `MouseDown`/`MouseMove`/
  `MouseUp` események, amelyek az alakzat felvételét vezérlik
- [[concepts/esemalk/esemeny-letrehozasa-kivaltasa]] — saját esemény
  (`ImageChanged`) létrehozása és kiváltása
