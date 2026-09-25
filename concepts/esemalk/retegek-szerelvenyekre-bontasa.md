---
tags: [concept, esemalk/winforms-architektura-es-teszteles]
sources: [elte_eva_ea04_winforms_architecture_testing.pdf]
derivation: source
updated: 2026-09-13
---

# Rétegek szerelvényekre bontása — perzisztencia interfész minta

A [[concepts/esemalk/modell-nezet-architektura]] rétegei külön
[[concepts/esemalk/szerelvenyek-osztalykonyvtarak|szerelvényekbe]] (projektekbe)
szervezhetők; az adatelérést pedig interfész mögé rejtve az adatkezelés
konkrét megvalósítása (szöveges fájl, bináris fájl, ...) szabadon cserélhető
anélkül, hogy a modellt vagy a nézetet módosítani kellene.

## Tartalom

### A minta

Az adatelérés befecskendezése a modellbe a következő szerelvényfelosztást
eredményezi:

- **View** — a nézet, maga a futtatható alkalmazás,
- **Model** — a modell, amely az alkalmazáslogikát tartalmazza,
- **Persistence (interface)** — az adatkezelés felülete (egy interfész),
  amelytől a modell függ,
- **Persistence (implementation)** — az adatkezelés konkrét, cserélhető
  megvalósítása, amely a Persistence interfészt implementálja.

A View a Modellre, a Modell a Persistence interfészre mutat; a Persistence
implementáció a Persistence interfészt valósítja meg, a View pedig
közvetlenül példányosítja és átadja a modellnek. Ezáltal a Modell és a View
csak az interfészt ismeri, a konkrét adatkezelési módot nem — ez a
[[concepts/esemalk/mock-objektumok|mock objektumokkal]] való teszteléshez is
szükséges leválasztás.

A nézet és a perzisztencia külön osztálykönyvtárként (nem futtatható
szerelvényként) szerepel, csak a View a futtatható alkalmazás.

### Példa: Tic-Tac-Toe

Egy két játékos által játszható Tic-Tac-Toe program négy projektre
(szerelvényre) épül:

- nézet: `TicTacToeGame.View.Drawing`,
- modell: `TicTacToeGame.Model`,
- adatkezelés felülete: `TicTacToeGame.Persistence` (`IPersistence`
  interfész, `Load(String):Player[]` és `Save(String, Player[]):void`
  műveletekkel),
- adatkezelés szöveges fájl alapú megvalósítása:
  `TicTacToeGame.Persistence.TextFile`.

A nézet a modellt, a modell a perzisztencia interfészt használja; a
szöveges fájl alapú megvalósítás (`TextFilePersistence.cs`) a fájl
tartalmát számmá, majd `Player`-ré konvertálja
(`numbers.Select(number => (Player)Int32.Parse(number)).ToArray()`), és
hiba esetén saját kivételt (`TicTacToeDataException`) dob.

A mintát tovább lehet bővíteni:

- egy **másik nézet** felcsatolásával, amely a korábbi, vezérlő alapú
  grafikus felületet helyezi vissza egy új alkalmazás-projektbe
  (`TicTacToeGame.View.Controls`), a modellt változatlanul hagyva,
- egy **másik perzisztencia-implementációval**, amely bináris fájlból
  olvas és ír (`TicTacToeGame.Persistence.BinaryFile`): a `File`
  osztály `ReadAllBytes`/`WriteAllBytes` műveleteivel bájtonként kezeli az
  adatokat (`fileData.Select(fileByte => (Player)fileByte).ToArray()`).

Az eredmény egy hatprojektes megoldás, amelyben a nézet és a perzisztencia
két-két, egymással felcserélhető változatban létezik, a modell pedig
mindkét kombinációban változatlan marad — ez szemlélteti a
szerelvényekre bontás fő hasznát: a komponensek függetlenül
cserélhetők és újrahasznosíthatók.

A szerkezeti (osztály-) diagram szerint a nézet (`View::TicTacToeForm`, egy
`Form`) tartja a modellt (`_model`) és a perzisztenciát (`_persistence`)
mezőként; a `Persistence::IPersistence` interfészt a
`Persistence::BinaryFilePersistence` (vagy a szöveges fájl változat)
valósítja meg.

## Kapocs

- [[concepts/esemalk/modell-nezet-architektura]] — az alap modell/nézet
  felosztás, amelyre ez a minta épül
- [[concepts/esemalk/szerelvenyek-osztalykonyvtarak]] — a szerelvény és
  osztálykönyvtár fogalma, amelyre a felbontás támaszkodik
- [[concepts/esemalk/mock-objektumok]] — az interfész mögé rejtett
  perzisztencia tesztelhetőségének alapja
- [[concepts/esemalk/dotnet-fajlrendszer-kezeles]] — a `File` osztály
  `ReadAllBytes`/`WriteAllBytes` műveletei a bináris perzisztenciában
- [[subjects/esemalk]]
