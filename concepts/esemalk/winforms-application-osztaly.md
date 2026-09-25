---
tags: [concept, esemalk/winforms-statikus-ui]
sources: [elte_eva_ea01_winforms_static.pdf]
derivation: source
updated: 2026-09-13
---

# WinForms Application osztály

A grafikus felületű WinForms alkalmazásokat a statikus `Application` osztály
vezérli: ez indítja el a fő ablakot, és fogja össze a program futását.

## Tartalom

### Az `Application` osztály szerepe

A grafikus felületű alkalmazásokat egy *alkalmazásnak* (`Application`) kell
vezérelnie. Ez egy statikus osztály, amelyet a főprogramban használunk.

- Legfőbb művelete a futtatás (`Run`), amely paraméterben megkapja az első
  indítandó képernyő (ablak) objektumát, illetve lehetőséget ad a kilépésre is
  (`Exit`).
- Alkalmas a környezet beállítására is (`SetHighDpiMode`,
  `EnableVisualStyles`, `UseWaitCursor`, …), valamint információgyűjtésre
  (`StartupPath`, `OpenForms`, `ProductName`, …).
- Eseményeivel követhető a programfutás (`ApplicationExit`, `Idle`).

### A főprogram (`Program.cs`)

Az alkalmazás a főprogram `Main` metódusából indul, amelyet a `[STAThread]`
attribútum jelöl meg (egyszálú, COM-kompatibilis szálmodellt ír elő a
felhasználói felület számára). A `Main` metódus indítja el az alkalmazást az
első ablakkal:

```csharp
// Program.cs
namespace MyFormsApplication
{
    class Program
    {
        [STAThread]
        static void Main() // főprogram
        {
            ApplicationConfiguration.Initialize();
            Application.Run(new MyForm());
            // alkalmazás indítása a megadott ablakkal
        }
    }
}
```

Az `Application.Run(...)` hívás indítja el az alkalmazást a megadott ablakkal
(`Form`-példánnyal): ez teszi a példányosított `Form`-ot az alkalmazás fő
ablakává, és ez futtatja az üzenetciklust, amíg az ablak be nem záródik.

## Kapocs

- [[concepts/esemalk/winforms-ablakok-felepitese]] — az ablak indítása az
  alkalmazás főprogramjából
- [[concepts/esemalk/winforms-vezerlok-alapjai]] — a `Form`, mint a
  vezérlőhierarchia egy speciális, konténer eleme
- [[subjects/esemalk]]
