---
tags: [concept]
sources: []
references: [Hutton, wiki.haskell.org]
derivation: unsourced
updated: 2026-05-18
---

# Összefésüléses rendezés (merge sort)

**Ötlet:** Felezzük a listát, mindkét felet rendezzük rekurzívan, majd összefésüljük.

**Haskell:**
```haskell
merge :: Ord a => [a] -> [a] -> [a]
merge []     ys     = ys
merge xs     []     = xs
merge (x:xs) (y:ys)
  | x <= y    = x : merge xs (y:ys)
  | otherwise = y : merge (x:xs) ys

halve :: [a] -> ([a], [a])
halve xs = splitAt (length xs `div` 2) xs

msort :: Ord a => [a] -> [a]
msort []  = []
msort [x] = [x]
msort xs  = merge (msort l) (msort r)
  where (l, r) = halve xs
```

**Bonyolultság:** $O(n \log n)$ legrosszabb, stabil.

**Kapcsolódó:** [[concepts/funprog/beszuras-rendezes|beszuras-rendezes]], [[concepts/funprog/quicksort|quicksort]]
