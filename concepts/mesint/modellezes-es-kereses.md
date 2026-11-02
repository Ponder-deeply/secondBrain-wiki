---
tags: [concept]
sources: [01.bevezetes.pdf]
derivation: source
kind: model
element: water
updated: 2026-10-12
---

# Modellezés és keresés

A kurzus alapgondolata: a feladatot **modellezéssel** útkeresési problémává (gráfreprezentációvá) alakítjuk, majd a megoldást **kereséssel** találjuk meg.

## Tartalom

```
feladat --modellezés--> útkeresési probléma (gráfreprezentáció) --keresés--> megoldás
```

**Modellezési módszerek:** állapottér modell, probléma redukció, probléma dekompozíció, korlátprogramozási modell, kétszemélyes játék modellje, logikai reprezentációk, valószínűségi háló.

**Keresési módszerek:** lokális keresések, visszalépéses keresés, gráfkeresések, evolúciós algoritmus, játékfa kiértékelő módszerek, logikai következtetések, bizonytalanság kezelés.

### Mire kell a modellezésnek fókuszálnia

- **Problématér elemei:** a probléma lehetséges válaszai.
- **Cél:** egy helyes válasz (megoldás) megtalálása.
- **Keresést segítő ötletek (heurisztikák):**
  - a problématér hasznos elemeinek elválasztása a haszontalanoktól,
  - kiinduló elem kijelölése,
  - az elemek szomszédsági kapcsolatainak kijelölése, hogy a problématér szisztematikus bejárását segítsük,
  - adott pillanatban elérhető elemek rangsorolása.

## Kapocs

- [[concepts/mesint/utkeresesi-problema]] — a modellezés célformája
- [[concepts/mesint/allapotter-modell]] — modellezési módszer
- [[concepts/mesint/problema-redukcios-modell]] — modellezési módszer
- [[concepts/mesint/kereso-rendszer]] — a keresés általános felépítése
- [[concepts/mesint/utazougynok-problema]] — példa
