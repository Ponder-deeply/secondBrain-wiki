---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-06
---

# Gauss–Osztrogradszkij tétel (divergenciatétel)

A divergencia integrálja a tartományon egyenlő a vektormező határon vett fluxusával. Ez teszi pontossá, hogy a forrássűrűség összegzése kiadja a forráserősséget.

## Tartalom

### Síkban

**Tétel (2-dimenziós Gauss–Osztrogradszkij tétel).** Ha $\operatorname{cl}(K)\subset G\subset\mathbb{R}^2$, $K$ Jordan-tartomány, amelynek határa pozitív irányítású, szakaszonként folytonosan differenciálható görbe, és $\mathbf{f} : G\to\mathbb{R}^2$ folytonosan differenciálható vektormező, akkor

$$\int_K (\operatorname{div}\mathbf{f})\,\mathrm{d}A = \int_{\partial K}\langle \mathbf{f}, \mathbf{n}\,\mathrm{d}s\rangle .$$

*Bizonyítás.* A $\mathbf{n}\,\mathrm{d}s = (\mathrm{d}y, -\mathrm{d}x)^t$ átírással és a Green-tétel két állításával:

$$\int_{\partial K}\langle\mathbf{f}, \mathbf{n}\,\mathrm{d}s\rangle = \int_{\partial K} f_1\,\mathrm{d}y - \int_{\partial K} f_2\,\mathrm{d}x = \int_K (D_1f_1)\,\mathrm{d}A + \int_K (D_2f_2)\,\mathrm{d}A = \int_K (\operatorname{div}\mathbf{f})\,\mathrm{d}A. \qquad \square$$

### Térben

**Tétel (3-dimenziós Gauss–Osztrogradszkij tétel).** Ha $G\subset\mathbb{R}^3$ nyílt, $K\subset G$ korlátos, zárt krumpli, amelynek $\partial K$ határa darabonként folytonosan differenciálható felület, és ezeken az irányított normálvektor mindig kifelé mutat, továbbá $\mathbf{f} : G\to\mathbb{R}^3$ folytonosan differenciálható, akkor

$$\int_K (\operatorname{div}\mathbf{f})\,\mathrm{d}V = \int_{\partial K}\langle \mathbf{f}, \overrightarrow{\mathrm{d}A}\rangle .$$

*Bizonyítás.* A Green-tétel háromdimenziós változatát koordinátánként alkalmazva:

$$\int_K(\operatorname{div}\mathbf{f})\,\mathrm{d}V = \int_K \bigl(D_1f_1 + D_2f_2 + D_3f_3\bigr)\,\mathrm{d}V = \int_{\partial K}\bigl(f_1\overrightarrow{\mathrm{d}A}_1 + f_2\overrightarrow{\mathrm{d}A}_2 + f_3\overrightarrow{\mathrm{d}A}_3\bigr) = \int_{\partial K}\langle\mathbf{f}, \overrightarrow{\mathrm{d}A}\rangle. \qquad \square$$

Mindkét bizonyítás ugyanaz a mozdulat: a skaláris szorzatot koordinátákra bontjuk, és minden koordinátára a Green-tételt (illetve annak térbeli lemmáját) alkalmazzuk.

### Következmények

- **A divergencia koordinátafüggetlen definíciója.** Egy pontra összehúzódó tartományokkal:
  $$\operatorname{div} f(\mathbf{a}) = \lim_{r\to+0}\left(\frac{1}{2\pi r}\int_{|\mathbf{x}-\mathbf{a}|=r}\langle f(\mathbf{x}), \mathbf{n}\,\mathrm{d}s\rangle\right).$$
- **Divergenciamentes mező fluxusa.** Ha $\operatorname{div}\mathbf{f}\equiv 0$, akkor minden szép krumpli határán a felületi integrál nulla. Ez a primitív függvényről szóló elmélet felületi analogonjának kiindulópontja, és ezzel bizonyítható például, hogy $\mathbb{R}^3\setminus\{(0,0,0)\}$ nem homeomorf $\mathbb{R}^3$-mal.
- **Gauss-törvény.** A Maxwell-egyenletek I. és III. tagjának differenciális és integrális alakja között pontosan ez a tétel teremt kapcsolatot.

## Kapocs

- [[concepts/analiii/divergencia]] — az integrandus és a fizikai jelentése
- [[concepts/analiii/green-tetel]] — a bizonyítás eszköze síkban
- [[concepts/analiii/green-tetel-harom-dimenzioban]] — a bizonyítás eszköze térben
- [[concepts/analiii/feluleti-integral]] — a jobb oldalon álló fluxus fogalma
- [[concepts/analiii/stokes-tetel]] — a párja: cirkuláció fluxus helyett
- [[concepts/analiii/altalanos-stokes-tetel]] — a közös általánosítás, amelyben $*$ a skaláris szorzás
- [[concepts/analiii/maxwell-egyenletek-es-integraltetelek]] — a tétel fizikai alkalmazása
