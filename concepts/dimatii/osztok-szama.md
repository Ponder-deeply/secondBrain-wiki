---
tags: [concept]
sources: [DimatIIEa01.pdf, DimatIIEa02.pdf]
derivation: source
updated: 2026-09-08
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

## Kapocs

- [[concepts/dimatii/szamelmelet-alaptetele]] — a kanonikus alak, amelyre a képlet épül
- [[concepts/dimatii/euler-fi-fuggveny]] — másik, kanonikus alakból számolható számelméleti függvény
- [[concepts/dimatii/oszthatosag]] — a megszámolt objektumok
