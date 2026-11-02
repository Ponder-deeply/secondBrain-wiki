---
tags: [concept]
sources: [02.modellek.pdf]
derivation: source
kind: model
element: water
updated: 2026-10-12
---

# Állapottér modell

Az állapottér modell a problémát állapotokkal, az állapotokat egymásba vivő műveletekkel, kezdő- és célállapotokkal írja le; gráfreprezentációja az állapot-gráf, a megoldás pedig egy startcsúcsból célcsúcsba vezető irányított út.

## Tartalom

### Összetevők

- **Állapottér**: a probléma leírásához szükséges adatok által felvett érték-együttesek (állapotok) halmaza.
  - Az állapot többnyire összetett szerkezetű érték.
  - Gyakran egy bővebb alaphalmazzal és egy azon értelmezett **invariáns állítással** definiáljuk.
- **Műveletek**: állapotból állapotba vezetnek. Megadásukhoz az **előfeltétel** és a **hatás** leírása kell; az invariáns tulajdonságot tartó leképezések.
- **Kezdőállapot(ok)** vagy a kezdeti feltétel.
- **Célállapot(ok)** vagy a célfeltétel.

Jelölés a példákban: `Művelet(paraméterek): AT → AT`, `HA előfeltétel AKKOR hatás`, ahol `this:AT` az aktuális állapot.

### Gráfreprezentáció

| Állapottér modell | Állapot-gráf |
|---|---|
| állapot | csúcs |
| művelet hatása egy állapotra | irányított él |
| művelet költsége | él költsége |
| kezdő állapot | startcsúcs |
| célállapot | célcsúcs |
| műveletsorozat hatása | irányított út |
| megoldás | irányított út a startcsúcsból egy célcsúcsba (vagy maga egy célcsúcs) |

- Egy állapotra véges sok művelet alkalmazható, így a gráf véges kifokú.
- A műveletek költségének van alsó pozitív korlátja ($\delta$).

### Bonyolultság és modellválasztás

A reprezentációs gráf bonyolultsága (a startcsúcsból induló utak száma) határozza meg a problématér méretét, azon múlik a keresés hatékonysága. A bonyolultság függ a csúcsok és élek számától, a csúcsok ki-fokától, a körök gyakoriságától és hosszuk sokféleségétől. Ugyanannak a feladatnak több modellje lehet, érdemes kisebb problématerű modellt keresni (lásd [[concepts/mesint/n-kiralyno-problema]]).

### Példák

- [[concepts/mesint/hanoi-tornyai]]
- [[concepts/mesint/n-kiralyno-problema]]
- [[concepts/mesint/tologato-jatek]]

## Kapocs

- [[concepts/mesint/allapotter-vs-problemater]] — az állapottér és a problématér különbsége
- [[concepts/mesint/modellezes-es-kereses]] — a modellezés szerepe a keresési feladatban
- [[concepts/mesint/graf-fogalmak]] — az állapot-gráf gráfelméleti fogalmai
- [[concepts/mesint/utkeresesi-problema]] — a megoldás útkeresés az állapot-gráfban
- [[concepts/mesint/visszafele-halado-keresesi-modell]] — a célból induló keresés
