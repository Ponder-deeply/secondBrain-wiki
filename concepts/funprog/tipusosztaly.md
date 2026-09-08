---
tags: [concept]
sources: []
references: [Hutton ch 3.9 / ch 8, wiki.haskell.org/Type_class]
derivation: unsourced
updated: 2026-05-18
---

# Típusosztály (type class)

**Def:** Olyan típusok kollekciója, amelyek támogatnak egy közös műveletkészletet (metódusok). Az ad-hoc polimorfizmus eszköze.

**Deklaráció:**
```haskell
class Eq a where
  (==), (/=) :: a -> a -> Bool
  x /= y = not (x == y)        -- default implementáció
  x == y = not (x /= y)
```

**Osztály-hierarchia (superclass):**
```haskell
class Eq a => Ord a where    -- Ord 'felette' Eq
  compare :: a -> a -> Ordering
  (<), (<=), (>), (>=) :: a -> a -> Bool
  ...
```

**Standard hierarchia (részlet):**
```
  Eq ─┬─ Ord
      └─ ... 
  Show, Read     -- független
  Num ─┬─ Real ─── Integral   (Int, Integer)
       └──── Fractional       (Float, Double)
  Enum, Bounded
```

**Kapcsolódó:** [[concepts/funprog/ad-hoc-polimorfizmus|ad-hoc-polimorfizmus]], [[concepts/funprog/peldanyositas|peldanyositas]], [[concepts/funprog/szabvanyos-tipusosztalyok|szabvanyos-tipusosztalyok]]
