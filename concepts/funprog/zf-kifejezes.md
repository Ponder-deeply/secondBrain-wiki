---
tags: [concept]
sources: []
references: [Hutton ch 5.5, "LYAH \"Starting out\""]
derivation: unsourced
updated: 2026-05-18
---

# ZF-kifejezés (list comprehension)

**Def:** Zermelo–Fraenkel-stílusú listageneráló kifejezés. `[ kifejezés | generátor, feltétel, ... ]`.

**Komponensek:**
- **Generátor**: `x <- xs` — sorra veszi `xs` elemeit.
- **Feltétel** (guard): Bool-kifejezés — szűr.
- **Lokális kötés**: `let y = ...`.

**Példák:**
```haskell
[ x*x | x <- [1..5] ]                  -- [1,4,9,16,25]
[ x | x <- [1..20], even x ]           -- páros számok
[ (x,y) | x <- [1..3], y <- [1..3], x /= y ]
[ x | xs <- [[1,2],[3,4]], x <- xs ]   -- lapít: [1,2,3,4]
```

**Kvíz csapda — ZF ↔ HOF ekvivalencia:**
```haskell
[ g x | x <- xs, f x ]   ≡   (map g . filter f) xs
[ g x | x <- xs ]        ≡   map g xs
[ x | x <- xs, f x ]     ≡   filter f xs
```
(Előbb **szűr**, aztán **transzformál** — `filter` belül, `map` kívül!)

**Több generátor:** kartézi szorzat, **jobboldali** generátor változik gyorsabban (belső ciklus).

**Kapcsolódó:** [[concepts/funprog/map-filter-fold|map-filter-fold]], [[concepts/funprog/lista-reprezentacio|lista-reprezentacio]]
