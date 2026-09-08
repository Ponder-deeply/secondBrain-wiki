---
tags: [concept]
sources: []
references: [Hutton ch 3.9, "LYAH \"Typeclasses 101\""]
derivation: unsourced
updated: 2026-05-18
---

# Szabványos típusosztályok (Prelude)

| Osztály | Metódusok | Jelentés |
|---|---|---|
| `Eq` | `(==)`, `(/=)` | egyenlőség |
| `Ord` | `compare`, `(<)`, `(<=)`, `max`, `min` | rendezés (superclass: `Eq`) |
| `Show` | `show :: a -> String` | szöveg-reprezentáció |
| `Read` | `read :: String -> a` | szövegből parse-olás |
| `Enum` | `succ`, `pred`, `toEnum`, `fromEnum` | felsorolható (`[1..5]` ehhez!) |
| `Bounded` | `minBound`, `maxBound` | alsó/felső korlát |
| `Num` | `(+)`, `(-)`, `(*)`, `negate`, `abs`, `signum`, `fromInteger` | számok |
| `Integral` | `div`, `mod`, `quot`, `rem`, `toInteger` | egészek (super: `Num`, `Real`) |
| `Fractional` | `(/)`, `recip`, `fromRational` | tört (super: `Num`) |
| `Floating` | `pi`, `sqrt`, `exp`, `log`, `sin`, ... | lebegőpont (super: `Fractional`) |

**Számliterál:** `42 :: Num a => a` — bármilyen `Num`-példányra.

**Kvíz csapda:** `(/)` csak `Fractional`-on. Egészen `div` vagy `quot` kell. `length :: [a] -> Int` ⇒ `length xs / 2` típushiba (`Int` nem `Fractional`).

**Kapcsolódó:** [[concepts/funprog/tipusosztaly|tipusosztaly]], [[concepts/funprog/peldanyositas|peldanyositas]], [[concepts/funprog/ad-hoc-polimorfizmus|ad-hoc-polimorfizmus]]
