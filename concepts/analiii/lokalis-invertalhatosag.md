---
tags: [concept]
sources: [SimonP-Anal2.pdf]
references: ["Simon Péter: Analízis II., 4.5.2.1. Tétel"]
derivation: source
updated: 2026-09-07
---

# Lokális invertálhatóság

Ha $f \in \mathbb{R}^n \to \mathbb{R}^n$ folytonosan differenciálható $a$-ban és $\det f'(a) \ne 0$, akkor $f$ egy $a$ körüli környezetre leszűkítve invertálható, és a lokális inverze folytonos.

## Tartalom

### A fogalom

Az $f \in \mathbb{R}^n \to \mathbb{R}^n$ függvény **lokálisan invertálható** az $a \in \operatorname{int} D_f$ pontban, ha van olyan $K(a) \subset D_f$ környezet, amelyre a $g := f|_{K(a)}$ leszűkítés invertálható. A $g^{-1}$ függvény az $f$ **$a$-beli lokális inverze**.

### Az egyváltozós minta

$h \in \mathbb{R}\to\mathbb{R}$, $h \in C^1\{a\}$, $h'(a) \ne 0$ esetén $h'$ előjeltartó egy $I = (a-r, a+r)$ intervallumon, ezért $h|_I$ szigorúan monoton, tehát invertálható; az inverz folytonos, sőt differenciálható, és $g'(x) = 1/h'(g(x))$. **Több változóban nincs monotonitás**, ezért egészen más bizonyítás kell.

### A tétel

Ha $f \in C^1\{a\}$ és az $f'(a) \in \mathbb{R}^{n\times n}$ Jacobi-mátrix invertálható (azaz $\det f'(a) \ne 0$), akkor $f$ lokálisan invertálható $a$-ban, és a lokális inverze folytonos.

### A bizonyítás gondolatmenete: fixpont-keresés

Normalizálás után feltehető $a = f(a) = 0$ és $f'(0) = I$. Az $f(x) = y$ egyenlet megoldását fixpontproblémává alakítjuk:

$$\Phi_y(x) := x - f(x) + y =: g(x) + y.$$

Ekkor $x$ pontosan akkor megoldás, ha $\Phi_y(x) = x$. Mivel $g \in C^1\{0\}$ és $g'(0) = \Theta$ a nullmátrix, a parciális deriváltak folytonossága miatt egy $G_r(0)$ zárt környezeten $|\partial_i g_k(x)| < q$ tetszőlegesen kicsi $q$-val; $nq < 1/2$ választással

$$\|g'(x)\|_{(\infty)} < \tfrac12 \qquad (x \in G_r(0)).$$

Innen a [[concepts/analiii/lagrange-kozepertektetel-tobbvaltozos|Lagrange-becsléssel]]

$$\|\Phi_y(x) - \Phi_y(t)\|_\infty = \|g(x)-g(t)\|_\infty \le \tfrac12\|x-t\|_\infty,$$

tehát $\Phi_y$ **kontrakció** minden $y$-ra, és $\|y\|_\infty < r/2$ esetén $G_r(0)$-t önmagába képezi. A [[concepts/analiii/banach-fixponttetel-metrikus-terben|Banach-fixponttétel]] szerint egyértelmű fixpont van: minden ilyen $y$-hoz **pontosan egy** $x$ tartozik $f(x) = y$-nal. Ez épp az injektivitás és a szürjektivitás egyszerre; a folytonosság szintén a kontrakciós becslésből, sőt Lipschitz-tulajdonságként adódik.

**Ez a szakasz architektúrája:** a metrikus terek fejezete (teljesség, fixponttétel) itt fizet vissza, és ebből az egy tételből épül fel az [[concepts/analiii/implicitfuggveny-tetel|implicitfüggvény-tétel]], abból pedig az [[concepts/analiii/inverzfuggveny-tetel|inverzfüggvény-tétel]] differenciálhatósági része.

### Amit a tétel nem mond

A feltétel **nem elégséges globális** invertálhatósághoz: $f(x,y) := (e^x\cos y, e^x \sin y)$ mindenütt kielégíti $\det f' \ne 0$-t, de $2\pi$ szerint periodikus a második változóban. A lokalitás lényegi, nem technikai korlát.

## Kapocs

- [[concepts/analiii/banach-fixponttetel-metrikus-terben]] — a bizonyítás motorja.
- [[concepts/analiii/lagrange-kozepertektetel-tobbvaltozos]] — a kontrakciós becslés forrása.
- [[concepts/analiii/inverzfuggveny-tetel]] — a folytatás: a lokális inverz differenciálható is.
- [[concepts/analiii/implicitfuggveny-tetel]] — erre épül.
- [[concepts/analiii/jacobi-matrix]] — a determináns, amelynek nem szabad eltűnnie.
