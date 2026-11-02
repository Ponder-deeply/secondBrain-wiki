---
tags: [concept]
sources: [SimonP-Anal2.pdf, 04_ea_An3_2022_tavasz.pdf, An_III_Gyak_2022_tavasz.pdf, Analizis-3-gyakorlati-jegyzet-ELTE-IK.pdf, gyakorlat.pdf, RopzhKerdesek.pdf, ElozetesKerdesekMegajanlottVizsgajegyhez1.pdf, 05_gyak_An_III_2022_tavasz.pdf, 06_gyak_An_III_2022_tavasz.pdf]
references: ["Simon Péter: Analízis II., 3.2. vi) és viii) megjegyzés"]
derivation: source
kind: definition
element: fire
updated: 2026-10-21
---

# Iránymenti derivált

A függvény leszűkítése az $a$ ponton átmenő, $e$ irányvektorú egyenesre egyváltozós függvény; ennek nulla helyen vett deriváltja az **iránymenti derivált**. A parciális derivált ennek az az esete, amikor $e$ egységvektor a koordinátatengely irányában.

## Tartalom

### A definíció

Legyen $1 \le n \in \mathbb{N}$, $h \in \mathbb{R}^n \to \mathbb{R}$, $a \in D_h$, és $e \in \mathbb{R}^n$, $\|e\| = 1$ egy **irány** ($\|\cdot\|$ a $\|\cdot\|_p$ normák valamelyike). A

$$D^{(a)}_{h,e} := \{t \in \mathbb{R} : a + te \in D_h\}, \qquad h_e(t) := h(a + te) \quad \bigl(t \in D^{(a)}_{h,e}\bigr)$$

függvény geometriailag a $h$ leszűkítése az $a$-n átmenő, $e$ irányú egyenesre. Mindig $0 \in D^{(a)}_{h,e}$, és $a \in \operatorname{int} D_h$ esetén $0 \in \operatorname{int} D^{(a)}_{h,e}$.

Ha $h_e \in D\{0\}$, akkor a

$$\partial_e h(a) := h_e'(0)$$

szám a $h$ **$a$-beli, $e$ irányú iránymenti deriváltja**.

### A parciális derivált mint speciális eset

Ha $e := (0, \dots, 0, 1, 0, \dots, 0)$ az $i$-edik egységvektor, akkor $h_e(t) = h_{a,i}(a_i + t)$, tehát $h_e \in D\{0\}$ ekvivalens a $h_{a,i} \in D\{a_i\}$ feltétellel, és

$$\partial_e h(a) = h_e'(0) = h_{a,i}'(a_i) = \partial_i h(a).$$

A [[concepts/analiii/parcialis-derivalt|parciális derivált]] tehát pontosan a koordinátatengely-irányú iránymenti derivált.

### Differenciálhatóságból: $\partial_e f(a) = f'(a)e$

**Állítás.** Ha $f \in \mathbb{R}^n \to \mathbb{R}^m$ és $f \in D\{a\}$ valamely $a \in \operatorname{int} D_f$ pontban, akkor tetszőleges $e \in \mathbb{R}^n$, $\|e\| = 1$ irányra az $f_e(t) := f(a + te)$ függvény differenciálható a $0$-ban, és

$$\partial_e f(a) = f_e'(0) = f'(a)\,e .$$

Speciálisan $m = 1$ esetén

$$\partial_e f(a) = \langle \operatorname{grad} f(a), e\rangle .$$

*Bizonyítás.* Az $f \in D\{a\}$ feltétel miatt alkalmas $\eta \to 0$ függvénnyel

$$f(a+x) - f(a) = f'(a)x + \eta(x)\cdot\|x\| .$$

Az $x := te$ helyettesítéssel, $\|te\| = |t|\cdot\|e\| = |t|$ miatt

$$f_e(t) - f_e(0) = f'(a)(te) + \eta(te)\cdot|t| = \bigl(f'(a)e\bigr)\cdot t + \varphi(t)\cdot|t|,$$

ahol $\varphi(t) := \eta(te) \to 0$ ($|t| \to 0$). Ez pontosan az $f_e \in D\{0\}$ egyváltozós differenciálhatóság kritériuma, $f_e'(0) = f'(a)e$. $\square$

