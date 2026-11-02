---
tags: [concept]
sources: [elte_eva_ea00_csharp.pdf, elte_eva_gy01_munkafuzet.pdf]
derivation: source
kind: procedure
element: earth
updated: 2026-10-21
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
var evens = union.Where(x => x % 2 == 0);         // páros számok kiválogatása
Int32 evenCount2 =
    s1.Union(s2).Sum(x => x % 2 == 0 ? 1 : 0);    // unió, majd a páros számok számlálása
```

Bonyolultabb lekérdezések is megvalósíthatóak (pl. unió, csoportosítás,
összekapcsolás, rendezés stb.).

### Gyakorlati példa: szóstatisztika (1. gyakorlat)

A `DocumentStatistics` osztályban a szűrés és rendezés LINQ-val: `words.Where(s => s.Length > 0).ToArray()`; `SkipWhile`/`Reverse`/`String.Concat` a szavak szélén lévő nem betű karakterek levágására; `DistinctWordCount.Where(...).Where(...).OrderByDescending(p => p.Value)` *method syntax*-szal, vagy `from ... orderby ... descending select ...` *query syntax*-szal; `Sum` az összes szó számához. Lásd [[concepts/esemalk/docustat-modell-szovegstatisztika]].

## Kapocs

- [[concepts/esemalk/csharp-tipusok]] — a lekérdezés eredménye gyűjteménytípus
  (`IEnumerable`)
- [[concepts/esemalk/csharp-nyelv-jellemzoi]] — a LINQ metódusok a `System.Linq`
  névtérben érhetőek el
- [[subjects/esemalk]] — a kurzus áttekintése
