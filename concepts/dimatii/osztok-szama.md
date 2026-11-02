---
tags: [concept]
sources: [DimatIIEa01.pdf, DimatIIEa02.pdf, Farkas-Gabor-Diszkret-matematika-II-eloadasdiak.pdf, dm2gy05_Szamelmelet.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-10-21
---

# Osztók száma

A $\tau(n)$ számelméleti függvény, amely a kanonikus alak kitevőiből közvetlenül kiszámolható.

## Tartalom

**Definíció.** Egy $n > 1$ egész esetén legyen $\tau(n)$ az $n$ pozitív **osztóinak száma**.

**Példa.** $\tau(6) = 4$, hiszen $6$ osztói $1, 2, 3, 6$; $\tau(96) = 12$, osztói $1, 2, 3, 4, 6, 8, \dots$

**Tétel.** Legyen $n > 1$ egész, $n = p_1^{\alpha_1}p_2^{\alpha_2}\cdots p_\ell^{\alpha_\ell}$ kanonikus alakkal. Ekkor
$$\tau(n) = (\alpha_1 + 1)\cdot(\alpha_2 + 1)\cdots(\alpha_\ell + 1).$$

**Bizonyítás.** Az $n$ lehetséges osztóit úgy kapjuk, hogy a $d = p_1^{\beta_1}p_2^{\beta_2}\cdots p_\ell^{\beta_\ell}$ kifejezésben az összes $\beta_i$ kitevőt végigfuttatjuk a $\{0, 1, \dots, \alpha_i\}$ halmazon. A [[concepts/dimatii/szamelmelet-alaptetele]] egyértelműsége miatt különböző kitevőrendszerekhez különböző osztók tartoznak. Így minden $\beta_i$ pontosan $\alpha_i + 1$ féleképpen választható. $\square$

**Példák.** $\tau(2\cdot 3) = (1+1)(1+1) = 4$; $\tau(2^5\cdot 3) = (5+1)(1+1) = 12$.

### Az osztók alakja (előadásdiák)

*(Farkas Gábor előadásdiái.)* Ha $n = p_1^{\alpha_1}\cdots p_r^{\alpha_r}$ kanonikus alak, akkor $n$ osztói pontosan a módosított kanonikus alakú $d = p_1^{\beta_1}\cdots p_r^{\beta_r}$ számok, ahol $0 \leq \beta_i \leq \alpha_i$, $i = 1,\dots,r$; ebből adódik a $\tau(n) = \prod(\alpha_i+1)$ képlet.

### Feladattípusok (2020. 5. feladatsor)

**Kanonikus alak és osztók száma** ($\tau(n) = \prod(\alpha_i+1)$):

| $n$ | kanonikus alak | $\tau(n)$ |
|---:|---|---:|
| $9$ | $3^2$ | $3$ |
| $7$ | $7$ | $2$ |
| $45$ | $3^2\cdot 5$ | $6$ |
| $360$ | $2^3\cdot 3^2\cdot 5$ | $24$ |
| $13882$ | $2\cdot 11\cdot 631$ | $8$ |
| $355218$ | $2\cdot 3\cdot 73\cdot 811$ | $16$ |

**Lnko és lkkt a kanonikus alakból.** Prímenként a kisebb (lnko), illetve a nagyobb (lkkt) kitevőt vesszük; negatív számnál az abszolútértékkel dolgozunk:
- $245 = 5\cdot 7^2$, $378 = 2\cdot 3^3\cdot 7$: $(245,-378) = 7$, $[245,-378] = 2\cdot 3^3\cdot 5\cdot 7^2 = 13230$.
- $147 = 3\cdot 7^2$, $514 = 2\cdot 257$: $(-147, 514) = 1$, $[-147,514] = 75558$.
- $713 = 23\cdot 31$, $276 = 2^2\cdot 3\cdot 23$: $(713,276) = 23$, $[713,276] = 2^2\cdot 3\cdot 23\cdot 31 = 8556$.

Közös ellenőrzés: $(a,b)\cdot[a,b] = |ab|$. Lásd [[concepts/dimatii/legnagyobb-kozos-oszto]] és [[concepts/dimatii/legkisebb-kozos-tobbszoros]]. A nagy tényezők ($631$, $811$) prímségét tényleges próbaosztással kell ellenőrizni ($\sqrt{n}$-ig).

## Kapocs

- [[concepts/dimatii/szamelmelet-alaptetele]] — a kanonikus alak, amelyre a képlet épül
- [[concepts/dimatii/euler-fi-fuggveny]] — másik, kanonikus alakból számolható számelméleti függvény
- [[concepts/dimatii/oszthatosag]] — a megszámolt objektumok
- [[concepts/dimatii/legnagyobb-kozos-oszto]] — lnko a kanonikus alakból
- [[concepts/dimatii/legkisebb-kozos-tobbszoros]] — lkkt a kanonikus alakból
