---
tags: [concept]
sources: [elte_eva_ea00_csharp.pdf]
derivation: source
kind: definition
element: earth
updated: 2026-09-30
---

# C# osztályok és felépítésük

Egy C# osztály (`class`/`struct`) mezőkből, metódusokból, tulajdonságokból és
eseményekből épül fel, mindegyik saját láthatósággal.

## Tartalom

### Az osztály fogalma

A .NET platform és a C# programozási nyelv tisztán objektumorientált, ezért
minden érték objektum, és minden típus egy osztály.

- Az osztály lehet érték szerint (`struct`), vagy referencia szerint kezelt
  (`class`); utóbbi élettartama független a blokktól.
- Az osztály tagjai lehetnek mezők, metódusok, események, tulajdonságok
  (*property*), illetve más (beágyazott) osztályok.
  - A tulajdonság lényegében a lekérdező (`get`) és beállító (`set`)
    műveletek absztrakciója.
- Minden tagnak, és az osztálynak is jelöljük a láthatóságát (`public`,
  `private`, `protected`, `internal`); minden tag a `.` operátorral érhető el.

### Az osztály felépítése

**Általános szintaxis.**

```
<láthatóság> class/struct <osztálynév> {
    <láthatóság> <típus> <mezőnév>;                              // mező
    <láthatóság> <típus> <metódusnév>([<paraméterek>]) { <törzs> } // metódus
    <láthatóság> <típus> <tulajdonságnév> {
        [ get { <törzs> } ]
        [ set { <törzs> } ]
    }                                                             // tulajdonság
    <láthatóság> event <delegált> <eseménynév>;                   // esemény
}
```

**Mezők.** Típusból és névből állnak, és — csak referencia szerinti
osztályban — kaphatnak kezdőértéket. Ha nem inicializáljuk őket, a mezők
alapértelmezett értéket kapnak.

**Metódusok.** Visszatérési típussal rendelkeznek (ha nincs, akkor `void`),
névvel és paraméterekkel. A konstruktor neve megegyezik az osztály típusával;
a destruktort a szemétgyűjtés miatt általában nem valósítjuk meg. A
paraméterek lehetnek cím szerinti (`ref`), kimenő (`out`), alapértelmezett
vagy tetszőleges számú (`params`) paraméterek, és átadhatók név szerint is.

**Példa (C++ és C# összevetés).** C++-ban a deklaráció (`class Rational { ... };`)
és a definíció (`Rational::Rational(int n, int d) { ... }`) elválik egymástól.
C#-ban ez nem lehetséges — a deklaráció és a definíció egy helyen, a
törzsön belül történik, és az osztálytest végén nem kell pontosvessző:

```csharp
struct Rational { // elemi osztály
    private Int32 num; // mező
    private Int32 denom;
        // mindenhol jelöljük a láthatóságot
    public Rational(Int32 n, Int32 d) { // metódus
        num = n;
        denom = d;
    }
} // nem kell a végén ;
```

Az osztályok részletes felépítéséről (tulajdonságok, felsorolási típusok,
érték- és referencia szerinti osztályok, öröklődés) a kapcsolódó fogalomlapok
adnak bővebb leírást.

### Statikus osztályok és tagok

Statikus osztályok, mezők, tulajdonságok és műveletek a `static` kulcsszóval
hozhatók létre; ezek nem egy adott példányhoz, hanem magához a típushoz
tartoznak.

```csharp
static class NumClass { // statikus osztály
    private static Int32 nr = 10;
        // statikus mező 10 kezdőértékkel
    public static Int32 Nr { get { return nr; } }
        // statikus tulajdonság
    public static void Increase() { nr++; }
        // statikus metódus
}

Console.WriteLine(NumClass.Nr); // eredmény: 10
NumClass.Increase();
Console.WriteLine(NumClass.Nr); // eredmény: 11
```

A statikus tagok a típusnéven keresztül érhetők el (`NumClass.Increase()`),
nem egy létrehozott példányon keresztül — statikus osztályból egyáltalán nem
is hozható létre példány.

## Kapocs

- [[concepts/esemalk/csharp-tulajdonsagok]] — a get/set/init tulajdonságok részletes tárgyalása
- [[concepts/esemalk/csharp-ertek-referencia-osztalyok]] — elemi (struct) és referencia (class) osztályok
- [[concepts/esemalk/csharp-oroklodes]] — öröklődés, virtuális és absztrakt tagok
- [[subjects/esemalk]] — a kurzus áttekintése
- [[concepts/esemalk/csharp-tipusok]] — a `class`/`struct` mint a referencia-
  illetve érték szerinti típuskategória megvalósítása
