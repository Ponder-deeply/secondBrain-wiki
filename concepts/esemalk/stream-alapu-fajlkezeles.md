---
tags: [concept]
sources: [elte_eva_ea04_winforms_architecture_testing.pdf, elte_eva_ea03_winforms_dynamic.pdf]
derivation: source
kind: procedure
element: earth
updated: 2026-09-25
---

# Fájlkezelés .NET-ben: fájlrendszer és adatfolyamok (Stream)

A .NET-ben az adatfolyamok (*stream*) kezelése egységes formátumban adott,
így azonos módon kezelhetők fájlok, hálózati adatforrások, memória stb.;
ez a réteg a fájlok *tartalmának* olvasására/írására szolgál, szemben a
`File`/`Directory`/`Path` osztályok által kezelt fájlrendszer-műveletekkel
(másolás, listázás, könyvtárkezelés), amelyeket az első szakasz tárgyal.

## Tartalom

### Fájlrendszer-műveletek (`File`, `Directory`, `Path`)

A fájlokkal és a fájlrendszerrel kapcsolatos műveletek a `System.IO`
névtérben helyezkednek el.

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

### Adatfolyamok (`Stream`, `StreamReader`, `StreamWriter`)

Az adatfolyamok ősosztálya a `Stream`, amely binárisan írható/olvasható.
Szöveges adatfolyamok írását, olvasását a `StreamReader` és
`StreamWriter` típusok biztosítják:

- létrehozáskor megadható az adatfolyam, vagy közvetlenül a fájlnév,
- csak karakterenként (`Read`), vagy soronként (`ReadLine`) tudunk
  olvasni, így a beolvasott adatot konvertálnunk kell a kívánt típusra,
- amennyiben a műveletek során hiba keletkezik, `IOException`-t kapunk.

```csharp
try
{
    StreamReader reader =
        new StreamReader("in.txt"); // megnyitás
    while (!reader.EndOfStream) // amíg nincs vége
    {
        Int32 val = Int32.Parse(reader.ReadLine());
        // sorok olvasása, majd konvertálás
        …
    }
    reader.Close(); // bezárás
}
catch (IOException) { … }
```

A `StreamReader` (és általában a `Stream`-ek) `IDisposable`-t
valósítanak meg, ezért lezárásukat, erőforrásaik felszabadítását
célszerű a [[concepts/esemalk/idisposable-eroforras-felszabaditasa]]
lapon leírt `using`-gal biztosítani, nem kézi `Close()`-zal.

### Teljes fájltartalom egy lépésben

Amennyiben egy fájl teljes tartalmát be szeretnénk tölteni, ezt
megtehetjük a `File` statikus osztály eljárásaival is, egyetlen
lépésben:

- a `ReadAllLines`, `ReadAllText` és `ReadAllBytes` metódusokkal olvasni
  tudjuk a fájlt,
- a `WriteAllLines`, `WriteAllText`, `WriteAllBytes` metódusokkal írni
  tudjuk a fájlt; a meglévő tartalomhoz az `AppendAll*` eljárásokkal is
  hozzáfűzhetünk.

Ilyen módon nem kell foglalkozni a fájlok megnyitásával és bezárásával,
viszont a fájlok szekvenciális feldolgozására nem alkalmas (pl. ha a
teljes állomány nem férne el a memóriában).

## Kapocs

- [[concepts/esemalk/idisposable-eroforras-felszabaditasa]] — a
  `StreamReader`/`StreamWriter` erőforrásainak biztonságos
  felszabadítása
- [[concepts/esemalk/tictactoe-haromreteg-pelda]] — a `TextFilePersistence`
  megvalósítása `StreamReader`-rel
- [[subjects/esemalk]]
- [[concepts/esemalk/winforms-kepek-megjelenitese]] — a projektbe beágyazott
  erőforrások kezelése, szemben a futásidőben elért fájlrendszeri
  fájlokkal
