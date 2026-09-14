---
tags: [concept]
sources: [elte_eva_ea05_winforms_multithread.pdf]
derivation: source
updated: 2026-09-13
---

# Szemafor

A `Semaphore` osztály: könnyebb súlyú, többszörös zárolást is lehetővé tevő
szinkronizációs objektum.

## Tartalom

A `Semaphore` típusú objektum használata a `Mutex`-hez hasonló mintát követ,
a `WaitOne()` / `Release()` metóduspárral:

```csharp
public Stack<T> {
    private Semaphore sem;
    private IList<T> values;

    public Stack() {
        sem = new Semaphore();
        values = new List<T>();
    }

    public void Push(T item) {
        sem.WaitOne();
        values.Add(item);  // critical section
        sem.Release();
    }
}
```

Megadható a kezdeti és a maximum zárolások száma:

```csharp
Semaphore sem = new Semaphore(0, 3);
```

A szemafor **elnevezhető**, **könnyebb súlyú** a mutexnél, és **többszörös
zárolást** is lehetővé tesz (a megadott maximumig egyszerre több szál is
beléphet a kritikus szakaszba). Hatóköre lehet rendszer vagy alkalmazás
szintű is; jó választás **szálak közötti** szinkronizációhoz.

## Kapocs

- [[concepts/esemalk/kritikus-szakasz-kolcsonos-kizaras]] — a kritikus
  szakasz és a kölcsönös kizárás fogalma, a szinkronizációs objektumok
  összehasonlítása
- [[concepts/esemalk/csharp-mutex]] — a `Mutex` típus
- [[concepts/esemalk/csharp-monitor-lock]] — a `Monitor` osztály és a `lock`
  utasítás
