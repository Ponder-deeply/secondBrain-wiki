---
tags: [concept]
sources: [01_ea_an_ii_a_b_merged.pdf]
references: ["An II A/B 1. előadás"]
derivation: source
updated: 2026-09-04
---

# Pontbeli derivált fogalma

Az $f$ függvény $a$ pontban **differenciálható** (deriválható), ha létezik és véges a különbségi hányados határértéke. Ezt a határértéket $f'(a)$-val jelöljük, és $f$ **pontbeli deriváltjának** (differenciálhányadosának) nevezzük.

## Definíció

Legyen $f \in \mathbb{R} \to \mathbb{R}$ és $a \in \text{int}\, \mathcal{D}_f$. Az $f$ függvény az $a \in \text{int}\, \mathcal{D}_f$ pontban **differenciálható** (vagy **deriválható**), ha

$$\exists \text{ és véges } a \quad \lim_{h \to 0} \frac{f(a+h) - f(a)}{h} \text{ határérték.}$$

Ezt $f'(a)$-val jelöljük, és az $f$ függvény **pontbeli deriváltjának** (vagy **differenciálhányadosának**) nevezzük:

$$f'(a) := \lim_{h \to 0} \frac{f(a+h) - f(a)}{h} \in \mathbb{R}.$$

Jelölés: $f \in D\{a\}$.

## Ekvivalens alakok

- $f \in D\{a\} \iff \exists f'(a) = \displaystyle\lim_{x \to a} \frac{f(x) - f(a)}{x - a} \in \mathbb{R}$.
- A határérték 0/0-típusú; a nevező $\to 0$, ezért csak belső pontban értelmes.

## Különbségi hányados-függvény

Ha $f \in \mathbb{R} \to \mathbb{R}$ és $a \in \text{int}\, \mathcal{D}_f$, akkor

$$\triangle_a f(x) := \frac{f(x) - f(a)}{x - a} \quad (x \in \mathcal{D}_f \setminus \{a\})$$

az $f$ függvény $a$ ponthoz tartozó **különbségi hányados-függvénye** (differenciálhányados-függvénye). Geometriailag az $(a, f(a))$ és $(x, f(x))$ pontokat összekötő szekáns meredeksége. Így

$$f'(a) = \lim_{x \to a} \triangle_a f(x).$$

## Példa: hatványfüggvény

Tetszőleges $n \geq 1$ természetes szám esetén $f(x) := x^n$ ($x \in \mathbb{R}$) minden $x \in \mathbb{R}$ pontban deriválható, és

$$\boxed{(x^n)' = nx^{n-1} \quad (x \in \mathbb{R}).}$$

**Bizonyítás.** Az $a^n - b^n = (a-b)(a^{n-1} + a^{n-2}b + \cdots + b^{n-1})$ azonosság alapján:

$$\lim_{h \to 0} \frac{(x+h)^n - x^n}{h} = \lim_{h \to 0} \left[(x+h)^{n-1} + (x+h)^{n-2}x + \cdots + x^{n-1}\right] = nx^{n-1},$$

a hatványfüggvény folytonossága alapján.

## Kapocs

- [[concepts/analii/folytonossag-es-derivalt]] — deriválhatóság $\Rightarrow$ folytonosság, de nem fordítva
- [[concepts/analii/linearkozelites]] — lineáris közelítés tétele ekvivalens a derivált definíciójával
- [[concepts/analii/erintofuggveny]] — érintő meredeksége = $f'(a)$
- [[concepts/analii/derivaltfuggveny]] — $f'$ mint operátor
- [[concepts/analii/egyoldali-derivaltak]] — jobb és bal oldali derivált
