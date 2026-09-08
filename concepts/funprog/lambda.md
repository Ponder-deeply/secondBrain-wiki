---
tags: [concept]
sources: []
references: [Hutton ch 4.5, "LYAH \"Lambdas\""]
derivation: unsourced
updated: 2026-05-18
---

# Lambda kifejezés

**Def:** Névtelen függvény. `\arg1 arg2 -> törzs`.

**Szintaxis:**
```haskell
\x -> x + 1            -- :: Num a => a -> a
\x y -> x * y          -- :: Num a => a -> a -> a
(\x -> x * x) 5        -- ⇒ 25
```

**Currying:** `\x y -> e` ≡ `\x -> \y -> e`.

**Használat:** HOF argumentumaként ad-hoc, kis függvény:
```haskell
map (\x -> x * x) [1,2,3]   -- ⇒ [1,4,9]
filter (\x -> x > 0) xs
```

**Eta-redukció:** `\x -> f x` = `f` (ha `x` nem szabad `f`-ben).

**Kapcsolódó:** [[concepts/funprog/currying|currying]], [[concepts/funprog/magasabb-rendu-fuggveny|magasabb-rendu-fuggveny]]
