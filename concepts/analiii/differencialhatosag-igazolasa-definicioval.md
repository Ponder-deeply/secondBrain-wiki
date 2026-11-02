---
tags: [concept]
sources: [Analizis-3-gyakorlati-jegyzet-ELTE-IK.pdf, An_III_Gyak_2022_tavasz.pdf, gyakorlat.pdf]
derivation: source
kind: procedure
element: fire
updated: 2026-10-22
---

# Differenciálhatóság igazolása definícióval és Jacobi-mátrixszal

Számolási recept: egy $f:\mathbb{R}^n\to\mathbb{R}^m$ függvény totális deriválhatóságát egy $a$ pontban a definícióból (lineáris rész leolvasása és a maradék becslése), majd ellenőrzésképpen a Jacobi-mátrixból és az elégséges feltételből vezetjük le.

## Tartalom

### A módszer

1. Számold ki $f(a+h)-f(a)$-t, és bontsd **lineáris tagokra** és **maradékra** ($h$ legalább másodfokú polinomja).
2. A lineáris tagok együtthatóiból olvasd le az $A$ mátrixot: $L(h)=Ah$.
3. Becsüld a maradékot: igazold, hogy $\dfrac{\|f(a+h)-f(a)-Ah\|}{\|h\|}\to0$. Véges dimenzióban a norma szabadon választható ([[concepts/analiii/ekvivalens-normak]]); a $\|\cdot\|_\infty$ rendszerint kényelmes, mert $|h_i|\le\|h\|_\infty$.
4. Ellenőrzés: $f'(a)$ a [[concepts/analiii/jacobi-matrix|Jacobi-mátrix]] $a$-beli értéke; ha a parciális deriváltak folytonosak, az [[concepts/analiii/differencialhatosag-elegseges-feltetele|elégséges feltétel]] már önmagában $f\in D\{a\}$-t ad.

### Kidolgozott példa

$f(x,y)=2x^2+3xy-y^2$, $a=(1,2)$, $h=(x,y)$ (a növekmény):
$$f(a+h)-f(a)=\underbrace{10x-y}_{\text{lineáris}}+\underbrace{2x^2+3xy-y^2}_{\text{maradék}}.$$
Tehát $A=\begin{pmatrix}10&-1\end{pmatrix}$, és $\dfrac{|2x^2+3xy-y^2|}{\|h\|_\infty}\le\dfrac{6\|h\|_\infty^2}{\|h\|_\infty}\to0$. Ellenőrzés: $\partial_1f=4x+3y$, $\partial_2f=3x-2y$, $f'(1,2)=(10,-1)$ — polinomok, így mindenhol folytonosak, $f\in D(\mathbb{R}^2)$.

Vektorértékű eset ($\mathbb{R}^2\to\mathbb{R}^3$): sorokként számolunk, minden koordinátafüggvény külön, az eredmény egy $3\times2$-es mátrix ([[concepts/analiii/koordinatafuggvenyek-differencialhatosaga]]).

### Az iránymenti derivált kiszámítása

Differenciálható $f$-re $\partial_ef(a)=\langle f'(a),e\rangle$, ahol $e$ **egységvektor** az adott normában (alapértelmezés: 2-es norma, tehát $e=u/\|u\|_2$). Példa: $f=x^2-xy+y^2$, $a=(1,1)$, $e=(\cos\alpha,\sin\alpha)$: $\partial_ef(1,1)=\cos\alpha+\sin\alpha$, amelynek maximuma $\sqrt2$ a gradiens $(1,1)$ irányában, minimuma az ellenkezőjében. Lásd [[concepts/analiii/gradiens-parcialis-derivaltakbol]].

### Az érintősík

Az $f$ differenciálható függvény grafikonjának érintősíkja az első Taylor-polinom: $z=f(a)+\partial_1f(a)(x-a_1)+\partial_2f(a)(y-a_2)$. Példa: $f=xy+y^2\cos(x-1)$, $a=(1,3)$: $f(a)=10$, $\partial_1f=3$, $\partial_2f=6$, tehát $3x+6y-z=11$ ([[concepts/analiii/fuggvenygrafikon-erintosikja]]).

### Visszafelé: parciálisokból függvény

Ha $\partial_1f=x^2y$ és $\partial_2f=1+x^3/3$, akkor $\partial_1$-ből $f=yx^3/3+c(y)$, majd $\partial_2$-ből $c'(y)=1$, tehát $f=\frac{yx^3}{3}+y+c$. Az integrálási "konstans" egy másik változótól függő függvény ([[concepts/analiii/konzervativ-vektormezo]], [[concepts/analiii/vektormezo-primitiv-fuggvenye]]).

## Kapocs

- [[concepts/analiii/frechet-derivalt]] — a definíció.
- [[concepts/analiii/jacobi-matrix]] — a derivált mátrixa.
- [[concepts/analiii/differencialhatosag-elegseges-feltetele]] — folytonos parciálisokból differenciálhatóság.
- [[concepts/analiii/iranymenti-derivalt]] — az iránymenti derivált és a gradiens.
- [[concepts/analiii/differencialhatosag-ellenpeldai]] — amikor a módszer nem működik, mert a függvény nem differenciálható.
