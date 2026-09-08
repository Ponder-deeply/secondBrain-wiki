---
tags: [concept]
sources: [SimonP-Anal2.pdf]
references: ["Simon Péter: Analízis II., 4.5.3. szakasz bevezetése"]
derivation: source
updated: 2026-09-07
---

# Implicitfüggvény

Ha az $f(x,y) = 0$ egyenletrendszer minden $x$-hez egyértelműen meghatároz egy $y$-t egy környezeten belül, akkor az így kapott $g$ leképezés az $f$ által meghatározott implicitfüggvény — az „egyenlettel megadott függvény" pontos fogalma.

## Tartalom

### Motiváció: alulhatározott lineáris rendszer

Legyen $m < n$ és $A = (\alpha_{ik}) \in \mathbb{R}^{m\times n}$; tekintsük az $\sum_{k=1}^n \alpha_{ik}y_k = 0$ ($i = 1,\dots,m$) rendszert. Ha az utolsó $m$ ismeretlent hagyjuk szabadon meghatározandónak, és az első $n-m$-et **paraméternek** tekintjük, akkor

$$\sum_{k=n-m+1}^n \alpha_{ik}y_k = -\sum_{k=1}^{n-m}\alpha_{ik}x_k$$

annyi egyenlet, ahány ismeretlen. Ha a bal oldal $A_2 \in \mathbb{R}^{m\times m}$ mátrixának determinánsa nem nulla, Cramer-szabállyal minden paraméterértékhez egyértelmű megoldás tartozik. **Az implicitfüggvény ennek a nemlineáris általánosítása**, és a $\det A_2 \ne 0$ feltételből lesz a $\det \partial_2 f(a,b) \ne 0$ feltétel.

### A jelölési megállapodás

$2 \le n$, $1 \le m < n$ mellett az $\mathbb{R}^n = \mathbb{R}^{n-m}\times\mathbb{R}^m$ azonosítással egy $\xi \in \mathbb{R}^n$ vektort $\xi = (x,y)$ alakban írunk, ahol $x := (\xi_1,\dots,\xi_{n-m})$ és $y := (\xi_{n-m+1},\dots,\xi_n)$. Az $f = (f_1,\dots,f_m) \in \mathbb{R}^n \to \mathbb{R}^m$ függvényt eszerint kétváltozós vektorfüggvénynek tekintjük, és $\partial_1 f \in \mathbb{R}^{m\times(n-m)}$, $\partial_2 f \in \mathbb{R}^{m\times m}$ a két blokk-Jacobi-mátrix.

### A definíció

Legyen $(a,b) \in D_f$ az $f$ zérushelye: $f(a,b) = 0$. Tegyük fel, hogy van olyan $K(a) \subset \mathbb{R}^{n-m}$ és $K(b) \subset \mathbb{R}^m$ környezet, hogy **minden $x \in K(a)$-hoz egyértelműen létezik olyan $y \in K(b)$, amelyre $f(x,y) = 0$.** A $g(x) := y$ hozzárendeléssel adott

$$g : K(a) \to K(b), \qquad f(x, g(x)) = 0 \quad (x \in K(a))$$

függvény az $f$ által $(a,b)$ körül meghatározott **implicitfüggvény**. Nyilván $g(a) = b$.

Más szóval az

$$f_1(x_1,\dots,x_{n-m}, y_1,\dots,y_m) = 0, \quad \dots, \quad f_m(\dots) = 0$$

egyenletrendszer minden $x$-re egyértelműen megoldható $y$-ra, és a megoldás az $x$ függvénye.

### A két kikötés, amit nem szabad elveszíteni

- **Lokális.** A $K(a)$, $K(b)$ környezeteken kívül semmit sem állítunk; ugyanaz az egyenlet másutt más megoldásokat adhat (a kör egyenlete a felső és az alsó félkört).
- **Egyértelműség $K(b)$-n belül.** Nem az kell, hogy globálisan egy megoldás legyen, csak az, hogy a rögzített $K(b)$-ben egy legyen.

### Geometriai olvasat

$\{f = 0\}$ egy [[concepts/analiii/nivofelulet-es-gradiens|nívóhalmaz]]. Az implicitfüggvény léte azt mondja, hogy ez a halmaz $(a,b)$ közelében **függvénygrafikon**: $(K(a)\times K(b)) \cap \{f = 0\} = \operatorname{graf} g$. Ez a többváltozós elmélet standard fogása — így lehet felületen vizsgálódni egyváltozós eszközökkel, például [[concepts/analiii/felteteles-szelsoertek|feltételes szélsőértéket]] keresni.

## Kapocs

- [[concepts/analiii/implicitfuggveny-tetel]] — mikor létezik, és mennyire sima.
- [[concepts/analiii/nivofelulet-es-gradiens]] — a $\{f = 0\}$ halmaz mint nívóhalmaz.
- [[concepts/analiii/felteteles-szelsoertek]] — a fő alkalmazás.
- [[concepts/analiii/jacobi-matrix]] — a $\partial_1 f$, $\partial_2 f$ blokkok.
