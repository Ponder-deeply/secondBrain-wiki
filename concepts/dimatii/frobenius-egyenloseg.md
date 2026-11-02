---
tags: [concept]
sources: [Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf]
derivation: source
kind: theorem
element: air
updated: 2026-10-21
---

# Frobenius-egyenlőség: $(a \pm b)^q = a^q \pm b^q$

Prímkarakterisztikájú testben a $q = p^n$-edik hatványra emelés additív: $(a \pm b)^q = a^q \pm b^q$.

## Tartalom

### Tétel

Tetszőleges $q$ elemű $F$ véges testben minden $a, b \in F$-re $(a \pm b)^q = a^q \pm b^q$. Az állítás tetszőleges prímkarakterisztikájú kommutatív gyűrűre érvényes.

### Bizonyítás

$F$ karakterisztikája $p$, ezért $q = p^n$. A binomiális együtthatók

$$\binom{p}{i} = \frac{p(p-1)\cdots(p-i+1)}{i(i-1)\cdots 1} \equiv 0 \pmod p \quad (0 < i < p),$$

mert a számlálóban szereplő $p$ nem egyszerűsíthető a nevezővel. Így

$$(a+b)^p = a^p + \binom{p}{1}a^{p-1}b + \dots + \binom{p}{p-1}ab^{p-1} + b^p = a^p + b^p.$$

$n$ szerinti indukcióval $(a+b)^{p^n} = a^{p^n} + b^{p^n}$. A különbségre: $a^{p^n} = \big((a-b)+b\big)^{p^n} = (a-b)^{p^n} + b^{p^n}$, tehát $(a-b)^{p^n} = a^{p^n} - b^{p^n}$.

### Használat

A tétel adja, hogy az $S = \{a \in F : a^q = a\}$ halmaz zárt a kivonásra (lásd [[concepts/dimatii/veges-testek-szerkezete]]).

## Kapocs

- [[concepts/dimatii/veges-testek-szerkezete]] — a bizonyítás fő felhasználója
- [[concepts/dimatii/veges-testek]] — a közeg: $p^n$ elemű testek
- [[concepts/dimatii/gyuru]] — a karakterisztika fogalma
