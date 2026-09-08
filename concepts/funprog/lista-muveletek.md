---
tags: [concept]
sources: []
references: [Hutton ch 5, Hoogle base Data.List]
derivation: unsourced
updated: 2026-05-18
---

# Lista műveletek (Prelude / Data.List)

**Alapfüggvények — típus + viselkedés:**
```haskell
(++)    :: [a] -> [a] -> [a]            -- konkatenáció
(!!)    :: [a] -> Int -> a              -- indexelés (0-tól)
head    :: [a] -> a                     -- első elem (parciális!)
tail    :: [a] -> [a]                   -- farok (parciális!)
last    :: [a] -> a                     -- utolsó (parciális!)
init    :: [a] -> [a]                   -- minden az utolsó kivéve (parciális!)
null    :: [a] -> Bool                  -- üres-e
length  :: [a] -> Int
reverse :: [a] -> [a]
take    :: Int -> [a] -> [a]
drop    :: Int -> [a] -> [a]
elem    :: Eq a => a -> [a] -> Bool
replicate :: Int -> a -> [a]
zip     :: [a] -> [b] -> [(a,b)]
zipWith :: (a -> b -> c) -> [a] -> [b] -> [c]
concat  :: [[a]] -> [a]
concatMap :: (a -> [b]) -> [a] -> [b]
```

**Kvíz csapda — totalitás:**
- **Parciális:** `head`, `tail`, `last`, `init`, `(!!)` üres/rövid listán ⇒ ⊥.
- **Totális:** `length`, `null`, `reverse`, `take`, `drop` (negatív indexen üres, nem hiba), `map`, `filter`.

**Kapcsolódó:** [[concepts/funprog/lista-reprezentacio|lista-reprezentacio]], [[concepts/funprog/map-filter-fold|map-filter-fold]], [[concepts/funprog/totalis-vs-parcialis|totalis-vs-parcialis]]
