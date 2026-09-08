---
tags: [concept]
sources: [01_ea_an_ii_a_b_merged.pdf]
references: ["An II A/B 1. előadás"]
derivation: source
updated: 2026-09-04
---

# Érintőfüggvény

Az $f$ görbe $(a, f(a))$ pontjában húzott **érintő** az a célszerűen definiált egyenes, amelyhez a szekánsok egyenesek konvergálnak, ha a másik metszéspontot $a$-hoz húzzuk.

## Motiváció

A szekánsoknak van „határhelyzete", ha $h \to 0$, mert

$$\exists \lim_{h \to 0} \frac{f(a+h) - f(a)}{h}$$

határérték létezik és véges. Ekkor azt mondjuk, hogy a függvény **deriválható az $a$ pontban**. A görbe **érintőjének** azt az egyenest célszerű nevezni, amelyhez a húrok egyenesei tartanak, ha $h \to 0$.

## Definíció

Ha $f \in D\{a\}$, akkor az $f$ grafikon $(a, f(a))$ pontjában húzott **érintő** egyenlete:

$$\ell(x) = f(a) + f'(a) \cdot (x - a).$$

Az érintő meredeksége $f'(a)$, és átmegy az $(a, f(a))$ ponton.

## Kapcsolat a lineáris közelítéssel

A [[concepts/analii/linearkozelites|linearkozelites]] tétele szerint pontosan akkor létezik érintő, ha $f \in D\{a\}$, és ilyenkor az érintő az $f$ legjobb elsőfokú közelítése az $a$ pont körül.

## Kapocs

- [[concepts/analii/derivalt-fogalma]] — $f'(a)$ az érintő meredeksége
- [[concepts/analii/linearkozelites]] — az érintő a lineáris közelítés geometriai megfelelője
- [[concepts/analii/derivaltfuggveny]] — $f'$ mint az érintő meredekségét megadó függvény
