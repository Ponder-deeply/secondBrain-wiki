---
tags: [concept]
sources: []
references: [Hutton ch 5, LYAH]
derivation: unsourced
updated: 2026-05-18
---

# Lista reprezentáció

**Def:** Haskell-ben a lista **rekurzív algebrai adattípus**: vagy üres `[]`, vagy fej-+-farok `x : xs`. Lényegében:
```haskell
data [a] = [] | a : [a]    -- (a "cons" konstruktor jobbra asszociatív)
```

**Szintaxis-cukor:**
```haskell
[1,2,3]   ≡   1 : 2 : 3 : []
"abc"     ≡   ['a','b','c']    -- String = [Char]
[1..5]    ≡   [1,2,3,4,5]
[1,3..9]  ≡   [1,3,5,7,9]
[1..]     -- végtelen (lusta)
```

**Mintaillesztés:**
```haskell
[]        -- üres
[x]       -- 1 elemű (= x:[])
(x:xs)    -- ≥1 elemű
(x:y:zs)  -- ≥2 elemű
```

**Kvíz csapda:** `(x,y):z` egy **lista**, fej egy **pár**. Nem 3-tuple!

**Kapcsolódó:** [[concepts/funprog/lista-muveletek|lista-muveletek]], [[concepts/funprog/mintaillesztes|mintaillesztes]], [[concepts/funprog/algebrai-adattipus|algebrai-adattipus]]
