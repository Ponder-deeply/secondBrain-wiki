---
tags: [concept]
sources: [elte_eva_ea00_csharp.pdf]
derivation: source
updated: 2026-09-12
---

# C# felsorolási típus (enum)

A felsorolási típus (`enum`) értékek egymásutánja: egy névvel ellátott,
egész számokra leképezhető értékkészlet.

## Tartalom

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

- [[concepts/esemalk/csharp-ertek-referencia-osztalyok]] — érték szerinti típusok (`ValueType`), amelyeknek az enum is leszármazottja
- [[subjects/esemalk]] — a kurzus áttekintése
