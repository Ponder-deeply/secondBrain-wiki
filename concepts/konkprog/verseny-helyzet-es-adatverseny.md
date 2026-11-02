---
tags: [concept]
sources: [Java-Language-Specification-SE-21.pdf, konkprog-canvas-feladat-4-lassu-szovegiras.md, konkprog-canvas-feladat-3-gyujtemenyek-eleresenek-szinkronizacioja.md, konkprog-canvas-feladat-1-gyakorlo-feladat-termelo-es-fogyaszto.md]
derivation: source
kind: pitfall
element: water
updated: 2026-10-23
---

# Versenyhelyzet és adatverseny

Szinkronizálatlan közös adat elérése nemdeterminisztikus, gyakran hibás eredményhez vezet. A JLS pontos fogalma az adatverseny: két ütköző hozzáférés, amelyet nem rendez happens-before reláció.

## Tartalom

### Adatverseny (JLS §17.4.1, §17.4.5)

Két hozzáférés ugyanahhoz a változóhoz *ütköző*, ha legalább az egyik írás. Ha két ütköző hozzáférést nem rendez happens-before reláció, a program **adatversenyt** tartalmaz; ilyenkor a nem várt eredmények gyakoriak. Helyesen szinkronizált a program, ha minden szekvenciálisan konzisztens végrehajtása adatversenymentes; ekkor minden végrehajtása szekvenciálisan konzisztensnek látszik (lásd [[concepts/konkprog/java-memoriamodell]]). A JLS megjegyzése: a szekvenciális konzisztencia még nem ment meg az olyan hibáktól, ahol *műveletcsoportok* atomicitása kellene.

### A Canvas-feladatok megfigyelései

- **Lassú szövegírás:** a `slowPrint` karakterenként ír ki, ezért a szálak kimenete karakter szintjén összekeveredik (a soronkénti `println` ritkábban törik meg). Javítás: a kiíró metódus `synchronized` ([[concepts/konkprog/synchronized-monitor]]).
- **Közös lista (CommonList):** két szál (páros és páratlan számok) egy szinkronizálatlan listába ír; a várt eredmény az összes szám volna, helyette hibás/hiányos tartalom vagy kivétel adódhat. Javítási módok: szinkronizált blokk vagy `Collections.synchronizedList` ([[concepts/konkprog/szinkronizalt-gyujtemenyek]]).
- **Termelő–fogyasztó:** a közös sor elérése versenyhelyzetes, a képernyőre írás sem konzisztens ([[concepts/konkprog/termelo-fogyaszto]]).

### Miért reordering is baj

A JLS 17.4 példái: a fordító vagy a processzor átrendezheti a független utasításokat, így `r2 == 2` és `r1 == 1` is előfordulhat a `r2 = A; B = 1;` / `r1 = B; A = 2;` programban, mert a kód nincs szinkronizálva.

## Kapocs

- [[concepts/konkprog/synchronized-monitor]] — kölcsönös kizárás
- [[concepts/konkprog/volatile-mezo]] — láthatóság zár nélkül
- [[concepts/konkprog/atomic-tipusok]] — atomi műveletek
