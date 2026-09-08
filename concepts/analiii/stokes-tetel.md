---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-06
---

# Stokes-tétel síkban és térben

A rotáció integrálja a tartományon egyenlő a vektormező határon vett cirkulációjával. Ez teszi pontossá, hogy az örvénysűrűség összegzése kiadja az örvényerősséget.

## Tartalom

### Síkban

**Tétel (2-dimenziós Stokes-tétel).** Ha $\operatorname{cl}(K)\subset G\subset\mathbb{R}^2$, $K$ Jordan-tartomány, amelynek határa pozitív irányítású, szakaszonként folytonosan differenciálható görbe, és $\mathbf{f} : G\to\mathbb{R}^2$ folytonosan differenciálható vektormező, akkor

$$\int_K (\operatorname{rot}\mathbf{f})\,\mathrm{d}A = \int_{\partial K}\langle\mathbf{f}, \mathrm{d}\mathbf{x}\rangle = -\int_{\partial K}\mathbf{f}\times(\mathbf{n}\,\mathrm{d}s).$$

*Bizonyítás.* A második két integrál azonos, mert

$$-\mathbf{f}\times(\mathbf{n}\,\mathrm{d}s) = -(f_1,f_2)\times(\mathrm{d}y, -\mathrm{d}x) = f_1\,\mathrm{d}x + f_2\,\mathrm{d}y = \langle\mathbf{f}, \mathrm{d}\mathbf{x}\rangle .$$

Ezután a Green-tételt kétszer alkalmazva,

$$\int_{\partial K}\langle\mathbf{f},\mathrm{d}\mathbf{x}\rangle = \int_{\partial K}(f_1\,\mathrm{d}x + f_2\,\mathrm{d}y) = \int_K\bigl(-D_2f_1 + D_1f_2\bigr)\,\mathrm{d}A = \int_K(\operatorname{rot}\mathbf{f})\,\mathrm{d}A. \qquad \square$$

Megjegyzés: a tétel adja a rotáció koordinátafüggetlen definícióját, egy pontra összehúzódó tartományokkal:

$$\operatorname{rot}\mathbf{f}(\mathbf{a}) = -\lim_{r\to+0}\frac{1}{2\pi}\int_{|\mathbf{x}-\mathbf{a}|=r}\mathbf{f}\times\mathbf{n}\,\mathrm{d}s .$$

### Térben

**Tétel (Stokes).** Ha $G\subset\mathbb{R}^3$ nyílt, $K\subset G$ korlátos, zárt krumpli, amelynek $\partial K$ határa darabonként folytonosan differenciálható felület, ezeken az irányított normálvektor mindig kifelé mutat, és $\mathbf{f} : G\to\mathbb{R}^3$ folytonosan differenciálható, akkor

$$\int_K (\operatorname{rot}\mathbf{f})\,\mathrm{d}V = -\int_{\partial K}\mathbf{f}\times\overrightarrow{\mathrm{d}A}.$$

*Bizonyítás.* Koordinátánként, a Green-tétel háromdimenziós lemmájával:

$$\int_K(\operatorname{rot}\mathbf{f})\,\mathrm{d}V = \begin{pmatrix}\int_K D_2f_3\,\mathrm{d}V - \int_K D_3f_2\,\mathrm{d}V \\ \int_K D_3f_1\,\mathrm{d}V - \int_K D_1f_3\,\mathrm{d}V \\ \int_K D_1f_2\,\mathrm{d}V - \int_K D_2f_1\,\mathrm{d}V\end{pmatrix} = \begin{pmatrix}\int_{\partial K} f_3\overrightarrow{\mathrm{d}A}_2 - \int_{\partial K} f_2\overrightarrow{\mathrm{d}A}_3 \\ \int_{\partial K} f_1\overrightarrow{\mathrm{d}A}_3 - \int_{\partial K} f_3\overrightarrow{\mathrm{d}A}_1 \\ \int_{\partial K} f_2\overrightarrow{\mathrm{d}A}_1 - \int_{\partial K} f_1\overrightarrow{\mathrm{d}A}_2\end{pmatrix} = \int_{\partial K}\bigl(-\mathbf{f}\times\overrightarrow{\mathrm{d}A}\bigr). \qquad \square$$

A negatív előjel forrása mindkét dimenzióban a vektoriális (illetve kereszt-) szorzás antiszimmetriája: a tényezőket fordított sorrendben szeretjük írni.

### Óvatosan: két különböző „Stokes-tétel"

A fenti térbeli Stokes-tétel **testre és annak zárt határfelületére** vonatkozik. Az, amit a fizikában rendszerint Stokes-tételként emlegetnek — a rotáció fluxusa egy peremes felületen egyenlő a perem menti cirkulációval — a [[concepts/analiii/kelvin-stokes-tetel]], és az valójában a **kétdimenziós** Stokes-tétel kiterjesztése felületdarabokra.

## Kapocs

- [[concepts/analiii/rotacio]] — az integrandus és a fizikai jelentése
- [[concepts/analiii/green-tetel]] — a bizonyítás eszköze síkban
- [[concepts/analiii/green-tetel-harom-dimenzioban]] — a bizonyítás eszköze térben
- [[concepts/analiii/kelvin-stokes-tetel]] — a peremes felületekre szóló változat
- [[concepts/analiii/gauss-osztrogradszkij-tetel]] — a párja: fluxus cirkuláció helyett
- [[concepts/analiii/altalanos-stokes-tetel]] — a közös általánosítás, amelyben $*$ a vektoriális szorzás
- [[concepts/analiii/valos-vonalintegral]] — a cirkuláció mint valós vonalintegrál
