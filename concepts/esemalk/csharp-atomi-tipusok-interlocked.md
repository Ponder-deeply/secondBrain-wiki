---
tags: [concept]
sources: [elte_eva_ea05_winforms_multithread.pdf]
derivation: source
updated: 2026-09-13
---

# Atomi típusok és az `Interlocked` osztály

Mely alaptípusok olvasása/írása atomi C#-ban, és hogyan tehetők atomivá az
összetettebb műveletek (pl. növelés) az `Interlocked` osztály segítségével.

## Tartalom

**Atomi adattípusok** (olvasás és írás): `bool`, `char`, `byte`, `sbyte`,
`short`, `ushort`, `uint`, `int`, `float`, és a referencia szerinti típusok.

**Nem atomi adattípusok**: `long`, `ulong`, `double`, `decimal`, stb. Ezekre
nincs garancia az atomi olvasásra, írásra, módosításra.

Komplexebb műveletek — például egy hozzáadás, ami egy olvasásból és egy
írásból áll — már az atomi adattípusokra sem atomiak. Ezen elemi műveletek
atomi módon az `Interlocked` osztály használatával érhetők el:

```csharp
int x = 41;
Interlocked.Increment(ref x);   // increment x

SomeType y = new SomeType();
SomeType z = new SomeType();
// ...
Interlocked.Exchange(ref y, z); // replace y with z
```

Az `Interlocked` osztály tehát megkerüli, hogy egy egyszerű növelő vagy
csere műveletért teljes szinkronizációs objektumot (Mutex, Szemafor,
Monitor) kelljen bevonni.

## Kapocs

- [[concepts/esemalk/kritikus-szakasz-kolcsonos-kizaras]] — a kritikus
  szakasz és a kölcsönös kizárás fogalma
- [[concepts/esemalk/csharp-monitor-lock]] — a `Monitor`/`lock` alapú
  szinkronizáció összetettebb kritikus szakaszokhoz
