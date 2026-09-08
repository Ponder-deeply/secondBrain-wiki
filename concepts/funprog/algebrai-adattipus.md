---
tags: [concept]
sources: []
references: [Hutton ch 8, "LYAH \"Making Our Own Types\""]
derivation: unsourced
updated: 2026-05-18
---

# Algebrai adattípus (ADT)

**Def:** `data` kulcsszóval definiált új típus, **konstruktorok diszjunkt uniójaként**. Mindegyik konstruktor 0+ argumentumot vesz.

**Példák:**
```haskell
data Bool = False | True                           -- enumeráció
data Maybe a = Nothing | Just a                    -- paraméteres
data Either a b = Left a | Right b
data Shape = Circle Double | Rect Double Double    -- sum + product
data Tree a = Leaf | Node (Tree a) a (Tree a)      -- rekurzív

data Point = Point Double Double                   -- konstruktor és típus
                                                    -- ugyanaz a név OK
```

**„Sum of products":** `|` = összeg (választás), egymás melletti argumentumok = szorzat (mind kell).

**Konstruktor mint függvény:** `Just :: a -> Maybe a`. Lásd [[concepts/funprog/adatkonstruktor-mint-fuggveny|adatkonstruktor-mint-fuggveny]].

**Mintaillesztés:**
```haskell
area :: Shape -> Double
area (Circle r)   = pi * r^2
area (Rect w h)   = w * h
```

**Rekorddal:**
```haskell
data Person = Person { name :: String, age :: Int }
-- automatikus mezőfüggvények: name :: Person -> String
```

**Kapcsolódó:** [[concepts/funprog/adatkonstruktor-mint-fuggveny|adatkonstruktor-mint-fuggveny]], [[concepts/funprog/rekurziv-adattipus|rekurziv-adattipus]], [[concepts/funprog/tipusszinonima|tipusszinonima]], [[concepts/funprog/newtype|newtype]]
