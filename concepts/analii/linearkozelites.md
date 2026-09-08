---
tags: [concept]
sources: [01_ea_an_ii_a_b_merged.pdf]
references: ["An II A/B 1. előadás"]
derivation: source
updated: 2026-09-04
---

# Lineáris közelítés

A derivált ekvivalens jellemzése: $f$ az $a$ pontban pontosan akkor deriválható, ha $f(x) - f(a)$ az $(x - a)$ elsőfokú függvényével közelíthető egy $a$-ban nullává váló hibataggal.

## Tétel

Legyen $f \in \mathbb{R} \to \mathbb{R}$ és $a \in \text{int}\, \mathcal{D}_f$. Ekkor $f \in D\{a\}$ ekvivalens azzal, hogy

$$\exists A \in \mathbb{R} \text{ és } \exists \varepsilon : \mathcal{D}_f \to \mathbb{R}, \lim_a \varepsilon = 0 :$$
$$f(x) - f(a) = A \cdot (x - a) + \varepsilon(x)(x - a) \quad (x \in \mathcal{D}_f),$$

és $A = f'(a)$.

## Bizonyítás

**($\Rightarrow$)** Ha $f \in D\{a\}$, azaz $\lim_{x \to a} \frac{f(x)-f(a)}{x-a} = f'(a) \in \mathbb{R}$, definiáljuk:

$$\varepsilon(x) := \frac{f(x) - f(a)}{x - a} - f'(a) \quad (x \in \mathcal{D}_f \setminus \{a\}).$$

Ekkor $\lim_a \varepsilon = 0$ és $f(x) - f(a) = f'(a)(x-a) + \varepsilon(x)(x-a)$, tehát $A = f'(a)$ választással teljesül.

**($\Leftarrow$)** Ha teljesül a feltétel, akkor

$$\frac{f(x) - f(a)}{x - a} = A + \varepsilon(x) \xrightarrow{x \to a} A,$$

ami azt jelenti, hogy $f \in D\{a\}$ és $f'(a) = A$. $\blacksquare$

## Értelmezés

A lineáris közelítés tétele azt mondja ki, hogy $f$ lokálisan az

$$\ell(x) := f(a) + f'(a)(x - a)$$

affin függvénnyel közelíthető, mégpedig úgy, hogy a hiba $(x-a)$-nál gyorsabban tart 0-ba ($o(x-a)$ kis ordó értelemben). Ez a [[concepts/analii/erintofuggveny|erintofuggveny]] meredeksége is.

## Kapocs

- [[concepts/analii/derivalt-fogalma]] — a derivált definíciója, amellyel ekvivalens ez a jellemzés
- [[concepts/analii/erintofuggveny]] — $\ell(x) = f(a) + f'(a)(x-a)$ az érintő egyenlete
- [[concepts/analii/taylor-polinom]] — magasabb rendű közelítések általánosítása
