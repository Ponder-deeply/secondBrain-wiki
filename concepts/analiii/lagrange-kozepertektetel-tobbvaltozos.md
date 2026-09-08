---
tags: [concept]
sources: [SimonP-Anal2.pdf]
references: ["Simon Péter: Analízis II., 4.3.3. Tétel, 4.4. viii) megjegyzés"]
derivation: source
updated: 2026-09-07
---

# Lagrange-középértéktétel több változóban

Differenciálható $f \in \mathbb{R}^n \to \mathbb{R}$ és $[a,b] \subset D_f$ esetén van olyan $c \in (a,b)$, hogy $f(b) - f(a) = \langle \operatorname{grad} f(c), b-a\rangle$ — vektorértékű függvényre viszont **nem** igaz, csak koordinátánként.

## Tartalom

### A tétel

Legyen $f \in \mathbb{R}^n \to \mathbb{R}$ differenciálható, $a \ne b$, $[a,b] \subset D_f$. Ekkor alkalmas $c \in (a,b)$ mellett

$$f(b) - f(a) = \langle \operatorname{grad} f(c),\, b - a\rangle.$$

Ez a [[concepts/analiii/tobbvaltozos-taylor-formula|Taylor-formula]] $s = 0$ esete: $T_{a,0}f \equiv f(a)$, és az $|i| = 1$ multiindexek szerinti összeg épp a skalárszorzat.

### Vektorértékű eset: koordinátánként, külön közbülső pontokkal

Ha $f = (f_1, \dots, f_m) \in \mathbb{R}^n \to \mathbb{R}^m$ differenciálható és $[a,b] \subset D_f$, akkor minden $i$-re **külön** $\xi^{(i)} \in (a,b)$ hellyel

$$f_i(b) - f_i(a) = \langle \operatorname{grad} f_i(\xi^{(i)}),\, h\rangle \qquad (h := b - a).$$

**A közbülső pontok általában különbözőek**, ezért nincs egyetlen $c$, amelyre $f(b) - f(a) = f'(c)(b-a)$ teljesülne. Ez a többváltozós elmélet egyik jellemző vesztesége.

### A használható pótlék: Lipschitz-becslés

Amit a vektorértékű eset helyett használni szoktunk, az a normabecslés: ha a szakaszon a Jacobi-mátrix normája korlátos, akkor

$$\|f(x) - f(t)\| \le \sup\{\|f'(\xi)\| : \xi \in [x,t]\}\cdot \|x - t\|.$$

Ez az, ami például a [[concepts/analiii/lokalis-invertalhatosag|lokális invertálhatóság]] bizonyításában a kontrakciós feltételt adja: ha a parciális deriváltak elég kicsik egy környezetben, a függvény ott $\tfrac12$-kontrakció, és jöhet a [[concepts/analiii/banach-fixponttetel-metrikus-terben|Banach-fixponttétel]].

## Kapocs

- [[concepts/analiii/tobbvaltozos-taylor-formula]] — ennek $s = 0$ esete.
- [[concepts/analiii/lokalis-invertalhatosag]] — a Lipschitz-becslés fő alkalmazása.
- [[concepts/analiii/banach-fixponttetel-metrikus-terben]] — a becslés adja a kontrakciós tulajdonságot.
- [[concepts/analii/kozeptertekek]] — az egyváltozós középértéktételek.
