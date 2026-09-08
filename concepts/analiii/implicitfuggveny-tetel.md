---
tags: [concept]
sources: [SimonP-Anal2.pdf]
references: ["Simon Péter: Analízis II., 4.5.3.1–4.5.3.3. Tétel"]
derivation: source
updated: 2026-09-07
---

# Implicitfüggvény-tétel

$f \in C^1$, $f(a,b) = 0$ és $\det \partial_2 f(a,b) \ne 0$ esetén az $f(x,y) = 0$ egyenlet lokálisan egyértelműen megoldható $y$-ra, a megoldásfüggvény folytonosan differenciálható, és $g'(x) = -\partial_2 f(x,g(x))^{-1}\cdot \partial_1 f(x, g(x))$.

## Tartalom

### Létezés

Legyen $2 \le n$, $1 \le m < n$, $f \in \mathbb{R}^{n-m}\times\mathbb{R}^m \to \mathbb{R}^m$. Ha az $(a,b) \in \operatorname{int} D_f$ helyen

$$f(a,b) = 0, \qquad f \in C^1\{(a,b)\}, \qquad \det \partial_2 f(a,b) \ne 0,$$

akkor létezik az $f$ által $(a,b)$ körül meghatározott **folytonos** [[concepts/analiii/implicitfuggveny|implicitfüggvény]].

**A bizonyítás fogása.** Tekintsük az $F(x,y) := (x, f(x,y))$ segédfüggvényt $\mathbb{R}^n \to \mathbb{R}^n$-be. Ennek Jacobi-mátrixa blokkháromszög alakú, determinánsa $\det \partial_2 f(a,b) \ne 0$, tehát a [[concepts/analiii/lokalis-invertalhatosag|lokális invertálhatósági tétel]] szerint $F$ lokálisan invertálható $(a,b)$ körül, és inverze folytonos, sőt Lipschitz. Az inverz második komponense adja $g$-t: $g(x) := \Phi_2(x,0)$, ahol $\Phi = F^{-1}$. Az egyértelműség az $F$ lokális injektivitásából jön: ha $f(x,z) = 0$ is teljesülne, akkor $F(x,g(x)) = (x,0) = F(x,z)$ volna, ellentmondás. A $\Phi \in \operatorname{Lip}(1)$ tulajdonságból pedig $g \in \operatorname{Lip}(1)$ öröklődik.

**Az egész tétel tehát a lokális invertálhatóság átfogalmazása** — a $(x,y)\mapsto(x,f(x,y))$ trükk az, ami az implicit problémát inverz problémává alakítja.

### Differenciálhatóság

Ugyanezen feltételek mellett a $g$ implicitfüggvény differenciálható $a$-ban, és

$$g'(a) = -\partial_2 f(a,b)^{-1}\cdot \partial_1 f(a,b).$$

A típusok stimmelnek: $\partial_2 f(a,b)^{-1} \in \mathbb{R}^{m\times m}$, $\partial_1 f(a,b) \in \mathbb{R}^{m\times(n-m)}$, tehát a szorzat $\mathbb{R}^{m\times(n-m)}$-beli — épp amit egy $\mathbb{R}^{n-m}\to\mathbb{R}^m$ függvény deriváltjától várunk.

**Honnan jön a képlet.** Deriváljuk az $f(x, g(x)) = 0$ azonosságot a [[concepts/analiii/lancszabaly|láncszabállyal]]:

$$\partial_1 f(x,g(x)) + \partial_2 f(x,g(x))\cdot g'(x) = 0,$$

és rendezzük $g'(x)$-re. A tétel érdemi tartalma nem a képlet, hanem az, hogy $g$ **egyáltalán differenciálható**.

### Az összefoglaló alak

Ha $f \in C^1$ (nem csak egy pontban), akkor alkalmas $K(a)$, $K(b)$ környezetekkel a $g : K(a)\to K(b)$ implicitfüggvény **folytonosan** differenciálható, és

$$g'(x) = -\partial_2 f(x, g(x))^{-1}\cdot \partial_1 f(x, g(x)) \qquad (x \in K(a)).$$

Az indoklás: a $\partial_i f_k$ függvények folytonosak, $g$ folytonos, ezért az $x \mapsto \partial_i f_k(x, g(x))$ összetételek is azok; a mátrixinvertálás és -szorzás pedig folytonos műveletek, tehát $g'$ minden komponensfüggvénye folytonos.

### Példa

$f(x,y) := x^2 + y^2 - 1$, $(a,b) = (0,1)$. Itt $\partial_2 f(0,1) = 2 \ne 0$, tehát $y$ kifejezhető: $g(x) = \sqrt{1-x^2}$, és

$$g'(x) = -\frac{\partial_1 f}{\partial_2 f} = -\frac{2x}{2y} = -\frac{x}{\sqrt{1-x^2}}.$$

A $(1,0)$ pontban viszont $\partial_2 f(1,0) = 0$ — és valóban, ott a kör nem grafikonja semmilyen $y = g(x)$ függvénynek.

## Kapocs

- [[concepts/analiii/implicitfuggveny]] — a fogalom, amelynek létezéséről a tétel szól.
- [[concepts/analiii/lokalis-invertalhatosag]] — a tétel forrása.
- [[concepts/analiii/inverzfuggveny-tetel]] — ebből vezethető le, körbezárva a hármast.
- [[concepts/analiii/lancszabaly]] — a deriváltképlet levezetése.
- [[concepts/analiii/felteteles-szelsoertek]] — a fő alkalmazás.
