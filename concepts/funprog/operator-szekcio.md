---
tags: [concept]
sources: []
references: [Hutton ch 4.5, LYAH]
derivation: unsourced
updated: 2026-05-18
---

# Operátor szekció

**Def:** Bináris operátor parciális alkalmazása zárójelben — egyik oldalát rögzítjük.

**Formák:**
```haskell
(+1)    :: Num a => a -> a    -- jobb szekció: \x -> x + 1
(1+)    :: Num a => a -> a    -- bal szekció:  \x -> 1 + x
(10-)   :: Num a => a -> a    -- \x -> 10 - x
(subtract 1)  :: Num a => a -> a   -- (-1) NEM ez! lásd csapda
(>0)    :: Ord a => a -> Bool
(`div` 2)  :: Integral a => a -> a
```

**Kvíz csapda:** `(-1)` az **szám** mínusz egy, **nem** `\x -> x - 1`. Ehhez `subtract 1` kell. (`-` az egyetlen operátor, amelynek jobb szekciója így nem írható.)

**Backtick-szekció:** `(x `f` y)` = `f x y`. `(`f` y)` = `\x -> f x y`.

**Kapcsolódó:** [[concepts/funprog/parcialis-alkalmazas|parcialis-alkalmazas]], [[concepts/funprog/currying|currying]]
