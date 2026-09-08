---
tags: [concept]
sources: []
references: [Hutton ch 3, "LYAH \"Believe the type\""]
derivation: unsourced
updated: 2026-05-18
---

# Alaptípusok

| Típus | Tartalom | Megjegyzés |
|---|---|---|
| `Bool` | `True`, `False` | |
| `Char` | `'a'`, `'\n'` | Unicode kódpont |
| `String` | `"abc"` | = `[Char]` |
| `Int` | rögzített méretű egész | min ±2^29; gyors |
| `Integer` | tetszőleges nagy egész | lassabb, pontos |
| `Float` | egyszeres pontosság | |
| `Double` | kettős pontosság | általában ez kell |
| `()` | egységtípus | egy érték: `()` |

**Listák, párok:**
```haskell
[Int]            -- Int-ek listája
(Int, Char)      -- pár
(Int, Char, Bool) -- 3-tuple
[a] -> Int       -- függvénytípus, polimorf
```

**Kvíz csapda — típusozhatóság:**
- `length [] ++ [1]` — `length [] :: Int`, `[1] :: Num a => [a]`, `(++)` listán: ⇒ **típushiba** (`Int` nem lista).
- `length "valami" / 2` — `length :: ... -> Int`, `(/) :: Fractional a => a -> a -> a` — `Int` nem `Fractional` ⇒ **típushiba**.
- `take 1` — parciálisan alkalmazott, `[a] -> [a]` ⇒ **típusozható**.

**Kapcsolódó:** [[concepts/funprog/tipus-szignatura|tipus-szignatura]], [[concepts/funprog/tipusozhatosag|tipusozhatosag]]
