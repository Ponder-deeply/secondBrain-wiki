---
tags: [concept]
sources: []
references: [Hutton ch 4, LYAH]
derivation: unsourced
updated: 2026-05-18
---

# Case kifejezés

**Def:** Mintaillesztés *kifejezés-szintű* formája. Bármely kifejezésen elvégezhető, értéket ad vissza.

**Szintaxis:**
```haskell
case expr of
  minta1 -> érték1
  minta2 -> érték2
  _      -> default
```

**Példa:**
```haskell
describe xs = case xs of
  []     -> "üres"
  [_]    -> "egyelemű"
  _      -> "több elemű"
```

**Guard case-ben:**
```haskell
case n of
  x | x > 0 -> "pozitív"
    | x < 0 -> "negatív"
    | otherwise -> "nulla"
```

**Kvíz csapda:** `case` kifejezés, nem utasítás — mindig értéke van, mindig azonos típusú minden ágban.

**Kapcsolódó:** [[concepts/funprog/mintaillesztes|mintaillesztes]], [[concepts/funprog/guard|guard]]
