---
tags: [concept, esemalk/architektura-es-esemenykezeles]
sources: [elte_eva_ea04_winforms_architecture_testing.pdf]
derivation: source
updated: 2026-09-13
---

# Háromrétegű architektúra

A háromrétegű (*three-tier*) architektúra a [[concepts/esemalk/modell-nezet-architektura]]
továbbfejlesztése: a modellről leválasztja a perzisztens adattárolást is,
így három, egymásra épülő réteget kapunk.

## Tartalom

A szoftver architektúra a fejlesztés során meghozott elsődleges tervezési
döntések halmaza: célja a rendszer magas szintű felépítésének és
működésének meghatározása, a komponensek és relációk kiépítése. A
tervezés során általában mintákra (*architectural pattern*)
hagyatkozunk.

### A perzisztencia réteg

Az adatkezelésnek fontos része az adatok tárolása egy *perzisztens*
(hosszú távú) adattárban — ez lehet fájlrendszer, adatbázis, hálózati
szolgáltatás stb., az adattárolás formátuma pedig egyedi (bináris,
szöveges) vagy strukturált (XML, JSON, …), aszerint, hogy az adatokat meg
szeretnénk-e osztani más szoftverekkel.

A kétrétegű ([[concepts/esemalk/modell-nezet-architektura]]) felbontásban
a perzisztens adattárolás is a modell feladata. Mivel azonban a
perzisztens adatkezelés formája, módja nem függ a modelltől, könnyen
leválasztható róla — ez a leválasztás teszi lehetővé, hogy a két
komponenst egymástól függetlenül módosítsuk vagy cseréljük, és egy
komponensnek se kelljen több dologért felelnie (*single responsibility
principle*).

### A három réteg

A leválasztás elvezet a háromrétegű architektúrához, amelyben elkülönül:

- a **nézet** (*presentation/view tier*, *presentation layer*) — a
  felhasználói felület megjelenítése és eseménykezelése,
- a **modell** (*logic/application tier*, *business logic layer*) — az
  alkalmazáslogika és állapotkezelés,
- a **perzisztencia**, vagy **adatelérés** (*data tier*, *data access
  layer*, *persistence layer*) — az adatmentés és -betöltés.

A felhasználó a nézettel, a nézet a modellel, a modell pedig a
perzisztencia réteggel kommunikál; az adattár (fájlrendszer, adatbázis,
…) csak a perzisztencia rétegen keresztül érhető el.

### Rétegek közötti függőségek

A rétegek között *függőségek* (*dependency*) alakulnak ki, mivel
felhasználják egymás funkcionalitását. A cél a minél kisebb függőség
elérése (*loose coupling*): a függőségeket úgy valósítjuk meg, hogy a
rétegek ne a konkrét megvalósítástól, hanem csak annak felületétől
(interfészétől) függjenek. A konkrét megvalósítást külön adjuk át a
rétegnek — ezt a technikát nevezzük
[[concepts/esemalk/fuggoseg-befecskendezes]]nek (*dependency injection*).

Háromrétegű architektúra esetén a függőség-befecskendezést jellemzően a
modell, illetve az adatkezelés esetén használjuk: a perzisztencia réteg
felületét (pl. `PersistenceInterface`) elválasztjuk a megvalósítástól
(pl. `PersistenceImplementation`), utóbbit pedig a nézet fecskendezi be
a modellbe.

Egy kidolgozott, háromrétegű architektúrában megvalósított példát lásd:
[[concepts/esemalk/tictactoe-haromreteg-pelda]].

## Kapocs

- [[concepts/esemalk/modell-nezet-architektura]] — a kétrétegű
  architektúra, amelyből a perzisztencia réteg leválasztásával jön
  létre a háromrétegű felépítés
- [[concepts/esemalk/monolitikus-architektura]] — a legegyszerűbb,
  rétegezetlen felépítés, amelynek korlátait a rétegzés oldja fel
- [[concepts/esemalk/fuggoseg-befecskendezes]] — a rétegek közötti
  függőségek lazítására szolgáló technika
- [[concepts/esemalk/tictactoe-haromreteg-pelda]] — kidolgozott példa
  háromrétegű architektúrában
- [[subjects/esemalk]]
