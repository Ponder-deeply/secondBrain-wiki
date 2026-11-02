---
tags: [concept]
sources: [konkprog-canvas-feladat-gyakorlo-feladat-banyaszok-es-epitok.md, konkprog-canvas-feladat-2-gyakorlo-feladat-szinkronizalt-metodusok-a-banyaszok-es-ep.md, konkprog-canvas-feladat-3-gyakorlo-feladat-szinkronizalt-blokkok-a-banyaszok-es-epit.md]
derivation: source
kind: model
element: earth
updated: 2026-10-23
---

# Bányászok és építők szimuláció

Szimuláció, amelyben bányász- és építőszálak közös erőforrásokon (arany, házak) dolgoznak; a feladatsor a szálindítást, bevárást, majd a szinkronizálás finomhangolását gyakoroltatja.

## Tartalom

### A szimuláció

Két féle dolgozó (szál) próbál 5 házat felépíteni: a bányászok (miner) aranyat bányásznak az aranybányából, az építészek (builder) ebből építenek házat. Osztályok:

- `Configuration` – a szimuláció konfigurációja (építkezés időtartama, dolgozók száma…); nem módosítandó.
- `Resources` – nyilvántartja a bányában maradt aranyat, a dolgozók aranyát és az épített házak számát.
- `ThreadCraft` – `main` és a dolgozók implementációja.

### Feladatok

1. **`ThreadCraft`:** a dolgozók szálainak indítása (`mineAction()`, `buildAction()`), egy logoló szál (`loggingAction()`), a dolgozók bevárása a `main`-ben, majd a vég kiírása; `sleepForMsec(int msec)` megvalósítása.
2. **Szinkronizált metódusok:** a `Resources` közös erőforrásainak szálbiztossá tétele `synchronized` metódusokkal; csak a `Resources.java` módosítható.
3. **Szinkronizált blokkok:** teljesítményjavítás – egész metódusok helyett csak a közös erőforrásokat elérő legrövidebb kódrészek kerülnek `synchronized` blokkba (`Resources2`).

Tanulság: a zár tartási ideje (granularitás) a teljesítményt befolyásolja; lásd [[concepts/konkprog/synchronized-monitor]], [[concepts/konkprog/szal-letrehozas]], [[concepts/konkprog/szal-varakozas-es-megszakitas]].

## Kapocs

- [[concepts/konkprog/synchronized-monitor]] — metódus vs blokk
- [[concepts/konkprog/szal-letrehozas]] — szálindítás
- [[concepts/konkprog/szal-varakozas-es-megszakitas]] — join és sleep
