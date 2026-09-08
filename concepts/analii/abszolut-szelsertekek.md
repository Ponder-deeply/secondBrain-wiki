---
tags: [concept]
sources: [01_ea_an_ii_a_b_merged.pdf]
references: ["An II A/B 3. előadás"]
derivation: source
updated: 2026-09-04
---

# Abszolút szélsőértékek

Zárt, korlátos intervallumon folytonos függvénynek léteznek abszolút szélsőértékei (Weierstrass-tétel), és ezeket az összes stacionárius pont, illetve a végpontok összevetésével meghatározhatjuk.

## Weierstrass-tétel

**Tétel.** Korlátos és zárt $[a, b] \subset \mathbb{R}$ intervallumon folytonos $f$ függvénynek léteznek abszolút szélsőértékei, azaz

$$\exists\, \alpha, \beta \in [a, b] \quad \text{úgy, hogy} \quad f(\beta) \leq f(x) \leq f(\alpha) \quad (\forall x \in [a, b]).$$

## Abszolút szélsőértékhelyek keresése

Ha $f \in C[a, b]$, akkor van legnagyobb és legkisebb értéke. Ha $f$ ezek valamelyikét egy $c$ pontban veszi fel, akkor vagy $c = a$, vagy $c = b$, vagy pedig $c \in (a, b)$. Ez utóbbi esetben lokális szélsőértékről van szó.

Ha feltesszük még azt is, hogy $f \in D(a, b)$, akkor megkeressük az összes olyan $c \in (a, b)$ pontot, amelyben $f'$ eltűnik, majd kiszámítjuk $f$ értékét ezekben a pontokban (nem feledkezve meg az $a$ és $b$ végpontokról sem), és kiválasztjuk azokat, amelyekben $f$ értéke a legnagyobb (ill. legkisebb).

**Algoritmus abszolút szélsőérték meghatározásához** $[a, b]$-n, $f \in C[a,b] \cap D(a,b)$ esetén:

1. Megoldjuk az $f'(x) = 0$ egyenletet $(a, b)$-n; legyenek a megoldások $c_1, \ldots, c_k$.
2. Kiszámítjuk az $f(a),\, f(c_1),\, \ldots,\, f(c_k),\, f(b)$ értékeket.
3. A lista maximuma az abszolút maximum, minimuma az abszolút minimum.

## Kapcsolat a lokális szélsőértékekkel

Az abszolút szélsőérték-helyek köre tágabb a lokális szélsőérték-helyekénél: a végpontok ($a$ és $b$) önmagukban is abszolút szélsőérték-helyek lehetnek anélkül, hogy lokális szélsőérték-helyek lennének (lokális szélsőérték csak belső pontban értelmes).

## Kapocs

- [[concepts/analii/lokalis-szelsertekek]] — lokális szélsőérték; Fermat-féle feltétel, előjelváltásos és másodrendű elégséges feltételek
- [[concepts/analii/teljes-fuggvenyvizsgalat]] — az abszolút szélsőérték a függvényvizsgálat egyik lépése
- [[concepts/analii/kozeptertekek]] — Weierstrass-tétel előfeltételei: folytonosság zárt intervallumon