A formula tartalma: **a differenciálhatóság egyetlen lineáris leképezésbe kódolja az összes irányban vett viselkedést.** Az összes iránymenti derivált előáll a deriváltmátrixból, egy mátrix-vektor-szorzással.

### A megfordítás hamis

Az összes iránymenti derivált létezése önmagában nem elég a differenciálhatósághoz, sőt a folytonossághoz sem. A klasszikus ellenpélda

$$f(x,y) := \begin{cases} 1 & (y = x^2 \ne 0) \\ 0 & \text{egyébként} \end{cases}$$

függvényre minden $e$ irányban $f_e \equiv 0$ az origó egy környezetében (az egyenes csak a $0$-ban metszi a parabolát), tehát $\partial_e f(0,0) = 0$ minden irányban létezik, de $f(t, t^2) \to 1 \ne 0 = f(0,0)$, azaz $f$ nem folytonos, így nem is differenciálható a $(0,0)$-ban. A parabola „megkerüli" az összes egyenest — lásd [[concepts/analiii/differencialhatosagi-fogalmak-hierarchiaja]].

<!-- src: 04_ea_An3_2022_tavasz.pdf -->
### Az irány mint 2-es normában vett egységvektor

A definícióban az irány $v\in\mathbb{R}^n$-re csak azt kötjük ki, hogy $\|v\|_2=1$ — kifejezetten a **2-es (euklideszi) normában**, mert csak ezzel lesz a $\langle f'(a),v\rangle$ skaláris szorzat alakja értelmes és az $\|v\|_2=1$ normálás garantálja, hogy $\partial_v f(a)$ valóban a "sebesség" a $v$ irányban, nem annak skalárszorosa.

### Vektorértékű és $m > 1$ eset

Az iránymenti (és a parciális) deriválhatóság fogalma szó szerint ugyanígy értelmezhető $f \in \mathbb{R}^n \to \mathbb{R}^m$ függvényekre $m > 1$ mellett is: ekkor $\partial_e f(a) \in \mathbb{R}^m$.

### Feladatok

Módszer: ha $f$ totálisan deriválható, $\partial_ef(a)=\langle f'(a),e\rangle$ ($\|e\|_2=1$). Ha az irányt a $u$ vektor adja, normáljuk: $e=u/\|u\|_2$ (más normánál az osztás is annak szerint történik).

- $f=x^2-xy+y^2$, $a=(1,1)$, $e=(\cos\alpha,\sin\alpha)$. Definíció szerint $F(t)=f(a+te)$, $\partial_ef(a)=F'(0)$. A gradiens $(2x-y,\,2y-x)=(1,1)$, ezért $\partial_ef(1,1)=\cos\alpha+\sin\alpha$. $60^\circ$-nál ($e=(\tfrac12,\tfrac{\sqrt3}2)$) $\tfrac{1+\sqrt3}{2}$. A maximum $\alpha=\tfrac\pi4$-nél $\sqrt2$ (az $e$ a gradiens irányába mutat), a minimum $\alpha=\tfrac{5\pi}4$-nél $-\sqrt2$.
- $f=y^3e^{-2x-1}$, $P(-\tfrac12,1)$, $u=(1,2)$: $\operatorname{grad}f(P)=(-2,3)$, $e=\tfrac1{\sqrt5}(1,2)$, $\partial_ef=\tfrac4{\sqrt5}$.
- $f=e^xy+x\cos y$, $a=(0,1)$, $u=(1,-\sqrt3)$: $\|u\|=2$, $e=(\tfrac12,-\tfrac{\sqrt3}2)$, $\operatorname{grad}f(0,1)=(1+\cos 1,\,1)$, így $\partial_ef=\dfrac{1-\sqrt3+\cos1}{2}$ (a jegyzet $\tfrac{1-\sqrt3-\cos 1}{2}$-t ad, de $\tfrac12(1+\cos1)-\tfrac{\sqrt3}2$ a helyes).
- $f=xe^{yx}-xy$, $(1,1)$, $v=(3,4)$: $\operatorname{grad}f=(2e-1,\,e-1)$, $\partial_ef=\tfrac{10e-7}{5}$.
- $f=x^2y+x\sqrt{1+z}$, $(1,2,3)$, $v=2i+j-2k$: $\operatorname{grad}f=(6,1,\tfrac14)$, $e=\tfrac13(2,1,-2)$, $\partial_ef=\tfrac{25}6$.
- **Legnagyobb meredekségű irány.** $\max_e\partial_ef(a)=\|\operatorname{grad}f(a)\|$, az $e=\operatorname{grad}f/\|\operatorname{grad}f\|$ irányban (Cauchy–Schwarz). Példa: $f=e^{y-2x}\sin\pi xy$ az $(1,2)$-ben: $\operatorname{grad}f=(2\pi,\pi)$, $e=\tfrac1{\sqrt5}(2,1)$, a maximum $\pi\sqrt5$.
- **Minden irányban deriválható, mégsem differenciálható.** $f=\dfrac{x^3}{x^2+y^2}$, $f(0,0)=0$: $\partial_ef(0,0)=\cos^3\alpha$ nem lineáris $e$-ben; $f=\sqrt[3]{x^3+y^3}$: $\partial_ef(0,0)=\sqrt[3]{\cos^3\alpha+\sin^3\alpha}$, szintén nem lineáris. Egy másik példa a $0$ pontban nem is folytonos függvényre: $f=1$, ha $x>0$ és $y=x^2$, különben $0$ — minden irányban deriválható ($0$), de az $y=x^2$ parabola mentén $1$, tehát nem folytonos, ezért nem differenciálható. Hasonló a $\chi_{A\cup B}$ jellemző függvény az $A$ (két érintő kör) és a $B$ (az $x$-tengely) uniójára. Lásd [[concepts/analiii/differencialhatosagi-fogalmak-hierarchiaja]].

