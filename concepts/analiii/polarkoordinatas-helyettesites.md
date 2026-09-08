---
tags: [concept]
sources: [Kos-Geza-Analizis-3-eloadasjegyzet-2024.pdf]
derivation: source
updated: 2026-09-06
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

### Mikor érdemes polárkoordinátázni?

- Ha az **integrálási tartomány** forgásszimmetrikus (körlap, körgyűrű, körcikk).
- Ha az **integrandus** csak $x^2 + y^2$-en keresztül függ a helytől, mert $x^2 + y^2 = r^2$ miatt ilyenkor az integrandus a $\varphi$-től független lesz.

A leképezés a $r > 0$, $0 < \varphi < 2\pi$ nyílt téglalapon injektív; a téglalap határán fellépő átfedés (a $\varphi = 0$ és $\varphi = 2\pi$ élek egymásra képződése, illetve az egész $r = 0$ él egyetlen pontba menése) nullmértékű, ezért a transzformációs tétel alkalmazható.

## Kapocs

- [[concepts/analiii/mertek-es-integraltranszformacio]] — az az általános tétel, amelynek ez a helyettesítés a legfontosabb speciális esete.
- [[concepts/analiii/gauss-integral]] — a $\int_{-\infty}^{\infty} e^{-x^2}\,\mathrm{d}x$ kiszámítása polárkoordinátákkal.
- [[concepts/analii/sikido-terulete]] — az egyváltozós integrállal kiszámított síkidomterület; a körlap területe ott is megkapható, itt viszont a transzformáció maga végzi el a munkát.
