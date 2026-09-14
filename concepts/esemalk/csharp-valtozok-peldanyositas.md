---
tags: [concept]
sources: [elte_eva_ea00_csharp.pdf]
derivation: source
updated: 2026-09-12
---

# Változók és példányosítás (C#)

Változókat bármely (nem névtér) blokkon belül létrehozhatunk a programkódban
típus, név és kezdőérték megadásával.

## Tartalom

- Pl.: `Int32 myInt = 10;`
- Felhasználás előtt mindenképpen kezdőértéket kell kapnia a változónak.
- Összetett (referencia-) típusok esetén a `new` operátort használjuk, pl.:
  `Stack<Int32> s = new Stack<Int32>();`
- A típusnév feloldható fordítási időben is a `var` kulcsszóval, pl.:
  `var myInt = 10;`
- Típusok futási időben is feloldhatóak (`dynamic`), és manipulálhatóak
  (pl. `ExpandoObject`).
- Konstansokat a `const` kulcsszóval, konstruktorban értékül adható mezőket a
  `readonly` kulcsszóval adhatunk meg.

## Kapocs

- [[concepts/esemalk/csharp-tipusok]] — a típuskategóriák, amelyekre a
  változódeklaráció épül
- [[concepts/esemalk/csharp-osztalyok]] — a `new` operátorral példányosított
  osztályok