- **Elégséges feltétel (gyak 5. lap tétele).** Ha $f\in\mathbb{R}^2\to\mathbb{R}$, $a\in\operatorname{int}D_f$, a parciálisok léteznek egy $K(a)$-ban és folytonosak $a$-ban, akkor minden $v=(v_1,v_2)$ egységvektor irányában létezik az iránymenti derivált és $\partial_vf(a)=\partial_1f(a)v_1+\partial_2f(a)v_2$. A definíciós számolás $F_v(t)=f(1+t\cos\alpha,1+t\sin\alpha)=(1-\sin\alpha\cos\alpha)t^2+(\sin\alpha+\cos\alpha)t+1$ polinom, tehát $F_v'(0)=\sin\alpha+\cos\alpha$; a tétellel ugyanez adódik. A maximum: $\sin\alpha+\cos\alpha=\sqrt2\sin(\alpha+\tfrac\pi4)$, azaz $\alpha=\tfrac\pi4$ (gyak 5. lap 4. feladat megoldása).
- **Minden irányban deriválható, folytonos, de nem differenciálható (gyak 6. lap 1. feladat).** $f=\dfrac{xy^2}{x^2+y^2}$, $f(0,0)=0$. Folytonos: $|f|\le\dfrac{|x|(x^2+y^2)}{x^2+y^2}=|x|\le\|(x,y)\|_2$. Irányban: $F_v(t)=f(t\cos\alpha,t\sin\alpha)=t\cos\alpha\sin^2\alpha$, így $\partial_vf(0,0)=\cos\alpha\sin^2\alpha$. Ha $f\in D\{(0,0)\}$ lenne, $f'(0,0)=(\partial_1f,\partial_2f)=(0,0)$ ($\alpha=0$, ill. $\tfrac\pi2$) és a hányados $\dfrac{|h_1|h_2^2}{(h_1^2+h_2^2)^{3/2}}\to0$ kellene; az $x_n=y_n=\tfrac1n$ sorozaton értéke $\tfrac1{\sqrt8}\neq0$. Tehát $f\notin D\{(0,0)\}$ (a $\cos\alpha\sin^2\alpha$ sem lineáris $\alpha$-ban).

## Kapocs

- [[concepts/analiii/parcialis-derivalt]] — a koordinátatengely-irányú speciális eset.
- [[concepts/analiii/gradiens-parcialis-derivaltakbol]] — a gradiens, amellyel az iránymenti derivált skaláris szorzatként áll elő.
- [[concepts/analiii/jacobi-matrix]] — az $f'(a)e$ szorzat objektuma.
- [[concepts/analiii/differencialhatosagi-fogalmak-hierarchiaja]] — az iránymenti deriválhatóság helye az implikációláncban.
- [[concepts/analiii/vizsgakerdesek-es-bizonyitando-tetelek]] — a témához tartozó megajánlott vizsgajegy- és röpdolgozat-kérdések.
