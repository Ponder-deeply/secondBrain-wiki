---
tags: [concept]
sources: [SimonP-Anal2.pdf]
references: ["Simon Péter: Analízis II., 4.5.5. szakasz, 4.5.5.1. Tétel"]
derivation: source
updated: 2026-09-07
---

# Feltételes szélsőérték és a Lagrange-multiplikátorok

Ha $f$-et csak a $\{g = 0\}$ halmazon vizsgáljuk, a szokásos $\operatorname{grad} f(c) = 0$ feltétel értelmetlen — helyette az $f + \lambda g$ függvény gradiensének kell eltűnnie alkalmas $\lambda \in \mathbb{R}^m$ multiplikátorvektorral.

## Tartalom

### Miért kell új elmélet

A klasszikus feladat: mekkora az egységnyi kerületű téglalapok közül a legnagyobb területű? Modellje: maximalizáljuk $f(x,y) = xy$-t a $g(x,y) := 2x + 2y - 1 = 0$ feltétel mellett. A baj az, hogy

$$D_{f|\{g=0\}} = \{g = 0\}$$

halmaznak **egyetlen belső pontja sincs** $\mathbb{R}^2$-ben, tehát a [[concepts/analiii/lokalis-szelsoertek-feltetelei|lokális szélsőérték feltételei]] szó szerint nem alkalmazhatók.

**Az egyik kiút — behelyettesítés.** Itt a feltétel megoldható: $y = h(x) = 1/2 - x$, tehát $\{g=0\} = \operatorname{graf} h$, és elég a $\Phi(x) := f(x,h(x)) = x(1/2 - x)$ egyváltozós függvényt vizsgálni. Általánosan ez az [[concepts/analiii/implicitfuggveny|implicitfüggvény]] léte, azaz az [[concepts/analiii/implicitfuggveny-tetel|implicitfüggvény-tétel]] — és ez lesz a bizonyítás motorja is. A **Lagrange-szabály** ugyanezt a redukciót végzi el, csak anélkül, hogy a feltételt ténylegesen meg kellene oldani.

### A fogalom

Legyen $\emptyset \ne U \subset \mathbb{R}^n$, $f : U \to \mathbb{R}$, $g : U \to \mathbb{R}^m$, továbbá

$$\{g = 0\} := \{\xi \in U : g(\xi) = 0\} \ne \emptyset.$$

Az $f$-nek a $g = 0$ feltételre nézve **feltételes lokális maximuma** van $c \in \{g=0\}$-ban, ha az $f$ leszűkítésének $\{g = 0\}$-ra van ott lokális maximuma, azaz egy $K(c)$ környezettel

$$f(\xi) \le f(c) \qquad (\xi \in \{g=0\}\cap K(c)).$$

A minimum és az abszolút változatok analóg módon.

### Elsőrendű szükséges feltétel (Lagrange)

Legyen $m < n$, $U \subset \mathbb{R}^n$ nyílt, $f \in D$, $g \in C^1$. Ha $f$-nek $c \in \{g=0\}$-ban feltételes lokális szélsőértéke van, **és a $g'(c) \in \mathbb{R}^{m\times n}$ mátrix rangja $m$**, akkor van olyan $\lambda \in \mathbb{R}^m$, hogy

$$\operatorname{grad}(f + \lambda g)(c) = 0,$$

ahol $(\lambda g)(\xi) := \langle \lambda, g(\xi)\rangle = \sum_{i=1}^m \lambda_i g_i(\xi)$. Koordinátánként:

$$\partial_k f(c) + \sum_{l=1}^m \lambda_l\,\partial_k g_l(c) = 0 \qquad (k = 1,\dots,n).$$

A $\lambda_i$ számok a **Lagrange-multiplikátorok**.

### A bizonyítás gondolatmenete

A rangfeltétel miatt a $g'(c)$ mátrixnak van invertálható $m\times m$-es részmátrixa; a változókat átrendezve feltehető, hogy $\det \partial_2 g(c) \ne 0$, ahol $c = (a,b)$. Az [[concepts/analiii/implicitfuggveny-tetel|implicitfüggvény-tétel]] szerint van $h : K(a)\to K(b)$, $g(x,h(x)) = 0$, és a feltételes szélsőérték ekkor az $x \mapsto f(x,h(x))$ **feltétel nélküli** szélsőértékévé válik. Erre alkalmazva a szokásos elsőrendű feltételt és a [[concepts/analiii/lancszabaly|láncszabályt]] kapjuk az utolsó $m$ koordinátára a $\lambda$ definícióját, az első $n-m$-re pedig a fenti egyenletek teljesülését.

### A rangfeltétel nem hagyható el

$g'(c)$ rangja $m$ azt jelenti, hogy a $g_1, \dots, g_m$ feltételek gradiensei **lineárisan függetlenek** $c$-ben. Ha ez sérül, a szabály hamis: például $g(x,y) := (x-y)^2$ és $f(x,y) := x$ esetén a feltételes szélsőértékhelyeken $\operatorname{grad} g = 0$, tehát semmilyen $\lambda$ nem hozza nullába $\operatorname{grad}(f+\lambda g)$-t.

### Geometriai olvasat

A feltétel azt mondja, hogy $\operatorname{grad} f(c)$ **benne van** a $\operatorname{grad} g_1(c), \dots, \operatorname{grad} g_m(c)$ vektorok által kifeszített altérben. Mivel a $g_i$-k gradiensei merőlegesek a saját [[concepts/analiii/nivofelulet-es-gradiens|nívófelületükre]], ez épp azt jelenti: $\operatorname{grad} f(c)$ merőleges a feltételhalmaz érintőterére, azaz a felület mentén elmozdulva $f$ elsőrendben nem változik.

### Gyakorlati recept

Az $F := f + \lambda g$ **Lagrange-függvény** $n + m$ ismeretlenre ($x_1,\dots,x_n,\lambda_1,\dots,\lambda_m$) $n+m$ egyenletet ad: $\operatorname{grad}_x F = 0$ és $g = 0$. A megoldások a feltételes szélsőérték **jelöltjei**; hogy melyik valóban az, azt a [[concepts/analiii/felteteles-szelsoertek-masodrendu-feltetelei|másodrendű feltételek]] döntik el.

## Kapocs

- [[concepts/analiii/felteteles-szelsoertek-masodrendu-feltetelei]] — a jelöltek osztályozása.
- [[concepts/analiii/implicitfuggveny-tetel]] — a bizonyítás motorja.
- [[concepts/analiii/lokalis-szelsoertek-feltetelei]] — a feltétel nélküli eset, amelyre visszavezetünk.
- [[concepts/analiii/nivofelulet-es-gradiens]] — a geometriai olvasat.
- [[concepts/analiii/lancszabaly]] — a redukció eszköze.
