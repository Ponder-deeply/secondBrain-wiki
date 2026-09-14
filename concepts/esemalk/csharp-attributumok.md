---
tags: [concept]
sources: [elte_eva_ea00_csharp.pdf]
derivation: source
updated: 2026-09-12
---

# C# attribútumok

Az *attribútumok* (`attribute`) olyan speciális osztályok, amelyek elsősorban
a virtuális gépnek (CLR) szolgálnak információkat (úgynevezett *metaadat*okat),
kiegészítve a kód deklarációit.

## Tartalom

Az attribútumok segítségre lehetnek a kód kezelésében, *reflexió*
segítségével kezelhetőek (lekérdezhetők futásidőben). A deklaráció elé,
szögletes zárójelben adjuk meg őket, alkalmazhatóak osztályra, metódusra,
paraméterre és más nyelvi elemekre is.

```csharp
[Serializable] // attribútumok
[ComVisible]
class SomeClass { ... }
```

## Kapocs

- [[concepts/esemalk/csharp-osztalyok]] — az attribútum maga is speciális
  osztály, és osztálydeklarációkra alkalmazható
- [[subjects/esemalk]] — a kurzus áttekintése
