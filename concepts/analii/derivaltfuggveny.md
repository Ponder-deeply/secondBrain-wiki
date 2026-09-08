---
tags: [concept]
sources: [01_ea_an_ii_a_b_merged.pdf]
references: ["An II A/B 1. előadás"]
derivation: source
updated: 2026-09-04
---

# Deriváltfüggvény

Ha $f$ egy valós-valós függvény, a **deriváltfüggvény** $f'$ az a függvény, amely minden belső ponthoz, ahol $f$ deriválható, hozzárendeli $f$ ott vett deriváltját.

## Definíció

$$\mathcal{D}_{f'} := \{a \in \text{int}\, \mathcal{D}_f \mid f \in D\{a\}\},$$
$$f'(a) := \lim_{h \to 0} \frac{f(a+h) - f(a)}{h} \quad (a \in \mathcal{D}_{f'}).$$

Jelölések: $f'$, $\frac{df}{dx}$, $Df$, $\dot{f}$.

## Deriválhatóság osztályok

- $f \in D(A)$: $f$ deriválható $A$ minden belső pontjában.
- $f \in D\{a\}$: $f$ deriválható az $a$ pontban.
- $f \in C^1(A)$: $f$ folytonosan deriválható $A$-n (azaz $f' \in C(A)$).

## Jelölési hagyományok

| Jelölés | Leírás |
|---|---|
| $f'(x)$ | Lagrange |
| $\frac{df}{dx}$ | Leibniz |
| $Df(x)$ | Euler–operátor |
| $\dot{f}(t)$ | Newton (fizikában, idő szerint) |

## Kapocs

- [[concepts/analii/derivalt-fogalma]] — pontbeli derivált, amelyből a függvény épül
- [[concepts/analii/derivalasi-szabalyok]] — a deriváltfüggvény kiszámítási szabályai
- [[concepts/analii/magasabb-rendu-derivaltak]] — $f''$, $f^{(n)}$ rekurzív definíciója
- [[concepts/analii/elemi-fuggvenyek-derivaltjai]] — konkrét deriváltfüggvények táblázata
