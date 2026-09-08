---
tags: [concept]
sources: [SimonP-Anal2.pdf]
references: ["Simon Péter: Analízis II., 3.1. szakasz és 3.2. v), vii) megjegyzés"]
derivation: source
updated: 2026-09-07
---

# Jacobi-mátrix, gradiens, deriváltvektor

Az $\mathcal{L}(\mathbb{R}^n, \mathbb{R}^m) \approx \mathbb{R}^{m\times n}$ azonosítás miatt az $f'(a)$ derivált mátrixként írható: ez a **Jacobi-mátrix**. Az $m = 1$, illetve $n = 1$ határesetekben a mátrix vektorrá fajul — ezek a gradiens és a deriváltvektor.

## Tartalom

### A deriváltmátrix

Ha $f \in D\{a\}$, akkor a [[concepts/analiii/frechet-derivalt|derivált]] $L := f'(a)$ egyértelműen létező korlátos lineáris leképezés, amelyhez pontosan egy $A \in \mathbb{R}^{m\times n}$ mátrix tartozik $L(x) = Ax$ ($x \in \mathbb{R}^n$) módon. Ezt a mátrixot magát is $f'(a)$-val jelöljük, és **deriváltmátrixnak** vagy **Jacobi-mátrixnak** nevezzük. Így

$$f(a+h) - f(a) = f'(a)h + \eta(h)\cdot\|h\| \qquad (h \in \mathbb{R}^n,\ a+h \in D_f),$$

ahol $\eta(h) \to 0$ ($\|h\| \to 0$), és $\|\cdot\|$ bármelyik $\|\cdot\|_p$ norma lehet.

### $m = 1$: a gradiens

Ha $f \in \mathbb{R}^n \to \mathbb{R}$, akkor $f'(a) \in \mathbb{R}^{1\times n} \approx \mathbb{R}^n$, azaz a Jacobi-mátrix egy $\mathbb{R}^n$-beli vektornak tekinthető — ez az $f$ **$a$-beli gradiense**, $\operatorname{grad} f(a)$. A mátrix-vektor-szorzat ilyenkor közönséges skaláris szorzat:

$$f(a+h) - f(a) = \langle \operatorname{grad} f(a), h\rangle + \eta(h)\cdot\|h\| .$$

Ha $D := \{a \in D_f : f \in D\{a\}\} \ne \emptyset$, akkor a $D \ni x \mapsto \operatorname{grad} f(x)$ leképezés az $f$ **gradiense** mint függvény: $\operatorname{grad} f \in \mathbb{R}^n \to \mathbb{R}^n$.

Ha ráadásul $n = 1$ is, akkor $\operatorname{grad} f(a) = f'(a) \in \mathbb{R}$ — visszakapjuk a klasszikus egyváltozós deriváltat.

### $n = 1$: a deriváltvektor

Ha $f \in \mathbb{R} \to \mathbb{R}^m$, akkor $f'(a) \in \mathbb{R}^{m\times 1} \approx \mathbb{R}^m$, az $f$ **$a$-beli deriváltvektora**, és

$$f(a+h) - f(a) = f'(a)h + \eta(h)\cdot|h| \qquad (h \in \mathbb{R}).$$

A deriváltfüggvény ekkor $f' \in \mathbb{R} \to \mathbb{R}^m$.

### A deriváltfüggvény általában

Tetszőleges $n, m$ esetén, ha $D := \{a \in D_f : f \in D\{a\}\} \ne \emptyset$, akkor a $D \ni x \mapsto f'(x)$ leképezés az $f$ **deriváltfüggvénye**, és az $\mathcal{L}(\mathbb{R}^n, \mathbb{R}^m) \approx \mathbb{R}^{m\times n}$ azonosítással

$$f' \in \mathbb{R}^n \to \mathbb{R}^{m\times n}.$$

Figyelemre méltó, hogy $f'$ **akkor és csak akkor** ugyanolyan típusú objektum ($\mathbb{R}^n \to \mathbb{R}^s$ alakú vektorfüggvény), mint maga $f$, ha $n = 1$ vagy $m = 1$. Egyébként a derivált egy mátrixértékű függvény, és a magasabb rendű deriváltak tárgyalása külön apparátust kíván.

### Sorvektoros írásmód

Egy $A \in \mathbb{R}^{m\times n}$ mátrixot sorvektoraival particionálva, $A_i := (a_{i1}, \dots, a_{in}) \in \mathbb{R}^n$ ($i = 1, \dots, m$),

$$A = \begin{pmatrix} A_1 \\ A_2 \\ \vdots \\ A_m\end{pmatrix}, \qquad Ax = \bigl(\langle A_1, x\rangle, \dots, \langle A_m, x\rangle\bigr) \quad (x \in \mathbb{R}^n).$$

Ez az az alak, amelyben a Jacobi-mátrix sorai a koordinátafüggvények gradienseiként azonosíthatók.

### Blokkfelbontás: vektorváltozó szerinti parciális derivált

A parciális derivált fogalma vektorváltozóra is kiterjed. Legyen $f \in \mathbb{R}^n \to \mathbb{R}^m$, $a \in D_f$, és $i = (i_1, \dots, i_s)$ szigorúan növő multiindex, $s \in \{1, \dots, n-1\}$; jelölje $j = (j_1, \dots, j_{n-s})$ a komplementer indexeket. Az $x \in \mathbb{R}^n$ vektor ennek megfelelő felbontása $x = (\xi_1, \xi_2)$, és $a = (u_1, u_2)$. A

$$f_{a,i}(\xi) := f(\xi, u_2) \qquad \bigl(\xi \in D^{(a)}_{f,i} := \{\xi \in \mathbb{R}^s : (\xi, u_2) \in D_f\}\bigr)$$

függvénnyel azt mondjuk, hogy $f$ az $a$-ban parciálisan deriválható az $i$ multiindex meghatározta **vektorváltozó** szerint, ha $f_{a,i} \in D\{u_1\}$, és ekkor $\partial_i f(a) := f_{a,i}'(u_1) \in \mathbb{R}^{m\times s}$.

Ha $f \in D\{a\}$, ez a **parciális deriváltmátrix** éppen az $f'(a)$ Jacobi-mátrix $i_1$-edik, …, $i_s$-edik **oszlopaiból** álló részmátrix. Az $\mathbb{R}^n = \mathbb{R}^s \times \mathbb{R}^{n-s}$ felbontásra utaló szokásos jelöléssel

$$f'(a) = [\,\partial_1 f(a) \ \ \partial_2 f(a)\,].$$

Ez a particionálás az implicitfüggvény-tétel szokásos írásmódjának alapja. Az $s = 1$ eset a közönséges [[concepts/analiii/parcialis-derivalt|parciális derivált]].

## Kapocs

- [[concepts/analiii/frechet-derivalt]] — a derivált definíciója és egyértelműsége; ez a lap annak mátrixalakja.
- [[concepts/analiii/koordinatafuggvenyek-differencialhatosaga]] — a Jacobi-mátrix sorai a koordinátafüggvények gradiensei.
- [[concepts/analiii/gradiens-parcialis-derivaltakbol]] — a mátrix elemei a $\partial_k f_i(a)$ parciális deriváltak.
- [[concepts/analiii/parcialis-derivalt]] — a mátrixelemek kiszámításának eszköze.
- [[concepts/analiii/rotaciomentes-vektormezo]] — a Jacobi-mátrix szimmetriája mint a primitív függvény szükséges feltétele.
- [[concepts/analiii/mertek-es-integraltranszformacio]] — a Jacobi-determináns szerepe a helyettesítéses integrálásban.
