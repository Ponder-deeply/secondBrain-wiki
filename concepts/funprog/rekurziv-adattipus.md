---
tags: [concept]
sources: []
references: [Hutton ch 8.4, "LYAH \"Recursive data structures\""]
derivation: unsourced
updated: 2026-05-18
---

# Rekurzív adattípus

**Def:** Olyan ADT, amelynek valamelyik konstruktor-argumentumában maga a típus szerepel.

**Példák:**
```haskell
data List a = Nil | Cons a (List a)            -- saját lista
data Tree a = Leaf | Node (Tree a) a (Tree a)  -- bin. fa
data Nat = Zero | Succ Nat                     -- Peano-számok
```

**Mintaillesztés strukturális rekurzióval:**
```haskell
length' :: List a -> Int
length' Nil         = 0
length' (Cons _ xs) = 1 + length' xs

size :: Tree a -> Int
size Leaf         = 0
size (Node l _ r) = 1 + size l + size r
```

**Tulajdonság:** A rekurzív struktúrákon definiált függvények mintája megegyezik a típus definíciójával (bázis + indukciós ág).

**Kapcsolódó:** [[concepts/funprog/algebrai-adattipus|algebrai-adattipus]], [[concepts/funprog/rekurzio|rekurzio]]
