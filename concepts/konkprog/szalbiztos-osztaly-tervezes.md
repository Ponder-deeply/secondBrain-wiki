---
tags: [concept]
sources: [konkprog-canvas-feladat-1-threadsafemutableinteger.md, konkprog-canvas-feladat-1-gyakorlo-feladat-tovabbi-metodusok-a-threadsafemutableinte.md, konkprog-canvas-feladat-2-threadsafemutableintarray.md, konkprog-canvas-feladat-2-gyakorlo-feladat-tovabbi-metodusok-a-threadsafemutableinta.md, konkprog-canvas-feladat-3-atomic-tipusok.md]
derivation: source
kind: procedure
element: earth
updated: 2026-10-23
---

# Szálbiztos osztályok tervezése (ThreadSafeMutableInteger és IntArray)

Egy `int` vagy `int[]` fölé épített szálbiztos absztrakció: az egész objektumot egyetlen zárral, a tömböt elemenkénti zárakkal védjük, hogy a különböző elemek párhuzamosan írhatók legyenek.

## Tartalom

### ThreadSafeMutableInteger

Absztrakció a beépített `int` fölött; több szál olvashatja/írhatja szálbiztosan.

- Konstruktorok: `ThreadSafeMutableInteger(int)` és alapértelmezett.
- Alapműveletek: `int get()`, `void set(int)`.
- Atomicitást biztosító műveletek: `getAndIncrement`, `getAndDecrement`, `getAndAdd(int)`, `incrementAndGet`, `decrementAndGet`, `addAndGet(int)`.
- Bővítés (gyakorló): `int getAndUpdate(IntUnaryOperator)`, `int updateAndGet(IntUnaryOperator)`.
- Tesztelés minél több szállal, az összes művelet hívásával.

### ThreadSafeMutableIntArray

Szálbiztos `int` tömb. **Követelmény:** a különböző elemek egyszerre írhatók/olvashatók legyenek, tehát nem zárolható az egész tömb; a `synchronized` *metódus* ezért nem jó. Megoldás: egy `Object` tömb, amely minden elemhez külön zárat (lock-objektumot) rendel, és egy elem elérésekor csak annak a zárát szerezzük meg.

- `ThreadSafeMutableIntArray(int capacity)` – `capacity` méretű `int` tömb és a hozzá tartozó zártömb;
- `int get(int n)`, `void set(int n, int)` – az `n`-edik elem zárját szerzik meg;
- bővítés: `int updateAndGet(int n, IntUnaryOperator)`, `int getAndUpdate(int n, IntUnaryOperator)`.

Az elemenkénti zárolás a [[concepts/konkprog/synchronized-monitor]] blokkos alakjával valósul meg; a beépített megfelelők: [[concepts/konkprog/atomic-tipusok]].

## Kapocs

- [[concepts/konkprog/synchronized-monitor]] — zárolás
- [[concepts/konkprog/atomic-tipusok]] — a beépített megfelelők
- [[concepts/konkprog/banyaszok-es-epitok]] — zár-granularitás
