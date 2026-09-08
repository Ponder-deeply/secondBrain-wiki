---
tags: [concept]
sources: []
references: [Hutton ch 3.6, "LYAH \"Curried functions\""]
derivation: unsourced
updated: 2026-05-18
---

# Currying (Curry-féle módszer)

**Def:** Több-argumentumos függvényt egyargumentumosok láncává alakítunk. `a -> b -> c` jelentése `a -> (b -> c)` — jobbra zárójelezett.

**Haskell:** **minden függvény eleve curry-zett**.

**Példa:**
```haskell
add :: Int -> Int -> Int
add x y = x + y

add 3 4        -- ⇒ 7
(add 3) 4      -- ugyanaz (alkalmazás balra zár)
add3 = add 3   -- parciális alkalmazás
add3 10        -- ⇒ 13
```

**Tuple-os ekvivalens:**
```haskell
addT :: (Int, Int) -> Int
addT (x, y) = x + y

curry   :: ((a,b) -> c) -> a -> b -> c
uncurry :: (a -> b -> c) -> (a,b) -> c
```

**Kvíz csapda:** `->` **jobbra**, alkalmazás **balra** zárójelez. `f x y` = `(f x) y`.

**Kapcsolódó:** [[concepts/funprog/parcialis-alkalmazas|parcialis-alkalmazas]], [[concepts/funprog/lambda|lambda]], [[concepts/funprog/magasabb-rendu-fuggveny|magasabb-rendu-fuggveny]]
