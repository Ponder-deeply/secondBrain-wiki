---
tags: [concept, esemalk/csharp-nyelvi-alapok]
sources: [elte_eva_ea00_csharp.pdf]
derivation: source
updated: 2026-09-12
---

# C# osztályok szerkezete

Egy C# osztály (`class`/`struct`) mezőkből, metódusokból, tulajdonságokból és
eseményekből épül fel, mindegyik saját láthatósággal.

## Tartalom

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

## Kapocs

- [[concepts/esemalk/csharp-osztalyok]] — az osztályok rövid, bevezető szintű áttekintése
- [[concepts/esemalk/csharp-tulajdonsagok]] — a get/set/init tulajdonságok részletes tárgyalása
- [[concepts/esemalk/csharp-ertek-referencia-osztalyok]] — elemi (struct) és referencia (class) osztályok
- [[concepts/esemalk/csharp-oroklodes]] — öröklődés, virtuális és absztrakt tagok
- [[subjects/esemalk]] — a kurzus áttekintése
