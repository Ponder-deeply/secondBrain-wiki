---
tags: [concept]
sources: [konkprog-canvas-feladat-3-gyujtemenyek-eleresenek-szinkronizacioja.md, konkprog-canvas-feladat-4-szinkronizalt-gyujtemenyek.md, konkprog-canvas-feladat-1-gyakorlo-feladat-banki-ugyfelek.md, konkprog-canvas-feladat-1-gyakorlo-feladat-termelo-es-fogyaszto.md]
derivation: source
kind: procedure
element: earth
updated: 2026-10-23
---

# Gyűjtemények szinkronizálása

A szinkronizálatlan gyűjtemény több szálból nem használható biztonságosan; két megoldás: a hozzáférést szinkronizált blokkba tesszük, vagy a gyűjteményt a `Collections.synchronizedXxx()` burkolóval szálbiztossá tesszük.

## Tartalom

### Probléma

A `CommonList` programban két szál (páros, páratlan számok) ad elemeket egy közös listához. Szinkronizálás nélkül nem a várt (teljes, hibamentes) eredményt kapjuk ([[concepts/konkprog/verseny-helyzet-es-adatverseny]]).

### Két javítás

1. **Szinkronizált blokk:** a szálakban a lista elérését `synchronized` blokkba tesszük (`CommonListSynchronized`).
2. **Szinkronizált burkoló:** `Collections.synchronizedList(list)` (`CommonListSynchronizedList`); térképre `Collections.synchronizedMap(map)`.

### Banki ügyfelek (tőzsdeszimuláció)

A részvények (3 nagybetűs azonosító) árát egy map tárolja; mind 100 $-ról indul. 100 bróker 10000 körön át vesz vagy ad: vételkor az ár 1%-kal nő, eladáskor ugyanennyivel csökken; egy további szál másodpercenként kiírja az árfolyamokat. A map szálbiztossá tétele: `Collections.synchronizedMap()`.

A termelő–fogyasztó feladat sorának szálbiztossá tétele szintén ide tartozik ([[concepts/konkprog/termelo-fogyaszto]]).

## Kapocs

- [[concepts/konkprog/synchronized-monitor]] — szinkronizált blokk
- [[concepts/konkprog/executor-es-thread-pool]] — a brókerek pool-ban futnak
- [[concepts/konkprog/verseny-helyzet-es-adatverseny]] — a hiba oka
