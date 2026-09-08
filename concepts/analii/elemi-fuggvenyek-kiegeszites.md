---
tags: [concept]
sources: [01_ea_an_ii_a_b_merged.pdf]
references: ["An II A/B 4. előadás"]
derivation: source
updated: 2026-09-04
---

# Elemi függvények — kiegészítés

Az Analízis I.-ben bevezetett $\exp$, $\ln$, $\exp_a$, $\log_a$, $x^\alpha$ ($x > 0$, $\alpha \in \mathbb{R}$), $\sin$, $\cos$ függvényeken túl az Analízis II. a következő elemi függvényekkel egészíti ki az eszköztárat.

## Szinusz és koszinusz kiegészítése

### Tangens és kotangens

$$\operatorname{tg} x := \frac{\sin x}{\cos x}, \qquad \mathcal{D}_{\operatorname{tg}} = \mathbb{R} \setminus \left\{\frac{\pi}{2} + k\pi : k \in \mathbb{Z}\right\}.$$

$$\operatorname{ctg} x := \frac{\cos x}{\sin x}, \qquad \mathcal{D}_{\operatorname{ctg}} = \mathbb{R} \setminus \{k\pi : k \in \mathbb{Z}\}.$$

Deriváltjaik:

$$(\operatorname{tg} x)' = \frac{1}{\cos^2 x} = 1 + \operatorname{tg}^2 x, \qquad (\operatorname{ctg} x)' = -\frac{1}{\sin^2 x} = -(1 + \operatorname{ctg}^2 x).$$

## Arkuszfüggvények (trigonometrikus inverz függvények)

A trigonometrikus függvények nem invertálhatók $\mathbb{R}$-en (nem injektívek), ezért egy megfelelő leszűkítésen értelmezzük az inverzeket.

| Függvény | Értelmezési tartomány | Értékkészlet | Derivált |
|---|---|---|---|
| $\arcsin x$ | $[-1, 1]$ | $[-\frac{\pi}{2}, \frac{\pi}{2}]$ | $\frac{1}{\sqrt{1-x^2}}$ |
| $\arccos x$ | $[-1, 1]$ | $[0, \pi]$ | $-\frac{1}{\sqrt{1-x^2}}$ |
| $\arctan x$ | $\mathbb{R}$ | $(-\frac{\pi}{2}, \frac{\pi}{2})$ | $\frac{1}{1+x^2}$ |
| $\operatorname{arc\,ctg} x$ | $\mathbb{R}$ | $(0, \pi)$ | $-\frac{1}{1+x^2}$ |

**Megjegyzés.** $\arcsin x + \arccos x = \frac{\pi}{2}$ és $\arctan x + \operatorname{arc\,ctg} x = \frac{\pi}{2}$ minden $x \in [-1,1]$, ill. $x \in \mathbb{R}$ esetén.

## Hiperbolikus függvények

A hiperbolikus függvények az exponenciális függvény segítségével definiálhatók, és sok tekintetben analógak a trigonometrikus függvényekkel.

$$\operatorname{sh} x := \frac{e^x - e^{-x}}{2}, \qquad \operatorname{ch} x := \frac{e^x + e^{-x}}{2} \qquad (x \in \mathbb{R}).$$

$$\operatorname{th} x := \frac{\operatorname{sh} x}{\operatorname{ch} x} = \frac{e^x - e^{-x}}{e^x + e^{-x}}, \qquad \operatorname{cth} x := \frac{\operatorname{ch} x}{\operatorname{sh} x} \qquad (x \neq 0).$$

**Alapazonosság:** $\operatorname{ch}^2 x - \operatorname{sh}^2 x = 1$ (analóg: $\cos^2 + \sin^2 = 1$).

**Deriváltak:**

$$(\operatorname{sh} x)' = \operatorname{ch} x, \qquad (\operatorname{ch} x)' = \operatorname{sh} x.$$

$$(\operatorname{th} x)' = \frac{1}{\operatorname{ch}^2 x} = 1 - \operatorname{th}^2 x, \qquad (\operatorname{cth} x)' = -\frac{1}{\operatorname{sh}^2 x}.$$

## Areafüggvények (hiperbolikus inverz függvények)

| Függvény | Értelmezési tartomány | Explicit alak | Derivált |
|---|---|---|---|
| $\operatorname{ar\,sh} x$ | $\mathbb{R}$ | $\ln(x + \sqrt{x^2+1})$ | $\frac{1}{\sqrt{x^2+1}}$ |
| $\operatorname{ar\,ch} x$ | $[1, +\infty)$ | $\ln(x + \sqrt{x^2-1})$ | $\frac{1}{\sqrt{x^2-1}}$ |
| $\operatorname{ar\,th} x$ | $(-1, 1)$ | $\frac{1}{2}\ln\frac{1+x}{1-x}$ | $\frac{1}{1-x^2}$ |
| $\operatorname{ar\,cth} x$ | $\mathbb{R} \setminus [-1,1]$ | $\frac{1}{2}\ln\frac{x+1}{x-1}$ | $\frac{1}{1-x^2}$ |

**Megjegyzés.** Az areafüggvényeket azért nevezzük így, mert a $\operatorname{ch}$/$\operatorname{sh}$ paraméteres ábrázolásban az „area" (terület) kifejezéséhez kapcsolódnak, hasonlóan ahhoz, ahogy az arkuszfüggvények az ívhosszhoz.

## Kapcsolat az elemi deriváltakkal

Ezek a függvények és deriváltjaik az [[concepts/analii/alapintegralok|alapintegrálok táblázatának]] fontos elemeivé válnak: például

$$\int \frac{dx}{\sqrt{1-x^2}} = \arcsin x + C, \qquad \int \frac{dx}{1+x^2} = \arctan x + C,$$

$$\int \frac{dx}{\sqrt{x^2+1}} = \operatorname{ar\,sh} x + C, \qquad \int \frac{dx}{\sqrt{x^2-1}} = \operatorname{ar\,ch} x + C.$$

## Kapocs

- [[concepts/analii/elemi-fuggvenyek-derivaltjai]] — az alaptáblázat ($\sin$, $\cos$, $\exp$, $\ln$, $x^n$)
- [[concepts/analii/derivalasi-szabalyok]] — inverz deriválásának szabálya (az arkusz- és areafüggvények deriváltjai ebből következnek)
- [[concepts/analii/alapintegralok]] — az arkusz- és areafüggvények az integrálás alaptáblázatában szerepelnek
- [[concepts/analii/hatarozatlan-integral]] — az arkuszfüggvények parciális integrálásban is megjelennek
