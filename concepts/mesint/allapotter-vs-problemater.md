---
tags: [concept]
sources: [02.modellek.pdf]
derivation: source
kind: comparison
element: water
updated: 2026-10-12
---

# Állapottér és problématér

Az állapottér és a problématér kapcsolata szoros, de nem azonosak: a problématér elemei (a lehetséges válaszok) többnyire a kezdőállapotból kiinduló műveletsorozatok (utak).

## Tartalom

- **Állapottér**: a problémát leíró adatok lehetséges értékei ([[concepts/mesint/allapotter-modell]]).
- **Problématér**: a lehetséges válaszok halmaza; amiben a keresés dolgozik.
- [[concepts/mesint/hanoi-tornyai]]: a válasz nem a korongok egy állapota, hanem a kezdőállapotra alkalmazott műveletsorozat; ezek között keressük azt, amelyik a célállapothoz vezet.
- [[concepts/mesint/n-kiralyno-problema]]: a válasz egy célállapot (királynő-elrendezés), de ezt egy alkalmas műveletsorozattal érhetjük el, tehát itt is a műveletsorozatok között keresünk, nem az állapotok között.

### Következmény a keresés költségére

A reprezentációs gráf bonyolultsága (a startcsúcsból induló utak száma, ami függ a csúcsok és élek számától, a ki-fokoktól, a körök gyakoriságától és hosszuk sokféleségétől) szabja meg a problématér méretét, azon pedig a keresés számításigénye múlik. Ezért érdemes olyan modellt választani, amely kisebb problémateret jelöl ki.

## Kapocs

- [[concepts/mesint/allapotter-modell]] — az állapottér definíciója
- [[concepts/mesint/modellezes-es-kereses]] — a keresés és a modell viszonya
- [[concepts/mesint/utkeresesi-problema]] — a megoldás út a gráfban
