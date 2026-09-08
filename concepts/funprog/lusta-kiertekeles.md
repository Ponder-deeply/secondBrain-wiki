---
tags: [concept]
sources: []
references: [wiki.haskell.org/Lazy_evaluation, Hutton ch 12]
derivation: unsourced
updated: 2026-05-18
---

# Lusta kiértékelés (lazy evaluation)

**Def:** Kifejezés csak akkor értékelődik ki, ha az eredménye ténylegesen szükséges. Az érték *normálalakra* (NF) vagy *gyenge fejnormálalakra* (WHNF) redukálódik, addig **thunk**-ként (késleltetett számítás) létezik.

**Kulcs következmények:**
- Végtelen adatszerkezetek kezelhetők: `take 5 [1..]` ⇒ `[1,2,3,4,5]`.
- Felesleges számítás kimarad: `fst (1, undefined)` ⇒ `1`.
- Argumentum nem értékelődik, ha a függvény nem használja.

**WHNF:** legkülső konstruktor vagy lambda már kiszámolt; belseje thunk maradhat.

**Példa:**
```haskell
ignore x = 42
ignore (1 `div` 0)   -- ⇒ 42 (nem hibázik)
```

**Kvíz csapda:** Haskell **alapból lusta**, ez a Haskell és pl. ML különbsége. `seq`, `!`, `BangPatterns` kényszerít szigorúságot.

**Kapcsolódó:** [[concepts/funprog/moho-kiertekeles|moho-kiertekeles]], [[concepts/funprog/bottom-undefined|bottom-undefined]], [[concepts/funprog/totalis-vs-parcialis|totalis-vs-parcialis]]
