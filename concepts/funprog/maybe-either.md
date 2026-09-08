---
tags: [concept]
sources: []
references: [Hutton ch 8, base Data.Maybe / Data.Either]
derivation: unsourced
updated: 2026-05-18
---

# `Maybe` és `Either`

**`Maybe a`** — opcionális érték, hibajelzés ⊥ nélkül:
```haskell
data Maybe a = Nothing | Just a

safeHead :: [a] -> Maybe a
safeHead []    = Nothing
safeHead (x:_) = Just x

fromMaybe :: a -> Maybe a -> a
fromMaybe d Nothing  = d
fromMaybe _ (Just x) = x
```

**`Either a b`** — két lehetőség (gyakran: hiba vs. érték):
```haskell
data Either a b = Left a | Right b

safeDiv :: Int -> Int -> Either String Int
safeDiv _ 0 = Left "0 osztó"
safeDiv x y = Right (x `div` y)
```

**Kvíz csapda — totalitás:** `Maybe a -> a` **parciális** (lásd `fromJust`). Totalizálás: alapérték (`fromMaybe`) vagy mintaillesztés mindkét konstruktoron.

**Kapcsolódó:** [[concepts/funprog/algebrai-adattipus|algebrai-adattipus]], [[concepts/funprog/totalis-vs-parcialis|totalis-vs-parcialis]]
