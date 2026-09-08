---
tags: [concept]
sources: [01_ea_an_ii_a_b_merged.pdf]
references: ["An II A/B 6. előadás"]
derivation: source
updated: 2026-09-04
---

# Határozatlan integrál

A határozatlan integrál az összes primitív függvényt magában foglaló halmaz; jelölése összefoglalja az integrálás eredményét egy konstans erejéig.

## Definíció

Az $I$ nyílt intervallumon értelmezett $f$ függvény primitív függvényeinek halmazát $f$ **határozatlan integráljának** nevezzük, és így jelöljük:

$$\int f := \int f(x)\, dx := \bigl\{ F : I \to \mathbb{R} \mid F \in D \text{ és } F' = f \bigr\}.$$

$f$ az **integrandus**, ill. az **integrálandó függvény**.

Ha $F \in \int f$, akkor $\int f = \{F + c \mid c \in \mathbb{R}\}$, amit rövidebben (és kissé pontatlanabban) így írunk:

$$\int f(x)\, dx = F(x) + c \quad (x \in I).$$

**Példa.** $\displaystyle\int \frac{1}{1+x^2}\, dx = \operatorname{arc\, tg}\, x + c \quad (x \in \mathbb{R})$.

## A linearitás tétele

**Tétel.** Legyen $I$ nyílt intervallum. Ha $f, g : I \to \mathbb{R}$ függvényeknek létezik primitív függvénye, akkor tetszőleges $\alpha, \beta \in \mathbb{R}$ mellett $(\alpha f + \beta g)$-nek is létezik primitív függvénye, és

$$\int \bigl(\alpha f(x) + \beta g(x)\bigr)\, dx = \alpha \int f(x)\, dx + \beta \int g(x)\, dx \quad (x \in I).$$

**Példa.** $\displaystyle\int (6x^2 - 8x + 3)\, dx = 6 \cdot \frac{x^3}{3} - 8 \cdot \frac{x^2}{2} + 3x + c = 2x^3 - 4x^2 + 3x + c \quad (x \in \mathbb{R})$.

## Az első helyettesítési szabály

**Tétel.** Legyenek adottak az $I, J$ nyílt intervallumok és a $g : I \to \mathbb{R}$, $f : J \to \mathbb{R}$ függvények. T.f.h. $g \in D(I)$, $\mathcal{R}_g \subset J$ és $f$-nek van primitív függvénye. Ekkor az $(f \circ g) \cdot g'$ függvénynek is van primitív függvénye, és

$$\int f\bigl(g(x)\bigr) \cdot g'(x)\, dx = F\bigl(g(x)\bigr) + c \quad (x \in I),$$

ahol $F$ az $f$ függvény egy primitív függvénye.

**Bizonyítás.** Legyen $F \in \int f$. Ekkor $F \in D(J)$ és $F' = f$. Az összetett függvény deriválási szabálya szerint $F \circ g \in D(I)$ és
$$(F \circ g)' = (F' \circ g) \cdot g' = f \circ g \cdot g'.$$
Tehát $F \circ g \in \int f \circ g \cdot g'$. $\blacksquare$

**Speciális esetek:**

