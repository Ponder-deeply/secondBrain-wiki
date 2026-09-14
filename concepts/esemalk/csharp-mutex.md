---
tags: [concept]
sources: [elte_eva_ea05_winforms_multithread.pdf]
derivation: source
updated: 2026-09-13
---

# Mutex

A `Mutex` osztály: elnevezhető, rendszer szintű hatókörű szinkronizációs
objektum a kritikus szakaszok védelmére.

## Tartalom

A `Mutex` típusú objektum a `WaitOne()` / `ReleaseMutex()` metóduspárral
zárolja, illetve oldja fel a kritikus szakaszt:

```csharp
public Stack<T> {
    private Mutex mutex;
    private IList<T> values;

    public Stack() {
        mutex = new Mutex();
        values = new List<T>();
    }

    public void Push(T item) {
        mutex.WaitOne();
        values.Add(item);  // critical section
        mutex.ReleaseMutex();
    }
}
```

Várakozhatunk megadott ideig vagy időpontig is: `mutex.WaitOne(Int32)` és
`mutex.WaitOne(TimeSpan)`.

A `Mutex` **elnevezhető** és **rendszer szintű hatókörrel** rendelkezik, ezért
jó választás **folyamatok (alkalmazások) közötti** szinkronizációhoz — nem
csak egy alkalmazáson belüli szálak, hanem különböző folyamatok is
szinkronizálhatók vele.

## Kapocs

- [[concepts/esemalk/kritikus-szakasz-kolcsonos-kizaras]] — a kritikus
  szakasz és a kölcsönös kizárás fogalma, a szinkronizációs objektumok
  összehasonlítása
- [[concepts/esemalk/csharp-szemafor]] — a `Semaphore` típus
- [[concepts/esemalk/csharp-monitor-lock]] — a `Monitor` osztály és a `lock`
  utasítás
