---
tags: [concept]
sources: [elte_eva_gy02_munkafuzet.pdf]
derivation: source
kind: procedure
element: earth
updated: 2026-10-21
---

# WinForms első alkalmazások: gombvadászat és digitális órák

A 2. gyakorlat bevezet a Windows Forms asztali alkalmazások fejlesztésébe (Visual Studio 2026, .NET 10): három feladaton gyakoroltatja a tervezőfelületet, az eseménykezelést, az időzítést és az egyedi vezérlőket.

## Tartalom

### Projekt és Designer

- Sablon: *Windows Forms App* (nem a *.NET Framework* változat). Generált elemek: `Form1` és `Program` (benne a `Main`). A `Form1.Designer.cs` generált kód — nem szerkesztjük; a saját kód a `Form1.cs`-ben van (*View code*).
- A Designer paneljei: középen a grafikus terv, balra a *Toolbox* (drag-and-drop vezérlők), jobbra a *Properties* (tulajdonságok és események, villám ikon). A `(Name)` tulajdonság a forráskódbeli változónevet is beállítja.
- Lásd [[concepts/esemalk/winforms-ablakok-felepitese]], [[concepts/esemalk/winforms-vezerlok-alapjai]].

### 1. feladat: kilépő gomb — eseménykezelő hozzárendelése

Négy mód az eseménykezelő feliratkoztatására:
1. kettős kattintás a gombra a Designerben (csak a `Click` eseményre) — `quitButton_Click` jön létre;
2. a *Properties* panel villám ikonján a `Click` mellé a kezelő nevét beírva;
3. a delegáltnak (`EventHandler(object sender, EventArgs e)`) megfelelő szignatúrájú metódust a legördülő menü felkínálja;
4. kódból: `quitButton.Click += new EventHandler(ButtonClicked);` — **az `InitializeComponent()` után**, mert addig a vezérlő `null`.

A kezelőben a `Close()` (a `Form` örökölt metódusa) bezárja az ablakot; egyablakos alkalmazásnál ez leállítja a programot. Lásd [[concepts/esemalk/vezerlo-esemenykezelo-tarsitas]].

### 2. feladat: Button Hunter (gombvadászat)

- Felület: `Text` = „Button Hunter”, `MinimumSize` beállítva; `pushButton` („PUSH ME”), `StatusStrip` (`statusStrip`) `statusLabel` címkével.
- A kezelőben a gomb új pozícióját a `Location` tulajdonsággal állítjuk, véletlen koordinátákkal (`Random generator`, az ablak szintjén példányosítva, nem kattintásonként); a határokat az ablak `ClientSize`-ából (nem tartalmazza a szegélyt és a címsort), a gomb méretéből és a státuszsor magasságából számítjuk: `generator.Next(ClientSize.Width - pushButton.Width)` stb.
- Időzítés: `System.Windows.Forms.Timer` (`Interval` = 1000 ms, a `Tick` eseményre feliratkozva az `UpdateStatusBar` frissíti az állapotsort); az első kattintás indítja (`timer.Start()`), eltelt idő: `(DateTime.Now - startTime).TotalSeconds`, `{elapsedSeconds:F0}` formázással.
- Záráskor a `FormClosing` esemény kezelője `MessageBox`-ban kiírja az átlagos kattintás/másodpercet (`F2`), csak ha a játék elindult, és `e.CloseReason == CloseReason.UserClosing` (hogy az OS leállítása ne blokkolódjon).
- Lásd [[concepts/esemalk/winforms-idozito-parhuzamositas]].

### 3. feladat: digitális órák (egyedi vezérlő)

- *Add → User Control*: a `Clock` osztály a `UserControl`-ból származik, saját Designer (`Clock.Designer.cs`) és kódfájl; két `Label` (`cityLabel`, `timeLabel`: Consolas betű, `BorderStyle`, `AutoSize = false`).
- Tulajdonságok: `City` (a címke szövegét kezeli) és `TimeZone` (az eltolás órában; a setter hívja a `RefreshTime`-ot). A `RefreshTime` `HH:mm` formátumban jeleníti meg az időt, másodpercenként villogó elválasztóval (`time.Second % 2 == 0 ? "HH:mm" : "HH mm"`); a vezérlő saját időzítője másodpercenként hívja.
- Főablakban `FlowLayoutPanel` (`Dock = Fill`) tartalmazza a 4 `Clock` példányt; ha a vezérlő nem látszik a Toolboxban, le kell fordítani a projektet (vagy az `AutoToolboxPopulate` beállítást igazra állítani).
- Attribútumok a tervező számára: `[Category("Appearance")]`, `[Description(...)]`, `[DesignerSerializationVisibility(Visible)]` — utóbbi **.NET 9 óta kötelező** az egyedi vezérlők publikus tulajdonságain (nélküle fordítási hiba); `[Browsable(false)]` elrejti a tulajdonságot a *Properties* panelről.
- Lásd [[concepts/esemalk/winforms-elrendezok]], [[concepts/esemalk/csharp-megjegyzesek]] (attribútumok).

## Kapocs

- [[concepts/esemalk/gyakorlati-munkafuzetek-attekintes]] — a gyakorlatok áttekintése
- [[concepts/esemalk/winforms-dinamikus-vezerlok]] — vezérlők futásidejű kezelése
- [[concepts/esemalk/docustat-winforms-nezet-esemenyek]] — a következő gyakorlat: modell és nézet együtt
- [[subjects/esemalk]]
