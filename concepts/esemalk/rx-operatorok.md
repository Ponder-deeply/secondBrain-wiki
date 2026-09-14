---
tags: [concept]
sources: [elte_eva_ea11_reactive.pdf]
derivation: source
updated: 2026-09-13
---

# ReactiveX operátorok

A ReactiveX megfigyelhető adatfolyamokat (`IObservable<T>`) operátorokkal
szűrhetjük, kombinálhatjuk és transzformálhatjuk; az egyes operátorok
hatását ún. *marble diagram*-okkal szokás szemléltetni, ahol a felső
idővonal a bemeneti, az alsó a kimeneti adatfolyamot ábrázolja.

## Tartalom

### Szűrő operátorok

- **`filter(x => predikátum)`** — csak a predikátumnak megfelelő elemeket
  engedi tovább. Példa: `filter(x => x > 10)` a `2, 30, 22, 5, 60, 1`
  sorozatból a `30, 22, 60` elemeket adja vissza. C# (Rx.NET):
  **`Where()`**
- **`debounce`** — csak akkor enged tovább egy elemet, ha egy adott ideig
  nem érkezett újabb; a gyors egymásutánban érkező elemeket az utolsóra
  cseréli (pl. `1, 2, 3, 4, 5, 6` → `1, 5, 6`, ha a `2`–`5` elemek gyorsan
  egymás után érkeztek). C# (Rx.NET): **`Throttle()`**
- **`distinct`** — csak az adatfolyamban korábban még elő nem fordult
  elemeket engedi tovább (pl. `1, 2, 2, 1, 3` → `1, 2, 3`). C# (Rx.NET):
  **`Distinct()`**, illetve az egymást követő ismétlődéseket szűrő
  **`DistinctUntilChanged()`**

### Transzformációs operátorok

- **`map(x => kifejezés)`** — minden elemet a megadott függvénnyel
  alakít át (pl. `map(x => 10 * x)` az `1, 2, 3` sorozatból `10, 20, 30`-at
  ad). C# (Rx.NET): **`Select()`**
- **`scan((x, y) => kifejezés)`** — futó (kumulatív) összesítést végez,
  minden kimeneti elem az addigi bemenetek akkumulált eredménye (pl.
  `scan((x, y) => x + y)` az `1, 2, 3, 4, 5` sorozatból `1, 3, 6, 10, 15`-öt
  ad). C# (Rx.NET): **`Scan()`**

### Kombinációs operátorok

- **`merge`** — több adatfolyam elemeit egyetlen adatfolyamba egyesíti,
  megőrizve az egyes elemek relatív időbeli sorrendjét. C# (Rx.NET):
  **`Merge()`**

### Csoportosító operátorok

- **`GroupBy`** — a bemeneti adatfolyam elemeit egy kulcs szerint
  szétosztja több kimeneti adatfolyamra (pl. alakzat szerint kör/
  háromszög csoportokra). C# (Rx.NET): **`GroupBy()`**

Az operátorok az [[concepts/esemalk/rx-observable-alapok]] lapon
bemutatott `Observable`-ökre alkalmazhatók, és láncolhatók egymás után.

## Kapocs

- [[concepts/esemalk/rx-observable-alapok]] — az `IObservable<T>` modell
  és a megfigyelhető felsorolások létrehozása
- [[concepts/esemalk/reaktiv-programozas-alapjai]] — a reaktív
  programozás áttekintése, az operátorok kategóriáinak összefoglalása
- [[concepts/esemalk/csharp-linq]] — a LINQ hasonló elvű, de
  `IEnumerable<T>`-re épülő lekérdezés-operátorai
- [[concepts/esemalk/reaktiv-szenzor-pelda]] — az operátorok alkalmazása egy
  konkrét szenzoradat-feldolgozó példán
