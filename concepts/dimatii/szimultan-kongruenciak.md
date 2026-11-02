---
tags: [concept]
sources: [DimatIIEa02.pdf, dimat2gyak04mo.pdf, dm2gy04_Szamelmelet.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-10-21
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

### Feladattípusok (gyakorlat 4.)

A „számrendszerbeli utolsó jegyek" feladat egymásba ágyazott kongruenciarendszer ($7 \mid 49$ típusú modulusok, így nem a kínai maradéktétel, hanem lépcsőzetes megoldás kell): előbb az utolsó jegyre vonatkozó feltételt oldjuk meg modulo $p$, majd az $x = pn + x_0$ alakot a mod $p^2$ feltételbe írva $n$-et határozzuk meg. A részletes kidolgozás ($13x$ utolsó két jegye $43_7$) a [[concepts/dimatii/linearis-kongruencia]] lapon van. A rendszer sorait a lap „Normalizálás" szakasza szerint előbb $x \equiv c \pmod m$ alakra kell hozni (relatív prímmel egyszerűsítve, a modulust is osztva).

### Feladattípusok és megoldások (2020. 4. feladatsor)

**Módszer.** (1) Minden sort $x \equiv c_i \pmod{m_i}$ alakra hozunk ([[concepts/dimatii/linearis-kongruencia]]); (2) páronkénti kompatibilitás: $c_i \equiv c_j \pmod{(m_i,m_j)}$ (különben nincs megoldás); (3) kínai maradéktétellel vagy lépcsőzetesen összevonunk; az eredmény egy osztály mod $[m_1,\dots,m_n]$. Az 1. feladat rendszerei:

| rendszer | normalizálva | megoldás |
|---|---|---|
| a) $x\equiv 2\ (3)$, $x\equiv 3\ (4)$, $x\equiv 1\ (5)$ | — | $x \equiv 11 \pmod{60}$ |
| b) $5x\equiv 3\ (7)$, $3x\equiv 7\ (8)$ | $x \equiv 2\ (7)$, $x \equiv 5\ (8)$ | $x \equiv 37 \pmod{56}$ |
| c) $3x\equiv 2\ (4)$, $4x\equiv 3\ (5)$ | $x \equiv 2\ (4)$, $x \equiv 2\ (5)$ | $x \equiv 2 \pmod{20}$ |
| d) $5x\equiv 1\ (6)$, $7x\equiv 9\ (10)$ | $x \equiv 5\ (6)$, $x \equiv 7\ (10)$ | $x \equiv 17 \pmod{30}$ (a $2$-es közös osztónál mindkettő páratlan) |
| e) $5x\equiv 2\ (6)$, $7x\equiv 3\ (10)$ | $x \equiv 4\ (6)$, $x \equiv 9\ (10)$ | **nincs**: $x$ páros és páratlan is lenne |
| f) $4x\equiv 2\ (3)$, $3x\equiv 2\ (7)$, $9x\equiv 7\ (11)$ | $x \equiv 2\ (3)$, $3\ (7)$, $2\ (11)$ | $x \equiv 101 \pmod{231}$ |
| g) $3x\equiv 1\ (4)$, $7x\equiv 2\ (9)$, $9x\equiv 3\ (13)$ | $x \equiv 3\ (4)$, $8\ (9)$, $9\ (13)$ | $x \equiv 35 \pmod{468}$ |
| h) $5x\equiv 3\ (6)$, $3x\equiv 9\ (10)$, $8x\equiv 9\ (15)$ | $x \equiv 3\ (6)$, $3\ (10)$, $3\ (15)$ | $x \equiv 3 \pmod{30}$ |

**Számjegyfeladatok és szöveges feladatok.**
- $23x$ hetes számrendszerben $\ldots 25_{(7)}$ ($x < 100$): $23x \equiv 2\cdot 7 + 5 = 19 \pmod{49}$, $x \equiv 20 \pmod{49}$: $x = 20$ és $69$ ($23\cdot 20 = 460 = 9\cdot 49 + 19$).
- Kínai maradéktétellel: $3$-mal osztva $1$, $4$-gyel $2$, $5$-tel $3$ maradékot adó egészek: $x \equiv 58 \pmod{60}$.
- Legkisebb természetes szám, amely $28$-as alapon $3$-ra, $19$-es alapon $4$-re végződik: $x \equiv 3 \pmod{28}$, $x \equiv 4 \pmod{19}$, $x \equiv 479 \pmod{532}$, a legkisebb $479$ ($479 = 17\cdot 28 + 3 = 25\cdot 19 + 4$).
- $463$ felbontása $14$-gyel és $23$-mal osztható tagokra: $463 = 14k + 23l$, $14k \equiv 463 \equiv 3 \pmod{23}$, $k \equiv 15$, tehát $463 = 210 + 253$ (az egyetlen pozitív felbontás).

**Általános eset** (6–7. szorgalmi feladat; a forrás megoldása nincs megadva): nem relatív prím modulusokra a rendszer pontosan akkor megoldható, ha minden $i \neq j$ párra $c_i \equiv c_j \pmod{(m_i,m_j)}$; a megoldás ekkor egy osztály mod $[m_1,\dots,m_n]$ — ez a lap „Relatív prím modulusok elérése" szakaszának általánosítása.

**Tipikus hibák.** Normalizálás nélkül közvetlenül összevonni ($5x \equiv 1 \pmod 6$ megoldása $x \equiv 5$, nem $c = 1$); a nem relatív prím modulusok közös osztóját figyelmen kívül hagyni (e) eset); a $[m_1,\dots,m_n]$ helyett a szorzatot venni modulusnak.

## Kapocs

- [[concepts/dimatii/kinai-maradektetel]] — a megoldhatóságot kimondó tétel
- [[concepts/dimatii/linearis-kongruencia]] — az egyes sorok normalizálása
- [[concepts/dimatii/kongruencia]] — az alapfogalom
- [[concepts/dimatii/bovitett-euklideszi-algoritmus]] — a példákban használt eszköz
- [[concepts/dimatii/utolso-jegyek-kongruenciaval]] — jegyfeltételek két számrendszerben egyszerre
