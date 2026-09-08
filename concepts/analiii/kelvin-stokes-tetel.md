---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-06
---

# Kelvin–Stokes tétel

A rotáció fluxusa egy peremes felületen egyenlő a vektormező perem menti cirkulációjával. A kétdimenziós Stokes-tétel kiterjesztése görbült felületdarabokra; ez az az integráltétel, amelyre a II. és IV. Maxwell-egyenlethez szükség van.

## Tartalom

### A tétel

**Tétel (Kelvin–Stokes).** Ha $S\subset G$ egy irányított, **peremes** felület — mondjuk darabonként folytonosan differenciálható, a határa pedig szakaszonként $C^1$ —, valamint $\mathbf{f} : G\to\mathbb{R}^3$ folytonosan differenciálható vektormező, akkor

$$\int_S \bigl\langle \operatorname{rot}\mathbf{f}, \overrightarrow{\mathrm{d}A}\bigr\rangle = \int_{\partial S}\langle \mathbf{f}, \mathrm{d}\mathbf{x}\rangle .$$

A jegyzet bizonyítás nélkül közli.

### Miben más, mint a térbeli Stokes-tétel

A [[concepts/analiii/stokes-tetel]] térbeli alakja **testre** és annak **zárt** határfelületére vonatkozik; ott a bal oldalon térfogati integrál áll. Itt viszont $S$ maga egy felületdarab, amelynek van pereme, és a bal oldal felületi integrál, a jobb oldal vonalintegrál. Jól felismerhető, hogy ez valójában a **kétdimenziós** Stokes-tétel kiterjesztése felületdarabokra: ha $S$ egy síkbeli Jordan-tartomány a $z=0$ síkban, akkor $\overrightarrow{\mathrm{d}A} = (0,0,1)\,\mathrm{d}A$, a skaláris szorzat a rotáció harmadik koordinátáját emeli ki — azaz éppen a síkbeli $\operatorname{rot}\mathbf{f}$-et —, és pontosan a síkbeli Stokes-tételt kapjuk vissza.

### Következmény: az irányítás szabadsága

Mivel a jobb oldal csak a peremtől függ, a bal oldal **nem függ attól, melyik peremes felületet feszítjük ki** az adott zárt görbére. Ez az elektrodinamikai alkalmazások kulcsa: az Ampère-törvényben a görbén átfolyó áram bármely, a görbére kifeszített felületen mérhető.

### Az Ampère-törvény levezetése

A Maxwell-féle kiegészítés nélküli Ampère-törvény differenciális alakja $\nabla\times\mathbf{B} = \mu_0\mathbf{J}$ (időben állandó elektromos mező esetén). Egy peremes $S$ felületre integrálva és a Kelvin–Stokes tételt alkalmazva:

$$\int_{\partial S}\langle B, \mathrm{d}\mathbf{x}\rangle \overset{\text{KSt}}{=} \int_S\bigl\langle \operatorname{rot} B, \overrightarrow{\mathrm{d}A}\bigr\rangle \overset{\text{M.IV.}}{=} \int_S\langle \mu_0 J, \overrightarrow{\mathrm{d}A}\rangle = \mu_0\int_S\langle J, \overrightarrow{\mathrm{d}A}\rangle = \mu_0 I,$$

ahol $\mathbf{J}$ az elektromos áramsűrűség-vektor (az egységnyi területen átfolyó áram), $\mathbf{B}$ a mágneses indukció, és $I$ a felületen keresztülfolyó áram. Az integrális alak tehát azt állítja, hogy a felület határán a **mágneses örvényerősség arányos a felületen átfolyó elektromos árammal**.

## Kapocs

- [[concepts/analiii/stokes-tetel]] — a rokon tételek, amelyeknek ez a peremes felületre szóló változata
- [[concepts/analiii/rotacio]] — az integrandus
- [[concepts/analiii/feluleti-integral]] — a bal oldalon álló fluxus
- [[concepts/analiii/maxwell-egyenletek-es-integraltetelek]] — a II. és IV. egyenlet két alakja közti kapcsolat
- [[concepts/analiii/osszekapcsolodasi-szam]] — az Ampère-törvény topológiai következménye
