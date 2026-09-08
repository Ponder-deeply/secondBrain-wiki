---
tags: [concept]
sources: [01_ea_an_ii_a_b_merged.pdf]
references: ["An II A/B 5. előadás"]
derivation: source
updated: 2026-09-04
---

# Taylor-sor és előállítás

A Taylor-sor egy $D^\infty$ függvényhez formálisan felírható, de két kérdés egymástól független: (1) hol konvergens a sor, és (2) hol állítja elő ténylegesen a függvényt?

## A sorfejtés két kérdése

Legyen $f \in D^\infty\{a\}$. Természetes módon vethetjük fel:

1. **A konvergencia kérdése.** Hol konvergens a $T_a f$ Taylor-sor? (Milyen $I \subset \mathbb{R}$ intervallumon?)

2. **Az előállítás kérdése.** Ha a Taylor-sor konvergens egy $I \subset \mathbb{R}$ intervallumon, vajon fennáll-e az

$$f(x) = \sum_{k=0}^{+\infty} \frac{f^{(k)}(a)}{k!}(x-a)^k \qquad (x \in I)$$

egyenlőség? Ha ez igaz, azt mondjuk, hogy **a Taylor-sor előállítja $f$-et az $I$ intervallumon**.

A két kérdés egymástól független: egy függvény Taylor-sora konvergálhat anélkül, hogy az összege maga a függvény lenne.

## Ellenpélda: $e^{-1/x^2}$

Az alábbi függvény mutatja, hogy konvergencia $\not\Rightarrow$ előállítás:

$$f(x) := \begin{cases} e^{-1/x^2}, & \text{ha } x \in \mathbb{R} \setminus \{0\} \\ 0, & \text{ha } x = 0. \end{cases}$$

Igazolható, hogy $f \in D^\infty(\mathbb{R})$ és $f^{(n)}(0) = 0$ minden $n \in \mathbb{N}$ esetén. Ezért a $T_0 f$ Maclaurin-sor minden együtthatója 0, összegfüggvénye az $\mathbb{R}$-en azonosan 0 függvény — ami $f$-et egyetlen $x \neq 0$ pontban sem állítja elő.

Ez azt jelenti: $f \in D^\infty(\mathbb{R})$ és a Taylor-sor $\mathbb{R}$-en konvergens, de **nem állítja elő** $f$-et.

## Elégséges feltétel az előállításra

Ha az $f$ függvény valamennyi deriváltja korlátosak — azaz létezik $M > 0$, hogy $|f^{(n)}(x)| \leq M$ minden $n \in \mathbb{N}$ és minden $x$ esetén egy intervallumban —, akkor a Lagrange-maradéktag nullához tart, és a Taylor-sor előállítja $f$-et.

Részletesen: [[concepts/analii/taylor-formula-maradektag|taylor-formula-maradektag]] (Lagrange-maradéktag és a konvergencia bizonyítása).

## Az „egyedi eszköz" módszer

Néhány függvénynél a sorfejtés problémáját közvetett úton oldjuk meg: ismert sorfejtésekből (tagonkénti deriválással, integrálással, helyettesítéssel) levezetjük az ismeretlen sorfejtést, majd igazoljuk, hogy a kapott sor valóban $f$-et állítja elő. Ezt a technikát alkalmazzák a [[concepts/analii/nevezetes-sorfejtesek|nevezetes-sorfejtesek]] mindegyikének bizonyítása során.

## Kapocs

- [[concepts/analii/taylor-polinom]] — Taylor-polinom és Taylor-sor definíciója, egyediség
- [[concepts/analii/taylor-formula-maradektag]] — Lagrange-maradéktag; az előállítás bizonyításának eszköze
- [[concepts/analii/nevezetes-sorfejtesek]] — konkrét sorfejtések: $\frac{1}{1+x}$, $\ln(1+x)$, $\arctan x$, binomiális sor, $\arcsin x$
- [[concepts/analii/magasabb-rendu-derivaltak]] — $D^\infty$ osztály fogalma
