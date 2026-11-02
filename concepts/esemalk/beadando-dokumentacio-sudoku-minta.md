---
tags: [concept]
sources: [elte_eva_feladatok_1_minta.pdf, elte_eva_feladatok_2_minta.pdf]
derivation: source
kind: model
element: earth
updated: 2026-10-21
---

# Beadandó dokumentáció mintája: Sudoku (WinForms és Avalonia)

A két mintadokumentáció ugyanazt a Sudoku játékot dokumentálja kétféle architektúrában: az 1. beadandó (WinForms, háromrétegű) és a 2. beadandó (Avalonia UI, MVVM) mintájaként mutatja a dokumentáció elvárt szerkezetét: készítő adatai, feladat, elemzés, tervezés, tesztelés.

## Tartalom

### A dokumentáció szerkezete

1. **Készítette** — név, e-mail.
2. **Feladat** — a feladat szöveges leírása.
3. **Elemzés** — a használati esetek (UML *use case* diagram) és a döntések.
4. **Tervezés** — programszerkezet (csomagdiagram), osztálydiagramok rétegenként, a rétegek leírása.
5. **Tesztelés** — a tesztesetek felsorolása (osztály, teszt neve, mit ellenőriz).

A dokumentációban nem lehet kódrészlet és képernyőkép; a diagramokat megfelelő szerkesztőeszközzel kell előállítani, a leadás PDF.

### A feladat: Sudoku

$9\times 9$-es tábla, a $3\times 3$-as házakkal; minden sorban, oszlopban és házban egy számjegy pontosan egyszer szerepelhet. Egy mezőre kattintva az érték eggyel nő (üres $\to 1 \to \dots \to 9 \to$ üres), de csak olyan érték állítható be, amely a sorban, oszlopban és házban még nem szerepel. A program számolja a lépéseket és az eltelt időt; új játék, betöltés és mentés; nehézségi szintek (könnyű: 60 perc, 6 generált mező; közepes: 20 perc, 12; nehéz: 10 perc, 18); az előre generált mezők zároltak (sárgával jelölve); játék vége dialógussal.

Használati esetek: Új játék, Betöltés, Mentés, Lépés, Nehézség állítása (`include` Könnyű/Közepes/Nehéz), Kilépés; a Játékidő múlása és a Lépés *invokes* a Játék vége esetet; a Betöltés és az Új játék *precedes* a Lépést.

### Közös osztályok

- **Perzisztencia**: `SudokuTable` (érvényes tábla; `_fieldValues`, `_fieldLocks`, `IsFilled`, `IsLocked`, `IsEmpty`, `GetValue`, `StepValue`, `SetValue`, `SetLock`, hátralévő idő, eltelt idő, lépésszám); `ISudokuDataAccess` (`LoadAsync`, `SaveAsync` — hatékonysági okból aszinkron); `SudokuFileDataAccess` (szöveges `.stl` fájl: első sor a tábla és a ház mérete, majd 9 sor 9 számmal, 0 az üres mező); `SudokuDataException`.
- **Modell**: `SudokuGameModel` (`NewGame`, `PauseGame`, `ResumeGame`, `StepGame`, időzítő `_timer`; események: `FieldChanged`, `GameAdvanced`, `GameOver`), `SudokuFieldEventArgs`, `SudokuEventArgs`, `GameDifficulty` felsorolás; a nehézség paraméterei konstansokban.
- **Tesztelés**: `SudokuGameModelTest`; az időzítőt `ITimer` interfészből származtatva a tesztben `MockTimer` helyettesíti (`RaiseElapsed` explicit kiváltása); tesztek: új játék könnyű/közepes/nehéz, lépés (többször azonos mezőn, esemény kiváltása), idő múlása a játék végéig, betöltés és mentés mockolt perzisztenciával. Lásd [[concepts/esemalk/mock-objektumok]].

### 1. beadandó (2025/26 ősz): WinForms, háromrétegű

