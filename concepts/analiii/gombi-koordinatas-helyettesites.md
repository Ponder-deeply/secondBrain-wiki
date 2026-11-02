---
tags: [concept]
sources: [An_III_Gyak_2022_tavasz.pdf, gyakorlat.pdf]
derivation: inferred
kind: procedure
element: fire
updated: 2026-10-21
---

# Gömbi (térbeli polár-) koordinátás helyettesítés

A térbeli integráltranszformáció másik nevezetes esete: egy pontot az origótól mért $r$ távolságával és két szöggel ($\varphi$ azimutszög, $\theta$ a $z$ tengellyel bezárt szög) írunk le; a Jacobi-determináns $r^2\sin\theta$, ami tipikus alkalmazásként a gömb térfogatának kiszámítására vezet.

## Tartalom

### Definíció

A **térbeli (gömbi) polárkoordinátás helyettesítés** a $g : \mathbb{R}^3 \to \mathbb{R}^3$,

$$g(r,\theta,\varphi) = (r\sin\theta\cos\varphi,\ r\sin\theta\sin\varphi,\ r\cos\theta), \qquad r \geq 0,\ \theta \in [0,\pi],\ \varphi \in [0,2\pi)$$

leképezés, ahol $r$ az origótól mért távolság, $\theta$ a $z$ tengellyel bezárt szög (poláris szög), $\varphi$ pedig az $(x,y)$-síkra vett vetület azimutszöge — ugyanaz a szög, mint a hengerkoordinátás helyettesítésben.

### Jacobi-determináns

$$g'(r,\theta,\varphi) = \begin{bmatrix} \sin\theta\cos\varphi & r\cos\theta\cos\varphi & -r\sin\theta\sin\varphi \\ \sin\theta\sin\varphi & r\cos\theta\sin\varphi & r\sin\theta\cos\varphi \\ \cos\theta & -r\sin\theta & 0 \end{bmatrix}$$

$$\det g'(r,\theta,\varphi) = r^2\sin\theta.$$

Mivel $\theta \in [0,\pi]$-n $\sin\theta \geq 0$, ezért $|\det g'| = r^2\sin\theta$.

### Integráltranszformáció

A [[concepts/analiii/mertek-es-integraltranszformacio]] tételét alkalmazva, ha $H$ a gömbi koordináták $(r,\theta,\varphi)$ terében Jordan-mérhető és $g$ injektív $\operatorname{int} H$-n, akkor

$$\iiint_{g[H]} f(x,y,z)\,\mathrm{d}x\,\mathrm{d}y\,\mathrm{d}z = \iiint_H f(r\sin\theta\cos\varphi,\ r\sin\theta\sin\varphi,\ r\cos\theta)\cdot r^2\sin\theta\,\mathrm{d}r\,\mathrm{d}\theta\,\mathrm{d}\varphi.$$

### Példa: a gömb térfogata

Az $r_0$ sugarú, origó középpontú gömb ($x^2+y^2+z^2 \leq r_0^2$) a gömbi koordinátákban a $H = [0,r_0]\times[0,\pi]\times[0,2\pi)$ tégla képe, ezért a térfogata

$$V = \iiint_H r^2\sin\theta\,\mathrm{d}r\,\mathrm{d}\theta\,\mathrm{d}\varphi = \int_0^{r_0} r^2\,\mathrm{d}r \cdot \int_0^\pi \sin\theta\,\mathrm{d}\theta \cdot \int_0^{2\pi} \mathrm{d}\varphi = \frac{r_0^3}{3}\cdot 2 \cdot 2\pi = \frac{4}{3}\pi r_0^3,$$

összhangban a [[concepts/analiii/p-dimenzios-gomb-terfogata]] lapon szereplő $\gamma_3 = \tfrac{4}{3}\pi$ konstanssal.

### Mikor érdemes használni

Gömbi koordináták akkor egyszerűsítik a számolást, ha a tartomány vagy az integrandus az origó körül gömbszimmetrikus (pl. gömb, gömbhéj, kúp az origóból nézve), szemben a hengerkoordinátákkal, amelyek tengelyszimmetrikus, de $z$-ben nem gömbszerűen változó tartományokra valók.

### Feladatok

- Az $\frac{x^2}{a^2}+\frac{y^2}{b^2}+\frac{z^2}{c^2}\le1$ ellipszoid térfogata: $x=ar\sin\theta\cos\varphi$, $y=br\sin\theta\sin\varphi$, $z=cr\cos\theta$, Jacobi-determináns $abc\,r^2\sin\theta$, így $V=abc\cdot\frac{4\pi}{3}$. *(An III gyak. 12.)*
- $\iiint_H\sqrt{x^2+y^2+z^2}$, $H$ az $x^2+y^2+z^2\le z$ gömb: a határ $\rho=\cos\theta$, $0\le\theta\le\frac\pi2$; $2\pi\int_0^{\pi/2}\sin\theta\int_0^{\cos\theta}\rho^3\,\mathrm{d}\rho\,\mathrm{d}\theta=\frac{\pi}{10}$. *(gyakorlat.pdf, Többdimenziós integrálok 13d)*
- Ellenőrző alkalmazások a gyakorlatról: gömb térfogata és felszíne, gömb tehetetlenségi nyomatéka a középpontján átmenő tengelyre. *(gyakorlat.pdf, 16.)*

## Kapocs

- [[concepts/analiii/hengerkoordinatas-helyettesites]] — a másik nevezetes térbeli helyettesítés, tengelyszimmetrikus tartományokra
- [[concepts/analiii/polarkoordinatas-helyettesites]] — a síkbeli eset, amelyből a $\varphi$ szög és az $r\sin\theta$ vetületi sugár öröklődik
- [[concepts/analiii/mertek-es-integraltranszformacio]] — az általános integráltranszformációs tétel, amelynek ez egy konkrét alkalmazása
- [[concepts/analiii/p-dimenzios-gomb-terfogata]] — a gömb térfogatának másik, szelettétellel kapott levezetése; ugyanaz az eredmény két úton
