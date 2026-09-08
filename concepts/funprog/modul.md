---
tags: [concept]
sources: []
references: [Hutton ch 7.7, "LYAH \"Modules\""]
derivation: unsourced
updated: 2026-05-18
---

# Modul

**Def:** Haskell-fájl egy modult definiál. Névtér, export-lista, import-lista.

**Szintaxis:**
```haskell
module Geom (Shape(..), area, perimeter) where
  -- Shape(..) = a típus és minden konstruktora exportálva
  -- nélküle csak a típus (absztrakt), nem a konstruktorai

import Data.List           -- minden
import Data.List (sort, nub)         -- csak ezek
import Data.List hiding (sort)       -- ezek nélkül
import qualified Data.Map as M       -- M.lookup, M.insert, ...
```

- Fájlnév és modulnév **egyeznie kell** (kivéve `Main`).
- A `Main` modul `main :: IO ()` belépési ponttal indul.

**Kapcsolódó:** [[concepts/funprog/margoszabaly|margoszabaly]]
