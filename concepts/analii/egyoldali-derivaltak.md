---
tags: [concept]
sources: [01_ea_an_ii_a_b_merged.pdf]
references: ["An II A/B 1. előadás", "An II A/B 2. előadás"]
derivation: source
updated: 2026-09-04
---

# Egyoldali deriváltak

A pontbeli derivált fogalmának általánosítása: a különbségi hányados csak egyik irányból való közelítése.

## Definíció

Legyen $f \in \mathbb{R} \to \mathbb{R}$ és $a \in \mathcal{D}_f$.

**Jobb oldali derivált:**
$$f'_+(a) := \lim_{h \to 0^+} \frac{f(a+h) - f(a)}{h},$$
ha a határérték létezik és véges.

**Bal oldali derivált:**
$$f'_-(a) := \lim_{h \to 0^-} \frac{f(a+h) - f(a)}{h},$$
ha a határérték létezik és véges.

## Kapcsolat a kétoldali deriválttal

$$f \in D\{a\} \iff f'_+(a) = f'_-(a) \in \mathbb{R}.$$

Azaz $f$ pontosan akkor deriválható $a$-ban, ha mindkét egyoldali derivált létezik, véges, és egyenlő egymással.

## Példa: abszolútérték-függvény

$$\text{abs}'_+(0) = \lim_{h \to 0^+} \frac{|h|}{h} = 1, \qquad \text{abs}'_-(0) = \lim_{h \to 0^-} \frac{|h|}{h} = -1.$$

Mivel $1 \neq -1$, ezért $\text{abs} \notin D\{0\}$ — összhangban a [[concepts/analii/folytonossag-es-derivalt|folytonossag-es-derivalt]] ellenpéldájával.

## Alkalmazás: intervallum végpontjai

Ha $f$ értelmezési tartománya egy $[a, b]$ zárt intervallum, az $a$ bal végpontban csak jobb oldali, a $b$ jobb végpontban csak bal oldali derivált értelmes. Így az egyoldali deriváltak kiterjesztik a deriválhatóság fogalmát a határpontokra is.

## Kapocs

- [[concepts/analii/derivalt-fogalma]] — kétoldali derivált definíciója, amelynek speciális esetei az egyoldaliak
- [[concepts/analii/folytonossag-es-derivalt]] — abs $\notin D\{0\}$ részletes elemzése
- [[concepts/analii/lokalis-szelsertekek]] — szélsőérték szükséges feltétele egyoldali deriváltakkal is megfogalmazható
