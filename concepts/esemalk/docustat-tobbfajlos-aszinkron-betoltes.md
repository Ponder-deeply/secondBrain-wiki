---
tags: [concept]
sources: [elte_eva_gy06_munkafuzet.pdf]
derivation: source
kind: procedure
element: earth
updated: 2026-10-21
---

# DocuStat: több fájl lapokon, aszinkron betöltés és haladásjelzés

A 6. gyakorlat kiterjeszti a DocuStat nézetet: egyszerre több fájlt nyit meg külön lapokon, a betöltést és elemzést háttérszálon, párhuzamosan végzi, és a feldolgozás előrehaladását jelzi.

## Tartalom

### UI kiszervezése és lapok

- A menü alatti felület egy `UserControl`-ba kerül (`DocuStatControl`), saját modellel: `LoadFile(IFileManager)` példányosítja a modellt és feliratkozik az eseményeire; `UpdateFileContent`, `UpdateTextStatistics`, `UpdateWordList`, `UpdateWordFilter`, publikus `ResetFilter`.
- A főablakban `TabControl` (`Dock = Fill`); az `OpenFileDialog` `Multiselect = true`, az útvonalak a `FileNames` tömbben; `AddTabPage` hoz létre `DocuStatControl`-t és `TabPage`-et (`Path.GetFileName` a címkének); a kivételeket itt kapjuk el (nem kerül lap a felületre). A `ResetFilter` a `tabControl.SelectedTab.Controls[0] as DocuStatControl` ResetFilter-ét hívja (a `SelectedTab == null` esetet kezelve).

### Párhuzamosítás `async`/`await`-tel

- Az `IFileManager.Load` → `Task<string> LoadAsync()` (az `Async` utótag konvenció; az interfészben nincs `async` kulcsszó). TXT: `File.ReadAllTextAsync`; PDF: az iText nem aszinkron, ezért az oldalbetöltést `await Task.Run(() => { ... })` foglalja taszkba (egy `PdfDocument`-hez egyszerre csak egy szál férhet hozzá, ezért oldalak párhuzamosítása nincs).
- A modell `Load` → `async Task LoadAsync()`: `FileContent = await _fileManager.LoadAsync();` majd a számításigényes metrikák `await Task.Run(...)`-ban.
- A nézet `LoadFileAsync`, `AddTabPageAsync` (a lap „Loading...” felirattal kerül fel, a betöltés végén kapja a fájlnevet); az `OpenDialog` `async void` (az eseménykezelő típusa miatt). A taszkokat `List<Task>`-ba gyűjtve indítjuk el, majd `await Task.WhenAll(tasks)` — egy-egy fájl `await`-elése sorban futtatna, nem párhuzamosan.
- Betöltés alatt a menüpontokat (`openFileDialogMenuItem`, `resetFilterMenuItem`) `Enabled = false`-ra tesszük, mert félkész lapon az újabb betöltés vagy `ResetFilter` hibát okozhat.
- Alternatíva: `Parallel.ForEach` (a `MaxDegreeOfParallelism` korlátozza a szálak számát). Lásd [[concepts/esemalk/csharp-async-await]], [[concepts/esemalk/csharp-task-alapok]].

### UI frissítés háttérszálról

Minden vezérlőt csak a létrehozó szál kezelhet (különben `InvalidOperationException`, *cross-thread operation*); a `Control.Invoke`/`BeginInvoke` a felületi szálon hajtja végre a lambdát.

- Az `async` metódus szinkronban fut az első `await`-ig; explicit indított taszk (`Task.Run`, `Task.Start`, `StartNew`) aszinkron.
- A WinForms alapértelmezett `SynchronizationContext`-je (`WindowsFormsSynchronizationContext`) az `await` után `BeginInvoke`-kal visszavisz a UI szálra, ezért az `AddTabPageAsync` `await loadTask` utáni kódja külön szinkronizáció nélkül is a UI szálon folytatódik.
- A modell eseményeinél ez nem ennyire egyértelmű: csak a `TextStatisticsReady` kerül ki háttérszálon (a `Task.Run` blokkból); a `FileContentReady` és `FilteredWordCountChanged` a UI szálon. Védelem: `if (InvokeRequired) { BeginInvoke(() => UpdateTextStatistics(sender, e)); return; }`.
- Tipp: hosszú szöveg `TextBox`-ba töltését a `WordWrap = false` gyorsítja. Lásd [[concepts/esemalk/winforms-vezerlo-invoke-begininvoke]].

### Haladásjelzés eseménnyel

- Modell: `AnalysisProgressEventArgs` (`Percentage`, 0–100), `event EventHandler<AnalysisProgressEventArgs>? AnalysisProgressChanged`, `OnAnalysisProgressChanged`. A `ComputeDistinctWords` ciklusából századonként jelezzük (`step = Math.Max(words.Length / 100, 1)`, `if (i % step == 0)`) — minden iterációban jelezni többe kerülne, mint a munka; a 100%-ot a `Task.Run` végén, az `OnTextStatisticsReady()` előtt.
- Nézet: `ProgressBar` (`progressBar`, kezdetben `Visible = false`), a `LoadFileAsync` a betöltés idejére láthatóvá teszi, `UpdateProgress` állítja az értékét `InvokeRequired`/`BeginInvoke` védelemmel — itt biztosan háttérszálról és sokszor érkezik az esemény. Ez az esemény egy *folyamat előrehaladását* jelzi, nem egy állapot végét.
- Kitekintés: `IProgress<T>`/`Progress<T>` eltárolja a létrehozáskor aktuális `SynchronizationContext`-et és a `Report()` hívásokat azon továbbítja — nincs kézi `Invoke`. Saját eseménynél a szinkronizáció a mi felelősségünk.
- Több fájlnál a lapok haladásjelzői párhuzamosan mozognak.

### Kitekintés: fájlváltozás figyelése

A megnyitott fájl külső módosításának kezelése: [[concepts/esemalk/filesystemwatcher-fajlvaltozas-figyeles]].

## Kapocs

- [[concepts/esemalk/docustat-winforms-nezet-esemenyek]] — az eredeti, egyfájlos nézet
- [[concepts/esemalk/docustat-perzisztencia-filemanager]] — az `IFileManager`, amelyet aszinkronná alakítunk
- [[concepts/esemalk/winforms-fibonacci-parhuzamositas-pelda]] — hasonló `async`/`await` példa az előadásról
- [[concepts/esemalk/taszk-megszakitasa-cancellationtoken]] — megszakítható műveletek
- [[subjects/esemalk]]
