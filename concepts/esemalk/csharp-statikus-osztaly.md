---
tags: [concept]
sources: [elte_eva_ea00_csharp.pdf]
derivation: source
updated: 2026-09-12
---

# C# statikus osztályok

Statikus osztályok, mezők, tulajdonságok és műveletek a `static` kulcsszóval
hozhatók létre; ezek nem egy adott példányhoz, hanem magához a típushoz
tartoznak.

## Tartalom

```csharp
static class NumClass { // statikus osztály
    private static Int32 nr = 10;
        // statikus mező 10 kezdőértékkel
    public static Int32 Nr { get { return nr; } }
        // statikus tulajdonság
    public static void Increase() { nr++; }
        // statikus metódus
}

Console.WriteLine(NumClass.Number) // eredmény: 10
NumClass.Increase();
Console.WriteLine(NumClass.Number) // eredmény: 11
```

A statikus tagok a típusnéven keresztül érhetők el (`NumClass.Increase()`),
nem egy létrehozott példányon keresztül — statikus osztályból egyáltalán nem
is hozható létre példány.

## Kapocs

- [[concepts/esemalk/csharp-osztaly-szerkezete]] — az osztályok általános (nem statikus) szintaxisa
- [[concepts/esemalk/csharp-tulajdonsagok]] — a statikus tulajdonság ugyanazon get/set logikával működik
- [[subjects/esemalk]] — a kurzus áttekintése
