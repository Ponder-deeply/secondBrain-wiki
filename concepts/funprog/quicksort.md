---
tags: [concept]
sources: []
references: [Hutton ch 1.5, "LYAH \"Recursion\""]
derivation: unsourced
updated: 2026-05-18
---

# Gyorsrendezés (quicksort)

**Ötlet:** Pivot kiválasztása (itt: első elem), partíció a pivotnál kisebb / nem-kisebb részre, rekurzív rendezés mindkét félre, konkatenáció.

**Haskell — kanonikus:**
```haskell
qsort :: Ord a => [a] -> [a]
qsort []     = []
qsort (x:xs) = qsort smaller ++ [x] ++ qsort larger
  where
    smaller = [ y | y <- xs, y <  x ]
    larger  = [ y | y <- xs, y >= x ]
```

**Bonyolultság:** átlag $O(n \log n)$, legrosszabb $O(n^2)$ (már rendezett, első-elem pivot).

**Megjegyzés:** A Haskell „1-soros" verziója oktatási, nem in-place. ZF-kifejezést használ partícióhoz.

**Kapcsolódó:** [[concepts/funprog/zf-kifejezes|zf-kifejezes]], [[concepts/funprog/beszuras-rendezes|beszuras-rendezes]], [[concepts/funprog/merge-sort|merge-sort]]
