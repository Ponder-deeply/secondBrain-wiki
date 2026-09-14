---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf, 11_ea_An3_2022_tavasz.pdf]
derivation: source
updated: 2026-09-14
---

# A többszörös integrál fizikai alkalmazásai

Adott sűrűségfüggvényű test tömege, tömegközéppontja és tehetetlenségi nyomatéka mind a Jordan-mérték szerinti hármas integrállal fejezhető ki, és szukcesszív integrálással számolható ki.

## Tartalom

### Alapmennyiségek

Legyen $A \in \mathcal{J}_3$ egy test, és $\varrho : A \to [0,\infty)$ az $A$ **sűrűségfüggvénye**.

**Tömeg:**

$$m = \int_A \varrho(x,y,z)\,\mathrm{d}x\mathrm{d}y\mathrm{d}z.$$

**Tömegközéppont** (súlypont):

$$(S_x, S_y, S_z) = \left(\frac{\int_A x\varrho\,\mathrm{d}x\mathrm{d}y\mathrm{d}z}{m},\ \frac{\int_A y\varrho\,\mathrm{d}x\mathrm{d}y\mathrm{d}z}{m},\ \frac{\int_A z\varrho\,\mathrm{d}x\mathrm{d}y\mathrm{d}z}{m}\right).$$

**Tehetetlenségi nyomaték a $z$ tengelyre:**

$$\Theta_z = \int_A (x^2+y^2)\varrho(x,y,z)\,\mathrm{d}x\mathrm{d}y\mathrm{d}z,$$

ahol $x^2+y^2$ éppen a $(x,y,z)$ pont $z$ tengelytől mért távolságának négyzete.

Homogén test esetén ($\varrho$ konstans) a sűrűség kiemelhető, és a tömegközéppont a geometriai súlyponttá egyszerűsödik.

### Példa: a homogén félgömb súlypontja

Számítsuk ki az $x^2+y^2+z^2 \leq r^2$, $z \geq 0$ homogén félgömb súlypontját. Szimmetriaokokból $S_x = S_y = 0$, és

$$m = \frac{2\pi}{3}r^3\varrho.$$

A $z$ koordinátára szukcesszív integrálással, $z$ szerint kifelé haladva: a $z$ magasságú szelet egy $\sqrt{r^2-z^2}$ sugarú körlap, amelynek területe $\pi(r^2-z^2)$, ezért

$$S_z = \frac{1}{m}\int_{z=0}^{r}\left(\int_{x^2+y^2\leq r^2-z^2} z\varrho\,\mathrm{d}x\mathrm{d}y\right)\mathrm{d}z = \frac{\varrho}{m}\int_{z=0}^{r}\pi(r^2z - z^3)\,\mathrm{d}z = \frac{\pi\varrho}{m}\cdot\frac{r^4}{4} = \frac{3}{8}r.$$

A félgömb súlypontja tehát az alaplaptól a sugár $3/8$ részére esik.

## Kapocs

- [[concepts/analiii/szukcessziv-integralas]] — a számolás technikája: a hármas integrált egyváltozós integrálásokra bontjuk
- [[concepts/analiii/jordan-mertek-szeletelessel]] — a példában a $z$ magasságú szeletek területével dolgozunk
- [[concepts/analiii/grafikon-alatti-halmaz-terfogata]] — a $\varrho \equiv 1$ eset, amikor a tömeg éppen a térfogat
- [[concepts/analiii/gombi-koordinatas-helyettesites]] — gömbszimmetrikus testek (pl. félgömb) tömegének, súlypontjának számítása gyakran gömbi koordinátákban egyszerűbb
- [[concepts/analii/kozeptertekek]] — a tömegközéppont formálisan egy súlyozott integrálközép; az egyváltozós integrálközép-tételek ennek egydimenziós előképei
