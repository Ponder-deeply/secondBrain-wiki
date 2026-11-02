---
tags: [concept]
sources: [Laki_Lecture_5.pdf]
derivation: source
kind: comparison
element: water
updated: 2026-09-25
---

# CSMA — vivőjel-érzékeléses többszörös hozzáférés

A *Carrier Sense Multiple Access* protokollok azzal a többletfeltevéssel élnek, hogy minden állomás **bele tud hallgatni a csatornába**, és el tudja dönteni, hogy azt más állomás éppen használja-e. Aki foglalt csatornát hall, nem kezd adni — ezzel az ütközések nagy része elkerülhető. A három változat abban tér el, mit tesz az állomás foglalt csatorna esetén.

## Tartalom

### 1-perzisztens CSMA

- Vivőjel-érzékelés van; **folytonos** időmodell.
- **Algoritmus:** keret leadása előtt belehallgat a csatornába:
  - ha **foglalt**, addig vár, amíg fel nem szabadul, és szabad csatorna esetén **azonnal** küld (*perzisztens* = kitartóan figyel);
  - ha **szabad**, küld.
- Ütközés esetén véletlen hosszú ideig vár, majd újrakezdi a keret leadását.
- **Tulajdonságok:** a terjedési késleltetés nagymértékben befolyásolhatja a teljesítményét (egy állomás adását a többiek csak $d$ késéssel hallják); jobb teljesítményt mutat, mint az ALOHA protokollok. Gyenge pont: ha többen várnak egy foglalt csatornára, a felszabaduláskor mind egyszerre kezdenek adni — biztos ütközés.

(A név onnan ered, hogy szabad csatornán 1 valószínűséggel ad.)

### Nem-perzisztens CSMA

- Vivőjel-érzékelés van; folytonos időmodell; cél a **mohóság kerülése**.
- **Algoritmus:** keret leadása előtt belehallgat:
  - ha **foglalt**, **véletlen ideig vár** (közben nem figyeli a forgalmat), majd előröl kezdi a küldési algoritmust;
  - ha **szabad**, küld.
- Ütközéskor véletlen ideig vár, majd újrakezd.
- **Tulajdonság:** (intuitívan) jobb teljesítmény, mint az 1-perzisztensé, mert a várakozók szétszóródnak időben; cserébe nagyobb a késleltetés.

### p-perzisztens CSMA

- Vivőjel-érzékelés van; **diszkrét** időmodell.
- **Algoritmus:** adáskész állapotban belehallgat a csatornába:
  - ha **foglalt**, vár a következő időrésig, majd megismétli az algoritmust;
  - ha **szabad**, **$p$ valószínűséggel küld**, $1-p$ valószínűséggel visszalép a következő időrésig. Várakozás esetén a következő időrésben megismétli az algoritmust. Ez addig folytatódik, amíg el nem küldi a keretet, vagy amíg egy másik állomás el nem kezd küldeni — ekkor úgy viselkedik, mintha ütközés történt volna.
- Ütközéskor véletlen ideig vár, majd újrakezd.

### Összevetés

| Változat | Szabad csatornán | Foglalt csatornán |
|---|---|---|
| 1-perzisztens | azonnal küld | figyel, és a felszabaduláskor azonnal küld |
| nem-perzisztens | azonnal küld | véletlen (konstans v. változó) ideig vár, újrapróbál |
| $p$-perzisztens | $p$ valószínűséggel küld, különben vár 1 időegységet | vár a következő résig |

A terhelés ($G$) függvényében az átvitelt ($S$) ábrázolva: a CSMA-változatok messze az ALOHA fölött teljesítenek; minél kisebb $p$ (pl. 0,01-perzisztens), illetve a nem-perzisztens változat, annál közelebb kerül a görbe nagy terhelésnél is az 1-hez — cserébe kis terhelésnél nő a késleltetés.

A következő lépés: ha az ütközést **adás közben** észleljük, a sérült keret küldését azonnal abba lehet hagyni — ez a [[concepts/telekom/csma-cd]].

**Vizsgaszempont:** a három perzisztencia-stratégia pontos algoritmusa és összevetése, valamint annak magyarázata, miért jobb a CSMA az ALOHA-nál.

## Kapocs

- [[concepts/telekom/aloha]] — vivőjel-érzékelés nélküli elődje
- [[concepts/telekom/csma-cd]] — ütközésdetektálással kiegészítve
- [[concepts/telekom/kozeghozzaferes-alapjai]] — időmodell és vivőjel-érzékelés a modellben
