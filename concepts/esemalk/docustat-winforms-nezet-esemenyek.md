---
tags: [concept]
sources: [elte_eva_gy03_munkafuzet.pdf]
derivation: source
kind: procedure
element: earth
updated: 2026-10-21
---

# DocuStat WinForms nézete: modell-események, push és pull

A 3. gyakorlat az 1. gyakorlat `DocumentStatistics` modelljére grafikus (WinForms) nézetet épít: a modell eseményekkel jelzi állapotváltozásait, a nézet pedig csak megjelenít és a vezérlők változásait a modellbe írja.

## Tartalom

### Felület

`DocuStatView` projekt (`DocuStat` solution): `DocuStatDialog` ablak (`FixedSingle`, `MaximizeBox = false`), `MenuStrip` (*File*: `openFileDialogMenuItem`, `resetFilterMenuItem`), csak olvasható több soros `TextBox` (`textBox`, `ScrollBars = Vertical`), `ListBox` (`listBoxCounter`), két `NumericUpDown` (`spinBoxMinLength`, `spinBoxMinOccurrence`, `Minimum = 1`, utóbbi `Maximum = 500`), `textBoxIgnoredWords` és a metrikák címkéi. A modell projektet *Add → Existing Project* + *Add Project Reference* adja a nézethez.

### A modell három eseménye

| Esemény | Jelentés | Stílus |
|---|---|---|
| `FileContentReady` | a fájl tartalmának beolvasása megtörtént | *pull* (jelzés) |
| `TextStatisticsReady` | a metrikák kiszámítása megtörtént; `TextStatisticsReadyEventArgs` szállítja az adatot | *push* |
| `FilteredWordCountChanged` | a megjelenítendő szólista megváltozott (szűrő átállítása **vagy** új fájl betöltése) | *pull* (jelzés) |

- **Pull**: az esemény csak jelez, a nézet kiolvassa a modell megfelelő tulajdonságát — egyszerűbb, kényelmes, ha a nézetnek sok összefüggő adatra van szüksége (szűrt szólista).
- **Push**: az `EventArgs` leszármazottja (csak olvasható tulajdonságok, konstruktorban kapott értékek) hordozza az adatot; a kezelő mindig érvényes adatot kap, nem kell a modellre hivatkoznia, így a `_documentStatistics` esetleges `null` volta nem gond.
- Kiváltás: privát `OnXxx` metódusokban `Event?.Invoke(this, ...)`. Lásd [[concepts/esemalk/esemeny-letrehozasa-kivaltasa]].

### Esemény csak tényleges változáskor

A szűrő tulajdonságok (`MinWordLength`, `MinWordOccurrence`, `IgnoredWords`) saját adatmezőt kapnak, és a setter csak akkor vált ki eseményt, ha az érték ténylegesen megváltozott (`if (_minWordLength == value) return;`); az `IgnoredWords` normalizált listáit `SequenceEqual()`-lal hasonlítjuk össze (az üres szavakat a normalizálás eldobja, különben egy üres szövegdoboz vagy záró vessző „változás” lenne).

Ennek oka: a nézet az `UpdateWordFilter`-ben mindhárom szűrőt beírja minden vezérlő-változásnál; őrfeltétel nélkül egyetlen billentyűleütés három eseményt és a lista háromszori újraépítését okozná — az ilyen fölösleges körök az eseményvezérelt alkalmazások tipikus teljesítményproblémái.

### Eseménykezelők a nézetben

- `OpenDialog`: `OpenFileDialog` (`InitialDirectory`, `Filter`, `RestoreDirectory`, `ShowDialog() == DialogResult.OK`) `using` blokkban; új `DocumentStatistics` példány, feliratkozás a három eseményre (`UpdateFileContent`, `UpdateTextStatistics`, `UpdateWordList`), `UpdateWordFilter` hívása (a felületen már beállított szűrő átadása), majd `Load()`; az `IOException`-t `MessageBox` jelzi. Eseménykezelőt a `-=` operátorral lehet levenni.
- `UpdateFileContent`: ha a `FileContent` megegyezik a `textBox.Text`-tel, nem tölt újra; különben beírja a szöveget és törli a `listBoxCounter.Items`-t.
- `UpdateTextStatistics(object?, TextStatisticsReadyEventArgs)`: a címkék szövegét az `e` tulajdonságaiból állítja (itt nincs szükség `_documentStatistics!` null-forgiving operátorra).
- `UpdateWordFilter`: a vezérlők értékét a modellbe írja (`Convert.ToInt32(spinBox.Value)`; az `IgnoredWords`-t a setter normalizálja); a három vezérlő `ValueChanged`/`TextChanged` eseményére kötve.
- `UpdateWordList`: `listBoxCounter.BeginUpdate()` / `EndUpdate()` közé zárva tölti fel az `Items`-t a `FilteredWordCount`-ból — enélkül minden elem hozzáadása frissítést váltana ki, ami villogást okozna.
- `ResetFilter`: ha nincs betöltött fájl, `MessageBox`; különben a vezérlőket visszaállítja az alapértékre — ezek eseményei az `UpdateWordFilter`-en át a modellbe írnak, a modell pedig a `FilteredWordCountChanged`-del frissíti a listát. A lista frissítésének így egyetlen útvonala van, bárhonnan jön a változás.

Az eseményvezérelt architektúra lényege itt kézzelfogható: nem kell külön „kiszámítás” menüpont, a lista magától, azonnal követi a beállításokat.

## Kapocs

- [[concepts/esemalk/docustat-modell-szovegstatisztika]] — a modell, amelyre a nézet épül
- [[concepts/esemalk/modell-nezet-architektura]] — a modell/nézet architektúra elve
- [[concepts/esemalk/docustat-tobbfajlos-aszinkron-betoltes]] — a felület kiszervezése egyedi vezérlőbe és párhuzamosítás
- [[concepts/esemalk/winforms-vezerlok-alapjai]] — `NumericUpDown`, `ListBox`, `MenuStrip` vezérlők
- [[subjects/esemalk]]
