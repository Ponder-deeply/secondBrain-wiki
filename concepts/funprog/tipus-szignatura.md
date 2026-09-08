---
tags: [concept]
sources: []
references: [Hutton ch 3, LYAH]
derivation: unsourced
updated: 2026-05-18
---

# Típus-szignatúra

**Def:** `név :: típus` — kifejezés/függvény típusának deklarálása. Opcionális (Haskell következtet), de jó stílus.

**Olvasás:** `->` jobbra zár, alkalmazás balra:
```haskell
f :: a -> b -> c -> d   ≡   a -> (b -> (c -> d))
f x y z                 ≡   ((f x) y) z
```

**Megszorítás (constraint):** `=>` előtt típusosztály-feltétel:
```haskell
(==)  :: Eq a => a -> a -> Bool
sort  :: Ord a => [a] -> [a]
show  :: Show a => a -> String
```

**Kanonikus szignatúrák — kötelező fejből:**
```haskell
id      :: a -> a
const   :: a -> b -> a
(.)     :: (b -> c) -> (a -> b) -> a -> c
($)     :: (a -> b) -> a -> b
flip    :: (a -> b -> c) -> b -> a -> c
map     :: (a -> b) -> [a] -> [b]
filter  :: (a -> Bool) -> [a] -> [a]
foldr   :: (a -> b -> b) -> b -> [a] -> b
foldl   :: (b -> a -> b) -> b -> [a] -> b
zip     :: [a] -> [b] -> [(a,b)]
zipWith :: (a -> b -> c) -> [a] -> [b] -> [c]
curry   :: ((a,b) -> c) -> a -> b -> c
uncurry :: (a -> b -> c) -> (a,b) -> c
```

**Kapcsolódó:** [[concepts/funprog/currying|currying]], [[concepts/funprog/parametrikus-polimorfizmus|parametrikus-polimorfizmus]], [[concepts/funprog/ad-hoc-polimorfizmus|ad-hoc-polimorfizmus]]
