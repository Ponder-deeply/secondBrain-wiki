---
tags: [concept]
sources: [elte_eva_gy04_munkafuzet.pdf]
derivation: source
kind: procedure
element: earth
updated: 2026-10-21
---

# DocuStat perzisztencia: `IFileManager`, gyártófüggvény, függőség-befecskendezés

A 4. gyakorlat háromrétegűvé teszi a DocuStat alkalmazást: a fájlkezelést `Persistence` könyvtárba választja le interfész mögé, a modellbe függőség-befecskendezéssel kerül, a megvalósítást a fájl kiterjesztése alapján gyártófüggvény választja.

## Tartalom

### Az interfész és megvalósításai

- `IFileManager`: `string Load()`. A `TextFileManager` konstruktorban kapja az elérési utat, és `File.ReadAllText`-tel olvas; a hibákat saját `FileManagerException` (az `IOException` leszármazottja) jelzi: `catch (Exception ex) { throw new FileManagerException(ex.Message, ex); }`.
- A `DocumentStatistics` konstruktora az elérési út helyett `IFileManager`-t vár — a modell nem függ a perzisztencia konkrét megvalósításától, csak az interfésztől. A hívási helyeken a konstruktorhívásokat és a `FileManagerException` kezelését módosítani kell. Lásd [[concepts/esemalk/fuggoseg-befecskendezes]].
- `PdfFileManager`: az *iText* NuGet-csomaggal (*Project → Manage NuGet Packages*). `PdfReader(path)` és `PdfDocument(reader)` (`using` — mindkettő `IDisposable`), oldalankénti feldolgozás (`GetNumberOfPages()`, `GetPage(i)` — az indexelés **egytől** kezdődik), `PdfTextExtractor.GetTextFromPage(page)`; az oldalak szövegét `StringBuilder.Append` gyűjti, végül `ToString()`.
- A `StringBuilder` indoka: a `string` módosíthatatlan, minden módosítás új példányt hoz létre; a `StringBuilder` módosítható pufferben tárol, szükség esetén nagyobbra cseréli. Lásd [[concepts/esemalk/idisposable-eroforras-felszabaditasa]].

### Gyártófüggvény (`FileManagerFactory`)

Statikus osztály egyetlen metódussal: `public static IFileManager? CreateForPath(string path)`. A `Path.GetExtension` alapján példányosítja a megfelelő megvalósítást (`.txt` → `TextFileManager`, `.pdf` → `PdfFileManager`); nem támogatott kiterjesztésnél `null`. A kiterjesztés vizsgálata külön osztályban van a kódismétlés elkerülésére.

- Konzolon: `do { ... fileManager = FileManagerFactory.CreateForPath(path); } while (fileManager == null);` — a program nem ismeri a támogatott formátumokat, a `null` jelzi a nem támogatottat.
- Grafikus felületen: az `OpenDialog`-ban `null` esetén `MessageBox` („Unsupported file format”); a dialógus szűrője: `"Text files (*.txt)|*.txt|PDF files (*.pdf)|*.pdf"`.

### IoC tároló kitekintés

Összetett, sok függőségű alkalmazásnál a példányosítást a keretrendszer végezheti: [[concepts/esemalk/ioc-tarolo-servicecollection]].

## Kapocs

- [[concepts/esemalk/docustat-winforms-nezet-esemenyek]] — az előző gyakorlat nézete, amely az új fájlkezelőt használja
- [[concepts/esemalk/docustat-egysegtesztek]] — az `IFileManager` mockolása a tesztekben
- [[concepts/esemalk/haromreteg-architektura]] — a háromrétegű architektúra
- [[concepts/esemalk/retegek-szerelvenyekre-bontasa]] — a perzisztencia interfész mögött
- [[concepts/esemalk/stream-alapu-fajlkezeles]] — a `File.ReadAllText` és társai
- [[subjects/esemalk]]
