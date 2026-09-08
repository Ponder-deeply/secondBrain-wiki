---
tags: [concept]
sources: []
references: [Hutton ch 7, LYAH, Hoogle]
derivation: unsourced
updated: 2026-05-18
---

# `map`, `filter`, `fold` — kanonikus HOF-ok

**Típusok:**
```haskell
map    :: (a -> b) -> [a] -> [b]
filter :: (a -> Bool) -> [a] -> [a]
foldr  :: (a -> b -> b) -> b -> [a] -> b
foldl  :: (b -> a -> b) -> b -> [a] -> b
foldr1 :: (a -> a -> a) -> [a] -> a    -- üres listán hibázik!
foldl1 :: (a -> a -> a) -> [a] -> a
```

**Definíciók:**
```haskell
map f []     = []
map f (x:xs) = f x : map f xs

filter p []     = []
filter p (x:xs) | p x       = x : filter p xs
                | otherwise = filter p xs

foldr f z []     = z
foldr f z (x:xs) = f x (foldr f z xs)
-- foldr f z [a,b,c] = a `f` (b `f` (c `f` z))

foldl f z []     = z
foldl f z (x:xs) = foldl f (f z x) xs
-- foldl f z [a,b,c] = ((z `f` a) `f` b) `f` c
```

**Kvíz csapda — ZF↔HOF:** `[g x | x <- xs, f x]` ≡ `(map g . filter f) xs` (előbb szűr, aztán transzformál).

**Gyakorlat:** `foldl'` (szigorú, `Data.List`) hosszú listára. `foldr` lusta, működik végtelen listán is, ha `f` nem mindig kényszeríti a 2. argot.

**Kapcsolódó:** [[concepts/funprog/magasabb-rendu-fuggveny|magasabb-rendu-fuggveny]], [[concepts/funprog/zf-kifejezes|zf-kifejezes]], [[concepts/funprog/fuggveny-kompozicio|fuggveny-kompozicio]]