- Egyablakos asztali alkalmazás; menü: *File* (Új játék, Játék betöltése, Játék mentése, Kilépés), *Beállítások* (Könnyű/Közepes/Nehéz játék); státuszsor a lépésszámmal és hátralévő idővel.
- Rétegek: `View`, `Model`, `Persistence` névterek; két projekt: felületfüggetlen (Persistence + Model) és WinForms-függő (View).
- Nézet: `GameForm` (aggregálja a modellt `_model` és az adatelérést `_dataAccess`); a táblát dinamikusan létrehozott gombmező (`_buttonGrid`) adja; `GenerateTable`, `SetupTable`; a fájlműveleteket dialógusablakok végzik.
- Lásd [[concepts/esemalk/haromreteg-architektura]], [[concepts/esemalk/winforms-dinamikus-vezerlok]].

### 2. beadandó (2026/27 ősz): Avalonia, MVVM

- .NET Avalonia alkalmazás, elsősorban asztali és Android platformra; egy fő nézet, portré tájolás; a játékállás mobilon háttérbe kerüléskor automatikusan mentődik, aktiváláskor visszatöltődik; érintéssel kezelhető $9\times 9$-es tábla; felugró üzenet a játék végén.
- Négy projekt: modellt és perzisztenciát tartalmazó osztálykönyvtár (.NET Standard Class Library), valamint a platformfüggetlen és platformfüggő Avalonia projektek.
- Névterek: `View`, `Model`, `ViewModel`, `Persistence`; az `App` osztály példányosítja a modellt, a nézetmodellt és a nézetet, összeköti őket, felügyeli az adatkezelést és kezeli a platformfüggő életciklust (`OnFrameworkInitializationCompleted`; `Deactivated` $\to$ mentés `SuspendedGame`-be, `Activated` $\to$ visszatöltés).
- Perzisztencia: az `ISudokuDataAccess` `Stream`-alapú műveletekkel is bővül (`LoadAsync(Stream)`, `SaveAsync(Stream, SudokuTable)`) a mobil platformok támogatására.
- Nézetmodell: `SudokuViewModel` (MVVM Toolkit `RelayCommand`, `ObservableObject`; `NewGameCommand`, `LoadGameCommand`, `SaveGameCommand`, `ExitCommand`, `Fields`, `GameStepCount`, `GameTime`, `IsGameEasy/Medium/Hard`, események `NewGame`, `LoadGame`, `SaveGame`, `ExitGame`); a nézetmodell csak információt kér a modelltől, nem avatkozik a játék futtatásába. `SudokuField`: pozíció, szöveg, engedélyezettség, `StepCommand`.
- Nézet: `MainView` (`UserControl`, `UniformGrid` `Button`-ökkel) beágyazva a `MainWindow`-ba — asztalon ablakként, mobilon lapként jelenik meg; betöltés/mentés a `StorageProvider` `OpenFilePickerAsync`/`SaveFilePickerAsync` metódusaival; felugró üzenetekhez a `MessageBox.Avalonia` NuGet csomag.
- Lásd [[concepts/esemalk/avalonia-mvvm-toolkit]], [[concepts/esemalk/avalonia-dialogusablakok]], [[concepts/esemalk/avalonia-mobil-alkalmazaskornyezet-eletciklus]].

### Különbség röviden

| | 1. beadandó | 2. beadandó |
|---|---|---|
| Keretrendszer | Windows Forms | Avalonia UI |
| Architektúra | háromrétegű (MV + perzisztencia) | MVVM |
| Esemény/parancs | eseménykezelők a `GameForm`-ban | parancsok a nézetmodellben, vezérlés az `App`-ban |
| Perzisztencia | fájlnév alapján | fájlnév és `Stream` (mobil) |
| Platform | Windows | asztali és Android |

## Kapocs

- [[concepts/esemalk/beadando-2-avalonia-feladatkiiras]] — a 2. beadandó közös követelményei és a feladatválaszték
- [[concepts/esemalk/beadando-statikus-analizis]] — a beadandókra vonatkozó kódminőségi ellenőrzés
- [[concepts/esemalk/tictactoe-haromreteg-pelda]] — a háromrétegű architektúra előadási példája
- [[concepts/esemalk/retegek-szerelvenyekre-bontasa]] — a felületfüggetlen és felületfüggő projektekre bontás
- [[subjects/esemalk]]
