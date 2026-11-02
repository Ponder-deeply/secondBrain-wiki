---
tags: [concept]
sources: [konkprog-canvas-feladat-1-callable-es-future-objektumok.md, konkprog-canvas-feladat-1-gyakorlo-feladat-banki-ugyfelek-tovabbfejlesztes.md]
derivation: source
kind: procedure
element: earth
updated: 2026-10-23
---

# Callable és Future

A `Callable` értéket visszaadó feladat; `ExecutorService.submit()` azonnal `Future`-t ad vissza, amelynek `get()` metódusa az eredményt (szükség esetén várakozással) szolgáltatja.

## Tartalom

- `Callable<V>` – mint a `Runnable`, de a `call()` értékkel tér vissza.
- `Future<V> f = pool.submit(callable);` – a beküldés azonnal visszatér.
- `f.get()` – lekérdezi a végeredményt (blokkol, amíg elkészül).

### Feladatok

- **Callable és Future objektumok** (`ThreadPools2.java`): az előző pool-os feladat `Runnable` helyett `Callable`-lel.
- **Banki ügyfelek (továbbfejlesztés):** az ügyfél kölcsöneinek összege már nem tömbbe íródik a szál végén, hanem a `submit()`-nak átadott névtelen metódus visszatérési értéke; az összegeket a `get()`-tel kérjük ki. A `shutdown()` csak a kétféle módon összesített kölcsönök egyezésének ellenőrzése után hívható.

A pool kezelése: [[concepts/konkprog/executor-es-thread-pool]].

## Kapocs

- [[concepts/konkprog/executor-es-thread-pool]] — a pool
