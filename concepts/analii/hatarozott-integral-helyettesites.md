---
tags: [concept]
sources: [01_ea_an_ii_a_b_merged.pdf]
references: ["An II A/B 10. előadás"]
derivation: source
updated: 2026-09-04
---

# Helyettesítéssel való integrálás (határozott integrál)

A láncszabály inverze határozott integrálra: az integrálási intervallum és az integrandus egyidejű transzformációja.

## Tétel

**T.f.h.** $f \in C[a,b]$ és $g : [\alpha, \beta] \to [a,b]$ függvény folytonosan deriválható. Ekkor

$$\int_{g(\alpha)}^{g(\beta)} f = \int_\alpha^\beta f \circ g \cdot g'.$$

## Bizonyítás

Tekintsük az

$$F(x) := \int_{g(\alpha)}^x f \qquad (x \in [a,b]), \qquad G(u) := \int_\alpha^u f \circ g \cdot g' \qquad (u \in [\alpha,\beta])$$

integrálfüggvényeket. Megmutatjuk, hogy

$$(*) \qquad \int_{g(\alpha)}^{g(\beta)} f = F(g(\beta)) = G(\beta) = \int_\alpha^\beta f \circ g \cdot g'.$$

Egyrészt $f \in C[a,b] \Rightarrow F' = f$; másrészt $f \circ g \cdot g' \in C[\alpha,\beta] \Rightarrow G' = f \circ g \cdot g'$.

Mivel $(F \circ g)' = F' \circ g \cdot g' = f \circ g \cdot g'$, ezért $(F \circ g - G)' = 0 \Rightarrow \exists c \in \mathbb{R}: F \circ g - G = c$.

Ugyanakkor $F(g(\alpha)) = 0 = G(\alpha)$, tehát $c = 0$, következésképpen $F \circ g = G \Rightarrow F(g(\beta)) = G(\beta)$.

A $(*)$ egyenlőség tehát valóban teljesül. $\blacksquare$

## Példa

Számítsuk ki a $\displaystyle\int_0^1 \frac{1}{\sqrt{3x+1}}\, dx$ határozott integrált.

**Megoldás.** Legyen $g(x) := 3x + 1$ ($0 \leq x \leq 1$), $f(x) := \frac{1}{\sqrt{x}}$ ($1 \leq x \leq 4$).

Ekkor $g \in D[0,1]$ és $g'(x) = 3$. Az előző tétel szerint

$$\int_0^1 \frac{1}{\sqrt{3x+1}}\, dx = \frac{1}{3} \cdot \int_0^1 (f \circ g) \cdot g' = \frac{1}{3} \cdot \int_1^4 f = \frac{1}{3} \cdot \int_1^4 \frac{1}{\sqrt{x}}\, dx = \frac{1}{3} \cdot \left[2\sqrt{x}\right]_1^4 = \frac{1}{3}(2\sqrt{4} - 2\sqrt{1}) = \frac{2}{3}.$$

## Megjegyzés: integráció határainak transzformációja

Lényeges különbség a határozatlan integrál helyettesítési szabályához képest: az integrálási határokat is transzformálni kell ($g(\alpha)$-tól $g(\beta)$-ig). Nem kell visszahelyettesíteni — az eredeti változóba való visszatérés elmarad.

## Kapocs

- [[concepts/analii/newton-leibniz-tetel]] — a bizonyítás az integrálfüggvény deriválhatóságán és a Newton–Leibniz-tételen alapul
- [[concepts/analii/integralfuggveny]] — $F$ és $G$ integrálfüggvények deriváltjai jelennek meg a bizonyításban
- [[concepts/analii/hatarozatlan-integral]] — a határozatlan integrál (második) helyettesítési szabálya; visszahelyettesítés szükséges
- [[concepts/analii/hatarozott-integral-parcialisintegrals]] — a másik fő integrálási technika határozott integrálra
- [[concepts/analii/derivalasi-szabalyok]] — a láncszabály $(F \circ g)' = F' \circ g \cdot g'$ alkalmazva
