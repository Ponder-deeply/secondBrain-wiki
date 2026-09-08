---
tags: [concept]
sources: []
references: [Hutton ch 3, LYAH]
derivation: unsourced
updated: 2026-05-18
---

# Típusozhatóság (well-typed)

**Def:** Egy kifejezés **típusozható**, ha létezik olyan típus, amelyet a Hindley–Milner típuskövetkeztető hozzárendel. Különben **típushiba**.

**Eljárás (kvíz):** Vegyük az aljelektől felfelé, írjuk fel minden részkifejezés típusát, ellenőrizzük az alkalmazási szabályt:
- `f :: a -> b` és `x :: a` ⇒ `f x :: b`
- Ha `x` típusa nem egyezik `a`-val ⇒ típushiba.

**Kvíz feladatok elemzése:**

| Kifejezés | Típusozható? | Indok |
|---|---|---|
| `length [] ++ [1]` | **nem** | `length [] :: Int`, de `(++)` listát vár |
| `length "valami" / 2` | **nem** | `length :: ... -> Int`, `(/) :: Fractional ⇒` nem ad `Int`-re |
| `take 1` | **igen** | parc. alk., `[a] -> [a]` |
| `(+) 1` | igen | `Num a => a -> a` |
| `1 + "a"` | nem | `Num` vs `String` |
| `if 1 then a else b` | nem | feltétel `Bool` legyen |
| `[1, 'a']` | nem | lista elemei azonos típusúak |

**Kapcsolódó:** [[concepts/funprog/tipus-szignatura|tipus-szignatura]], [[concepts/funprog/alaptipusok|alaptipusok]], [[concepts/funprog/szabvanyos-tipusosztalyok|szabvanyos-tipusosztalyok]]
