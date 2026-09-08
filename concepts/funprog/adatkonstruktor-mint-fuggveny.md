---
tags: [concept]
sources: []
references: [Hutton ch 8, LYAH]
derivation: unsourced
updated: 2026-05-18
---

# Adatkonstruktor mint függvény

**Def:** Egy ADT konstruktora **függvény**, amelyik a mezőértékekből épít értéket. Típusa a mezőtípusokból a típus-eredménybe vezet.

**Példa:**
```haskell
data SomeDays a b = Monday a | Saturday a b

Monday   :: a -> SomeDays a b
Saturday :: a -> b -> SomeDays a b
```

**Kvíz csapda — adatkonstruktor típusa konkretizálva:**
`data SomeDays a b = Monday a | Saturday a b`. `Saturday` típusa:
- ✓ `Int -> Char -> SomeDays Int Char`
- ✓ `String -> Int -> SomeDays String Int` (de a kvíz szerint `SomeDays Int String` — **HIBÁS**!)
- ✓ `Char -> Char -> SomeDays Char Char`
- ✓ `Int -> Bool -> SomeDays Int Bool`

Vagyis a `Saturday` aláírásban az első argumentum az `a`-t, második a `b`-t rögzíti, és **ugyanezen sorrend** áll az eredménytípusban. Ha az eredmény `SomeDays Int String`, akkor `a = Int, b = String`, tehát az argumentumok: `Int -> String -> SomeDays Int String`. **`String -> Int -> SomeDays Int String` nem helyes!**

**Általános módszer:** unifikáld az eredmény-típusargumentumokat az `a`, `b` paraméterekkel, aztán helyettesítsd be az argumentumtípusokat.

**Kapcsolódó:** [[concepts/funprog/algebrai-adattipus|algebrai-adattipus]], [[concepts/funprog/tipus-szignatura|tipus-szignatura]]
