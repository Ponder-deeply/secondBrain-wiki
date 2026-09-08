---
tags: [concept]
sources: [SimonP-Anal2.pdf]
references: ["Simon Péter: Analízis II., 4.1.5. és 4.5.4.1. Tétel"]
derivation: source
updated: 2026-09-07
---

# Inverzfüggvény-tétel

Ha $f \in \mathbb{R}^n\to\mathbb{R}^n$ folytonosan differenciálható és $\det f'(a) \ne 0$, akkor $a$ egy környezetében invertálható, a lokális inverz **folytonosan differenciálható**, és $h'(x) = \big(f'(h(x))\big)^{-1}$.

## Tartalom

### Az elemi előfutár

Már a differenciálási szabályok között kimondható a következő: ha $f \in \mathbb{R}^n\to\mathbb{R}^n$ (a) invertálható, (b) $f \in D\{a\}$ és $f'(a)$ invertálható, (c) $b := f(a)$ belső pontja $R_f$-nek, (d) $f^{-1}$ folytonos $b$-ben, akkor $f^{-1} \in D\{b\}$, és

$$\big(f^{-1}\big)'(b) = \big(f'(a)\big)^{-1}.$$

Ez azonban **négy feltételt tesz fel**, köztük az inverz létezését és folytonosságát — épp azt, amit tudni szeretnénk. A bizonyítás az $x - a = A(y-b) - A\eta(x-a)\|x-a\|$ átrendezésen múlik ($A := f'(a)^{-1}$), ahol a $\|f^{-1}(y)-f^{-1}(b)\| / \|y-b\| \le 2q$ korlátosságot külön kell kicsikarni.

### A tétel

Legyen $f \in \mathbb{R}^n\to\mathbb{R}^n$ **folytonosan** differenciálható, és az $a \in \operatorname{int} D_f$ pontban $\det f'(a) \ne 0$. Ekkor alkalmas $K(a) \subset D_f$ környezettel az $f|_{K(a)}$ leszűkítés invertálható, a $h := (f|_{K(a)})^{-1}$ lokális inverz folytonosan differenciálható, és

$$h'(x) = \big(f'(h(x))\big)^{-1} \qquad (x \in D_h).$$

Itt tehát **semmit sem teszünk fel az inverzről** — a $C^1$-ség és az egyetlen determinánsfeltétel mindent maga után von.

### A levezetés: implicitfüggvényként

Legyen $b := f(a)$ és $F(u,v) := f(v) - u$. Ekkor $F(b,a) = 0$, továbbá

$$F'(u,v) = [\partial_1 F\ \ \partial_2 F] = [-I \ \ f'(v)],$$

tehát $F \in C^1\{(b,a)\}$ és $\det \partial_2 F(b,a) = \det f'(a) \ne 0$. Az [[concepts/analiii/implicitfuggveny-tetel|implicitfüggvény-tétel]] szerint van olyan $g : K(b)\to K(a)$ implicitfüggvény, amelyre $F(x,g(x)) = f(g(x)) - x = 0$, azaz $f(g(x)) = x$, és

$$g'(b) = -\partial_2 F(b,a)^{-1}\partial_1 F(b,a) = -\big(f'(a)\big)^{-1}(-I) = \big(f'(a)\big)^{-1}.$$

Végül a [[concepts/analiii/lokalis-invertalhatosag|lokális invertálhatósági tételből]] tudjuk, hogy $f$-nek van lokális inverze, amelynek értelmezési tartománya nyílt; az egyértelműség miatt $g = h$ ezen a környezeten, tehát $h$ örökli $g$ tulajdonságait.

### A logikai lánc

$$\text{Banach-fixponttétel} \ \to\ \text{lokális invertálhatóság} \ \to\ \text{implicitfüggvény-tétel} \ \to\ \text{inverzfüggvény-tétel}.$$

A kör bezárul: az inverzfüggvény-tétel az implicitfüggvény-tételből jön, az pedig a lokális invertálhatóságból. A három tétel logikailag ekvivalens, csak a bizonyítási sorrend rögzített.

### Ellenőrző példa

$f(x,y) := (x-y, 2x+3y)$. Itt $f'(x,y) = \begin{bmatrix}1 & -1\\ 2 & 3\end{bmatrix}$, $\det = 5 \ne 0$, és $f$ globálisan bijekció:

$$f^{-1}(u,v) = \left(\frac{v+3u}{5}, \frac{v-2u}{5}\right), \qquad (f^{-1})'(u,v) = \frac{1}{5}\begin{bmatrix}3&1\\-2&1\end{bmatrix},$$

ami valóban $f'(x,y)$ inverze.

## Kapocs

- [[concepts/analiii/lokalis-invertalhatosag]] — a lánc első tagja.
- [[concepts/analiii/implicitfuggveny-tetel]] — amiből ez levezethető.
- [[concepts/analiii/egyszeru-lekepezesekre-bontas]] — az inverzfüggvény-tétel egy erős következménye.
- [[concepts/analiii/mertek-es-integraltranszformacio]] — ahol a lokálisan invertálható, $C^1$ helyettesítések használatba kerülnek.
- [[concepts/analiii/jacobi-matrix]] — a mátrix, amelyet invertálunk.
