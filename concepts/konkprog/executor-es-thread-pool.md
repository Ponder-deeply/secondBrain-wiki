---
tags: [concept]
sources: [konkprog-canvas-feladat-2-egyszeru-thread-pool-ok.md, konkprog-canvas-feladat-1-gyakorlo-feladat-banki-ugyfelek.md, konkprog-canvas-feladat-1-gyakorlo-feladat-banki-ugyfelek-tovabbfejlesztes.md]
derivation: source
kind: procedure
element: earth
updated: 2026-10-23
---

# ExecutorService és thread pool

Az `ExecutorService` rögzített számú szálon hajtja végre a beküldött feladatokat (`Executors.newFixedThreadPool`); a pool leállítása `shutdown()`, a befejezés megvárása `awaitTermination()`.

## Tartalom

### Életciklus

1. Létrehozás: `ExecutorService pool = Executors.newFixedThreadPool(n);` – egyszerre legfeljebb `n` szál fut.
2. Feladatok beküldése: `pool.submit(...)` (Runnable vagy Callable; lásd [[concepts/konkprog/callable-es-future]]).
3. Leállítás: `pool.shutdown()` – új feladatot nem fogad el, a beküldötteket befejezi.
4. Várakozás: `pool.awaitTermination(1, TimeUnit.MINUTES)` – a Canvas-feladatban „egy percet” várunk.

A `shutdown()`-t csak azután szabad hívni, hogy minden szükséges eredmény elkészült (a banki feladatban az összegek egyezésének vizsgálata után).

### Feladatok

- **Egyszerű thread pool-ok** (`ThreadPools1.java`): fix méretű pool, néhány feladat, leállítás és várakozás.
- **Banki ügyfelek:** 100 bróker szál feladatként; a szálak eredményeit egy tömbbe írták, a továbbfejlesztett változatban `submit()` visszatérési értékét használjuk.

Szálak kézi indításához képest: [[concepts/konkprog/szal-letrehozas]].

## Kapocs

- [[concepts/konkprog/callable-es-future]] — értéket adó feladatok
- [[concepts/konkprog/szal-letrehozas]] — kézi szálkezelés
- [[concepts/konkprog/szinkronizalt-gyujtemenyek]] — közös map
