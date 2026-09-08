---
tags: [concept]
sources: []
references: [Hutton ch 4.6, wiki.haskell.org/Let_vs._Where]
derivation: unsourced
updated: 2026-05-18
---

# `let` vs `where`

**`let ... in ...`** — kifejezés:
```haskell
cylinder r h =
  let side = 2 * pi * r * h
      top  = pi * r^2
  in side + 2 * top
```

**`where`** — definíció utáni segédkötések, csak függvény-egyenlethez:
```haskell
cylinder r h = side + 2 * top
  where side = 2 * pi * r * h
        top  = pi * r^2
```

**Különbségek:**
| | `let` | `where` |
|---|---|---|
| hely | kifejezésben bárhol | csak egyenlet végén |
| hatókör | a `in` utáni rész | egész egyenlet (több guard is) |
| guard-okkal | nem oszt | **oszt** — guard-ok között megosztott |

**Kapcsolódó:** [[concepts/funprog/margoszabaly|margoszabaly]], [[concepts/funprog/guard|guard]]
