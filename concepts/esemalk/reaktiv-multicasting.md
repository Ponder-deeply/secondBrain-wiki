---
tags: [concept, esemalk/reaktiv-programozas]
sources: [elte_eva_ea11_reactive.pdf]
derivation: source
updated: 2026-09-13
---

# Multicasting és hideg/meleg megfigyelhető felsorolók

Alapesetben minden feliratkozás újra végrehajtja a megfigyelhető felsoroló inicializálási logikáját; a `Publish()`/`Connect()`/`RefCount()` operátorokkal ez egyetlen, megosztott (multicast) felsorolássá alakítható.

## Tartalom

### Az alapeset: minden feliratkozás önálló felsorolást indít

Alapértelmezetten egy új feliratkozáskor a megfigyelhető felsoroló inicializálási logikája újra végrehajtódik — ha például egy `sensorStream`-re két helyen iratkozunk fel, két független szenzor-generálás indul.

### `Publish()` és `Connect()`

A *multicast* megoldáshoz a megfigyelhető felsoroló elindítását a `Publish()` eljárással manuálissá alakítjuk:

```csharp
var sensorStream = Observable
    .Interval(TimeSpan.FromMilliseconds(250))
    //...
    .Publish(); // multicast

var sub1 = sensorStream.Subscribe(/* ... */);
var sub2 = sensorStream.Subscribe(/* ... */);

sensorStream.Connect(); // felsorolás indítása
```

Így mindkét feliratkozó ugyanazokat a kibocsátott elemeket kapja, és a felsorolás csak a `Connect()` hívásakor indul el.

### `RefCount()` — automatikus indítás és felszabadítás

Az elindítást és a felszabadítást automatizálhatjuk a `RefCount()` használatával: ez egy hivatkozás- (referencia-)számlálást végez a háttérben, és az első feliratkozáskor indítja a felsorolást, az utolsó feliratkozás felszabadításakor pedig a felsorolót is felszabadítja:

```csharp
var sensorStream = Observable
    .Interval(TimeSpan.FromMilliseconds(250))
    //...
    .Publish().RefCount(); // multicast

var sub1 = sensorStream.Subscribe(/* ... */);
// az első feliratkozással indul a felsorolás
var sub2 = sensorStream.Subscribe(/* ... */);
```

### Cold vs. hot observable

A ReactiveX-ben a megfigyelhető felsorolókat (*observable*) két kategóriára oszthatjuk:

- **Cold observable**: a feliratkozás (`Subscribe()`) hozza létre a gyártót, amely az elemeket felsorolja. Többszörös feliratkozás több gyártót hoz létre.
- **Hot observable**: a feliratkozás nem hoz létre gyártót, hanem egy azon kívül létező objektumot figyel meg és sorol fel. Többszörös feliratkozás nem duplikálja a gyártót.

Ebben a terminológiában a multicast használata (`Publish()`) a cold observable-ből egy hot observable-t készít.

## Kapocs

- [[concepts/esemalk/reaktiv-szenzor-pelda]] — a `sensorStream` mint alapesetben cold observable
- [[concepts/esemalk/reaktiv-feliratkozas]] — a `Subscribe()` eljárás alapjai
- [[concepts/esemalk/rx-observable-alapok]] — az `IObservable<T>` modell, amelyre a cold/hot megkülönböztetés vonatkozik
- [[subjects/esemalk]] — a kurzus áttekintése
