---
tags: [concept, esemalk/winforms-statikus-ui]
sources: [elte_eva_ea01_winforms_static.pdf]
derivation: source
updated: 2026-09-12
---

# WinForms ablakok felépítése

Egy WinForms ablak a `Form` osztály leszármazottja, amelynek forráskódja két
fájlban, egy `partial` osztályként oszlik meg: a saját kód és a
felülettervezővel generált kód elkülönül egymástól.

## Tartalom

### Az ablak, mint osztály

Az ablakok osztályok (a `Form` osztály leszármazottai), amelyekben
definiálhatjuk az ablak vezérlőit és azok viselkedését. Speciális
tulajdonságokkal szabályozható a megjelenésük, pl. vezérlő eszköztár
(`ControlBox`, `MinimizeBox`, `MaximizeBox`), menü (`Menu`), kezdőpozíció
(`StartPosition`).

### Parciális osztály, három fájl

Az ablakok általában parciális (`partial`) osztályok, amelyek két `.cs`
fájlban helyezkednek el:

- `<osztálynév>.cs` — a programozott rész (saját kód, eseménykezelők,
  dinamikusan létrehozott vezérlők);
- `<osztálynév>.Designer.cs` — a felülettervezővel generált kód, benne az
  `InitializeComponent()` metódussal, amelyet az osztály konstruktora futtat
  (így a vezérlők csak ennek lefutását követően érhetők el), valamint a
  `Dispose()` metódussal, amely az ablak megsemmisítéséért felel;
- `<osztálynév>.resx` — az ablakhoz tartozó erőforrások (képek, hangok).

```csharp
// MyForm.cs
namespace MyFormsApplication
{
    partial class MyForm : Form {
        // parciális ablak osztály
        public MyForm() // konstruktor
        {
            InitializeComponent();
                // generált vezérlők létrehozása
            … // további tevékenységek
        }
    }
}
```

```csharp
// MyForm.Designer.cs
namespace MyFormsApplication
{
    partial class MyForm {
        // parciális ablak osztály másik része
        public void Dispose() { … }
            // ablak megsemmisítése
        public void InitializeComponent(){ … }
            // vezérlők inicializálása
        // … vezérlők mezői
    }
}
```

## Kapocs

- [[concepts/esemalk/winforms-vezerlok-alapjai]] — a `Form`-ban elhelyezett
  vezérlők és tulajdonságaik
- [[concepts/esemalk/winforms-application-osztaly]] — az ablak indítása az
  alkalmazás főprogramjából
- [[subjects/esemalk]]
