---
tags: [concept]
sources: [elte_eva_gy06_munkafuzet.pdf]
derivation: source
kind: pitfall
element: water
updated: 2026-10-21
---

# Fájlváltozás figyelése (`FileSystemWatcher`) és buktatói

Az eddigi modell-események a felhasználó műveleteiből fakadtak; a fájlváltozás figyelésénél a változás az alkalmazáson kívülről érkezik — a nézet ezt lekérdezéssel nem pótolhatná, hiszen nem tudja, mikor kellene kérdeznie.

## Tartalom

### Vázlat

1. A perzisztencia rétegben az `IFileManager` kap egy `event EventHandler? ContentChanged` eseményt; a megvalósítások a `System.IO.FileSystemWatcher`-rel figyelik a fájlt. A figyelő erőforrást tart életben, ezért az interfésznek `IDisposable`-nek is kell lennie.
2. A modell a konstruktorában feliratkozik, a kezelőben újra hívja a `LoadAsync()`-et. A nézet változtatás nélkül frissül, mert a `LoadAsync` a megszokott eseményeket váltja ki — ezért érdemes az eseményeket a hatásukról elnevezni (a nézetet nem érdekli, hogy a lista szűrés vagy fájlváltozás miatt módosult).

### Buktatók

- A `FileSystemWatcher` **háttérszálról** jelez, ezért az így indított újratöltés egésze háttérszálon fut — az `InvokeRequired` szerinti szinkronizációt a többi eseménykezelőre is ki kell terjeszteni.
- A szerkesztők több lépésben írnak (ideiglenes fájl + átnevezés), egy mentés értesítések sorozatát váltja ki; kezeletlenül minden mentés több teljes újratöltést és újraelemzést indítana. Megoldás: **debounce** — minden értesítés újraindít egy időzítőt, és csak az értesítések elállta után jelzünk.
- A késleltetés lejártakor is lehet, hogy az író még zárolja a fájlt (`IOException`): a debounce csak valószínűtlenné teszi; kivételkezelés mellett néhányszor, rövid szünetekkel újra kell próbálni.
- Az eseménykezelő `async void`, ezért kötelező a kivételkezelés: az `async void`-ból kiszabaduló kivétel nem kapható el, az egész alkalmazás terminál.
- A zárolást nem kerüli meg a `FileShare.ReadWrite`: a megosztási mód egyeztetés kérdése (ha az író kizárólagosan nyitott, a kérés elbukik; ahol sikerül, félig kiírt fájlt olvashatunk — csendben hibás statisztika kezelt hiba helyett).

### Tesztelés

Valódi fájl nélkül ellenőrizhető: a Moq `Raise` metódusa kiváltja a mockolt interfész eseményét: `_mock.Raise(fileManager => fileManager.ContentChanged += null, EventArgs.Empty);`.

## Kapocs

- [[concepts/esemalk/docustat-tobbfajlos-aszinkron-betoltes]] — az aszinkron betöltés és UI-szinkronizáció, amelyre az újratöltés épül
- [[concepts/esemalk/docustat-egysegtesztek]] — a Moq-os tesztelés
- [[concepts/esemalk/idisposable-eroforras-felszabaditasa]] — az erőforrást tartó figyelő felszabadítása
- [[concepts/esemalk/winforms-vezerlo-invoke-begininvoke]] — háttérszálról érkező esemény kezelése
- [[subjects/esemalk]]
