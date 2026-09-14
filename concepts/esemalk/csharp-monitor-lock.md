---
tags: [concept]
sources: [elte_eva_ea05_winforms_multithread.pdf]
derivation: source
updated: 2026-09-13
---

# Monitor és a `lock` utasítás

A `Monitor` osztály: név nélküli, a zárolt objektummal egyező hatókörű
szinkronizációs mechanizmus, amely a `lock` utasítással kényelmesen
használható.

## Tartalom

A `Monitor` osztály a `Monitor.Enter()` / `Monitor.Exit()` metóduspárral
zárolja, illetve oldja fel a kritikus szakaszt egy adott objektumra nézve:

```csharp
public Stack<T> {
    private IList<T> values;

    public Stack(){
        values = new List<T>();
    }

    public void Push(T item) {
        Monitor.Enter(values);
        values.Add(item);  // critical section
        Monitor.Exit(values);
    }
}
```

Ezzel megegyező a `lock` utasítás használatával:

```csharp
public void Push(T item) {
    lock(values)  {
        values.Add(item);  // critical section
    }
}
```

A `Monitor` **név nélküli**, hatóköre a zárolt objektummal egyezik meg
(legfeljebb alkalmazás szintű), és a `lock` utasítással kényelmesen
használható — ez a leggyakoribb módja a kölcsönös kizárás megvalósításának
egy alkalmazáson belül.

## Kapocs

- [[concepts/esemalk/kritikus-szakasz-kolcsonos-kizaras]] — a kritikus
  szakasz és a kölcsönös kizárás fogalma, a szinkronizációs objektumok
  összehasonlítása
- [[concepts/esemalk/csharp-mutex]] — a `Mutex` típus
- [[concepts/esemalk/csharp-szemafor]] — a `Semaphore` típus
