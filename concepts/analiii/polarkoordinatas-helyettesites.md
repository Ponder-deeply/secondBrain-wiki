---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf, 10_ea_An3_2022_tavasz.pdf]
derivation: source
updated: 2026-09-14
---

# Polárkoordinátás helyettesítés

A síkbeli integráltranszformáció legfontosabb konkrét esete: $x = r\cos\varphi$, $y = r\sin\varphi$, amelynek Jacobi-determinánsa $r$, tehát $\mathrm{d}x\,\mathrm{d}y = r\,\mathrm{d}r\,\mathrm{d}\varphi$.

## Tartalom

### Definíció

A **polárkoordinátás helyettesítés** a

$$g\binom{r}{\varphi} = \binom{r\cos\varphi}{r\sin\varphi}, \qquad \text{azaz} \qquad x = r\cos\varphi, \quad y = r\sin\varphi$$

leképezés. Jacobi-mátrixának determinánsa

$$\det g' = \det \begin{pmatrix} \cos\varphi & -r\sin\varphi \\ \sin\varphi & r\cos\varphi \end{pmatrix} = r(\cos^2\varphi + \sin^2\varphi) = r,$$

tehát a mérték- és integráltranszformáció tétele szerint

$$\mathrm{d}x\,\mathrm{d}y = r\,\mathrm{d}r\,\mathrm{d}\varphi.$$

Az $r$ tényező szemléletes jelentése: a $\varphi$ irányban egy $\mathrm{d}\varphi$ szögnyi elmozdulás $r$ sugárnál $r\,\mathrm{d}\varphi$ hosszú ívet fut be, tehát az origótól távolodva ugyanakkora szögtartomány egyre nagyobb területet takar.

### Példa: az $R$ sugarú kör területe

Az origó középpontú, $R$ sugarú körlapot a $0 \leqslant r \leqslant R$, $0 \leqslant \varphi \leqslant 2\pi$ paramétertartomány, azaz az $A = [0,R] \times [0,2\pi]$ **téglalap** képeként állítjuk elő. Ekkor

$$t(B(0,R)) = \int_A r\,\mathrm{d}r\,\mathrm{d}\varphi = \int_{r=0}^{R}\left(\int_{\varphi=0}^{2\pi} r\,\mathrm{d}\varphi\right)\mathrm{d}r = \int_{r=0}^{R} 2\pi r\,\mathrm{d}r = \pi R^2.$$

A helyettesítés haszna éppen ez: egy bonyolult alakú tartomány (körlap) helyett egy téglalapon integrálunk, ahol a szukcesszív integrálás akadálytalanul elvégezhető.

### Példa: $\iint_T x^2 y \,\mathrm{d}x\,\mathrm{d}y$ körgyűrűcikken

Legyen $T$ az

$$1 \leqslant x^2+y^2 \leqslant 4, \qquad y \geqslant 0, \qquad x \geqslant 0$$

egyenlőtlenségekkel meghatározott korlátos síkrész (egy negyed körgyűrű). Polárkoordinátás helyettesítéssel $T = g\bigl([1,2] \times [0,\pi/2]\bigr)$, tehát

$$\iint_T x^2 y \,\mathrm{d}x\,\mathrm{d}y = \iint_{[1,2]\times[0,\pi/2]} (r\cos\varphi)^2 \cdot (r\sin\varphi) \cdot r \,\mathrm{d}r\,\mathrm{d}\varphi = \iint_{[1,2]\times[0,\pi/2]} r^4 \sin\varphi \cos^2\varphi \,\mathrm{d}r\,\mathrm{d}\varphi.$$

A szukcesszív integrálás szorzattá esik szét, mert az integrandus $r$-ben és $\varphi$-ben szorzat alakú, és a tartomány is téglalap:

$$= \left(\int_1^2 r^4\,\mathrm{d}r\right) \cdot \left(\int_0^{\pi/2} \sin\varphi \cos^2\varphi\,\mathrm{d}\varphi\right) = \left[\frac{r^5}{5}\right]_1^2 \cdot \left[-\frac{\cos^3\varphi}{3}\right]_0^{\pi/2} = \left(\frac{32}{5} - \frac{1}{5}\right) \cdot \frac{1}{3} = \frac{31}{15}.$$

Ez a példa jól mutatja a módszer erejét: a körgyűrűcikken vett integrál polárkoordinátákban egy téglalapon vett, szorzat alakú integrandusú integrállá esik szét, amit a szukcesszív integrálás azonnal kezel.

### Mikor érdemes polárkoordinátázni?

- Ha az **integrálási tartomány** forgásszimmetrikus (körlap, körgyűrű, körcikk).
- Ha az **integrandus** csak $x^2 + y^2$-en keresztül függ a helytől, mert $x^2 + y^2 = r^2$ miatt ilyenkor az integrandus a $\varphi$-től független lesz.

A leképezés a $r > 0$, $0 < \varphi < 2\pi$ nyílt téglalapon injektív; a téglalap határán fellépő átfedés (a $\varphi = 0$ és $\varphi = 2\pi$ élek egymásra képződése, illetve az egész $r = 0$ él egyetlen pontba menése) nullmértékű, ezért a transzformációs tétel alkalmazható.

## Kapocs

- [[concepts/analiii/mertek-es-integraltranszformacio]] — az az általános tétel, amelynek ez a helyettesítés a legfontosabb speciális esete.
- [[concepts/analiii/gauss-integral]] — a $\int_{-\infty}^{\infty} e^{-x^2}\,\mathrm{d}x$ kiszámítása polárkoordinátákkal.
- [[concepts/analiii/hengerkoordinatas-helyettesites]] — a térbeli megfelelője: ugyanez a helyettesítés az $(x,y)$-síkon, a $z$ koordinátával kiegészítve.
- [[concepts/analiii/gombi-koordinatas-helyettesites]] — a másik térbeli általánosítás, origó körüli gömbszimmetriára.
- [[concepts/analii/sikido-terulete]] — az egyváltozós integrállal kiszámított síkidomterület; a körlap területe ott is megkapható, itt viszont a transzformáció maga végzi el a munkát.
