---
tags: [concept]
sources: []
references: [wiki.haskell.org/Partial_application — nem ezt; wiki.haskell.org/Bottom]
derivation: unsourced
updated: 2026-05-18
---

# Totális vs. parciális függvény

**Totális:** Minden inputra **véges idő** alatt **nem-⊥** értéket ad. `undefined`, `error`, végtelen rekurzió, mintaillesztési hiba **nélkül**.

**Parciális:** Van olyan input, amelyre ⊥ az érték (kivétel, végtelen, exit).

**Példák — Prelude parciális:**
```haskell
head, tail, init, last :: [a] -> ...   -- üres listán ⊥
(!!)   :: [a] -> Int -> a              -- túl nagy index
div, mod :: Integral a => a -> a -> a  -- 0-val osztva ⊥
fromJust :: Maybe a -> a
read   :: Read a => String -> a        -- rossz formátum
```

**Kvíz feladat — adott típusszignatúra totálisan kitölthető-e?**

| Aláírás | Totális? | Indok |
|---|---|---|
| `f :: [a] -> a` | nem | `[]` esetén nincs `a` |
| `g :: Maybe a -> a` | nem | `Nothing` esetén nincs `a` |
| `h :: (a,a) -> a` | **igen** | `fst` vagy `snd` |
| `i :: (a -> a) -> a` | nem | semmi konkrét `a`-t nem kapunk |
| `j :: a -> (a -> b) -> b` | igen | `\x f -> f x` |

**Heurisztika:** Polimorf `a` csak ott "származtatható", ahol az input típusa tartalmazza. Ha nem garantáltan, parciális.

**Mintaillesztés totalitása:**
```haskell
f (x,_)  = x           -- totális (pár mindig illeszt)
f (x:_)  = x           -- PARCIÁLIS ([] nem illeszt!)
f (x:[]) = x           -- PARCIÁLIS (csak 1 elemű)
f (x,[]) = x           -- PARCIÁLIS (pár második komponensének üresnek kell lennie)
```

**Kapcsolódó:** [[concepts/funprog/bottom-undefined|bottom-undefined]], [[concepts/funprog/mintaillesztes|mintaillesztes]], [[concepts/funprog/parametrikus-polimorfizmus|parametrikus-polimorfizmus]]
