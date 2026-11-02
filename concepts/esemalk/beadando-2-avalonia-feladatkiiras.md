---
tags: [concept]
sources: [elte_eva_feladatok_2.pdf]
derivation: source
kind: overview
element: earth
updated: 2026-10-21
---

# 2. beadandó: Avalonia többplatformos alkalmazás — követelmények és feladatok

A 2026/27 őszi félév 2. beadandója egy Avalonia UI alapú játék, amelyet asztali platformra (Windows, Linux, macOS) és legalább egy mobil célplatformra (Android vagy iOS) kell elkészíteni MVVM architektúrában; a feladatot a hallgató a tíz közül kapja.

## Tartalom

### Közös követelmények

- A beadandó dokumentációból és programból áll; csak a megfelelő dokumentáció bemutatásával értékelhető. Csak funkcionálisan teljes, önállóan megvalósított, személyesen bemutatott program fogadható el.
- Felhasználóbarát, könnyen kezelhető megvalósítás, különös tekintettel a mobil eszköz sajátosságaira (pl. fizikai billentyűzet nem érhető el); az objektumorientált szemlélet megtartása.
- Platformkülönbségek kezelése, különösen a mobil platformok eltérő életciklusáé: háttérbe kerüléskor a játék automatikusan szünetel. Lásd [[concepts/esemalk/avalonia-mobil-alkalmazaskornyezet-eletciklus]].
- **MVVM architektúra**: a megjelenítés rétege elkülönül a nézetmodelltől, a modelltől és az adatkezeléstől. A modell és az adatkezelés nem tartalmazhat hivatkozást grafikus felületi osztályra, csak eseményeket küldhet a nézetmodellnek; a nézetmodell nem tartalmazhat játékbeli adatot, a nézet pedig háttérkódot. Lásd [[concepts/esemalk/wpf-mvvm-alapok]].
- **Eseményvezérelt paradigma**: a rétegben bekövetkező változásokról a nézetmodellt a modell eseményei értesítik. Ha időzítés kell, az időzítő helye a modell, amennyiben az idő múlásának pontos ismerete a játéklogika szempontjából lényeges. Lásd [[concepts/esemalk/avalonia-idozites]].
- **Egységtesztek** a modellre: a lényeges funkciók és hatásaik (játékos lépései, nyerési kondíciók, modell eseményeinek kiváltása); a betöltés/mentés teszteléséhez a perzisztencia működését szimulálni kell. Lásd [[concepts/esemalk/mock-objektumok]].
- **Dokumentáció**: fejlesztői adatok, feladatleírás, elemzés, használati esetek (diagram), a program szerkezete (UML osztálydiagram), tesztek leírása; kódrészlet és képernyőkép nélkül, megfelelő szerkesztőeszközzel készített diagramokkal, PDF formátumban. Mintája: [[concepts/esemalk/beadando-dokumentacio-sudoku-minta]].

### A feladatválaszték (n × n pályás játékok)

Minden feladatban közös: új játék pályaválasztással (legalább 3 különböző méretű pálya, fájlban tárolva, vagy méretmegadás), szüneteltetés (ilyenkor nem telik az idő), a játék végének felismerése és kijelzése, folyamatos kijelzés a játékidőről és a feladatra jellemző számlálóról.

| # | Feladat | Lényeg |
|---|---|---|
| 1 | Pac-Man | labirintus, pontok, erőpirulák; üldöző és kóborló szellemek; 3 élet; erőpirula után a szellemek megijednek |
| 2 | Raktáros (Sokoban) | ládák célmezőre tolása; elakadt láda felismerése (sarok, $2\times 2$-es blokk); megoldható kezdőállás generálása visszafelé játszással; mentés a kezdőállással |
| 3 | Gyémántbánya (Boulder Dash) | gravitáció: szikla és gyémánt leesik/legörül; ellenfelek a bal kéz szabállyal; gyémánt gyűjtése, kijárat; időkorlát |
| 4 | Billenő labirintus | golyók gurulása falnak ütközésig; azonos színű lyukba kell juttatni; visszavonás is lépés; legjobb eredmény (legkevesebb billentés) tartós tárolása |
| 5 | Festőgolyó (Roller Splat) | a golyó falig gurul és kifesti az érintett mezőket; kapcsolók és kapuk; legjobb eredmény pályánként |
| 6 | Képrejtvény (nonogram) | számsorok alapján a fekete mezők megtalálása; kitöltés/kizárás üzemmód; 3 élet; mentés/betöltés |
| 7 | Baktériumtenyészet (Ataxx) | két játékos felváltva; osztódás vagy ugrás; szomszédos ellenséges baktériumok átszíneződése; gondolkodási idők mentése |
| 8 | Pentago | $n\times n$ tábla négy $(n/2)\times(n/2)$-es negyeddel; korong lehelyezése, majd egy negyed 90°-os forgatása; győzelem adott hosszú vonallal |
| 9 | Torpedó | két tábla, hajók elhelyezése (kézi vagy véletlen); szonár; játékosváltáskor a nézet elrejtése és megerősítése |
| 10 | Ökoszisztéma (Wa-Tor) | fű, nyulak, rókák; energia és szaporodás; populációs grafikon; lépésenkénti léptetés szüneteltetve |

A mintaadatok: Pac-Man 3 pályaméret; Raktáros $8\times 8$/3 láda, $10\times 10$/4, $12\times 12$/5; Képrejtvény $5\times 5$, $10\times 10$, $15\times 15$; Baktériumtenyészet $5\times 5$, $7\times 7$, $9\times 9$; Pentago $6\times 6$/5 korong, $8\times 8$/6, $10\times 10$/7; Torpedó $8\times 8$, $10\times 10$, $12\times 12$; Ökoszisztéma $10\times 10$, $20\times 20$, $30\times 30$. Több feladatban mentés és betöltés is kötelező (Raktáros, Képrejtvény, Baktériumtenyészet, Pentago, Torpedó, Ökoszisztéma).

## Kapocs

- [[concepts/esemalk/beadando-dokumentacio-sudoku-minta]] — a Sudoku mintafeladat Avalonia-s dokumentációja
- [[concepts/esemalk/beadando-statikus-analizis]] — a feltöltött megoldás automatikus ellenőrzése
- [[concepts/esemalk/avalonia-projekt-felepites]] — a többprojektes Avalonia megoldás szerkezete
- [[concepts/esemalk/avalonia-platformfuggetlen-perzisztencia]] — mentés/betöltés platformfüggetlenül
- [[subjects/esemalk]]
