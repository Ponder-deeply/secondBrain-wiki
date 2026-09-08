---
tags: [concept]
sources: []
references: [wiki.haskell.org/Bottom]
derivation: unsourced
updated: 2026-05-18
---

# Bottom (⊥), `undefined`, `error`

**Def:** ⊥ ("bottom") = nem-terminálódó vagy hibával végződő számítás. Minden Haskell-típus tartalmazza ⊥-t.

**Előállítás:**
```haskell
undefined :: a
error     :: String -> a
let x = x in x          -- végtelen rekurzió
```

**Tipikus ⊥-források:** `head []`, `1 `div` 0`, `fromJust Nothing`, nem-totális mintaillesztés.

**Kvíz csapda:** Egy függvény akkor **totális**, ha **soha** nem ad ⊥-t — `undefined`, `error`, **végtelen rekurzió** mind kizárandó.

**Lustaság és ⊥:** `fst (1, undefined) ⇒ 1` (lusta) — az `undefined` nem kényszerül kiértékelésre.

**Kapcsolódó:** [[concepts/funprog/totalis-vs-parcialis|totalis-vs-parcialis]], [[concepts/funprog/lusta-kiertekeles|lusta-kiertekeles]]
