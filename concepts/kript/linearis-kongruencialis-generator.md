---
tags: [concept]
sources: [véletlenek.pdf, véletlenek_feladatsor.pdf]
derivation: source
updated: 2026-09-04
---

# Lineáris kongruenciális generátor (LCG)

A klasszikus, szorzás–összeadás–maradék alakú pszeudovéletlen generátor és annak $c = 0$ szorzós esete, a Lehmer RNG. Hosszú periódust adnak és gyorsak, de a linearitás miatt néhány kimenetből a paraméterek — és így a teljes jövőbeli sorozat — visszafejthetők.

## Tartalom

### Lehmer RNG (multiplikatív eset)

$$X_{k+1} = a \cdot X_k \bmod m$$

- $m$ prím, $a$ primitív gyök $\bmod m$ esetén a periódus $m - 1$.
- Ismert $m$ és két egymást követő elem $(b_1, b_2)$: $a = b_2 \cdot b_1^{-1} \bmod m$ — **visszafejthető**.
- 4 egymást követő elemből ($b_1, b_2, b_3, b_4$) mind $a$, mind $m$ meghatározható.

### Általános LCG

$$X_{k+1} = a \cdot X_k + c \bmod m$$

- POSIX `rand()`: $a = 1103515245$, $c = 12345$, $m = 2^{31}$.
- RANDU (IBM): $a = 65539$, $m = 2^{31}$ — híresen gyenge (3D-ben síkokon koncentrálódik).
- Pár kimenetből $a$, $c$, $m$ visszafejthetők → nem kriptográfiai.

**A közös tanulság:** a linearitás az, ami megöli. Ugyanez a szerkezeti hiba jelenik meg $\text{GF}(2)$ fölött az [[concepts/kript/lfsr]] esetében, ahol a Berlekamp–Massey algoritmus játssza a paraméter-visszafejtés szerepét.

## Kapocs

- [[concepts/kript/veletlenek]] — PRNG vs. CSPRNG; hova esnek ezek a generátorok
- [[concepts/kript/lfsr]] — ugyanez a linearitási gyengeség bitszinten
- [[concepts/kript/feladatok]] — Lehmer-inverz feladat a véletlenek feladatsorban
- [[subjects/kript]] — tantárgy áttekintő
