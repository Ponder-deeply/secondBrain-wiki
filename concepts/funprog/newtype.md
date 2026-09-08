---
tags: [concept]
sources: []
references: [Hutton, wiki.haskell.org/Newtype]
derivation: unsourced
updated: 2026-05-18
---

# `newtype`

**Def:** Új típus, **pontosan egy** konstruktorral, **pontosan egy** mezővel. `data`-hoz hasonló szintaxis, de fordítási időben nincs runtime overhead.

**Szintaxis:**
```haskell
newtype Age = Age Int
newtype Wrapper a = Wrapper { unwrap :: a }
```

**Mikor:** Típusbiztonság új névvel, **futás közbeni költség nélkül**:
```haskell
newtype Meter = Meter Double
newtype Foot  = Foot  Double
-- Meter és Foot összeadás már típushiba!
```

**Összevetés:**
| | `type` | `newtype` | `data` |
|---|---|---|---|
| új típus? | nem | igen | igen |
| futásidejű burok | – | nincs | van |
| konstruktor | – | 1, 1 mező | tetszőleges |

**Kapcsolódó:** [[concepts/funprog/tipusszinonima|tipusszinonima]], [[concepts/funprog/algebrai-adattipus|algebrai-adattipus]]
