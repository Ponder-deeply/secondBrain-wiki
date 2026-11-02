---
tags: [concept]
sources: [elte_eva_ea05_winforms_multithread.pdf]
derivation: source
kind: comparison
element: water
updated: 2026-09-30
---

# Kritikus szakasz, kölcsönös kizárás és szinkronizációs objektumok

A közös erőforrások több szál általi elérésének problémája, és a
szinkronizációs objektumok (Mutex, Szemafor, Monitor) áttekintő
összehasonlítása, majd a `Mutex`, a `Semaphore` és a `Monitor`/`lock` használata.

## Tartalom

A gyerekszál nem tud egy végeredményt közvetlenül visszaadni a szülőszálnak
— a szálak közötti adatkommunikáció megosztott erőforrások (jellemzően
memória, közös változók) segítségével történhet, méghozzá nem csak a
gyerekszál tevékenységének végén, hanem közben is, és mindkét irányban.

A közös erőforrások kezelését a program **kritikus szakaszának** (*critical
section*) nevezzük. Azonos erőforrásra vonatkozó kritikus szakaszok
párhuzamos végrehajtása — kivéve, ha minden művelet csak olvasni próbálja az
erőforrást — hibát, nem várt futásidejű viselkedést okozhat.

A szálakat a közös erőforrások használatakor **szinkronizálni kell**,
**kölcsönös kizárás** (*mutual exclusion*) segítségével garantálva, hogy
egyszerre csak egy kritikus szakasz kerül végrehajtásra.

### Szinkronizációs objektumok összehasonlítása

| Mutex | Szemafor | Monitor |
|---|---|---|
| elnevezhető | elnevezhető | név nélküli |
| rendszer szintű hatókör | könnyebb súlyú | zárolt objektummal egyező hatókör (legfeljebb alkalmazás szintű) |
| jó választás folyamatok (alkalmazások) közötti szinkronizációhoz | többszörös zárolás lehetősége; rendszer / alkalmazás szintű hatókör; jó választás szálak közötti szinkronizációhoz | `lock` utasítással kényelmesen használható |

### `Mutex`

A `Mutex` osztály: elnevezhető, rendszer szintű hatókörű szinkronizációs
objektum a kritikus szakaszok védelmére.

A `Mutex` típusú objektum a `WaitOne()` / `ReleaseMutex()` metóduspárral
zárolja, illetve oldja fel a kritikus szakaszt:

```csharp
public class Stack<T> {
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

### Szemafor (`Semaphore`)

A `Semaphore` osztály: könnyebb súlyú, többszörös zárolást is lehetővé tevő
szinkronizációs objektum.

A `Semaphore` típusú objektum használata a `Mutex`-hez hasonló mintát követ,
a `WaitOne()` / `Release()` metóduspárral:

```csharp
public class Stack<T> {
    private Semaphore sem;
    private IList<T> values;

    public Stack() {
        sem = new Semaphore(1, 1);
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

### Monitor és a `lock` utasítás

A `Monitor` osztály: név nélküli, a zárolt objektummal egyező hatókörű
szinkronizációs mechanizmus, amely a `lock` utasítással kényelmesen
használható.

A `Monitor` osztály a `Monitor.Enter()` / `Monitor.Exit()` metóduspárral
zárolja, illetve oldja fel a kritikus szakaszt egy adott objektumra nézve:

```csharp
public class Stack<T> {
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

- [[concepts/esemalk/csharp-szal-letrehozasa-kezelese]] — miért nem tudja a
  gyerekszál egyszerűen visszaadni az eredményét a szülőszálnak
- [[concepts/esemalk/csharp-atomi-tipusok-interlocked]] — a kölcsönös kizárást
  a gyűjtemény metódusaiban maga megvalósító, szálbiztos gyűjtemények
