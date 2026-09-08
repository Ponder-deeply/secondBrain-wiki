---
tags: [concept]
sources: []
references: [Hutton ch 3.8]
derivation: unsourced
updated: 2026-05-18
---

# Típusszinonima (`type`)

**Def:** Meglévő típushoz **alias** — nem új típus, csak rövidítés. Csere-érték a fordítónál.

**Példa:**
```haskell
type String   = [Char]
type Name     = String
type Pair a   = (a, a)
type Assoc k v = [(k, v)]
```

**Kvíz csapda:** `type` **nem** új típus — `Name` és `String` ekvivalensek a fordító számára, nem ad típusvédelmet. Ehhez `newtype` kell.

**Kapcsolódó:** [[concepts/funprog/newtype|newtype]], [[concepts/funprog/algebrai-adattipus|algebrai-adattipus]]
