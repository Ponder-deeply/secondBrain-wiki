---
tags: [concept]
sources: []
references: [Hutton ch 3.6, LYAH]
derivation: unsourced
updated: 2026-05-18
---

# Parciális alkalmazás

**Def:** Curry-zett függvényt kevesebb argumentummal hívunk, mint a teljes argumentumlista — eredménye új függvény, ami a maradék argumentumokat várja.

**Példa:**
```haskell
add :: Int -> Int -> Int
add x y = x + y

inc :: Int -> Int
inc = add 1            -- 1 + _

map (add 10) [1,2,3]   -- ⇒ [11,12,13]
```

**Operátor szekcióval:**
```haskell
(+1)   :: Num a => a -> a    -- bal szekció
(10-)  :: Num a => a -> a    -- jobb szekció
(>0)   :: Ord a => a -> Bool
```

**Kvíz csapda:** Parciális alkalmazás != parciális függvény. Az első normál, hasznos; a másik [[concepts/funprog/totalis-vs-parcialis|⊥]]-t adhat.

**Kapcsolódó:** [[concepts/funprog/currying|currying]], [[concepts/funprog/operator-szekcio|operator-szekcio]], [[concepts/funprog/totalis-vs-parcialis|totalis-vs-parcialis]]
