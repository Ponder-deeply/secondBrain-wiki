---
tags: [concept]
sources: []
references: [Hutton ch 4.5, "LYAH \"Guards\""]
derivation: unsourced
updated: 2026-05-18
---

# Őrfeltétel (guard)

**Def:** Függvény-egyenlet kiegészítése Bool-feltételekkel: `|` jellel bevezetve, fentről lefelé az első igaz vált ki egyezést.

**Szintaxis:**
```haskell
abs' n | n >= 0    = n
       | otherwise = -n

bmi w h | bmi < 18.5 = "sovány"
        | bmi < 25.0 = "normál"
        | bmi < 30.0 = "túlsúlyos"
        | otherwise  = "elhízott"
  where bmi = w / h^2
```

- `otherwise = True` (a `Prelude`-ban).
- Egyik ág sem igaz ⇒ futás közben hiba (parciális!).

**Kvíz csapda:** Guard után **nincs** `=` az egyenlőség jel előtt — `| feltétel = érték`.

**Kapcsolódó:** [[concepts/funprog/mintaillesztes|mintaillesztes]], [[concepts/funprog/case-kifejezes|case-kifejezes]], [[concepts/funprog/let-where|let-where]]
