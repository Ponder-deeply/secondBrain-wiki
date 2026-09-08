---
tags: [concept]
sources: [01_ea_an_ii_a_b_merged.pdf]
references: ["An II A/B 7. előadás"]
derivation: source
updated: 2026-09-04
---

# A határozott integrál motivációja

A határozott integrál fogalma a terület, térfogat, ívhossz stb. kiszámítási igényéből nőtt ki — ezeket téglalapok területeinek összegeként közelítjük, majd határértéket veszünk.

## A síkidom területének problémája

Legyen $f \geq 0$ korlátos függvény az $[a,b]$ intervallumon. Tekintsük az $f$ grafikonja alatti

$$A_f := \{(x,y) \mid x \in [a,b],\ 0 \leq y \leq f(x)\}$$

síkidomot. Kérdés: hogyan értelmezhető és számítható ki $t(A_f)$?

**Alapötlet:** a síkidom területét téglalapok területeinek összegével közelítjük (beírt és körülírt téglalapok).

## Példa: $f(x) = x^2$ az $[0,1]$-en

Osszuk fel a $[0,1]$ intervallumot $n$ egyenlő részre: $x_k = \frac{k}{n}$.

$$s_n = \frac{1}{n}\left(\left(\frac{1}{n}\right)^2 + \left(\frac{2}{n}\right)^2 + \cdots + \left(\frac{n-1}{n}\right)^2\right) = \frac{(n-1)n(2n-1)}{6n^3},$$

$$S_n = \frac{1}{n}\left(\left(\frac{1}{n}\right)^2 + \left(\frac{2}{n}\right)^2 + \cdots + \left(\frac{n}{n}\right)^2\right) = \frac{n(n+1)(2n+1)}{6n^3}.$$

(Felhasználva: $1^2 + 2^2 + \cdots + m^2 = \frac{m(m+1)(2m+1)}{6}$.)

Minden $n$-re $s_n \leq t(A_f) \leq S_n$, és

$$\lim_{n\to+\infty} s_n = \frac{1}{6}\cdot 1 \cdot 2 = \frac{1}{3}, \qquad \lim_{n\to+\infty} S_n = \frac{1}{6}\cdot 1 \cdot 2 = \frac{1}{3},$$

tehát $t(A_f) = \frac{1}{3}$.

## Történeti áttekintő

- **Eudoxosz** (i.e. 408–355): kimerítés módszere — tetszőleges pontossággal közelítő sorozatok.
- **Arkhimédész** (i.e. 287–212): a módszert továbbfejlesztette; meghatározta parabolaszelet, gömb, spirálok területét/ívhosszát.
- **XVII. századi európai matematikusok** (Barrow, Cavalieri, Fermat, Kepler, Newton, Leibniz): kidolgozták a kalkulus (differenciál- és integrálszámítás) elméletét.
- **L'Hospital** (1661–1704): *Infinitézimál-számítás* (1696) — közel 100 évig a téma legfontosabb tankönyve.
- **XIX. század** (Cauchy, Weierstrass, Dedekind): a kalkulus homályos fogalmait precízen definiált matematikai fogalmakkal helyettesítették; megszületett a modern **analízis**.

## Kapocs

- [[concepts/analii/hatarozott-integral-ertelmezese]] — a határozott integrál formális értelmezése
- [[concepts/analii/primitiv-fuggveny]] — a határozatlan integrál kapcsolata
