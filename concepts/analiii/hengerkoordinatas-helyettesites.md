---
tags: [concept]
sources: [An_III_Gyak_2022_tavasz.pdf, gyakorlat.pdf]
derivation: inferred
kind: procedure
element: fire
updated: 2026-10-21
---

# Hengerkoordinátás helyettesítés

A térbeli integráltranszformáció egyik nevezetes esete: az $(x,y)$ síkbeli koordinátapárt polárkoordinátázzuk, a $z$ koordinátát változatlanul hagyjuk; a Jacobi-determináns ugyanaz, mint a síkbeli polárkoordinátás helyettesítésé.

## Tartalom

### Definíció

A **hengerkoordinátás helyettesítés** a $g : \mathbb{R}^3 \to \mathbb{R}^3$,

$$g(r,\varphi,z) = (r\cos\varphi,\ r\sin\varphi,\ z), \qquad r \geq 0,\ \varphi \in [0, 2\pi),\ z \in \mathbb{R}$$

leképezés. A neve onnan ered, hogy az $r = \text{áll.}$ felületek az $Oz$ tengely körüli hengerpalástok.

### Jacobi-determináns

$$g'(r,\varphi,z) = \begin{bmatrix} \cos\varphi & -r\sin\varphi & 0 \\ \sin\varphi & r\cos\varphi & 0 \\ 0 & 0 & 1 \end{bmatrix}, \qquad \det g'(r,\varphi,z) = r.$$

A determináns kifejtése a harmadik sor szerint pontosan a síkbeli polárkoordinátás helyettesítés Jacobi-determinánsára ($r$) vezet vissza, hiszen a $z$ koordináta változatlan marad.

### Integráltranszformáció

A [[concepts/analiii/mertek-es-integraltranszformacio]] tételét alkalmazva, ha $H$ a hengerkoordinátás $(r,\varphi,z)$ térben Jordan-mérhető és $g$ injektív $\operatorname{int} H$-n, akkor

$$\iiint_{g[H]} f(x,y,z)\,\mathrm{d}x\,\mathrm{d}y\,\mathrm{d}z = \iiint_H f(r\cos\varphi, r\sin\varphi, z)\cdot r\,\mathrm{d}r\,\mathrm{d}\varphi\,\mathrm{d}z.$$

### Mikor érdemes használni

Hengerkoordináták akkor egyszerűsítik a számolást, ha a tartomány vagy az integrandus az $Oz$ tengely körül forgásszimmetrikus (pl. henger, kúp, forgástest), de a $z$ irányú kiterjedés nem gömbszerűen, hanem függetlenül változik a sugártól.

### Feladatok

- $\iiint_H(x^2+y^2)\,\mathrm{d}V$, $H$ az $x^2+y^2=2z$ paraboloid és a $z=2$ sík között: $r\le2$, $\frac{r^2}{2}\le z\le2$; $2\pi\int_0^2r^3\left(2-\frac{r^2}2\right)\mathrm{d}r=\frac{16\pi}{3}$. *(gyakorlat.pdf, Többdimenziós integrálok 13c)*
- A Viviani-test térfogata (hengerkoordinátákban $0\le r\le R\cos\varphi$, $|z|\le\sqrt{R^2-r^2}$), lásd [[concepts/analiii/grafikon-alatti-halmaz-terfogata]]. *(An III gyak. 12.)*

## Kapocs

- [[concepts/analiii/polarkoordinatas-helyettesites]] — a síkbeli eset, amelynek a hengerkoordináták a $z$ tengellyel kiegészített változata
- [[concepts/analiii/mertek-es-integraltranszformacio]] — az általános integráltranszformációs tétel, amelynek ez egy konkrét alkalmazása
- [[concepts/analiii/gombi-koordinatas-helyettesites]] — a másik nevezetes térbeli helyettesítés, forgásszimmetrikus (gömbszerű) tartományokra
- [[concepts/analiii/tobbszoros-integral-fizikai-alkalmazasai]] — hengerszimmetrikus testek tömegének, súlypontjának számítása jellemzően hengerkoordinátákban egyszerűbb
