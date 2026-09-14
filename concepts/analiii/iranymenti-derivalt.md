---
tags: [concept]
sources: [SimonP-Anal2.pdf, 04_ea_An3_2022_tavasz.pdf]
references: ["Simon Péter: Analízis II., 3.2. vi) és viii) megjegyzés"]
derivation: source
updated: 2026-09-14
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

## Kapocs

- [[concepts/analiii/parcialis-derivalt]] — a koordinátatengely-irányú speciális eset.
- [[concepts/analiii/gradiens-parcialis-derivaltakbol]] — a gradiens, amellyel az iránymenti derivált skaláris szorzatként áll elő.
- [[concepts/analiii/jacobi-matrix]] — az $f'(a)e$ szorzat objektuma.
- [[concepts/analiii/differencialhatosagi-fogalmak-hierarchiaja]] — az iránymenti deriválhatóság helye az implikációláncban.
