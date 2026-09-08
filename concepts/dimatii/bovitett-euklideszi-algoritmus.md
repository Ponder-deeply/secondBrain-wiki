---
tags: [concept]
sources: [DimatIIEa01.pdf, DimatIIEa02.pdf]
derivation: source
updated: 2026-09-08
---

# Bővített euklideszi algoritmus

Az euklideszi algoritmus melléktermékként azt is megadja, hogyan áll elő a legnagyobb közös osztó a két szám egész együtthatós lineáris kombinációjaként.

## Tartalom

**Tétel.** Minden $a, b$ egész szám esetén léteznek olyan $x, y$ egészek, hogy
$$(a,b) = x\cdot a + y\cdot b.$$

**Bizonyítás.** Legyenek $q_i, r_i$ az [[concepts/dimatii/euklideszi-algoritmus]]sal kapott hányadosok és maradékok. Legyen

$$x_{-1} = 1,\quad x_0 = 0,\qquad x_i = x_{i-2} - q_ix_{i-1} \ \ (i \geq 1),$$
$$y_{-1} = 0,\quad y_0 = 1,\qquad y_i = y_{i-2} - q_iy_{i-1} \ \ (i \geq 1).$$

Ekkor $i \geq 1$ esetén $x_ia + y_ib = r_i$ (indukcióval). Speciálisan $x_na + y_nb = r_n = (a,b)$. $\square$

### Az algoritmus

$$r_{i-2} = r_{i-1}q_i + r_i, \qquad x_i = x_{i-2} - q_ix_{i-1}, \qquad y_i = y_{i-2} - q_iy_{i-1}.$$

**Példa.** Számítsuk ki $(172,62)$ értékét és oldjuk meg a $172x + 62y = (172,62)$ egyenletet!

| $i$ | $r_i$ | $q_{i+1}$ | $x_i$ | $y_i$ | $r_i = 172x_i + 62y_i$ |
|---:|---:|---:|---:|---:|---|
| $-1$ | 172 | — | 1 | 0 | $172 = 172\cdot 1 + 62\cdot 0$ |
| 0 | 62 | 2 | 0 | 1 | $62 = 172\cdot 0 + 62\cdot 1$ |
| 1 | 48 | 1 | 1 | $-2$ | $48 = 172\cdot 1 + 62\cdot(-2)$ |
| 2 | 14 | 3 | $-1$ | 3 | $14 = 172\cdot(-1) + 62\cdot 3$ |
| 3 | 6 | 2 | 4 | $-11$ | $6 = 172\cdot 4 + 62\cdot(-11)$ |
| 4 | 2 | 4 | $-9$ | 25 | $2 = 172\cdot(-9) + 62\cdot 25$ |
| 5 | 0 | — | 31 | $-86$ | $0 = 172\cdot 31 + 62\cdot(-86)$ |

A felírás: $2 = 172\cdot(-9) + 62\cdot 25$, azaz $x = -9$, $y = 25$.

### Mire használjuk

A bővített euklideszi algoritmus a kurzus legtöbbet használt konstruktív eszköze:

- a *felbonthatatlan $\Rightarrow$ prím* implikáció bizonyítása $\mathbb{Z}$-ben;
- a [[concepts/dimatii/linearis-kongruencia]] megoldása;
- a [[concepts/dimatii/linearis-diofantikus-egyenlet]] megoldása;
- a [[concepts/dimatii/kinai-maradektetel]] konstruktív bizonyítása;
- multiplikatív inverz keresése $\mathbb{Z}_m$-ben, lásd [[concepts/dimatii/invertalhatosag-zm-ben]].

## Kapocs

- [[concepts/dimatii/euklideszi-algoritmus]] — az alapalgoritmus, amit ez kiterjeszt
- [[concepts/dimatii/legnagyobb-kozos-oszto]] — az előállított mennyiség
- [[concepts/dimatii/felbonthatatlan-es-prim]] — a két fogalom egybeesésének bizonyítási eszköze
- [[concepts/dimatii/linearis-kongruencia]] — közvetlen alkalmazás
- [[concepts/dimatii/kinai-maradektetel]] — konstruktív bizonyítás
