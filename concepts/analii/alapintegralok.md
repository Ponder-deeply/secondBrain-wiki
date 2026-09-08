---
tags: [concept]
sources: [01_ea_an_ii_a_b_merged.pdf]
references: ["An II A/B 6. előadás"]
derivation: source
updated: 2026-09-04
---

# Alapintegrálok

Az alapintegrálok az elemi függvények primitív függvényeinek alaptáblázata. Ezek ismerete szükséges a határozatlan integrálok kiszámításához; a táblázat az elemi deriváltak „megfordítása".

## Az alaptáblázat

Minden képlet egy nyílt intervallumon értendő, ahol az integrandus értelmezett. Az additive $+c$ állandó minden sorban elhagyható a jelölés végén.

| Integrandus $f(x)$ | Primitív függvény $F(x)$ | Értelmezési tartomány |
|---|---|---|
| $x^\alpha$ ($\alpha \neq -1$) | $\dfrac{x^{\alpha+1}}{\alpha+1}$ | $(0,+\infty)$, ill. $\alpha \in \mathbb{N}$: $\mathbb{R}$ |
| $\dfrac{1}{x}$ | $\ln x$ | $(0, +\infty)$ |
| $\dfrac{1}{x}$ | $\ln(-x)$ | $(-\infty, 0)$ |
| $e^x$ | $e^x$ | $\mathbb{R}$ |
| $a^x$ ($a > 0$, $a \neq 1$) | $\dfrac{a^x}{\ln a}$ | $\mathbb{R}$ |
| $\sin x$ | $-\cos x$ | $\mathbb{R}$ |
| $\cos x$ | $\sin x$ | $\mathbb{R}$ |
| $\dfrac{1}{\cos^2 x}$ | $\operatorname{tg}\, x$ | $\Bigl(-\tfrac{\pi}{2}, \tfrac{\pi}{2}\Bigr)$ |
| $\dfrac{1}{\sin^2 x}$ | $-\operatorname{ctg}\, x$ | $(0, \pi)$ |
| $\dfrac{1}{1+x^2}$ | $\operatorname{arc\, tg}\, x$ | $\mathbb{R}$ |
| $\dfrac{1}{\sqrt{1-x^2}}$ | $\arcsin x$ | $(-1, 1)$ |
| $\operatorname{sh}\, x$ | $\operatorname{ch}\, x$ | $\mathbb{R}$ |
| $\operatorname{ch}\, x$ | $\operatorname{sh}\, x$ | $\mathbb{R}$ |
| $\dfrac{1}{\operatorname{ch}^2 x}$ | $\operatorname{th}\, x$ | $\mathbb{R}$ |

## Megjegyzések az $1/x$ esethez

Az $\int \tfrac{1}{x}\, dx$ integrálandó kétféleképpen adódik:

$$\int \frac{1}{x}\, dx = \ln x + c \quad (x \in (0,+\infty)), \qquad \int \frac{1}{x}\, dx = \ln(-x) + c \quad (x \in (-\infty, 0)).$$

Mindkettő felírható egységesen: $\int \tfrac{1}{x}\, dx = \ln |x| + c$, ha $x \neq 0$ — de ezt az $I$-n értelmezett összefüggés mindig egy összefüggő intervallumra vonatkozik, ahol az előjel rögzített.

## Hatványfüggvény általánosan

$$\int x^\alpha\, dx = \frac{x^{\alpha+1}}{\alpha+1} + c \quad (x \in (0,+\infty),\; \alpha \in \mathbb{R} \setminus \{-1\}).$$

Különleges esetek: $\alpha = \tfrac{1}{2}$ esetén $\int \sqrt{x}\, dx = \tfrac{2}{3} x^{3/2} + c$; $\alpha = -\tfrac{1}{2}$ esetén $\int \tfrac{1}{\sqrt{x}}\, dx = 2\sqrt{x} + c$.

## Kapcsolat az alapintegrálok és a deriválási táblázat között

Az alapintegrálok pontosan az [[concepts/analii/elemi-fuggvenyek-derivaltjai|elemi függvények deriváltjainak]] és az [[concepts/analii/elemi-fuggvenyek-kiegeszites|kiegészítő elemi függvények deriváltjainak]] (tg, ctg, arkusz-, hiperbolikus) „visszaolvasásával" kaphatók. Az $\ln x$ sor például az $(\ln x)' = 1/x$ visszafordítása.

## Alkalmazás az integrálási szabályokkal

Az alapintegrálok a [[concepts/analii/hatarozatlan-integral|határozatlan integrál]] linearitásával, az első és második helyettesítési szabállyal, valamint a parciális integrálással kombinálva kiterjedt függvényosztályok primitív függvényeinek kiszámítását teszik lehetővé.

## Kapocs

- [[concepts/analii/hatarozatlan-integral]] — linearitás, helyettesítési szabályok, parciális integrálás
- [[concepts/analii/primitiv-fuggveny]] — primitív függvény fogalma, Darboux-tétel, Liouville-féle nem elemi esetek
- [[concepts/analii/elemi-fuggvenyek-derivaltjai]] — az alaptáblázat forrása: deriváltak megfordítása
- [[concepts/analii/elemi-fuggvenyek-kiegeszites]] — tg, ctg, arkuszfüggvények, hiperbolikus függvények deriváltjai
