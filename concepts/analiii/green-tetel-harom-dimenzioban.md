---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-06
---

# A Green-tétel három-dimenziós változata

Egyetlen parciális derivált térfogati integrálját a határfelületen vett, a megfelelő koordinátájú felületelemmel vett integrállal fejezi ki. Ez a lemma minden térbeli integráltétel közös építőköve.

## Tartalom

### A lemma

**Lemma.** Legyen $G\subset\mathbb{R}^3$ nyílt, $K\subset G$ korlátos, zárt krumpli, amelynek $\partial K$ határa darabonként folytonosan differenciálható felület, és ezeken az irányított normálvektor mindig kifelé mutat; legyen továbbá $f : G\to\mathbb{R}$ folytonosan differenciálható és $i\in\{1,2,3\}$. Ekkor

$$\int_K (D_i f)\,\mathrm{d}V = \int_{\partial K} f\cdot\overrightarrow{\mathrm{d}A}_i .$$

Itt $\mathrm{d}V = \mathrm{d}x\,\mathrm{d}y\,\mathrm{d}z$ a térfogatelem, $\overrightarrow{\mathrm{d}A}_i$ pedig a $\overrightarrow{\mathrm{d}A}$ területvektor $i$-edik koordinátája.

Az alak pontosan a síkbeli Green-tételé, egy dimenzióval feljebb: bal oldalon egyetlen derivált a testen, jobb oldalon a függvény maga a határon, a határ „$i$-edik irányú vetületével" súlyozva.

### Bizonyítás (szép normáltartományokra)

A $z$-koordinátára bizonyítunk, azaz $i = 3$, és feltesszük, hogy $K$ normáltartomány a $P$ szép paramétertartomány fölött: az alsó és a felső határoló grafikon $\varphi(x,y)$ és $\psi(x,y)$, tehát

$$K = \{(x,y,z) : (x,y)\in P,\ \varphi(x,y)\le z\le\psi(x,y)\}.$$

A határ függőleges darabjain $\overrightarrow{\mathrm{d}A}_3 = 0$ (ott a normális vízszintes), tehát azok nem adnak járulékot. Az alsó grafikonon a **lefelé** mutató normálvektort kell használnunk — ezért fordul meg ott az előjel. A grafikon felületelemére vonatkozó lemmát behelyettesítve:

$$\int_{\partial K} f\,\overrightarrow{\mathrm{d}A}_3 = \int_{(x,y)\in P} f(x,y,\psi(x,y))\cdot 1\,\mathrm{d}x\,\mathrm{d}y + \int_{(x,y)\in P} f(x,y,\varphi(x,y))\cdot(-1)\,\mathrm{d}x\,\mathrm{d}y$$

$$= \int_{(x,y)\in P}\bigl( f(x,y,\psi(x,y)) - f(x,y,\varphi(x,y)) \bigr)\,\mathrm{d}x\,\mathrm{d}y = \int_{(x,y)\in P}\left(\int_{\varphi(x,y)}^{\psi(x,y)} D_3f(x,y,z)\,\mathrm{d}z\right)\mathrm{d}x\,\mathrm{d}y = \int_K D_3f\,\mathrm{d}V. \qquad \square$$

A lényeg megint ugyanaz, mint síkban: minden függőleges szekción az **egyváltozós Newton–Leibniz formulát** alkalmazzuk, és a két végponti érték a felső, illetve alsó határfelület járuléka lesz.

### Mire használjuk

A lemmából koordinátánkénti alkalmazással közvetlenül adódik

- a térbeli Newton–Leibniz formula ($\operatorname{grad}$, skalár-vektor szorzással),
- a 3-dimenziós Gauss–Osztrogradszkij tétel ($\operatorname{div}$, skaláris szorzással),
- a térbeli Stokes-tétel ($\operatorname{rot}$, vektoriális szorzással).

Mindhárom ugyanennek a lemmának a három koordinátára vett, más-más szorzással összefésült változata — ezt teszi explicitté az általános Stokes-tétel.

## Kapocs

- [[concepts/analiii/green-tetel]] — a síkbeli eredeti, amelynek ez a térbeli megfelelője
- [[concepts/analiii/parameteres-felulet]] — a bizonyításban használt grafikon-felületelem
- [[concepts/analiii/newton-leibniz-formula-tobbvaltozos]] — a lemma első következménye
- [[concepts/analiii/gauss-osztrogradszkij-tetel]] — a lemma következménye skaláris szorzással
- [[concepts/analiii/stokes-tetel]] — a lemma következménye vektoriális szorzással
- [[concepts/analii/newton-leibniz-tetel]] — az egyváltozós formula, amelyet a szekciókon alkalmazunk
