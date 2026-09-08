---
tags: [concept]
sources: []
references: [Hutton ch 6.6]
derivation: unsourced
updated: 2026-05-18
---

# Beszúrásos rendezés (insertion sort)

**Ötlet:** A lista minden elemét sorban beszúrjuk egy már rendezett listába a helyére.

**Haskell:**
```haskell
insert :: Ord a => a -> [a] -> [a]
insert x []     = [x]
insert x (y:ys)
  | x <= y    = x : y : ys
  | otherwise = y : insert x ys

isort :: Ord a => [a] -> [a]
isort []     = []
isort (x:xs) = insert x (isort xs)
```

**Fold-os alak:**
```haskell
isort = foldr insert []
```

**Bonyolultság:** $O(n^2)$ átlagos és legrosszabb.

**Kapcsolódó:** [[concepts/funprog/merge-sort|merge-sort]], [[concepts/funprog/quicksort|quicksort]], [[concepts/funprog/rekurzio|rekurzio]], [[concepts/funprog/map-filter-fold|map-filter-fold]]
