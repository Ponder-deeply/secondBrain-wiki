---
tags: [concept, esemalk/csharp-nyelvi-alapok]
sources: [elte_eva_ea00_csharp.pdf]
derivation: source
updated: 2026-09-12
---

# Nyelvbe ágyazott lekérdezések (LINQ)

A *nyelvbe ágyazott lekérdezések* (*Language Integrated Query*, LINQ) célja,
hogy objektumorientált környezetben, a relációs adatbázisok SQL nyelvéhez
hasonlóan lehessen lekérdező utasításokat megfogalmazni gyűjteményeken.

## Tartalom

**Lekérdezés-szintaxis.** Az SQL-hez hasonló, deklaratív forma:

```csharp
List<Person> pList = new List<Person> { … };
var pQuery = from p in pList     // honnan
             where p.Age >= 18   // feltétel
             select p.Name;      // mit
```

Az eredmény egy gyűjtemény (`IEnumerable`), és a kifejezés csak akkor
értékelődik ki, amikor azt bejárjuk (*késleltetett végrehajtás*).

**Metódus-szintaxis.** A lekérdezés-szintaxis mögött $\lambda$-kifejezésekkel
dolgozó metódusok állnak, amelyek bármilyen gyűjteményre futtathatóak
(akár egymás után láncolva is):

```csharp
var pQuery = pList                        // honnan
             .Where(p => p.Age >= 18)      // feltétel
             .Select(p => p.Name);         // mit
```

A metódusok úgynevezett *bővítő metódusként* (*extension method*) vannak
definiálva, amelyek a `System.Linq` névtérben érhetőek el. További példák
tömbökön (`Sum`, `Union`):

```csharp
Int32[] s1 = { 1, 2, 3 }, s2 = { 2, 3, 4 };
Int32 sum = s1.Sum();                             // számok összege
Int32 evenCount = s1.Sum(x => x % 2 == 0 ? 1 : 0);
    // megadjuk, mit összegezzen, így a páros számok számlálása lesz
var union = s1.Union(s2);
    // két gyűjtemény uniója: { 1, 2, 3, 4 }
var evens = union.Select(x => x % 2 == 0);        // páros számok kiválogatása
Int32 evenCount2 =
    s1.Union(s2).Sum(x => x % 2 == 0 ? 1 : 0);    // unió, majd a páros számok számlálása
```

Bonyolultabb lekérdezések is megvalósíthatóak (pl. unió, csoportosítás,
összekapcsolás, rendezés stb.).

## Kapocs

- [[concepts/esemalk/csharp-tipusok]] — a lekérdezés eredménye gyűjteménytípus
  (`IEnumerable`)
- [[concepts/esemalk/csharp-nevterek]] — a LINQ metódusok a `System.Linq`
  névtérben érhetőek el
- [[subjects/esemalk]] — a kurzus áttekintése
