---
tags: [concept]
sources: [elte_eva_ea11_reactive.pdf]
derivation: source
kind: procedure
element: earth
updated: 2026-09-30
---

# ReactiveX és az Observable alapjai

A reaktív programozáshoz használt egyik népszerű szoftverkönyvtár az
eredetileg a Microsoft által kidolgozott, mára nyílt forráskódú
[ReactiveX](https://www.reactivex.io/) (röviden: Rx) könyvtár, amely
számos programozási nyelvhez elérhető; C#/.NET-hez az
[Rx.NET](https://reactivex.io/) (*Reactive Extensions for .NET*)
könyvtárban, a `System.Reactive` NuGet csomaggal.

## Tartalom

### Az `IObservable<T>`/`IObserver<T>` modell

Rx.NET-ben a megfigyelhető felsorolók közös ős interfésze az
`IObservable<T>` típus — ez a klasszikus *Iterator* és *Observer*
tervezési minták kombinációjából adódó modell (lásd
[[concepts/esemalk/reaktiv-iterator-tervezesi-minta]] és
[[concepts/esemalk/reaktiv-observer-tervezesi-minta]]):

- `Observable.subscribe(Observer): Subscription`
- `Observer.onNext(item)`, `onError(error)`, `onCompleted()`
- `Subscription.unsubscribe()`

Megfigyelhető felsorolókat számos módon létrehozhatunk az `Observable`
osztály gyártó műveleteivel.

### Megfigyelhető felsorolás létrehozása: `Observable.Create<T>()`

A legelemibb módja egy megfigyelhető felsorolás előállításának az
`Observable.Create<T>()` használata. Példa egy szöveges állomány
soronkénti megfigyelhető felsorolására:

```csharp
var myObservable = Observable.Create<string>(observer =>
{
  try {
    using var reader = new StreamReader("file.txt");
    string line;
    while ((line = reader.ReadLine()) != null)  {
      observer.OnNext(line);
      // Minden sor esetén új elemet jelzünk
    }
    observer.OnCompleted();
    // Jelezzük, hogy véget ért a felsorolás
  }
  catch (Exception ex) {
    observer.OnError(ex);
    // Jelezzük, hogy hibával ért véget a felsorolás
  }
  return () => { };
  // a felsoroló felszabadítását végző tevékenység
});
```

### Segéd gyártó eljárások

Számos segéd gyártó eljárás segíti a leggyakoribb feladatok
definiálását:

- `Observable.Return()` — megadott érték egyszeri megfigyelhető
  felsorolása
- `Observable.Generate()` — megadott kiindulási állapotból, megállási
  feltétellel és iterációs szabállyal elemek felsorolása
- `Observable.Interval()` — elemek időzített felsorolása megadott
  időközönként
- `Observable.Start()` — számításigényes eljárás aszinkron végrehajtása
  és az eredmény megfigyelhető felsorolása

A felsorolt elemeket operátorokkal szűrhetjük, transzformálhatjuk,
csoportosíthatjuk — lásd [[concepts/esemalk/rx-operatorok]].

### Feliratkozás (`Subscribe`)

A `Subscribe()` eljárás kapcsolja össze a megfigyelőt (observer) a megfigyelhető felsorolóval (observable); három opcionális callback-et vehet át.

A ReactiveX (Rx.NET) mintában egy megfigyelhető felsorolóra (`IObservable<T>`) a `Subscribe()` eljárással lehet feliratkozni:

```csharp
subscription = myObservable.Subscribe(
    param => /* … */, // onNext
    ex => /* … */,    // onError
    () => /* … */     // onSuccess
);
```

- `onNext` — minden egyes kibocsátott elemre lefut
- `onError` — hiba esetén hívódik meg (kivétel a folyamban)
- `onCompleted` — a felsorolás sikeres végén fut le (a diasoron `onSuccess` néven, ami az RxJava elnevezése)

A hibakezelő és a befejezést jelző callback megadása opcionális; a legegyszerűbb feliratkozás csak az `onNext` callback-et adja meg:

```csharp
subscription = myObservable.Subscribe(
    param => Console.WriteLine(param)
);
```

## Kapocs

- [[concepts/esemalk/reaktiv-iterator-tervezesi-minta]] — az Iterator
  tervezési minta, a modell egyik forrása
- [[concepts/esemalk/reaktiv-observer-tervezesi-minta]] — az Observer
  tervezési minta, a modell másik forrása
- [[concepts/esemalk/rx-operatorok]] — a megfigyelhető adatfolyamokon
  végezhető operátorok
- [[concepts/esemalk/reaktiv-programozas-alapjai]] — a reaktív
  programozás áttekintése
- [[concepts/esemalk/csharp-async-await]] — a taszk-alapú aszinkron
  programozás, kontrasztban az `Observable`-alapú modellel
- [[concepts/esemalk/stream-alapu-fajlkezeles]] — a `StreamReader`-alapú
  fájlolvasás, amit a példa `Observable.Create` felhasznál
- [[concepts/esemalk/reaktiv-multicasting]] — multicasting és a cold/hot
  observable megkülönböztetés
- [[subjects/esemalk]] — a kurzus áttekintése
- [[concepts/esemalk/reaktiv-szenzor-pelda]] — feliratkozás egy konkrét, feldolgozott adatfolyamra
