---
tags: [concept]
sources: []
references: [Hutton ch 8, "LYAH \"Making Our Own Typeclasses\""]
derivation: unsourced
updated: 2026-05-18
---

# Példányosítás (instance)

**Def:** Adott típus számára az osztály metódusainak konkrét implementációja.

**Szintaxis:**
```haskell
data Color = Red | Green | Blue

instance Eq Color where
  Red   == Red   = True
  Green == Green = True
  Blue  == Blue  = True
  _     == _     = False

instance Show Color where
  show Red   = "piros"
  show Green = "zöld"
  show Blue  = "kék"
```

**`deriving` — automatikus levezetés:**
```haskell
data Color = Red | Green | Blue
  deriving (Eq, Ord, Show, Read, Enum, Bounded)
```

**Kvíz csapda:** `class` = osztály-**deklaráció** (metódus-aláírások). `instance` = adott típus **implementációja**. Egy osztály több instance-szal, de adott (típus, osztály) párra csak **egy** instance.

**Kapcsolódó:** [[concepts/funprog/tipusosztaly|tipusosztaly]], [[concepts/funprog/algebrai-adattipus|algebrai-adattipus]]
