---
tags: [concept]
sources: [Java-Language-Specification-SE-21.pdf, konkprog-canvas-feladat-1-elso-szalak.md, konkprog-canvas-feladat-1-a-runnable-interfesz.md, konkprog-canvas-feladat-2-harom-szal.md, konkprog-canvas-feladat-3-szovegiro-szalak.md, konkprog-canvas-feladat-pelda-alternativ-modszer-szalak-letrehozasara-szalak-bevaras.md]
derivation: source
kind: procedure
element: earth
updated: 2026-10-23
---

# Szálak létrehozása és indítása (Thread, Runnable)

Java-ban szál a `Thread` osztály példánya; két szokásos létrehozási mód van: a `Thread` kiterjesztése, vagy a `Runnable` interfész megvalósítása. A szál a `start()` hívással indul.

## Tartalom

### A szál a nyelvben

A JLS szerint a szálakat a `Thread` osztály reprezentálja, és a felhasználó **kizárólag** `Thread`-objektum létrehozásával tud szálat létrehozni; a szál a megfelelő objektum `start()` metódusának hívásakor indul el. A szálak egymástól függetlenül hajtanak végre kódot, a közös (heap) memórián osztoznak. A JLS nem írja elő, *hogyan* kell a programot végrehajtani: csak a megengedett viselkedéseket írja le (lásd [[concepts/konkprog/java-memoriamodell]]).

### Két létrehozási mód

1. **Öröklés:** az osztály kiterjeszti a `Thread`-et és felülírja a `run()` metódust.
2. **Interfész:** az osztály megvalósítja a `Runnable` interfészt (`run()`), a példányt pedig a `Thread` konstruktorának adjuk át. Ez a feladatsor szerint az „alternatív módszer”; az öröklődést nem foglalja le, ezért általában ezt részesítjük előnyben.

A `run()` közvetlen hívása nem indít új szálat; a párhuzamos végrehajtást a `start()` indítja.

### Feladatok (Canvas)

- **Első szálak:** két szál, az egyik 1, 2, 3, … a másik 1, −1, 2, −2, … sorozatot ír ki, mindkettő 100000 lépést tesz; megfigyelendő, hogy a két kimenet összekeveredik.
- **A Runnable interfész:** az előző feladat átírása `Thread`-kiterjesztésről `Runnable`-re.
- **Három szál:** `szia n`, `világ n`, `másik n` szövegeket író három szál.
- **Szövegíró szálak:** egy sztringtömb minden eleméhez egy szál, amely `<szöveg> 1`, `<szöveg> 2`, … kiírást végez.
- A „példa” oldal öt segédprogramot sorol fel: létrehozás örökléssel, létrehozás interfésszel, szál indítása, bevárás/altatás/szinkronizált metódusok, szál megszakítása.

A kimenet keveredése az ütemezés nemdeterminisztikus voltából következik; ennek következményei: [[concepts/konkprog/verseny-helyzet-es-adatverseny]].

## Kapocs

- [[concepts/konkprog/szal-varakozas-es-megszakitas]] — join, sleep, interrupt
- [[concepts/konkprog/verseny-helyzet-es-adatverseny]] — miért keveredik a kimenet
- [[concepts/konkprog/executor-es-thread-pool]] — szálak helyett feladatok beküldése
