---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-06
---

# Gauss-integrál

A $\int_{-\infty}^{\infty} e^{-x^2}\,\mathrm{d}x = \sqrt{\pi}$ nevezetes improprius integrál, amelynek kiszámítása az integrál négyzetét kétdimenziós integrállá alakítja, majd polárkoordinátázik.

## Tartalom

### A tétel

$$\int_0^\infty e^{-x^2}\,\mathrm{d}x = \frac{\sqrt{\pi}}{2}, \qquad \int_{-\infty}^\infty e^{-x^2}\,\mathrm{d}x = \sqrt{\pi}, \qquad \int_{-\infty}^\infty e^{-\frac{1}{2}x^2}\,\mathrm{d}x = \sqrt{2\pi}.$$

A három állítás az $x = \sqrt{2}\,y$ helyettesítéssel, illetve a páros integrandus miatti felezéssel egymásba vihető; elég tehát a középsőt igazolni.

### A bizonyítás terve

Az $e^{-x^2}$ függvénynek nincs elemi primitív függvénye, ezért az integrált **nem** a Newton–Leibniz-formulával kapjuk meg. A trükk: az integrál **négyzetét** számoljuk ki, mert

$$e^{-x^2} \cdot e^{-y^2}\,\mathrm{d}x\,\mathrm{d}y = e^{-(x^2+y^2)}\,\mathrm{d}x\,\mathrm{d}y = e^{-r^2}\, r\,\mathrm{d}r\,\mathrm{d}\varphi,$$

vagyis a kétdimenziós integrandus forgásszimmetrikus, és polárkoordinátákban azonnal integrálható.

### A bizonyítás

Legyen $R > 0$ esetén $I(R) = \int_{-R}^{R} e^{-x^2}\,\mathrm{d}x$; ekkor $\int_{-\infty}^{\infty} e^{-x^2}\,\mathrm{d}x = \lim_{R \to \infty} I(R)$. A szorzatfüggvények integráljáról szóló tétel szerint

$$(I(R))^2 = \left(\int_{-R}^{R} e^{-x^2}\,\mathrm{d}x\right)\left(\int_{-R}^{R} e^{-y^2}\,\mathrm{d}y\right) = \int_{[-R,R]\times[-R,R]} e^{-(x^2+y^2)}\,\mathrm{d}x\,\mathrm{d}y.$$

Ez tehát egy **négyzeten** vett integrál, a polárkoordinátázás viszont **körlapon** kényelmes. Ezért a négyzetet a beírt és a köréírt körrel szorítjuk közre:

$$B(0,R) \subset [-R,R]\times[-R,R] \subset B(0,\sqrt{2}R).$$

Mivel az integrandus pozitív, az alsó becslés:

$$(I(R))^2 > \int_{B(0,R)} e^{-(x^2+y^2)}\,\mathrm{d}x\,\mathrm{d}y = \int_{r=0}^{R}\left(\int_{\varphi=0}^{2\pi} e^{-r^2} r\,\mathrm{d}\varphi\right)\mathrm{d}r = \int_{r=0}^{R} 2\pi e^{-r^2} r\,\mathrm{d}r = \Bigl[-\pi e^{-r^2}\Bigr]_{r=0}^{R} = \pi\left(1 - e^{-R^2}\right).$$

A felső becslés ugyanez a számolás, csak a kör sugara $\sqrt{2}R$:

$$(I(R))^2 < \int_{B(0,\sqrt{2}R)} e^{-(x^2+y^2)}\,\mathrm{d}x\,\mathrm{d}y = \pi\left(1 - e^{-2R^2}\right).$$

Gyököt vonva

$$\sqrt{\pi} \cdot \sqrt{1 - e^{-R^2}} < I(R) < \sqrt{\pi} \cdot \sqrt{1 - e^{-2R^2}}.$$

Mindkét becslés $\sqrt{\pi}$-hez tart, tehát a rendőrelv szerint

$$\int_{-\infty}^{\infty} e^{-x^2}\,\mathrm{d}x = \lim_{R \to \infty} I(R) = \sqrt{\pi}.$$

### Miért fontos

A $\frac{1}{\sqrt{2\pi}} e^{-\frac{1}{2}x^2}$ függvény éppen a standard normális eloszlás sűrűségfüggvénye; a harmadik formula az, ami a $\frac{1}{\sqrt{2\pi}}$ normálótényezőt megmagyarázza.

## Kapocs

- [[concepts/analiii/polarkoordinatas-helyettesites]] — a bizonyítás gerince: ez alakítja a kétdimenziós integrált elemien számolhatóvá.
- [[concepts/analiii/szorzathalmaz-merteke-es-integralja]] — ez indokolja, hogy $(I(R))^2$ egyetlen kétdimenziós integrállá írható át.
- [[concepts/analii/improprius-integral]] — a nem korlátos értelmezési tartományon vett integrál egyváltozós fogalma; a Gauss-integrál ennek egy nevezetes, konvergens példája.
- [[concepts/analiii/gamma-fuggveny]] — szintén improprius paraméteres integrál, és $\Gamma(1/2) = \sqrt{\pi}$ révén közvetlenül kapcsolódik.
