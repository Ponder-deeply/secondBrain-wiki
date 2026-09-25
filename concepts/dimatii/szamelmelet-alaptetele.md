---
tags: [concept, dimatii/elemi-szamelmelet]
sources: [DimatIIEa01.pdf, DimatIIEa02.pdf]
derivation: source
updated: 2026-09-08
---

# Számelmélet alaptétele

Minden egész lényegében egyértelműen bomlik prímek szorzatára; ez az elemi számelmélet szerkezeti alaptétele.

## Tartalom

**Tétel.** Minden nem nulla, nem egység egész szám sorrendtől és asszociáltaktól eltekintve egyértelműen felírható prímszámok szorzataként.

**Bizonyítás** (elég nemnegatív számokra).

*Létezés*, indukcióval. $n = 2$, $n = 3$ esetén igaz (prímek). Általában, ha $n$ prím, akkor készen vagyunk; ha nem, akkor $n$ szorzatra bomlik nemtriviális módon, és a tényezők az indukciós feltevés alapján már felbonthatók.

*Egyértelműség*, indukcióval. $n = 2$, $n = 3$ esetén igaz. Tegyük fel, hogy $n = p_1p_2\cdots p_k = q_1q_2\cdots q_\ell$, ahol $p_1,\dots,p_k, q_1,\dots,q_\ell$ prímek. $p_1$ osztja a bal oldalt, tehát osztja a jobb oldalt is; a prímtulajdonság miatt osztja valamelyik $q_j$-t, ami átrendezéssel $p_1 = q_1$-nek vehető. Egyszerűsítve: $n' = p_2\cdots p_k = q_2\cdots q_\ell$, és az indukciós feltevés alapján ez már egyértelmű. $\square$

Az egyértelműség tehát azon múlik, hogy $\mathbb{Z}$-ben a [[concepts/dimatii/felbonthatatlan-es-prim]] fogalom egybeesik.

### Kanonikus alak

**Definíció.** Egy $n$ nem nulla egész szám **kanonikus alakja**
$$n = \pm p_1^{\alpha_1}p_2^{\alpha_2}\cdots p_\ell^{\alpha_\ell} = \pm\prod_{i=1}^{\ell}p_i^{\alpha_i},$$
ahol $p_1, \dots, p_\ell$ pozitív prímek és $\alpha_1, \dots, \alpha_\ell$ pozitív egészek.

**Következmény.** Legyenek $n, m > 1$ pozitív egészek, közös prímeken felírva $n = p_1^{\alpha_1}\cdots p_\ell^{\alpha_\ell}$, $m = p_1^{\beta_1}\cdots p_\ell^{\beta_\ell}$ (most $\alpha_i, \beta_i \geq 0$ megengedett). Ekkor

$$(m,n) = p_1^{\min\{\alpha_1,\beta_1\}}\cdots p_\ell^{\min\{\alpha_\ell,\beta_\ell\}}, \qquad [m,n] = p_1^{\max\{\alpha_1,\beta_1\}}\cdots p_\ell^{\max\{\alpha_\ell,\beta_\ell\}},$$

és $(m,n)\cdot[m,n] = m\cdot n$.

A kanonikus alak a további számelméleti függvények — [[concepts/dimatii/osztok-szama]], [[concepts/dimatii/euler-fi-fuggveny]] — kiszámításának alapja is.

## Kapocs

- [[concepts/dimatii/felbonthatatlan-es-prim]] — az egyértelműség forrása
- [[concepts/dimatii/legnagyobb-kozos-oszto]] — kitevők minimuma
- [[concepts/dimatii/legkisebb-kozos-tobbszoros]] — kitevők maximuma
- [[concepts/dimatii/osztok-szama]] — a kanonikus alakból számolt $\tau(n)$
- [[concepts/dimatii/euler-fi-fuggveny]] — a kanonikus alakból számolt $\varphi(m)$
- [[concepts/dimatii/primek-eloszlasa]] — az építőkövek készlete
