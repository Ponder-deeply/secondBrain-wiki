---
tags: [concept]
sources: [elte_eva_ea11_reactive.pdf]
derivation: source
updated: 2026-09-13
---

# Feliratkozás megfigyelhető felsorolóra (Subscribe)

A `Subscribe()` eljárás kapcsolja össze a megfigyelőt (observer) a megfigyelhető felsorolóval (observable); három opcionális callback-et vehet át.

## Tartalom

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
- `onSuccess` (`onCompleted`) — a felsorolás sikeres végén fut le

A hibakezelő és a befejezést jelző callback megadása opcionális; a legegyszerűbb feliratkozás csak az `onNext` callback-et adja meg:

```csharp
subscription = myObservable.Subscribe(
    param => Console.WriteLine(param);
);
```

## Kapocs

- [[subjects/esemalk]] — a kurzus áttekintése
- [[concepts/esemalk/reaktiv-szenzor-pelda]] — feliratkozás egy konkrét, feldolgozott adatfolyamra
- [[concepts/esemalk/reaktiv-multicasting]] — több feliratkozás ugyanarra a megfigyelhető felsorolóra
- [[concepts/esemalk/rx-observable-alapok]] — az `IObservable<T>`/`IObserver<T>` modell, amelyre a `Subscribe()` épül
