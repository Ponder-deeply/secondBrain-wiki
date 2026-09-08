---
tags: [concept]
sources: []
references: [Hutton ch 7, LYAH]
derivation: unsourced
updated: 2026-05-18
---

# Függvény kompozíció `(.)`

**Def:** `(f . g) x = f (g x)`. Két függvény összefűzése — előbb `g`, aztán `f`.

**Típus:**
```haskell
(.) :: (b -> c) -> (a -> b) -> a -> c
```

**Példa:**
```haskell
negEven = negate . filter even      -- [Int] -> [Int]
sumSqrs = sum . map (^2)

-- pointfree stílus:
f = (*2) . (+1)
f 3   -- ⇒ 8
```

**`($)`** operátor: `f $ x = f x`, **legalacsonyabb** precedencia ⇒ zárójel elhagyásra:
```haskell
print (sqrt (1 + 2))   ≡   print $ sqrt $ 1 + 2
```

**Kvíz csapda:** `f . g . h $ x` = `f (g (h x))`. `(.)` **jobbra** asszociatív, `($)` is.

**Kapcsolódó:** [[concepts/funprog/magasabb-rendu-fuggveny|magasabb-rendu-fuggveny]], [[concepts/funprog/operator-szekcio|operator-szekcio]]
