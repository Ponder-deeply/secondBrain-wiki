---
tags: [concept]
sources: []
references: [wiki.haskell.org/Referential_transparency]
derivation: unsourced
updated: 2026-05-18
---

# Referencia-transzparencia

**Def:** Egy kifejezés bármely előfordulása helyettesíthető az értékével a program jelentésének megváltoztatása nélkül. Azonos input ⇒ azonos output, **minden hívásnál**.

**Következmény:** mellékhatás (állapotmódosítás, I/O, kivétel) tilos a tiszta részben. Egyenlőségi okfejtés (*equational reasoning*) lehetséges.

**Példa (transzparens):**
```haskell
let x = 2 + 3 in x * x   ≡   5 * 5   ≡   25
```

**Példa (NEM transzparens — más nyelvekben):**
```python
x = input()        # minden hívás más eredmény → nem transzparens
```

**Haskellben:** I/O az `IO a` típusba kapszulázva (monád), tiszta értékként kezelt.

**Kapcsolódó:** [[concepts/funprog/tiszta-fuggveny|tiszta-fuggveny]], [[concepts/funprog/lusta-kiertekeles|lusta-kiertekeles]]
