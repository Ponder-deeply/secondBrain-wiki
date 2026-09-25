---
tags: [concept, dimatii/elemi-szamelmelet]
sources: [DimatIIEa01.pdf]
derivation: source
updated: 2026-09-08
---

# Számrendszerek

Minden pozitív egész egyértelműen felírható egy rögzített $q > 1$ alap hatványainak összegeként; a felírás jegyeit ismételt maradékos osztás adja.

## Tartalom

**Példa.** A $123$ a 10-es számrendszerben $123 = 100 + 20 + 3 = 1\cdot 10^2 + 2 \cdot 10^1 + 3 \cdot 10^0$; a 2-es számrendszerben
$$1111011_{(2)} = 1\cdot 2^6 + 1\cdot 2^5 + 1\cdot 2^4 + 1\cdot 2^3 + 0\cdot 2^2 + 1\cdot 2^1 + 1\cdot 2^0 = 64 + 32 + 16 + 8 + 0 + 2 + 1.$$

**Tétel.** Legyen $q > 1$ rögzített egész. Ekkor bármely $n$ pozitív egész egyértelműen felírható
$$n = \sum_{i=0}^{k} a_i q^i$$
alakban, ahol $0 \leq a_i < q$ és $a_k \neq 0$.

Ez a felírás az $n$ szám $q$ **számrendszerben történő felírása**; $q$ a számrendszer **alapja**, $a_0, \dots, a_k$ az $n$ **jegyei**, és $k = \lceil \log_q n \rceil$.

**Bizonyítás** (indukcióval). $n = 0$ esetén a tétel igaz. Tegyük fel, hogy minden $n$-nél kisebb szám egyértelműen felírható $q$ alapú számrendszerben. A [[concepts/dimatii/maradekos-osztas]] tétele szerint egyértelműen létezik $0 \leq a_0 < q$ egész, hogy $q \mid n - a_0$. Az indukciós feltevés alapján írjuk fel $q$ alapú számrendszerben az $\frac{n - a_0}{q} = \sum_{i=1}^{k} a_i q^{i-1}$ számot; a felírás egyértelmű. Ekkor $n = \sum_{i=0}^{k} a_i q^i$. $\square$

### Az átváltás algoritmusa

A bizonyítás módszere közvetlenül algoritmust ad: ismételten vegyük a szám $q$-val vett maradékát (ez a következő jegy), majd osszuk le a maradékkal csökkentett számot $q$-val.

**Példa.** $n = 123$ átírása 2-es számrendszerbe:

| $i$ | $n$ | $n \bmod 2$ | $\frac{n - a_i}{2}$ | jegyek |
|---:|---:|---:|---:|---|
| 0 | 123 | 1 | 61 | 1 |
| 1 | 61 | 1 | 30 | 11 |
| 2 | 30 | 0 | 15 | 011 |
| 3 | 15 | 1 | 7 | 1011 |
| 4 | 7 | 1 | 3 | 11011 |
| 5 | 3 | 1 | 1 | 110011 |
| 6 | 1 | 1 | 0 | 1110011 |

## Kapocs

- [[concepts/dimatii/maradekos-osztas]] — a felírás létezésének és egyértelműségének eszköze
- [[concepts/dimatii/oszthatosag]] — az alapfogalom
