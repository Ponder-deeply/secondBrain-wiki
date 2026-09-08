---
tags: [concept]
sources: []
references: [wiki.haskell.org/Performance/Strictness, Hutton ch 12]
derivation: unsourced
updated: 2026-05-18
---

# Mohó kiértékelés (eager / strict evaluation)

**Def:** Kifejezés azonnal kiértékelődik, függetlenül attól, hogy felhasználják-e. Argumentumok kiértékelődnek a függvényhívás előtt (call-by-value).

**Haskellben kikényszerítés:**
- `seq :: a -> b -> b` — első argumentumot WHNF-ig kiértékeli.
- `($!)` — szigorú alkalmazás: `f $! x` = `x` előbb kiértékel.
- `!` (BangPatterns), `Data.List.foldl'` — szigorú variánsok.

**Példa:**
```haskell
foldl  (+) 0 [1..1000000]   -- thunk-halmozás, stack overflow lehet
foldl' (+) 0 [1..1000000]   -- szigorú, konstans memória
```

**Kvíz csapda:** Java/ML/Python = mohó. Haskell **alapból lusta**, csak kérésre szigorú.

**Kapcsolódó:** [[concepts/funprog/lusta-kiertekeles|lusta-kiertekeles]], [[concepts/funprog/map-filter-fold|map-filter-fold]]
