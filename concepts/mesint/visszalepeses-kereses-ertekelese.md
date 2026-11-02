---
tags: [concept]
sources: [04.visszalep.pdf]
derivation: source
kind: comparison
element: water
updated: 2026-10-12
---

# A visszalépéses keresés értékelése

A visszalépéses keresés előnyei (terminál, könnyen implementálható, kicsi a memóriaigénye) és hátrányai (nem optimális, rossz kezdeti döntés drágán javítható, zsákutcákat ismételten bejárhat).

## Tartalom

### Előnyök

- **Mindig terminál** (mélységi korláttal, vagy körfigyeléssel véges gráfon).
- **Talál megoldást**, ha van olyan a mélységi korláton belül.
- **Könnyen implementálható** (rekurzív eljárásként).
- **Kicsi a memóriaigénye**, mert csak az aktuális utat (a mélységi korlát által határolt hosszút) kell tárolni.

### Hátrányok

- **Nem ad optimális megoldást** (az első megtalált megoldást adja vissza); ez iterációba szervezhető, például a mélységi korlát fokozatos növelésével.
- **Egy kezdeti rossz döntés csak sok visszalépéssel korrigálható** (visszaugrásos keresés: a keresés a hibás döntés helyére csak a közbülső csúcsok sorra visszalépésével jut vissza).
- **Egy zsákutca-részt többször is bejárhat** a keresés, mert nem jegyzi meg, hogy egy állapotról már kiderült: onnan nincs megoldás.

### Összefüggés a mélységi korláttal

A mélységi korlát adja a terminálást és a kis memóriaigényt, de a korlátnál hosszabb megoldást nem talál meg, és a kisebb körök miatt a lépésszám nőhet; részletek: [[concepts/mesint/melysegi-korlatos-visszalepes]].

## Kapocs

- [[concepts/mesint/visszalepeses-kereses]] — az értékelt eljárás
- [[concepts/mesint/melysegi-korlatos-visszalepes]] — a mélységi korlát hatása a tulajdonságokra
- [[concepts/mesint/visszalepes-feltetelei]] — a zsákutca-bejárás mérséklése a visszalépési feltételekkel
- [[concepts/mesint/kereso-rendszer]] — a keresőrendszer-modell, amelynek vezérlési stratégiája a visszalépés
