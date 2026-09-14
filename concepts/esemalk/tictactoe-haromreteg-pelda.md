---
tags: [concept]
sources: [elte_eva_ea04_winforms_architecture_testing.pdf]
derivation: source
updated: 2026-09-13
---

# Tic-Tac-Toe példa háromrétegű architektúrában

Egy két játékos által játszható Tic-Tac-Toe program tankönyvi példa
arra, hogyan épül fel egy alkalmazás a
[[concepts/esemalk/haromreteg-architektura]] szerint, perzisztencia
réteggel és [[concepts/esemalk/fuggoseg-befecskendezes]]sel.

## Tartalom

### Feladat

- Két játékos ('X' és 'O') felváltva léphet; a felhasználó új játékot is
  kezdhet, illetve bármikor újrakezdhet (`Ctrl+N`).
- A program automatikusan jelez, ha vége a játéknak (előugró
  üzenetben), majd automatikusan új játékot kezd.
- Lehetőség van a játékállás elmentésére (`Ctrl+S`) és betöltésére
  (`Ctrl+L`), a fájlnevet a felhasználó adja meg.
- A programot háromrétegű architektúrában valósítjuk meg.

### Tervezés — használati esetek

A felhasználó a következő műveleteket végezheti: *új játék*, *lépés*
(az *új játékot* mindig *lépés* követi), *mentés*, *betöltés*,
*kilépés*.

### Tervezés — architektúra

- Létrehozunk egy adatelérési névteret (`Persistence`), ebben egy
  interfész (`IPersistence`) biztosítja a betöltés (`Load`) és mentés
  (`Save`) funkciókat.
- Az adatelérés egy tömböt (`Player[]`) használ a modellel történő
  kommunikációra, amely sorfolytonosan tartalmazza a tábla értékeit.
- Megvalósítjuk az interfészt szöveges fájl alapú adatkezelésre
  (`TextFilePersistence`).
- A nézet fecskendezi be a modellbe a fájl alapú adatkezelést, ami a
  betöltés (`LoadGame`) és mentés (`SaveGame`) műveleteivel bővül.

### Tervezés — szerkezet

- `View::TicTacToeForm` (`Form`) — a nézet; egy `Model::TicTacToeModel`
  példányt (`_model`) tart.
- `Model::TicTacToeModel` — a modell; mezői: `_currentPlayer` (`Player`),
  `_gameTable` (`Player[,]`), `_stepNumber` (`Int32`),
  `_persistence` (`IPersistence`, befecskendezve konstruktorban:
  `TicTacToeModel(IPersistence)`); metódusai: `NewGame()`,
  `NewGame(Player[])`, `StepGame(Int32, Int32)`, `LoadGame(String)`,
  `SaveGame(String)`, valamint belső `CheckGame()`, `OnGameWon()`,
  `OnGameOver()`, `OnFieldChanged(Int32, Int32, Player)`; tulajdonságok:
  `StepNumber`, `CurrentPlayer`; indexelő: `this[Int32, Int32]`;
  események: `GameWon` (`EventHandler<GameWonEventArgs>`), `GameOver`
  (`EventHandler`), `FieldChanged` (`EventHandler<FieldChangedEventArgs>`).
- `Persistence::Player` (`enumeration`) — `NoPlayer`, `PlayerX`,
  `PlayerO`.
- `Persistence::IPersistence` (`interface`) — `Load(String): Player[]`,
  `Save(String, Player[]): void`.
- `Persistence::TextFilePersistence` — az `IPersistence` megvalósítása;
  `Load(String): Player[]`, `Save(String, Player[]): void`.
- `Persistence::DataException` (`Exception`) — `DataException(String)`;
  a `TextFilePersistence` ezzel jelez adatolvasási hibát.

A modell a perzisztencia réteget csak az `IPersistence` felületén
keresztül ismeri — a konkrét `TextFilePersistence` megvalósítást a
nézet fecskendezi be a modell konstruktorába, a
[[concepts/esemalk/fuggoseg-befecskendezes]] lapon leírt technika
szerint.

### Megvalósítás — `TextFilePersistence.cs`

```csharp
public Player[] Load(String path) {
    if (path == null)
        throw new ArgumentNullException("path");

    try {
        using (StreamReader reader =
                new StreamReader(path))
                // fájl megnyitása olvasásra
        {
            String[] numbers =
                reader.ReadToEnd().Split();
                // fájl tartalmának feldarabolása a
                // whitespace karakterek mentén
            …
        }
    }
    …
}
```

A `StreamReader` felnyitása [[concepts/esemalk/idisposable-eroforras-felszabaditasa]]
szerinti `using`-gal történik, a fájlolvasás technikájáról lásd
[[concepts/esemalk/stream-alapu-fajlkezeles]].

## Kapocs

- [[concepts/esemalk/haromreteg-architektura]] — az architektúra, amelynek
  ez a konkrét alkalmazása
- [[concepts/esemalk/fuggoseg-befecskendezes]] — a `TextFilePersistence`
  befecskendezése a modellbe
- [[concepts/esemalk/stream-alapu-fajlkezeles]] — a `StreamReader`-alapú
  fájlolvasás, amelyet a `TextFilePersistence` használ
- [[concepts/esemalk/idisposable-eroforras-felszabaditasa]] — a `using`
  utasítás, amellyel a `StreamReader` erőforrásait felszabadítjuk
- [[concepts/esemalk/modell-nezet-architektura]] — a korábbi, kétrétegű
  felbontás (számológép-példa), amelyhez képest itt a perzisztencia is
  önálló réteg
- [[subjects/esemalk]]
