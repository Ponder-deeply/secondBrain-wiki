---
tags: [concept]
sources: [véletlenek.pdf, véletlenek_feladatsor.pdf]
derivation: source
updated: 2026-09-04
---

# LFSR (Linear Feedback Shift Register)

Bitenkénti shift-regiszter XOR-visszacsatolással: olcsó, hardverben triviálisan megvalósítható kulcsfolyam-előállító, amely hosszú periódust ad — és amelyet a Berlekamp–Massey algoritmus önmagában teljesen megtör.

## Tartalom

**Állapot:** $[b_{n-1}, \ldots, b_0]$ (bal = legmagasabb helyiértékű), kimeneti bit: $b_0$, jobbra shiftelünk, az új bal bit:

$$f = \bigoplus_{i \in T} b_i$$

ahol $T$ a visszacsatolási polinom nem-vezető tagjai kitevői (a konstans tag $1$ azt jelenti, hogy $0 \in T$).

**Maximális periódus:** $2^m - 1$ (az összes nem-nulla állapot), ha a visszacsatolási polinom **primitív** $\text{GF}(2)$ felett. A csupa-nulla állapot fixpont, ezért esik ki a periódusból.

**Berlekamp–Massey algoritmus:** $2m$ ismert kimeneti bitből meghatározza a minimális visszacsatolási polinomot ($m$-fokú). Ezért az LFSR kimenete kriptográfiailag nem biztonságos önmagában: a linearitás miatt a megfigyelt kimenet lineáris egyenletrendszerré válik. A gyakorlati folyamtitkosítók ezért nemlineáris elemmel (kombináló függvény, szabálytalan léptetés) egészítik ki.

### Példa: $f = b_3 \oplus b_2 \oplus b_0$ (4-bites), kezdő állapot $[1,0,0,1]$

Az LFSR $2^4 - 1 = 15$ bites periódussal működik, ha a polinom $x^4 + x^3 + x^2 + 1$ primitív.

## Kapocs

- [[concepts/kript/veletlenek]] — a véletlengenerálás keretei; PRNG vs. CSPRNG
- [[concepts/kript/folyam-titkositok]] — az LFSR mint kulcsfolyam-előállító, és a nemlineáris kiegészítései
- [[concepts/kript/linearis-kongruencialis-generator]] — ugyanaz a gyengeség egész számok fölött: a linearitás visszafejthetővé teszi
- [[concepts/kript/feladatok]] — 6. feladat: 18 kimeneti bit, Berlekamp–Massey
- [[subjects/kript]] — tantárgy áttekintő
- [[concepts/kript/synthesis-szimmetrikus-primitivek]] — hol áll az LFSR a szimmetrikus primitívek képében
