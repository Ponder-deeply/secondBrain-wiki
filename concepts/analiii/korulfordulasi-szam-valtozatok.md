---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-06
---

# Körülfordulási és összekapcsolódási szám változatok

Három rokon képlet egy közös sémára: a $\frac{\mathbf{x}-\mathbf{a}}{|\mathbf{x}-\mathbf{a}|^d}$ mező integrálja az egységgömb felszínével normálva mindig egész számot ad — a megkerülések, átdöfések, illetve átbújások számát.

## Tartalom

### Kiindulópont: divergenciamentes mezők zárt felületeken

A Gauss–Osztrogradszkij tétel szerint divergenciamentes vektormezőnek minden szép krumpli határán nulla a felületi integrálja. Ez lehetőséget ad a primitív függvényről szóló fejezet általánosítására: meg lehetne csinálni a Goursat-lemma felületi integrálokról szóló variánsát, és bebizonyítani, hogy minden nullhomotóp zárt felületen (vagy akár csak poliéderen) nulla a felületi integrál. Ezzel az eszközzel bizonyítható például, hogy $\mathbb{R}^3\setminus\{(0,0,0)\}$ nem homeomorf $\mathbb{R}^3$-mal.

### A síkbeli körülfordulási szám átírása

Két dimenzióban a $\gamma$ görbe $\mathbf{a}$ pont körüli körülfordulási száma a külső normálissal is felírható:

$$n(\gamma,\mathbf{a}) = \frac{1}{2\pi}\int_{\mathbf{x}\in\gamma}\left\langle \frac{\mathbf{x}-\mathbf{a}}{|\mathbf{x}-\mathbf{a}|^2};\ \mathbf{n}\,\mathrm{d}s\right\rangle,$$

ahol az integrál előtti $2\pi$ az **egységkör kerülete**. Ez a felírás már nem a szög növekményét összegzi, hanem egy vektormező fluxusát méri a görbén — és éppen ez az alak általánosodik magasabb dimenzióra.

### Zárt felület pont körüli fokszáma

Ennek mintájára: ha $S$ darabonként folytonosan differenciálható, irányított **zárt felület** $\mathbb{R}^3$-ban, amely nem megy át az $\mathbf{a}$ ponton, akkor az

$$\frac{1}{4\pi}\int_{\mathbf{x}\in S}\left\langle \frac{\mathbf{x}-\mathbf{a}}{|\mathbf{x}-\mathbf{a}|^3};\ \overrightarrow{\mathrm{d}A}\right\rangle$$

felületi integrál azt számolja meg, hogy az $S$ felület hányszor „kerüli meg" az $\mathbf{a}$ pontot.

Hogy ez működik, két észrevételen múlik: a $\frac{\mathbf{x}-\mathbf{a}}{|\mathbf{x}-\mathbf{a}|^3}$ vektormező **divergenciamentes** (ezért a felület folytonos deformálása nem változtat az integrálon, amíg át nem megy $\mathbf{a}$-n), az origó középpontú gömbökön pedig a fluxusa $4\pi$, ami az **egységgömb felszíne** (ezért lesz a normálás után épp $1$ egyetlen megkerülésre).

### A három képlet egymás mellett

- $\mathbb{R}^2$-ben az $\mathbf{a}$ pontot a $\gamma$ zárt görbe ennyiszer kerüli meg:
  $$\frac{1}{2\pi}\int_{\mathbf{x}\in\gamma}\frac{\mathbf{x}-\mathbf{a}}{|\mathbf{x}-\mathbf{a}|^2}\times\mathrm{d}\mathbf{x} = \frac{1}{2\pi}\int_{\mathbf{x}\in\gamma}\left\langle \frac{\mathbf{x}-\mathbf{a}}{|\mathbf{x}-\mathbf{a}|^2};\ \mathbf{n}\,\mathrm{d}s\right\rangle$$
- $\mathbb{R}^3$-ban az $\mathbf{a}$ pontot az $S$ zárt felület ennyiszer kerüli meg:
  $$\frac{1}{4\pi}\int_{\mathbf{x}\in S}\left\langle \frac{\mathbf{x}-\mathbf{a}}{|\mathbf{x}-\mathbf{a}|^3};\ \overrightarrow{\mathrm{d}A}\right\rangle$$
- $\mathbb{R}^3$-ban a $\gamma_1$ zárt görbén a $\gamma_2$ zárt görbe ennyiszer bújik át:
  $$\frac{1}{4\pi}\int_{\mathbf{x}\in\gamma_1}\int_{\mathbf{y}\in\gamma_2}\left\langle \frac{\mathbf{x}-\mathbf{y}}{|\mathbf{x}-\mathbf{y}|^3};\ \mathrm{d}\mathbf{x}\times\mathrm{d}\mathbf{y}\right\rangle$$

Mindháromban ugyanaz a szerkezet: a szinguláris pont felé mutató, megfelelő hatvánnyal normált mező integrálja, elosztva az egységgömb (illetve egységkör) mértékével. A normáló konstans mindig a megfelelő dimenziójú egységgömbfelszín — ez teszi az eredményt egésszé.

## Kapocs

- [[concepts/analiii/korulfordulasi-szam]] — a síkbeli alapeset
- [[concepts/analiii/osszekapcsolodasi-szam]] — a harmadik képlet és fizikai eredete
- [[concepts/analiii/gauss-osztrogradszkij-tetel]] — a divergenciamentesség és a deformációinvariancia forrása
- [[concepts/analiii/feluleti-integral]] — a felületi fluxus fogalma
- [[concepts/analiii/kulso-normalis]] — az $\mathbf{n}\,\mathrm{d}s$ jelölés a síkbeli átírásban
