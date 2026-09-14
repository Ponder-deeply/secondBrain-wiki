---
tags: [concept]
sources: [elte_eva_ea11_reactive.pdf]
derivation: source
updated: 2026-09-13
---

# Reaktív programozás alapjai

A reaktív programozás egy deklaratív programozási paradigma, amely az
aszinkron eseményfeldolgozás és az adatfolyamok (*data streams*) fogalmára
épül: "*Reactive programming is a declarative programming paradigm that is
based on the idea of asynchronous event processing and data streams.*"

## Tartalom

Az Avalonia UI a reaktív programozást a *ReactiveUI* keretrendszeren
keresztül támogatja, amely maga az *Rx.NET* (*Reactive Extensions for .NET*)
könyvtárra épül.

A reaktív programozás legfontosabb elemei:

- **Időben változó, megfigyelhető változók** (*time variant variables*),
  amelyeket adatfolyamokként (*data streams*) is felfoghatunk — a
  hagyományos `int c = a + b;` kiértékelés egyszeri, statikus eredményt ad;
  a reaktív modellben a változó értéke a bemenetek időbeli változásával
  együtt frissül.
- **Aszinkron végrehajtás és ütemezők (*schedulers*) támogatása** — hogy az
  *observerek* és *observable*-ök melyik szálon hajtódjanak végre.
- **Operátorok**, amelyekkel a megfigyelhető adatfolyamok szűrhetők,
  kombinálhatók és transzformálhatók:
  - Szűrők: `filter`, `skip`, `take`
  - Kombinációs operátorok: `concat`, `merge`, `zip`
  - Transzformációs operátorok: `map`, `groupby`
  - stb.

A reaktív programozás modellje a klasszikus *Iterator* és *Observer* GoF
tervezési minták kombinálásából adódik: lásd
[[concepts/esemalk/reaktiv-iterator-tervezesi-minta]] és
[[concepts/esemalk/reaktiv-observer-tervezesi-minta]]. Az így kapott
`Observable`/`Observer`/`Subscription` modellt és a konkrét ReactiveX
könyvtárat a [[concepts/esemalk/rx-observable-alapok]] lap tárgyalja
részletesen, az operátorokat pedig a
[[concepts/esemalk/rx-operatorok]] lap.

## Kapocs

- [[concepts/esemalk/reaktiv-iterator-tervezesi-minta]] — az egyik forrás
  tervezési minta, amely a megfigyelhető felsorolók alapját adja
- [[concepts/esemalk/reaktiv-observer-tervezesi-minta]] — a másik forrás
  tervezési minta, a C# eseményeinek is alapja
- [[concepts/esemalk/rx-observable-alapok]] — a ReactiveX könyvtár és az
  `IObservable<T>`/`IObserver<T>` modell
- [[concepts/esemalk/rx-operatorok]] — a megfigyelhető adatfolyamokon
  végezhető operátorok
- [[concepts/esemalk/csharp-async-await]] — a taszk-alapú aszinkron
  programozás, a reaktív modelltől eltérő paradigma ugyanarra a problémára
- [[concepts/esemalk/avalonia-mvvm-toolkit]] — az Avalonia UI MVVM
  Toolkitja, amely reaktív-jellegű (de nem Rx-alapú) kötési mechanizmusokat
  kínál
