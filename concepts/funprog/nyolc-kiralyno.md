---
tags: [concept]
sources: []
references: [Hutton ch 7, "Bird \"Thinking Functionally with Haskell\""]
derivation: unsourced
updated: 2026-05-18
---

# 8 királynő probléma (funkcionális megoldás)

**Probléma:** Helyezzünk 8 királynőt egy $8\times 8$ sakktáblára úgy, hogy egyikük se támadja a másikat (sor, oszlop, átló).

**Reprezentáció:** `[Int]` — `i`-edik elem a sor `i+1`-ben lévő királynő oszlopa. Sor szerinti elhelyezés garantálja, hogy minden sorban pontosan egy van.

**Haskell:**
```haskell
queens :: Int -> [[Int]]
queens n = solve n
  where
    solve 0 = [[]]
    solve k = [ q:qs | qs <- solve (k-1), q <- [1..n], safe q qs ]

    safe q qs = and [ q /= c          -- nincs oszlop-ütközés
                    && abs (q - c) /= i  -- nincs átló-ütközés
                    | (i, c) <- zip [1..] qs ]
```

**Magyarázat:** Rekurzív ZF-kifejezés, backtrack-szerűen építi a megoldásokat. `solve k` az `k`-soros részmegoldásokat adja vissza.

**Kapcsolódó:** [[concepts/funprog/zf-kifejezes|zf-kifejezes]], [[concepts/funprog/rekurzio|rekurzio]]
