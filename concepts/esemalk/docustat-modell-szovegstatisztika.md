---
tags: [concept]
sources: [elte_eva_gy01_munkafuzet.pdf]
derivation: source
kind: procedure
element: earth
updated: 2026-10-21
---

# DocuStat: dokumentumstatisztika modell (konzolos alkalmazás)

Az 1. gyakorlat egy konzolos alkalmazást épít: beolvas egy szöveges fájlt, és szóstatisztikát, valamint metrikákat számol belőle — a `DocumentStatistics` osztály a konzolt nem kezeli, így később változtatás nélkül szolgálja ki a grafikus felületet (ez a *modell*).

## Tartalom

### Projekt és fájlbeolvasás

- Projektsablon: *Console App* (nem a *.NET Framework* változat), cél: .NET 10 (LTS), *Do not use top-level statements* bejelölve, hogy a `Main` és osztálya legenerálódjon.
- A `DocumentStatistics` privát `_filePath` mezőt és `FileContent` tulajdonságot kap (publikus `get`, privát `set`); az elérési utat a konstruktor veszi át. Lásd [[concepts/esemalk/csharp-tulajdonsagok]].
- A `Main` addig olvas a `Console.ReadLine()`-nal, amíg létező `.txt` fájlt kap (`Path.GetExtension`, `File.Exists`).
- `Load()`: `File.ReadAllText(_filePath)`; az `IOException`-t a hívó (`Main`) kapja el `try-catch`-csel, kiírja az üzenetet, és nem nulla értékkel lép ki (`int Main`, `return -1`).

### Szavak előfordulása

- `ComputeDistinctWords`: a szöveget `Split()`-tel (paraméter nélkül a whitespace-eknél) szavakra bontja, az üres elemeket LINQ-val szűri (`words.Where(s => s.Length > 0).ToArray()`).
- A szavak elejéről és végéről a nem betű karaktereket le kell vágni (`Char.IsLetter`, `Remove`, ill. a `^1` indexszel a végéről; LINQ-alternatíva: `SkipWhile` + `Reverse` + `SkipWhile` + `Reverse`, majd `String.Concat`). Ha üres szó maradt (pl. évszám), kihagyjuk; a szót `ToLower()`-rel normalizáljuk, majd `ContainsKey`/`Add`/index operátorral számoljuk a `Dictionary<string, int>`-ben.
- **Szűk felület elve**: a szótárat nem tesszük ki írhatóan; privát `_distinctWordCount` (`Dictionary`) mögé `IReadOnlyDictionary<string, int> DistinctWordCount => _distinctWordCount` tulajdonság kerül (`Clear`, `Add` kifelé nem elérhető). A modell a lehető legszűkebb, épp elegendő felületet adja ki, az interfészbe (`IDocumentStatistics`) is ez a típus kerül.
- `FilteredWordCount` (csak olvasható tulajdonság): `OrderByDescending(p => p.Value)` az előfordulások szerint csökkenő sorrendben — *method syntax* vagy *query syntax* (`from ... orderby ... descending select`) is használható. A rendezést a modellben végezzük, nem a `Main`-ben. Lásd [[concepts/esemalk/csharp-linq]].

### Szűrés

- `MinWordLength`, `MinWordOccurrence` (írható tulajdonságok, kezdőérték 1) és `IgnoredWords`: a `FilteredWordCount` `Where` feltételei (`p.Value >= MinWordOccurrence`, `p.Key.Length >= MinWordLength`, `!IgnoredWords.Contains(p.Key)`).
- A beolvasáshoz `static int ReadPositive(string message)` segédeljárás (`int.TryParse`, újrapróbálkozás hibás bemenetnél).
- Az `IgnoredWords` setter maga normalizál (`Trim().ToLower()`, üres szavak eldobása), így a hívó oldalon elég `line.Split(',').ToList()` — a modell hívási módja egységes, bárhonnan jönnek a szavak.
- A `DistinctWordCount` a teljes szóstatisztika, a `FilteredWordCount` ennek szűrt nézete; a metrikák mindig a szűretlen statisztikára épülnek.

### További metrikák

Mind csak olvasható tulajdonság, a `Load`-ban számítva:

| Metrika | Számítás |
|---|---|
| `CharacterCount`, `NonWhiteSpaceCharacterCount` | karakterek száma szóközökkel és anélkül |
| `SentenceCount` | mondatvégi írásjelek (`.`, `?`, `!`) száma; egymást követők egy mondatnak számítanak (közelítés) |
| `ProperNounCount` | nagybetűvel kezdődő szavak, ha az előző karakter nem mondatvégi írásjel |
| `ColemanLiauIndex` | $0{,}0588\cdot L - 0{,}296\cdot S - 15{,}8$, ahol $L$ a 100 szóra jutó átlagos karakterhossz, $S$ a 100 szóra jutó mondatszám; az amerikai osztályszintet közelíti |
| `FleschReadingEase` | $206{,}835 - 1{,}015\cdot\frac{\text{szószám}}{\text{mondatszám}} - 84{,}6\cdot\frac{\text{szótagszám}}{\text{szószám}}$; 0–100, magasabb = könnyebben olvasható (60–70: 7–8. osztály; 30 alatt: felsőoktatás) |

- Szószám: `DistinctWordCount.Sum(w => w.Value)`.
- `CountSyllables`: minden magánhangzó (a `y` is) egy szótag, kivéve a dupla magánhangzókat; a szó végi `es`, `ed`, `le` általában nem új szótag, a szó végi `e` csak akkor, ha az egyetlen magánhangzó.

## Kapocs

- [[concepts/esemalk/docustat-winforms-nezet-esemenyek]] — a modell grafikus felülete és eseményei (3. gyakorlat)
- [[concepts/esemalk/docustat-perzisztencia-filemanager]] — a fájlkezelés leválasztása (4. gyakorlat)
- [[concepts/esemalk/docustat-egysegtesztek]] — a modell egységtesztjei (5. gyakorlat)
- [[concepts/esemalk/stream-alapu-fajlkezeles]] — fájlkezelés `File`/`Path` osztályokkal
- [[concepts/esemalk/csharp-kivetelkezeles]] — `try-catch`, `IOException`
- [[concepts/esemalk/gyakorlati-munkafuzetek-attekintes]] — a gyakorlatok áttekintése
- [[subjects/esemalk]]
