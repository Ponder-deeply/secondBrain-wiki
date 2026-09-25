---
tags: [concept, dimatii/kongruenciak]
sources: [DimatIIEa02.pdf]
derivation: source
updated: 2026-09-08
---

# Euler-féle $\varphi$ függvény

A modulushoz relatív prím maradékok száma — egyben a redukált maradékosztályok száma modulo $m$.

## Tartalom

**Definíció.** Egy $m > 0$ egész szám esetén legyen $\varphi(m)$ az $m$-nél kisebb, hozzá relatív prím pozitív egészek száma:
$$\varphi(m) = |\{i \,:\, 0 < i < m,\ (m,i) = 1\}|.$$

**Példák.** $\varphi(5) = 4$ ($1,2,3,4$); $\varphi(6) = 2$ ($1,5$); $\varphi(12) = 4$ ($1,5,7,11$); $\varphi(15) = 8$ ($1,2,4,7,8,11,13,14$).

**Megjegyzés.** $\varphi(m)$ éppen a redukált maradékosztályok száma modulo $m$, azaz $|\mathbb{Z}_m^*|$ — lásd [[concepts/dimatii/redukalt-maradekrendszer]].

### Kiszámítása a kanonikus alakból

**Tétel.** Legyen $m$ prímtényezős felbontása $m = p_1^{e_1}p_2^{e_2}\cdots p_\ell^{e_\ell}$. Ekkor
$$\varphi(m) = \prod_{i=1}^{\ell}\left(p_i^{e_i} - p_i^{e_i - 1}\right) = m\prod_{i=1}^{\ell}\left(1 - \frac{1}{p_i}\right).$$

Következmények:

- ha $a_1, \dots, a_r$ páronként relatív prímek, akkor $\varphi(a_1\cdots a_r) = \varphi(a_1)\cdots\varphi(a_r)$ (a $\varphi$ multiplikatív);
- ha $p$ prím, akkor $\varphi(p^m) = p^m - p^{m-1}$; speciálisan $\varphi(p) = p - 1$.

**Példák.**
$$\varphi(5) = 5\left(1 - \tfrac15\right) = 4, \quad \varphi(6) = 6\left(1-\tfrac12\right)\left(1-\tfrac13\right) = 2,$$
$$\varphi(12) = 12\left(1-\tfrac12\right)\left(1-\tfrac13\right) = 4, \quad \varphi(15) = 15\left(1-\tfrac13\right)\left(1-\tfrac15\right) = 8.$$

## Kapocs

- [[concepts/dimatii/redukalt-maradekrendszer]] — a megszámolt osztályok
- [[concepts/dimatii/euler-fermat-tetel]] — a $\varphi$ fő alkalmazása
- [[concepts/dimatii/szamelmelet-alaptetele]] — a képlet alapja
- [[concepts/dimatii/osztok-szama]] — másik, kanonikus alakból számolható függvény
- [[concepts/dimatii/invertalhatosag-zm-ben]] — az invertálható osztályok száma $\varphi(m)$
