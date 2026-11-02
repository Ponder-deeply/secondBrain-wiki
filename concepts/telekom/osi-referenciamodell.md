---
tags: [concept]
sources: [Laki_Lecture_1.pdf, Laki_Lecture_2.pdf]
derivation: source
kind: comparison
element: air
updated: 2026-09-25
---

# OSI referenciamodell

Az *Open System Interconnection Reference Model* (ISO/IEC 7498-1) hétrétegű, koncepcionális standard a kommunikációs hálózatok belső funkcióinak leírására. Minden rétegét a szolgáltatás–interfész–protokoll hármassal jellemezzük ([[concepts/telekom/retegzett-halozati-architektura]]).

## Tartalom

### A hét réteg alulról felfelé

| # | Réteg | Szolgáltatás | Interfész | Protokoll | Példa |
|---|---|---|---|---|---|
| 1 | **Fizikai** (*physical*) | információt visz át két fizikailag összekötött eszköz között; definiálja az eszköz és a közeg kapcsolatát | egy bit átvitelét specifikálja | bitkódolási séma, feszültségszintek, jelek időzítése | koax, optikai kábel, rádiófrekvenciás adó |
| 2 | **Adatkapcsolati** (*data link*) | keretekre tördelés (határok a csomagok között); közeghozzáférés-vezérlés (MAC); *per-hop* megbízhatóság és folyamvezérlés | keret küldése két, közös médiumra kötött eszköz között | fizikai címzés (MAC-cím, IB-cím) | Ethernet, Wi-Fi, InfiniBand |
| 3 | **Hálózati** (*network*) | csomagtovábbítás, útvonalválasztás, fragmentálás kezelése, csomagütemezés, pufferkezelés | csomag küldése egy adott végpontnak | globálisan egyedi címek; routing táblák karbantartása | IPv4, IPv6 |
| 4 | **Szállítói** (*transport*) | multiplexálás/demultiplexálás, torlódásvezérlés, megbízható, sorrendhelyes továbbítás | üzenet küldése egy célállomásnak | portszám, megbízhatóság/hibajavítás, folyamfelügyelet | UDP, TCP |
| 5 | **Ülés / munkamenet** (*session*) | kapcsolatmenedzsment (felépítés, fenntartás, bontás), a munkamenet típusa, szinkronizációs pontok (*checkpoint*) | „attól függ” | tokenmenedzsment, checkpointok beszúrása | nincs önálló példa |
| 6 | **Megjelenítési** (*presentation*) | adatkonverzió reprezentációk között (big endian ↔ little endian, ASCII ↔ Unicode) | „attól függ” | adatformátumokat definiál, transzformációs szabályokat alkalmaz | nincs önálló példa |
| 7 | **Alkalmazási** (*application*) | bármi | bármi | bármi | a telefonod appjai |

Emlékeztető a sorrendhez (alulról): **F**izikai – **A**datkapcsolati – **H**álózati – **Sz**állítói – **Ü**lés – **M**egjelenítési – **A**lkalmazási.

### Kommunikáció a modellben

A rétegek logikailag *peer-to-peer* módon kommunikálnak a másik hoszt azonos rétegével. A köztes eszközök (router, switch) csak az alsó 2–3 réteget valósítják meg: a csomag a küldő hosztban a fizikai rétegig lemegy, a routerben a hálózati rétegig felmegy és vissza, majd a célhosztban az alkalmazásig felmegy.

### Az adatkapcsolati réteg két alrétege

A tárgy felépítése szerint az adatkapcsolati réteg két alrétegre bomlik: az **LLC** (*Logical Link Control* — keretezés, hibakezelés, forgalomszabályozás; [[concepts/telekom/keretezes]]) és a **MAC** (*Medium Access Control* — közös közeg megosztása; [[concepts/telekom/kozeghozzaferes-alapjai]]).

### Viszony a gyakorlathoz

Az OSI modell a gyakorlatban nem valósult meg önállóan: az ülés- és megjelenítési rétegnek nincs külön protokollja, feladataikat az alkalmazások végzik. Ezért a tárgy a **hibrid, ötrétegű** modellt használja, amelyben az OSI felső három rétege egyetlen alkalmazási rétegbe olvad ([[concepts/telekom/tcp-ip-modell]]).

**Vizsgaszempont:** gyakori kérdés, hogy egy adott feladat (pl. útvonalválasztás, portszám, bitkódolás, keretezés) melyik réteghez tartozik, illetve hogy egy eszköz (switch, router) meddig „látja” a vermet.

## Kapocs

- [[concepts/telekom/retegzett-halozati-architektura]] — a rétegzés elve, beburkolás
- [[concepts/telekom/tcp-ip-modell]] — az Internet gyakorlati rétegmodellje és a hibrid modell
- [[concepts/telekom/fourier-analizis-es-savkorlat]] — az 1. réteg: jelátvitel és sávkorlát
