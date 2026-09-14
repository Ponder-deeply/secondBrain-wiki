---
tags: [concept]
sources: [elte_eva_ea11_reactive.pdf]
derivation: source
updated: 2026-09-13
---

# Observer tervezési minta

A GoF egyik tervezési mintája, amely egy megfigyelt objektum (`Subject`)
állapotváltozásáról egy vagy több megfigyelő (`Observer`) objektumot
értesít, anélkül hogy a `Subject` a megfigyelők konkrét típusát ismerné.

## Tartalom

### Szerkezet

- `Subject` — nyilvántartja a megfigyelőket (`observers`),
  `Attach(Observer)`/`Detach(Observer)` metódusokkal regisztrálja/törli
  őket, és `Notify()`-jal minden megfigyelőt értesít
  (`for all o in observers { o->Update() }`)
- `ConcreteSubject` — a konkrét megfigyelt állapot (`subjectState`),
  `GetState()`/`SetState()`
- `Observer` — az értesítés interfésze: `Update()`
- `ConcreteObserver` — a konkrét megfigyelő, amely `Update()`-ben lekéri
  az állapotot a `subject`-től (`observerState = subject->GetState()`)

### C#-beli megvalósítás

A C# saját eseménykezelési mechanizmusa (események és eseménykezelők) az
*Observer* tervezési mintát valósítja meg: az eseményt kiváltó objektum a
`Subject`, a feliratkozott eseménykezelők az `Observer` szerepét töltik be.

Az *Iterator* és az *Observer* minta kombinálásából adódik a
megfigyelhető felsorolók (*observable sequences*) modellje: egy
`Observable` `subscribe(Observer)`-en keresztül egy `Subscription`-t ad
vissza, az `Observer` pedig `onNext(item)`, `onError(error)` és
`onCompleted()` metódusokkal értesül az adatfolyam eseményeiről, a
`Subscription.unsubscribe()` pedig a leiratkozásra szolgál. Ez a modell a
ReactiveX könyvtár alapja, lásd
[[concepts/esemalk/rx-observable-alapok]].

## Kapocs

- [[concepts/esemalk/reaktiv-iterator-tervezesi-minta]] — a másik GoF
  minta, amellyel kombinálva a megfigyelhető felsorolók adódnak
- [[concepts/esemalk/rx-observable-alapok]] — az `IObservable<T>`/
  `IObserver<T>` modell, amely az Iterator és az Observer minta
  kombinációja
- [[concepts/esemalk/esemeny-letrehozasa-kivaltasa]] — saját esemény
  létrehozása és kiváltása C#-ban, a C#-os Observer-megvalósítás
- [[concepts/esemalk/reaktiv-programozas-alapjai]] — a reaktív
  programozás áttekintése
