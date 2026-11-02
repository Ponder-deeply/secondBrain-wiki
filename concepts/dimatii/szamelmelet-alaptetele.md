---
tags: [concept]
sources: [DimatIIEa01.pdf, DimatIIEa02.pdf, Lehman-Leighton-Meyer-Mathematics-for-Computer-Science.pdf, Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf]
derivation: source
kind: theorem
element: water
updated: 2026-10-21
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

### Bizonyítás jól rendezéssel és az $n + m\sqrt{-5}$ ellenpélda (Lehman–Leighton–Meyer 9.4)

A forrás a tételt így fogalmazza: minden pozitív egész egyértelműen áll elő **gyengén csökkenő** prímsorozat szorzataként (az 1 az üres szorzat; 1 nem prím, különben $15 = 5\cdot 3\cdot 1 \cdot 1 \cdots$ megsértené az egyértelműséget). Példa: $75237393 = 23\cdot 17\cdot 17\cdot 11\cdot 7\cdot 7\cdot 7\cdot 3$.

Két segédállítás (nem szabad az egyértelműségből levezetni őket, mert körkörös lenne):

1. Ha $p$ prím és $p \mid ab$, akkor $p \mid a$ vagy $p \mid b$. Bizonyítás: ha $(a,p) = p$, akkor $p \mid a$; különben $(a,p) = 1 = sa + tp$, így $b = s(ab) + (tb)p$, és $p$ mindkét tagot osztja, tehát $p \mid b$.
2. Ha $p \mid a_1a_2\cdots a_n$, akkor $p \mid a_i$ valamely $i$-re (indukcióval).

*Egyértelműség (indirekt, jólrendezéssel).* Ha lenne többféleképp felírható szám, legyen a legkisebb $n = p_1\cdots p_j = q_1\cdots q_k$, mindkettő gyengén csökkenő, $p_1 \le q_1$. Ha $p_1 = q_1$, akkor $n/p_1 < n$ is két különböző felírással rendelkezne — ellentmondás. Ha $p_1 < q_1$, akkor minden $p_i < q_1$, de $q_1 \mid n = p_1\cdots p_j$, így a 2. segédállítás szerint $q_1$ osztja valamelyik $p_i$-t, ami lehetetlen.

Az egyértelműség nem magától értetődő: a $\{n + m\sqrt{-5} : m,n \in \mathbb{Z}\}$ számkörben már nem teljesül.

### A bizonyítás az előadásdiák szerint

*(Farkas Gábor előadásdiái, pozitív számokra.)* Minden nem nulla, nem egység egész szám sorrendtől és asszociáltságtól eltekintve egyértelműen bontható felbonthatatlanok szorzatára.

*Egzisztencia*, teljes indukcióval ($n > 1$): $n = 2$ kész. Ha $n$ felbonthatatlan, kész. Ha nem, akkor $n = ab$, ahol $a, b$ nem egység, így $a, b < n$ és rájuk igaz az indukciós feltevés; $n$ felbontása $a$ és $b$ felbontásának szorzata.

*Unicitás*, indirekten: legyen $n$ a legkisebb olyan szám, amelynek felbontása nem egyértelmű: $n = p_1\cdots p_k = q_1\cdots q_r$. Ekkor $p_1 \mid n$, így $p_1 \mid q_1\cdots q_r$; a prímtulajdonság miatt $p_1 \mid q_i$ valamely $i$-re, tehát $p_1 = q_i$. Az $n_1 = n/p_1 = p_2\cdots p_k = q_1\cdots q_{i-1}q_{i+1}\cdots q_r$ számnak $n_1 < n$ mellett két lényegesen különböző felbontása van — ellentmondás. $\square$

### Kanonikus és módosított kanonikus alak

Egy $n > 1$ egész **kanonikus alakja** $n = \prod_{i=1}^r p_i^{\alpha_i}$, ahol $p_i$ különböző pozitív prímek és $\alpha_i > 0$. **Módosított kanonikus alak**, ha $\alpha_i = 0$ is megengedett (így két szám közös prímekre írható). Az $n$ osztói ekkor a módosított kanonikus alakú $d = \prod p_i^{\beta_i}$, $0 \leq \beta_i \leq \alpha_i$ számok.

## Kapocs

- [[concepts/dimatii/felbonthatatlan-es-prim]] — az egyértelműség forrása
- [[concepts/dimatii/legnagyobb-kozos-oszto]] — kitevők minimuma
- [[concepts/dimatii/legkisebb-kozos-tobbszoros]] — kitevők maximuma
- [[concepts/dimatii/osztok-szama]] — a kanonikus alakból számolt $\tau(n)$
- [[concepts/dimatii/euler-fi-fuggveny]] — a kanonikus alakból számolt $\varphi(m)$
- [[concepts/dimatii/primek-eloszlasa]] — az építőkövek készlete
