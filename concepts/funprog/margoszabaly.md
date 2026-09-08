---
tags: [concept]
sources: []
references: [haskell.org/onlinereport/haskell2010 §10.3, wiki.haskell.org/Layout]
derivation: unsourced
updated: 2026-05-18
---

# Margószabály (layout / off-side rule)

**Def:** Behúzás alapján határozza meg a blokk-struktúrát, kapcsos zárójelek helyett. `let`, `where`, `do`, `of` után megnyíló blokk *referencia-oszlopa* az első nem-szóköz karakter pozíciója.

**Szabályok:**
- Új sor **azonos** oszlopban ⇒ új definíció/utasítás (új `;`).
- Új sor **mélyebben** behúzva ⇒ folytatás.
- Új sor **kevésbé** behúzva ⇒ blokk vége (`}`).

**Példa:**
```haskell
f x = let y = x + 1
          z = y * 2     -- y és z azonos oszlopban: két def
      in z              -- in kevésbé behúzva: let blokk vége
```

**Explicit alternatíva:** `{ ; }` használható helyett.

**Kvíz csapda:** TAB és szóköz keverése tipikus hiba. Mindig szóköz.

**Kapcsolódó:** [[concepts/funprog/modul|modul]], [[concepts/funprog/guard|guard]]
