---
tags: [concept]
sources: [SimonP-Anal2.pdf]
references: ["Simon Péter: Analízis II., 4.4. i)–iii) megjegyzés"]
derivation: source
updated: 2026-09-07
---

# Laplace-operátor és a radiális függvények

A $\Delta F := \sum_{i=1}^n \partial_{ii}F$ operátor a másodrendű parciális deriváltak legfontosabb kombinációja; radiálisan szimmetrikus függvényre egyváltozós alakra egyszerűsödik.

## Tartalom

### Az operátor

$F \in \mathbb{R}^n \to \mathbb{R}$, $F \in D^2$ esetén

$$\Delta F := \sum_{i=1}^n \partial_{ii}F,$$

azaz a [[concepts/analiii/hesse-matrix|Hesse-mátrix]] nyoma. Ugyanez $\Delta F = \operatorname{div}(\operatorname{grad} F)$ alakban is írható, lásd [[concepts/analiii/divergencia]].

### Radiális függvények

Legyen $r(x) := \sqrt{\sum_{i=1}^n x_i^2} = \|x\|_2$ és $f : (0,\infty) \to \mathbb{R}$, $f \in D^2$. Ekkor az $F := f \circ r$ radiális függvényre

$$\Delta F = f'' \circ r + \frac{n-1}{r}\cdot f' \circ r.$$

A parciális derivált kétszeri, [[concepts/analiii/lancszabaly|láncszabállyal]] való kiszámítása után a $\sum_i x_i^2 / r^2 = 1$ azonosság gyűjti össze a tagokat; az $(n-1)/r$ tag a dimenziófüggés, és ez az, amiért a Laplace-egyenlet megoldásai dimenziónként mások.

**Speciális eset.** $F := 1/r$ és $n = 3$ mellett $f(r) = 1/r$, $f' = -1/r^2$, $f'' = 2/r^3$, tehát

$$\Delta F = \frac{2}{r^3} + \frac{2}{r}\cdot\left(-\frac{1}{r^2}\right) = 0,$$

azaz $1/r$ kielégíti a **Laplace-egyenletet** $\mathbb{R}^3 \setminus \{0\}$-n. Ez a pontszerű forrás potenciálja, a térelmélet alapmegoldása.

### Három nevezetes egyenlet

| Egyenlet | Alak | Példamegoldás |
|---|---|---|
| hővezetési | $\partial_t f = a^2 \partial_{xx} f$ | $f(x,t) = \dfrac{1}{2a\sqrt{\pi t}}\exp\!\left(-\dfrac{(x-b)^2}{4a^2 t}\right)$ |
| Helmholtz | $\partial_{xx}f + \partial_{yy}f + \partial_{zz}f = c^2 f$ | $f = \dfrac{a e^{-cr} + b e^{cr}}{r}$, ahol $r = \sqrt{x^2+y^2+z^2}$ |
| Laplace | $\Delta F = 0$ | $F = 1/r$ ($n = 3$) |

Mindhárom közvetlen behelyettesítéssel ellenőrizhető; a fizikai jelentésük az, ami a többváltozós differenciálszámítást a matematikai fizika nyelvévé teszi.

## Kapocs

- [[concepts/analiii/magasabbrendu-parcialis-derivaltak]] — az operátorban szereplő deriváltak.
- [[concepts/analiii/hesse-matrix]] — a $\Delta$ ennek a nyoma.
- [[concepts/analiii/divergencia]] — a $\Delta = \operatorname{div}\operatorname{grad}$ felbontás.
- [[concepts/analiii/lancszabaly]] — a radiális formula levezetése.
- [[concepts/analiii/maxwell-egyenletek-es-integraltetelek]] — a fizikai alkalmazások másik iránya.
