---
tags: [concept]
sources: [01_ea_an_ii_a_b_merged.pdf]
references: ["An II A/B 1. előadás"]
derivation: source
updated: 2026-09-04
---

# Folytonosság és a derivált kapcsolata

A deriválhatóság erősebb tulajdonság a folytonosságnál: minden deriválható függvény folytonos, de nem minden folytonos függvény deriválható.

## Tétel

Tegyük fel, hogy $f \in \mathbb{R} \to \mathbb{R}$ és $a \in \text{int}\, \mathcal{D}_f$. Ekkor

$$1^\circ \quad f \in D\{a\} \implies f \in C\{a\},$$
$$2^\circ \quad \text{Az állítás megfordítása nem igaz.}$$

## Bizonyítás ($1^\circ$)

$f \in D\{a\}$ esetén $a \in \text{int}\, \mathcal{D}_f \Rightarrow a \in \mathcal{D}'_f \Rightarrow a \in \mathcal{D}_f \cap \mathcal{D}'_f$. Ezért:

$$f \in C\{a\} \iff \exists \lim_{x \to a} f(x) = f(a) \iff \lim_{x \to a}(f(x) - f(a)) = 0.$$

$$\lim_{x \to a}(f(x) - f(a)) = \lim_{x \to a} \left(\frac{f(x) - f(a)}{x - a} \cdot (x - a)\right) = f'(a) \cdot 0 = 0. \quad \blacksquare$$

## Ellenpélda ($2^\circ$): abszolútérték-függvény

$$\text{abs} \in C\{0\}, \quad \text{de} \quad \text{abs} \notin D\{0\},$$

mert a különbségi hányados-függvény:

$$\mathbb{R} \setminus \{0\} \ni x \mapsto \frac{|x| - |0|}{x - 0} = \frac{|x|}{x} = \begin{cases} 1, & \text{ha } x > 0 \\ -1, & \text{ha } x < 0 \end{cases}$$

függvénynek a $0$ pontban nincs határértéke (bal és jobb oldali határértékek különböznek).

## Mindenhol folytonos, de sehol sem deriválható függvények

Léteznek $\mathbb{R}$-en mindenhol folytonos, de sehol sem deriválható függvények:

- **K. Weierstrass (1861):**
$$f(x) := \sum_{n=0}^{+\infty} \frac{\cos(15^n \pi x)}{2^n} \quad (x \in \mathbb{R})$$

- **T. Takagi (1903) / B. L. van der Waerden (1930):**
$$f(x) := \sum_{n=0}^{+\infty} \frac{\langle 10^n x \rangle}{10^n} \quad (x \in \mathbb{R}),$$
ahol $\langle \alpha \rangle := \min\{|\alpha - k| \mid k \in \mathbb{Z}\}$ az $\alpha$-hoz legközelebbi egész távolsága.

Ezek fraktálszerű grafikonú, „töréspontokból álló" függvények.

## Kapocs

- [[concepts/analii/derivalt-fogalma]] — derivált definíciója és különbségi hányados
- [[concepts/analii/egyoldali-derivaltak]] — bal/jobb oldali derivált; $|\cdot|$ a 0-ban egyoldali deriváltjai $\pm 1$
- [[concepts/analii/kozeptertekek]] — középértéktételek folytonosságot és deriválhatóságot igényelnek
