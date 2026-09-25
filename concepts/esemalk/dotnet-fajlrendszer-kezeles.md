---
tags: [concept, esemalk/winforms-dinamikus-ui]
sources: [elte_eva_ea03_winforms_dynamic.pdf]
derivation: source
updated: 2026-09-13
---

# Fájlrendszer-kezelés a .NET-ben

A fájlokkal és a fájlrendszerrel kapcsolatos műveletek a `System.IO`
névtérben helyezkednek el.

## Tartalom

Fájlműveleteket a `File`, könyvtárműveleteket a `Directory` osztály statikus
műveleteivel hajthatunk végre, például:

```csharp
Directory.CreateDirectory(@"c:\Data");            // könyvtár létrehozása
String[] paths = Directory.GetFiles(@"c:\Data");  // könyvtár listázása
File.Copy(@"c:\data.txt", @"c:\Data\data.txt");   // fájl másolása
```

Az elérési útvonallal kapcsolatos műveletek (pl. szülő könyvtár lekérdezése)
a `Path` osztályban találhatóak:

```csharp
Path.GetParent(@"c:\Data"); // szülő lekérdezése
```

Egy kidolgozott példában (mozgókép-megjelenítő alkalmazás) a képek
megnyitásához könyvtárböngésző dialógust (`FolderBrowserDialog`) használunk,
amely a felhasználó által kiválasztott könyvtár elérési útját adja vissza; a
könyvtár tartalmának lekérdezéséhez a fenti `Directory`/`Path` műveletek
szolgálnak (lásd [[concepts/esemalk/winforms-kepek-megjelenitese]]).

## Kapocs

- [[concepts/esemalk/dotnet-eroforraskezeles]] — a projektbe beágyazott
  erőforrások kezelése, szemben a futásidőben elért fájlrendszeri
  fájlokkal
- [[concepts/esemalk/winforms-kepek-megjelenitese]] — a `FolderBrowserDialog`
  alkalmazási példája képek betöltésére
