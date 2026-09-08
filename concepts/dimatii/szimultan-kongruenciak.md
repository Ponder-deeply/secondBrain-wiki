---
tags: [concept]
sources: [DimatIIEa02.pdf]
derivation: source
updated: 2026-09-08
---

# Szimultán kongruenciák

Kongruenciarendszer: olyan $x$ egészet keresünk, amely egyszerre elégít ki több kongruenciát. A rendszer előbb normalizálható, majd a kínai maradéktétellel oldható meg.

## Tartalom

### A feladat

Keressünk olyan $x$-et, amelyre egyszerre teljesül
$$2x \equiv 1 \pmod 3, \qquad 4x \equiv 3 \pmod 5.$$

A kongruenciákat külön megoldva $x \equiv 2 \pmod 3$ és $x \equiv 2 \pmod 5$ adódik; látszik, hogy $x = 2$ megoldás. További megoldások: $2, 17, 32, \dots, 2 + 15\ell$.

### Normalizálás

Általánosan az
$$a_1x \equiv b_1 \pmod{m_1}, \quad \dots, \quad a_nx \equiv b_n \pmod{m_n}$$
rendszer minden egyes sora külön megoldható a [[concepts/dimatii/linearis-kongruencia]] módszerével, így a rendszer mindig
$$x \equiv c_1 \pmod{m_1}, \quad \dots, \quad x \equiv c_n \pmod{m_n}$$
alakra hozható.

### Relatív prím modulusok elérése

Feltehető, hogy a modulusok páronként relatív prímek. Ha például $m_1 = m_1'd$ és $m_2 = m_2'd$, akkor az első két sor helyettesíthető a
$$x \equiv c_1 \pmod{m_1'}, \quad x \equiv c_1 \pmod{d}, \quad x \equiv c_2 \pmod{m_2'}, \quad x \equiv c_2 \pmod{d}$$
négyessel. Ha itt $c_1 \not\equiv c_2 \pmod d$, akkor a rendszernek **nincs megoldása**; különben az egyik $d$ modulusú sor törölhető.

Ezután a rendszer megoldhatóságát és megoldásait a [[concepts/dimatii/kinai-maradektetel]] adja.

### Példák

**1.** $x \equiv 2 \pmod 3$, $x \equiv 3 \pmod 5$. Oldjuk meg a $3x_1 + 5x_2 = 1$ egyenletet: $x_1 = -3$, $x_2 = 2$. Ekkor $c_{1,2} = 3\cdot(-3)\cdot 3 + 5\cdot 2\cdot 2 = -27 + 20 = -7$. Összes megoldás: $\{-7 + 15\ell\} = \{8 + 15\ell \,:\, \ell \in \mathbb{Z}\}$.

**2.** $x \equiv 2 \pmod 3$, $x \equiv 3 \pmod 5$, $x \equiv 4 \pmod 7$. Az első kettőt összevonva ($c_{1,2} = 8$) marad $x \equiv 8 \pmod{15}$, $x \equiv 4 \pmod 7$. Oldjuk meg a $15x_{1,2} + 7x_3 = 1$ egyenletet: $x_{1,2} = 1$, $x_3 = -2$. Ekkor $c_{1,2,3} = 15\cdot 1\cdot 4 + 7\cdot(-2)\cdot 8 = 60 - 112 = -52$. Összes megoldás: $\{-52 + 105\ell\} = \{53 + 105\ell \,:\, \ell \in \mathbb{Z}\}$.

## Kapocs

- [[concepts/dimatii/kinai-maradektetel]] — a megoldhatóságot kimondó tétel
- [[concepts/dimatii/linearis-kongruencia]] — az egyes sorok normalizálása
- [[concepts/dimatii/kongruencia]] — az alapfogalom
- [[concepts/dimatii/bovitett-euklideszi-algoritmus]] — a példákban használt eszköz
