---
tags: [concept]
sources: [Laki_Lecture_1.pdf]
derivation: source
kind: overview
element: air
updated: 2026-09-25
---

# Az Internet története és tervezési elvei

Az Internet a hidegháborús DARPA-kutatásokból, az ARPANET-ből nőtt ki. Mai működését négy, Robert Kahn által 1972-ben megfogalmazott alapelv határozza meg — ezek közül a *best effort* továbbítás a legfontosabb, mert minden felső rétegbeli megbízhatósági mechanizmus erre épül.

## Tartalom

### Főbb állomások

| Év | Esemény |
|---|---|
| 1957 | Kapcsolat egy távoli számítógéppel; a Szputnyik–1 fellövése |
| 1958 | A DARPA (*Advanced Research Projects Agency*) megalapítása |
| 1961 | „Packet Switching Theory” (J.C.R. Licklider) |
| 1962 | A „Galactic Network” koncepciója (Licklider) |
| 1965 | Az Internet első őse (Thomas Merrill, Laurence G. Roberts) |
| 1966–67 | Az ARPANET tervezésének kezdete, tervezete |
| 1969 | Az ARPANET első csomópontja (UCLA, SRI, UCSB, Utah) |
| 1972 | Robert Kahn koncepciója — az Internet alapelvei |
| 1982 | A TCP/IP az amerikai katonai hálózatok standardja lesz |
| 1990 | Az ARPANET megszűnése |

Más, történetileg fontos korai hálózatok: **RAND** (USA, katonai célokkal), **NPL** (Anglia, kereskedelmi), **CYCLADES** (Franciaország, tudományos). Az ARPANET 1969 decemberében 4, 1971 márciusában már kb. 15, 1972 szeptemberére több tucat csomóponttal működött.

### Robert Kahn koncepciója (DARPA, 1972) — az Internet alapelvei

1. **Minden (lokális) hálózat autonóm.** Önállóan dolgozik, és nem kell külön konfigurálni ahhoz, hogy a WAN része legyen.
2. **Best effort („legjobb szándék”) kommunikáció.** Ha egy csomag nem éri el a célt, egyszerűen törlődik; ilyenkor az **alkalmazás** (végpont) küldi újra. A hálózat tehát nem garantál kézbesítést.
3. **„Black box” megközelítés a kapcsolatokhoz.** A hálózatokat összekötő fekete dobozokat később *gateway*-nek és *router*-nek nevezték el. Ezek nem őrzik meg a csomaginformációkat, és nincs folyam-felügyeletük (állapotmentesek).
4. **Nincs globális felügyelet.**

**Vizsgaszempont:** a 2. és 3. elv együtt adja az Internet „buta hálózat, okos végpontok” jellegét: a routerek csak továbbítanak, a megbízhatóságot (újraküldés, sorrendhelyesség) a szállítói réteg ([[concepts/telekom/tcp-ip-modell]]) vagy az alkalmazás adja.

### Miért kell rétegzés?

Az Internet sokféle hálózati technológiát (Ethernet, Wi-Fi, Bluetooth, optikai szál, kábelmodem, DSL), hálózattípust (áramkör- és csomagkapcsolt; vezetékes, vezeték nélküli, optikai, műholdas) és alkalmazást (e-mail, web/HTTP, FTP, BitTorrent, VoIP) köt össze. Ha minden alkalmazásnak minden médiumhoz külön kellene illeszkednie, az $N \times M$ illesztés „rémálom” lenne: új alkalmazás vagy médium bevezetése drága, a növekedés korlátozott — ráadásul a két végpont eltérő médiumot is használhat (egyik Ethernet, másik Wi-Fi). A megoldás egy közbülső absztrakciós réteg (API), amellyel új alkalmazás vagy médium $O(1)$ munkával bevezethető. Ez a [[concepts/telekom/retegzett-halozati-architektura]] alapgondolata.

## Kapocs

- [[concepts/telekom/halozati-alapfogalmak]] — WAN, LAN, csomagkapcsolás fogalma
- [[concepts/telekom/retegzett-halozati-architektura]] — a rétegzés mint válasz az összekapcsolási problémára
- [[concepts/telekom/tcp-ip-modell]] — az Internet rétegmodellje, amely 1982-ben lett standard
