---
tags: [concept]
sources: [01_ea_an_ii_a_b_merged.pdf]
references: ["An II A/B 10. előadás"]
derivation: source
updated: 2026-09-04
---

# Síkidom területe

A Riemann-integrál alkalmazása: két görbe közé zárt síkidom területének kiszámítása.

## Az egyszerű eset: $f \geq 0$

Ha $f \in K[a,b]$ és $f \geq 0$, akkor az

$$A_f := \{(x,y) \mid x \in [a,b],\ 0 \leq y \leq f(x)\}$$

síkidomnak **van területe**, ha $f \in R[a,b]$. Ekkor a terület:

$$t(A_f) := \int_a^b f(x)\, dx.$$

(Ez a motiváló definíció, amelyet a [[concepts/analii/hatarozott-integral-motivacio|határozott integrál motivációjánál]] vezettünk be.)

## Általános eset: két görbe között

**Definíció.** Legyen $f, g \in K[a,b]$ és t.f.h. $f(x) \leq g(x)$ minden $x \in [a,b]$-re. A m.h. az

$$A := \{(x,y) \in \mathbb{R}^2 \mid a \leq x \leq b,\ f(x) \leq y \leq g(x)\}$$

síkidomnak **van területe**, ha $f, g \in R[a,b]$. Ekkor a terület:

$$t(A) := \int_a^b \bigl(g(x) - f(x)\bigr)\, dx.$$

**Megjegyzés.** Ez a definíció összhangban van a területtől elvárt tulajdonságokkal. Az $f \geq 0$ eset könnyen meggondolható; az ellenkező esetben toljuk fel $A$-t az $x$ tengely fölé.

## Példa: az egységsugarú körlap területe

Helyezzük el a körlapot a koordináta-rendszerben úgy, hogy az origó legyen a körlap középpontja. Ekkor

$$g(x) = \sqrt{1-x^2}, \qquad f(x) = -\sqrt{1-x^2} \qquad (|x| \leq 1).$$

Mivel $f, g \in R[-1,1]$ ($g-f = 2\sqrt{1-x^2}$ folytonos), a körlap területe:

$$t(A) = \int_{-1}^1 \bigl(g(x) - f(x)\bigr)\, dx = 2\int_{-1}^1 \sqrt{1-x^2}\, dx.$$

A [[concepts/analii/newton-leibniz-tetel|Newton–Leibniz-tétel]] szerint (ismert primitív függvény):

$$t(A) = 2 \cdot \left[\frac{\arcsin x + x\sqrt{1-x^2}}{2}\right]_{-1}^1 = \arcsin 1 - \arcsin(-1) = \frac{\pi}{2} - \left(-\frac{\pi}{2}\right) = \pi.$$

## Kapocs

- [[concepts/analii/hatarozott-integral-motivacio]] — a területfogalom motiválta a határozott integrál bevezetését
- [[concepts/analii/newton-leibniz-tetel]] — a területszámítás fő eszköze: primitív függvény különbsége
- [[concepts/analii/hatarozott-integral-helyettesites]] — bonyolultabb területszámításoknál helyettesítés is szükséges lehet
- [[concepts/analii/folytonos-fuggvenyek-integralhatasaga]] — $C[a,b] \subset R[a,b]$; a folytonosság garantálja a terület létezését
