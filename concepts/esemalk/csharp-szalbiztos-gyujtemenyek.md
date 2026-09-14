---
tags: [concept]
sources: [elte_eva_ea05_winforms_multithread.pdf]
derivation: source
updated: 2026-09-13
---

# Szálbiztos gyűjtemények

A `System.Collections.Concurrent` névtér gyűjteményei: metódusaikban maguk
valósítják meg a kölcsönös kizárást.

## Tartalom

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
- [[concepts/esemalk/csharp-monitor-lock]] — a `Monitor`/`lock` alapú kézi
  szinkronizáció, amit a szálbiztos gyűjtemények kiváltanak
