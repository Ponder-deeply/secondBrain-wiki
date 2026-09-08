---
tags: [concept]
sources: []
references: [Hutton ch 7, "LYAH \"Higher order functions\""]
derivation: unsourced
updated: 2026-05-18
---

# Magasabb rendű függvény (HOF)

**Def:** Olyan függvény, amelyik (1) függvényt vesz argumentumként és/vagy (2) függvényt ad vissza. Haskellben minden curry-zett több-argumentumos függvény automatikusan HOF.

**Kanonikus példák:**
```haskell
map    :: (a -> b) -> [a] -> [b]
filter :: (a -> Bool) -> [a] -> [a]
foldr  :: (a -> b -> b) -> b -> [a] -> b
foldl  :: (b -> a -> b) -> b -> [a] -> b
(.)    :: (b -> c) -> (a -> b) -> a -> c
flip   :: (a -> b -> c) -> b -> a -> c
($)    :: (a -> b) -> a -> b
```

**Példa:**
```haskell
twice :: (a -> a) -> a -> a
twice f x = f (f x)

twice (+3) 7    -- ⇒ 13
```

**Kvíz csapda — `foldr` típusa:** `(a -> b -> b) -> b -> [a] -> b`. Akkumulátor a 2. paraméter, **jobbról** halad.

**Kapcsolódó:** [[concepts/funprog/map-filter-fold|map-filter-fold]], [[concepts/funprog/fuggveny-kompozicio|fuggveny-kompozicio]], [[concepts/funprog/lambda|lambda]]
