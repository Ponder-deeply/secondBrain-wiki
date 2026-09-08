---
tags: [concept]
sources: []
references: [Hutton ch 6]
derivation: unsourced
updated: 2026-05-18
---

# Rekurzió

**Def:** Függvény önmagát hívja. Funkcionális stílusban a fő iterációs eszköz (nincs `for`/`while`).

**Sémák:**
- **Bázis** + **rekurzív eset**, mintaillesztéssel:
```haskell
length' []     = 0
length' (_:xs) = 1 + length' xs
```

**Típusok:**
- **Lineáris**: egy önhívás (`length`, `map`).
- **Kettős/elágazó**: két önhívás (`fib`, `quicksort`).
- **Kölcsönös**: `even`/`odd` egymást hívja.
- **Farok-rekurzió** (tail): önhívás az utolsó művelet — akkumulátorral lineáris memóriában futhat.

**Példa (akkumulátoros):**
```haskell
sum' = go 0
  where go acc []     = acc
        go acc (x:xs) = go (acc + x) xs
```

**Kvíz csapda:** Haskellben a `foldr`/`foldl` általában jobb, mint kézi rekurzió.

**Kapcsolódó:** [[concepts/funprog/mintaillesztes|mintaillesztes]], [[concepts/funprog/map-filter-fold|map-filter-fold]], [[concepts/funprog/totalis-vs-parcialis|totalis-vs-parcialis]]
