---
tags: [concept]
sources: []
references: [Hutton ch 3.7, wiki.haskell.org/Polymorphism]
derivation: unsourced
updated: 2026-05-18
---

# Parametrikus polimorfizmus

**Def:** Egy függvény **azonos** módon működik **bármely** típusra. Típusváltozó (kisbetűs: `a`, `b`) jelöli.

**Példa:**
```haskell
id      :: a -> a              -- bármilyen 'a'-ra ugyanaz
length  :: [a] -> Int          -- bármilyen elemtípusú listán
reverse :: [a] -> [a]
fst     :: (a,b) -> a
```

**Tulajdonság — parametricitás:** Ha a típus polimorf, a függvénynek **nincs információja** a konkrét típusról. `f :: a -> a` ⇒ csak `id` lehet (Wadler "Theorems for free").

**Kontraszt:** [[concepts/funprog/ad-hoc-polimorfizmus|ad-hoc-polimorfizmus]] — viselkedés típusonként **eltérő** (pl. `(==)`).

**Kvíz csapda — totalitás polimorf típusból:**
- `f :: [a] -> a` ⇒ **parciális** (üres lista esetén nincs `a`).
- `g :: Maybe a -> a` ⇒ **parciális** (`Nothing` esetén nincs `a`).
- `h :: (a,a) -> a` ⇒ **totális** (`fst` vagy `snd`).
- `i :: (a -> a) -> a` ⇒ **parciális** (nincs honnan `a`-t előállítani).

**Kapcsolódó:** [[concepts/funprog/tipus-szignatura|tipus-szignatura]], [[concepts/funprog/ad-hoc-polimorfizmus|ad-hoc-polimorfizmus]], [[concepts/funprog/totalis-vs-parcialis|totalis-vs-parcialis]]
