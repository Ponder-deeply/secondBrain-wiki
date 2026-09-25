---
tags: [concept, esemalk/tobbszalu-programozas-csharp-ban]
sources: [elte_eva_ea05_winforms_multithread.pdf]
derivation: source
updated: 2026-09-13
---

# Kritikus szakasz és kölcsönös kizárás

A közös erőforrások több szál általi elérésének problémája, és a
szinkronizációs objektumok (Mutex, Szemafor, Monitor) áttekintő
összehasonlítása.

## Tartalom

A gyerekszál nem tud egy végeredményt közvetlenül visszaadni a szülőszálnak
— a szálak közötti adatkommunikáció megosztott erőforrások (jellemzően
memória, közös változók) segítségével történhet, méghozzá nem csak a
gyerekszál tevékenységének végén, hanem közben is, és mindkét irányban.

A közös erőforrások kezelését a program **kritikus szakaszának** (*critical
section*) nevezzük. Azonos erőforrásra vonatkozó kritikus szakaszok
párhuzamos végrehajtása — kivéve, ha minden művelet csak olvasni próbálja az
erőforrást — hibát, nem várt futásidejű viselkedést okozhat.

A szálakat a közös erőforrások használatakor **szinkronizálni kell**,
**kölcsönös kizárás** (*mutual exclusion*) segítségével garantálva, hogy
egyszerre csak egy kritikus szakasz kerül végrehajtásra.

### Szinkronizációs objektumok összehasonlítása

| Mutex | Szemafor | Monitor |
|---|---|---|
| elnevezhető | elnevezhető | név nélküli |
| rendszer szintű hatókör | könnyebb súlyú | zárolt objektummal egyező hatókör (legfeljebb alkalmazás szintű) |
| jó választás folyamatok (alkalmazások) közötti szinkronizációhoz | többszörös zárolás lehetősége; rendszer / alkalmazás szintű hatókör; jó választás szálak közötti szinkronizációhoz | `lock` utasítással kényelmesen használható |

## Kapocs

- [[concepts/esemalk/csharp-szal-letrehozasa-kezelese]] — miért nem tudja a
  gyerekszál egyszerűen visszaadni az eredményét a szülőszálnak
- [[concepts/esemalk/csharp-mutex]] — a `Mutex` típus
- [[concepts/esemalk/csharp-szemafor]] — a `Semaphore` típus
- [[concepts/esemalk/csharp-monitor-lock]] — a `Monitor` osztály és a `lock`
  utasítás
- [[concepts/esemalk/csharp-szalbiztos-gyujtemenyek]] — a kölcsönös kizárást
  a gyűjtemény metódusaiban maga megvalósító, szálbiztos gyűjtemények
