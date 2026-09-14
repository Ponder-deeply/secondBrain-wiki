---
tags: [concept]
sources: [elte_eva_ea10_avaloniaui_complex.pdf]
derivation: source
updated: 2026-09-13
---

# Avalonia UI — platformfüggetlen perzisztencia

Az Avalonia UI-ban a fájlrendszer-alapú adatmegőrzés a jól ismert
`System.IO` osztályokra épül, kiegészítve a platformfüggő speciális
mappák (`Environment.SpecialFolder`) egységes lekérdezésével.

## Tartalom

A `System.IO` névtér korábban (WinForms/WPF kontextusban) megismert osztályai
és eljárásai adják a fájlkezelés eszköztárát Avalonia UI alatt is:

- könyvtárak (`Directory`) elérése, listázása (`GetFiles`,
  `GetDirectories`), létrehozása (`CreateDirectory`), fájlok/könyvtárak
  törlése (`Delete`)
- fájlok (`File`) létrehozása, megnyitása (`Open`), olvasása
  (`ReadAllBytes`, `ReadAllLines`, `ReadAllText`), írása (`WriteAllBytes`,
  …), másolása (`Copy`)
- adatfolyam-alapú írás/olvasás a megszokott módon (`StreamReader`,
  `StreamWriter`)

Speciális, jól ismert útvonalakat az `Environment.SpecialFolder` `enum`
segítségével kérhetünk le — ügyelve arra, hogy az egyes útvonalak
platformfüggően mást jelenthetnek:

- Dokumentumok könyvtár asztali operációs rendszereken:
  `Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments)`
- alkalmazás saját adatkönyvtára mobil platformokon:
  `Environment.GetFolderPath(Environment.SpecialFolder.LocalApplicationData)`
  — ez az útvonal asztali operációs rendszeren azonban nem alkalmazás
  specifikus

**Példa — vizsgatétel generáló alkalmazás:** az alkalmazást életciklus-
kezeléssel egészítjük ki ([[concepts/esemalk/avalonia-eletciklus-kezeles]]):
a modell állapotát és a generálás állapotát az alkalmazás lokális
könyvtárába JSON formátumban szerializálva tároljuk el. Mivel nincs külön
perzisztencia réteg, közvetlenül a modelltől kérjük el az információkat, és
tároljuk el egyenként. Az alkalmazás életciklusát az `Application` vezérli,
ezért itt egy `SaveState` és egy `LoadState` eljárást definiálunk: indításkor,
illetve folytatáskor a korábbi állapotot betöltjük, és ennek megfelelően
inicializáljuk a modellt.

Egy másik példában (Tic-Tac-Toe) a mentéshez az útvonalat a felhasználó
választhatja meg — ekkor csak egy adott kiterjesztésű (pl. `.data`) fájlok
mentését és betöltését kínáljuk fel, lásd
[[concepts/esemalk/avalonia-dialogusablakok]]. Android támogatásához az
`AndroidManifest.xml` állományban a szükséges `READ_EXTERNAL_STORAGE` és
`WRITE_EXTERNAL_STORAGE` jogosultságokat kell megkérni. Mindkét példában az
alkalmazás leállításakor / háttérbe kerülésekor automatikusan is történik
mentés.

## Kapocs

- [[concepts/esemalk/avalonia-eletciklus-kezeles]] — az életciklus-
  eseményekhez (indítás/leállítás) kötött állapotmentés és -betöltés
- [[concepts/esemalk/avalonia-dialogusablakok]] — felhasználó által
  választott útvonalra történő mentés/betöltés fájlválasztó dialógussal
- [[concepts/esemalk/dotnet-fajlrendszer-kezeles]] — a `System.IO` alapú
  fájlrendszer-kezelés WinForms kontextusban
- [[concepts/esemalk/avalonia-alkalmazas-tulajdonsagok-kihelyezes]] — az
  `AndroidManifest.xml` és más platformspecifikus leírók szerepe a
  kihelyezésben
