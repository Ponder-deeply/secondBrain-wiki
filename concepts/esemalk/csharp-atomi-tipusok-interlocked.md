---
tags: [concept]
sources: [elte_eva_ea05_winforms_multithread.pdf]
derivation: source
kind: pitfall
element: earth
updated: 2026-09-25
---

# Atomi típusok, `Interlocked` és szálbiztos gyűjtemények

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

### Szálbiztos gyűjtemények

A `System.Collections.Concurrent` névtér gyűjteményei: metódusaikban maguk
valósítják meg a kölcsönös kizárást.

A **szálbiztos**, metódusaikban kölcsönös kizárást megvalósító gyűjtemények a
.NET Standard Library részét képezik, a `System.Collections.Concurrent`
névtérben:

- `ConcurrentBag`
- `ConcurrentDictionary`
- `ConcurrentQueue`
- `ConcurrentStack`
- `BlockingCollection` (gyártó-fogyasztó minta megvalósításához)

Műveleteik szignatúrája néhol eltér a nem szálbiztos megfelelőikétől, de a
szokásos gyűjtemény-interfészeket megvalósítják, például:

```csharp
IDictionary<String, Object> dictionary =
    new ConcurrentDictionary<String, Object>();
```

A szálbiztos gyűjtemények használatával elkerülhető, hogy a fejlesztőnek
saját maga kelljen a kritikus szakaszt szinkronizációs objektummal (Mutex,
Szemafor, Monitor) védenie a gyűjtemény minden egyes elérésekor.

## Kapocs

- [[concepts/esemalk/kritikus-szakasz-kolcsonos-kizaras]] — a kritikus
  szakasz és a kölcsönös kizárás fogalma
