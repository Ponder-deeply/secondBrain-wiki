---
tags: [concept]
sources: [01_ea_an_ii_a_b_merged.pdf]
references: ["An II A/B 1. előadás"]
derivation: source
updated: 2026-09-04
---

# Elemi függvények deriváltjai

Az alapvető elemi függvények deriváltjainak összefoglalása. Az eredmények a [[concepts/analii/derivalt-fogalma|derivalt-fogalma]] definíciójából, a [[concepts/analii/derivalasi-szabalyok|derivalasi-szabalyok]] alkalmazásával, illetve az inverz derivált szabályával vezethetők le.

## Alaptáblázat

| Függvény $f(x)$ | Derivált $f'(x)$ | Értelmezési tartomány |
|---|---|---|
| $c$ (konstans) | $0$ | $\mathbb{R}$ |
| $x^n$ ($n \geq 1$, $n \in \mathbb{N}$) | $nx^{n-1}$ | $\mathbb{R}$ |
| $x^\alpha$ ($\alpha \in \mathbb{R}$) | $\alpha x^{\alpha-1}$ | $(0, +\infty)$ |
| $\sqrt{x}$ | $\dfrac{1}{2\sqrt{x}}$ | $(0, +\infty)$ |
| $e^x$ | $e^x$ | $\mathbb{R}$ |
| $a^x$ ($a > 0$, $a \neq 1$) | $a^x \ln a$ | $\mathbb{R}$ |
| $\ln x$ | $\dfrac{1}{x}$ | $(0, +\infty)$ |
| $\log_a x$ | $\dfrac{1}{x \ln a}$ | $(0, +\infty)$ |
| $\sin x$ | $\cos x$ | $\mathbb{R}$ |
| $\cos x$ | $-\sin x$ | $\mathbb{R}$ |
| $\tan x$ | $\dfrac{1}{\cos^2 x}$ | $x \neq \frac{\pi}{2} + k\pi$ |
| $\cot x$ | $-\dfrac{1}{\sin^2 x}$ | $x \neq k\pi$ |

## Hatványfüggvény: bizonyítás (n természetes)

$$\lim_{h \to 0} \frac{(x+h)^n - x^n}{h} = \lim_{h \to 0} \left[(x+h)^{n-1} + (x+h)^{n-2}x + \cdots + x^{n-1}\right] = nx^{n-1}.$$

Az $a^n - b^n = (a-b)(a^{n-1} + a^{n-2}b + \cdots + b^{n-1})$ faktorizáció alapján.

## Megjegyzések

- Az $e^x$ deriváltja önmaga: ez az $e$ természetes alap kitüntetett tulajdonsága.
- A $\ln x$ deriváltja az inverz derivált szabályával adódik az $e^x$-ből.
- A $\sin$ és $\cos$ deriváltjai egymásból adódnak a [[concepts/analii/derivalasi-szabalyok|derivalasi-szabalyok]] láncszabályával.
- A bővített táblázat (arkusz-, hiperbolikus, areafüggvények) a [[concepts/analii/elemi-fuggvenyek-kiegeszites|elemi-fuggvenyek-kiegeszites]] lapon található.

## Kapocs

- [[concepts/analii/derivalt-fogalma]] — derivált definíciója, hatványfüggvény bizonyítása
- [[concepts/analii/derivalasi-szabalyok]] — összeg, szorzat, hányados, lánc, inverz szabályok
- [[concepts/analii/elemi-fuggvenyek-kiegeszites]] — tg, ctg, arkusz-, hiperbolikus és areafüggvények
- [[concepts/analii/alapintegralok]] — az elemi deriváltak megfordítása: primitív függvények
