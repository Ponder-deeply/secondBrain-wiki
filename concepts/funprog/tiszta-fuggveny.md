---
tags: [concept]
sources: []
references: [wiki.haskell.org/Pure]
derivation: unsourced
updated: 2026-05-18
---

# Tiszta függvény (pure function)

**Def:** Függvény, amely (1) ugyanazon inputra ugyanazt az outputot adja, és (2) nincs mellékhatása (állapotot nem módosít, I/O-t nem végez).

**Haskell:** minden függvény tiszta. Mellékhatás csak `IO`-ba burkolva (`getLine :: IO String`).

**Példa:**
```haskell
sqr :: Int -> Int
sqr x = x * x          -- tiszta

main :: IO ()
main = putStrLn "hi"   -- mellékhatás IO-ban
```

**Kvíz csapda:** Tiszta ≠ totális. `head []` tiszta, de **parciális** (⊥).

**Kapcsolódó:** [[concepts/funprog/referencia-transzparencia|referencia-transzparencia]], [[concepts/funprog/totalis-vs-parcialis|totalis-vs-parcialis]]