- Ha $f > 0$ és $f \in D(I)$:
$$\int \frac{f'(x)}{f(x)}\, dx = \ln f(x) + c \quad (x \in I,\; c \in \mathbb{R}).$$

- Ha $f > 0$, $f \in D(I)$ és $\alpha \in \mathbb{R} \setminus \{-1\}$:
$$\int f^\alpha(x) f'(x)\, dx = \frac{f^{\alpha+1}(x)}{\alpha+1} + c \quad (x \in I,\; c \in \mathbb{R}).$$

- Ha $f : I \to \mathbb{R}$ függvénynek van primitív függvénye, $a, b \in \mathbb{R}$, $a \neq 0$:
$$\int f(ax + b)\, dx = \frac{F(ax+b)}{a} + c \quad (x \in I,\; c \in \mathbb{R}).$$

**Példa.** Ha $x \in \bigl(0, \tfrac{\pi}{2}\bigr) =: I$:
$$\int \frac{1}{\cos^2 x \cdot \operatorname{tg}^3 x}\, dx = \int (\operatorname{tg} x)^{-3/2} \cdot (\operatorname{tg} x)'\, dx = \frac{(\operatorname{tg} x)^{-1/2}}{-1/2} + c = -\frac{2}{\sqrt{\operatorname{tg} x}} + c.$$

## A parciális integrálás szabálya

**Tétel.** Legyen $I$ nyílt intervallum. T.f.h. $f, g \in D(I)$ és az $f'g$ függvénynek létezik primitív függvénye $I$-n. Ekkor az $fg'$ függvénynek is van primitív függvénye, és

$$\int f(x) g'(x)\, dx = f(x)g(x) - \int f'(x) g(x)\, dx \quad (x \in I).$$

**Bizonyítás.** Ha $F \in \int f'g$, akkor $fg - F \in D(I)$ és $(fg - F)' = f'g + fg' - f'g = fg'$. Tehát $fg - F \in \int fg'$. $\blacksquare$

A tételt akkor célszerű alkalmazni, ha az $f'g$ határozatlan integrálja már ismert, de az $fg'$-é nem.

**Példák.**

$1^\circ$ $\displaystyle\int x \sin x\, dx \quad (x \in \mathbb{R})$:

$$\int x \cdot \sin x\, dx = \int x \cdot (-\cos x)'\, dx = -x\cos x - \int (x)' \cdot (-\cos x)\, dx = -x\cos x + \sin x + c.$$

$2^\circ$ $\displaystyle\int \ln x\, dx \quad (x \in (0, +\infty))$:

$$\int \ln x\, dx = \int (\ln x) \cdot (x)'\, dx = x\ln x - \int \frac{1}{x} \cdot x\, dx = x\ln x - x + c = x(\ln x - 1) + c.$$

$3^\circ$ $\displaystyle\int \sqrt{1-x^2}\, dx \quad (x \in (-1,1))$:

Parciális integrálással: $\displaystyle\int \sqrt{1-x^2}\, dx = x\sqrt{1-x^2} + \int \frac{x^2}{\sqrt{1-x^2}}\, dx$, majd az integrandust átalakítva:
$$\int \sqrt{1-x^2}\, dx = \frac{x\sqrt{1-x^2} + \arcsin x}{2} + c.$$

## A második helyettesítési szabály

**Tétel.** T.f.h. $I, J \subset \mathbb{R}$ nyílt intervallumok, $f : I \to \mathbb{R}$, $g : J \to I$ **bijekció**, $g \in D(J)$, $g'(x) \neq 0$ ($\forall x \in J$) és $f \circ g \cdot g'$ függvénynek van primitív függvénye $J$-n. Ekkor $f$-nek is van primitív függvénye, és

$$\int f(x)\, dx = \int f\bigl(g(t)\bigr) \cdot g'(t)\, dt\bigg|_{t = g^{-1}(x)} \quad (x \in I).$$

**Megjegyzés.** A Darboux-tétel szerint $0 \notin \mathcal{R}_{g'}$ $\Rightarrow$ $g$ szigorúan monoton $J$-n, tehát $g^{-1}$ létezik.

**Alkalmazás.** Az $\int f(x)\, dx$ határozatlan integrált az $x = g(t)$ helyettesítéssel $\int f(g(t)) \cdot g'(t)\, dt$ alakra hozzuk, amelyik könnyebben kiszámítható; az eredményt visszahelyettesítve $t = g^{-1}(x)$-szel kapjuk $f$ primitív függvényét.

**Példa.** $\displaystyle\int \sqrt{1-x^2}\, dx \quad (x \in (-1,1))$ — trigonometrikus helyettesítéssel:

Legyen $x = \sin t =: g(t)$, $t \in \bigl(-\tfrac{\pi}{2}, \tfrac{\pi}{2}\bigr)$. Ekkor $g'(t) = \cos t > 0$, tehát $g$ invertálható és $t = \arcsin x$.

$$\int \sqrt{1-x^2}\, dx = \int \cos^2 t\, dt = \int \frac{1 + \cos 2t}{2}\, dt = \frac{t}{2} + \frac{\sin 2t}{4} + c\bigg|_{t = \arcsin x}.$$

Mivel $\sin(2\arcsin x) = 2x\sqrt{1-x^2}$, ezért:
$$\int \sqrt{1-x^2}\, dx = \frac{\arcsin x}{2} + \frac{x\sqrt{1-x^2}}{2} + c \quad (x \in (-1,1)).$$

Ez egyezik a parciális integrálással kapott eredménnyel.

## Kapocs

- [[concepts/analii/primitiv-fuggveny]] — primitív függvény definíciója, Darboux-tétel, egyediség
- [[concepts/analii/alapintegralok]] — az alaptáblázat, amelyre a számítások támaszkodnak
- [[concepts/analii/derivalasi-szabalyok]] — a helyettesítési és parciális szabályok a deriválási szabályok „megfordításai"
- [[concepts/analii/elemi-fuggvenyek-kiegeszites]] — arkuszfüggvények és hiperbolikusok, amelyek az integrálokban megjelennek
- [[concepts/analii/nevezetes-sorfejtesek]] — $\arcsin x$ sorfejtése parciális integrálással is levezethető
