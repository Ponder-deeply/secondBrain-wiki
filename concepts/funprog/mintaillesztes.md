---
tags: [concept]
sources: []
references: [Hutton ch 4, "LYAH \"Syntax in Functions\""]
derivation: unsourced
updated: 2026-05-18
---

# Mintaillesztés (pattern matching)

**Def:** Érték dekonstruálása a struktúrája alapján: a definíció bal oldalán adatkonstruktor-minta áll, érték illeszkedik ⇒ az ágban a változók kötődnek.

**Minták:**
- Változó: `x` — bármire illeszkedik, köti.
- Wildcard: `_` — bármire, nem köt.
- Literál: `0`, `True`, `'a'`.
- Konstruktor: `Just x`, `(a,b)`, `x:xs`, `[]`, `[x]`.
- As-minta: `all@(x:xs)` — egész értéket *és* részeit köti.

**Példa:**
```haskell
head' (x:_)  = x
head' []     = error "üres"

fst' (a,_)   = a
```

**Kvíz csapda — minta struktúrája:**
- `(x,y):z` ⇒ **lista**, fejeleme **pár**. Illeszkedik pl. `[(1,2)]`, `[('a','b'), ('c','d')]`-re.
- `x:[]` ⇒ pontosan **egyelemű** lista.
- `[x,y]` ⇒ pontosan **kételemű** lista (= `x:y:[]`).

**Kapcsolódó:** [[concepts/funprog/case-kifejezes|case-kifejezes]], [[concepts/funprog/guard|guard]], [[concepts/funprog/algebrai-adattipus|algebrai-adattipus]]
