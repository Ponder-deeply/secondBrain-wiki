---
tags: [concept]
sources: [01_ea_an_ii_a_b_merged.pdf]
references: ["An II A/B 1. előadás"]
derivation: source
updated: 2026-09-04
---

# Deriválási szabályok

Az alapvető algebrai műveletek és a kompozíció hogyan viselkednek a deriválás szempontjából.

## Összeadás és skaláris szorzás (linearitás)

Ha $f, g \in D\{a\}$ és $\lambda \in \mathbb{R}$, akkor

$$(\lambda f + g)'(a) = \lambda f'(a) + g'(a).$$

## Szorzatszabály (Leibniz-szabály)

Ha $f, g \in D\{a\}$, akkor $fg \in D\{a\}$ és

$$(fg)'(a) = f'(a)\,g(a) + f(a)\,g'(a).$$

## Hányadosszabály

Ha $f, g \in D\{a\}$ és $g(a) \neq 0$, akkor $\frac{f}{g} \in D\{a\}$ és

$$\left(\frac{f}{g}\right)'(a) = \frac{f'(a)\,g(a) - f(a)\,g'(a)}{g(a)^2}.$$

## Láncszabály (kompozíció deriváltja)

Ha $g \in D\{a\}$ és $f \in D\{g(a)\}$, akkor $f \circ g \in D\{a\}$ és

$$(f \circ g)'(a) = f'(g(a)) \cdot g'(a).$$

Leibniz-jelöléssel: $\frac{d(f \circ g)}{dx} = \frac{df}{dy}\bigg|_{y=g(x)} \cdot \frac{dg}{dx}$.

## Inverz függvény deriváltja

Ha $f$ szigorúan monoton és $f \in D\{a\}$, $f'(a) \neq 0$, akkor $f^{-1} \in D\{f(a)\}$ és

$$(f^{-1})'(f(a)) = \frac{1}{f'(a)}, \qquad \text{azaz} \qquad (f^{-1})'(b) = \frac{1}{f'(f^{-1}(b))}.$$

## Hatványsor deriváltja

Ha $f(x) = \sum_{n=0}^{\infty} a_n (x-x_0)^n$ konvergens egy $(x_0-r, x_0+r)$ intervallumon, akkor $f$ tagról tagra deriválható:

$$f'(x) = \sum_{n=1}^{\infty} n\, a_n (x-x_0)^{n-1}.$$

## Kapocs

- [[concepts/analii/derivalt-fogalma]] — a derivált definíciója, amelyre a szabályok épülnek
- [[concepts/analii/elemi-fuggvenyek-derivaltjai]] — a szabályok alkalmazásai konkrét függvényekre
- [[concepts/analii/magasabb-rendu-derivaltak]] — Leibniz-szorzatszabály $n$-edik deriváltra
