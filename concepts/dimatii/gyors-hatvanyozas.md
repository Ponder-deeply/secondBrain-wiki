---
tags: [concept, dimatii/alkalmazasok-kriptografia]
sources: [DimatIIEa03.pdf]
derivation: source
updated: 2026-09-08
---

# Gyors hatványozás

Az $a^n \bmod m$ maradék kiszámítása a kitevő kettes számrendszerbeli jegyei mentén, $O(\log n)$ moduláris szorzással a naiv $n-1$ szorzás helyett.

## Tartalom

Legyenek $m, a, n$ pozitív egészek, $m > 1$. A kitevőt írjuk fel kettes számrendszerben:

$$n = \sum_{i=0}^{k} \varepsilon_i 2^i = (\varepsilon_k \varepsilon_{k-1} \ldots \varepsilon_0)_{(2)}, \qquad \varepsilon_i \in \{0, 1\}.$$

Jelölje $n_j = \lfloor n / 2^{k-j} \rfloor = (\varepsilon_k \varepsilon_{k-1} \ldots \varepsilon_{k-j})_{(2)}$ az első $j+1$ jegy által meghatározott számot ($0 \le j \le k$). Minden $j$-re kiszámoljuk az

$$x_j \equiv a^{n_j} \pmod m$$

maradékot. Az indulás $n_0 = \varepsilon_k = 1$, $x_0 = a$, a rekurzió pedig az $n_j = 2 n_{j-1} + \varepsilon_j$ összefüggésből adódik:

$$x_j = a^{\varepsilon_j} x_{j-1}^2 \bmod m = \begin{cases} 1 \cdot x_{j-1}^2 \bmod m, & \text{ha } \varepsilon_j = 0,\\ a \cdot x_{j-1}^2 \bmod m, & \text{ha } \varepsilon_j = 1,\end{cases}$$

és a végén $x_k = a^n \bmod m$. Az algoritmus helyessége az

$$a^n = a^{\sum_{i=0}^{k} \varepsilon_i 2^i} = \prod_{i=0}^{k} \left(a^{2^i}\right)^{\varepsilon_i}$$

formulából következik.

### Példa

$3^{111} \bmod 10$, ahol $111_{(10)} = 1101111_{(2)}$, tehát $k = 6$ és $a = 3$:

| $j$ | $\varepsilon_j$ | $x_j = a^{\varepsilon_j} x_{j-1}^2$ | $x_j \bmod 10$ |
|---:|---:|---|---:|
| 0 | 1 | — | 3 |
| 1 | 1 | $3 \cdot 3^2$ | 7 |
| 2 | 0 | $7^2$ | 9 |
| 3 | 1 | $3 \cdot 9^2$ | 3 |
| 4 | 1 | $3 \cdot 3^2$ | 7 |
| 5 | 1 | $3 \cdot 7^2$ | 7 |
| 6 | 1 | $3 \cdot 7^2$ | 7 |

Vagyis $3^{111} \equiv 7 \pmod{10}$, ami egybevág az Euler–Fermat-tételből kapott eredménnyel ($\varphi(10) = 4$, így $3^{111} = 3^{4 \cdot 27 + 3} \equiv 3^3 = 27 \equiv 7$).

Ugyanígy oldható meg a $23x \equiv 4 \pmod{211}$ kongruencia: $\varphi(211) = 210$ miatt $x \equiv 4 \cdot 23^{209} \pmod{211}$, a gyors hatványozás pedig $23^{209} \equiv 156$-ot ad, tehát $x \equiv 202 \pmod{211}$.

### Miért fontos

Gyors hatványozás nélkül a nyilvános kulcsú kriptográfia nem működne: az [[concepts/dimatii/rsa]] titkosítása és kititkosítása, valamint a [[concepts/dimatii/diffie-hellman-kulcscsere]] is 1024–2048 bites kitevőjű moduláris hatványozásra épül, ami csak $O(\log n)$ lépésben végezhető el.

## Kapocs

- [[concepts/dimatii/rsa]] — a titkosítás és a kititkosítás magja a moduláris hatványozás
- [[concepts/dimatii/diffie-hellman-kulcscsere]] — a nyilvános kulcsok $g^a \bmod p$ alakú hatványok
- [[concepts/dimatii/diszkret-logaritmus]] — a gyors hatványozás inverz feladata, amire nincs hasonlóan gyors eljárás
- [[concepts/dimatii/primitiv-gyok]] — a hatványsorozat $\mathbb{Z}_p^*$-beli viselkedése
