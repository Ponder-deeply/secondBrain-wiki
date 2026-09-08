---
tags: [concept]
sources: []
references: [Hutton ch 3.9, "LYAH \"Typeclasses 101\""]
derivation: unsourced
updated: 2026-05-18
---

# Ad-hoc polimorfizmus (túlterhelés)

**Def:** Ugyanaz a név **különböző** típusoknál **különböző** implementációval — Haskellben **típusosztály** + **példány** mechanizmussal.

**Szintaxis:**
```haskell
(==)   :: Eq a => a -> a -> Bool      -- Eq megszorítás
show   :: Show a => a -> String
(+)    :: Num a => a -> a -> a
```

A `=>` előtti rész a **megszorítás** — `a` csak olyan típus lehet, amely példánya az adott osztálynak.

**Tulajdonság:** A megszorítás "feloldódik" az osztály metódusainak konkrét implementációjára példányonként (lásd [[concepts/funprog/peldanyositas|peldanyositas]]).

**Kontraszt:** [[concepts/funprog/parametrikus-polimorfizmus|parametrikus-polimorfizmus]]: nincs megszorítás, **egységes** viselkedés.

**Kapcsolódó:** [[concepts/funprog/tipusosztaly|tipusosztaly]], [[concepts/funprog/peldanyositas|peldanyositas]], [[concepts/funprog/szabvanyos-tipusosztalyok|szabvanyos-tipusosztalyok]]
