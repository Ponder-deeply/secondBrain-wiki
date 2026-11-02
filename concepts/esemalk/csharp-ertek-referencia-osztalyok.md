---
tags: [concept]
sources: [elte_eva_ea00_csharp.pdf]
derivation: source
kind: comparison
element: earth
updated: 2026-09-25
---

# C# elemi és referencia osztályok (struct, class, enum)

A C# két fő osztálykategóriát különböztet meg: az elemi osztályt (`struct`,
érték szerint kezelve) és a referencia osztályt (`class`, cím szerint
kezelve).

## Tartalom

**Elemi osztály (`struct`).** Egyszerűsített osztály, amely:

- mindig érték szerint van kezelve, ezért különleges bánásmódot igényel,
- nem szerepelhet öröklődésben, de implementálhat interfészt,
- alapértelmezett konstruktora mindig létezik, amely alapértelmezett
  értékekre inicializálja a változóit.

```csharp
struct Rational { /* ... */ } // elemi osztály

Rational r = new Rational(10, 5);
Rational t = r;              // r érték szerint másolódik
t.Denominator = 10;          // itt r.Denominator == 5
```

**Referencia osztály (`class`).** A teljes értékű osztály, amely
öröklődésben is szerepelhet:

- csak egy őse lehet, de bármennyi interfészt megvalósíthat,
- mezőit lehet közvetlenül inicializálni,
- az öröklődés miatt lehet absztrakt osztály, és szerepelhetnek benne
  absztrakt és virtuális elemek.

```csharp
class Rational { /* ... */ } // referencia osztály

Rational r = new Rational(10, 5);
Rational t = r;              // r cím szerint másolódik
t.Denominator = 10;          // itt r.Denominator == 10
```

A két példa (`struct` vs. `class` `Rational`) ugyanazzal a szintaxissal és
tulajdonsággal (lásd [[concepts/esemalk/csharp-tulajdonsagok]]) épül fel — a
különbség kizárólag a másolási szemantikában (érték szerint vs. cím szerint)
jelentkezik az értékadáskor.

### Felsorolási típus (`enum`)

A felsorolási típus (`enum`) értékek egymásutánja: egy névvel ellátott,
egész számokra leképezhető értékkészlet.

**Definíció és hivatkozás.**

```csharp
enum Day { Monday, Tuesday, Wednesday, /* ... */ }
```

A hivatkozás a típusnéven át történik:

```csharp
Day day = Day.Monday;
// ...
if (day == Day.Wednesday) { /* ... */ }
```

**Egész értékek.** Az enum értékek egész számoknak feleltethetők meg,
alapértelmezésben 0-tól sorszámozva, de ez felüldefiniálható:

```csharp
enum Day { Monday = 1, Wednesday = 3, /* ... */ }
```

**Az `enum` mint osztály.** Az `enum` maga is egy osztály a `System`
névtérben, a `ValueType`-ból származik:

```csharp
public abstract class Enum : ValueType, /* ... */
```

Ebből következik, hogy — a `ValueType` leszármazottjaként — érték szerint
viselkedik, hasonlóan az elemi osztályokhoz (`struct`).

## Kapocs

- [[concepts/esemalk/csharp-osztaly-szerkezete]] — az osztályok közös szintaxisa (mező, metódus, tulajdonság, esemény)
- [[concepts/esemalk/csharp-tulajdonsagok]] — a `Rational` példában használt tulajdonság
- [[concepts/esemalk/csharp-nullable-tipusok]] — az érték és referencia szerinti típusok null-képessége
- [[concepts/esemalk/csharp-oroklodes]] — a referencia osztályok öröklődési képessége
- [[subjects/esemalk]] — a kurzus áttekintése
