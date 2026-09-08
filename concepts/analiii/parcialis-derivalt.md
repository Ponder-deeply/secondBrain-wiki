---
tags: [concept]
sources: [SimonP-Anal2.pdf]
references: ["Simon Péter: Analízis II., 3.1. szakasz és 3.2. xiii), xiv) megjegyzés"]
derivation: source
updated: 2026-09-07
---

# Parciális derivált

A $h \in \mathbb{R}^n \to \mathbb{R}$ függvény $i$-edik változó szerinti parciális deriváltja a **parciális függvény** — a többi változó rögzítésével kapott egyváltozós függvény — közönséges deriváltja. Ez a Jacobi-mátrix elemeinek kiszámítási eszköze.

## Tartalom

### Parciális függvények

Legyen $h \in \mathbb{R}^n \to \mathbb{R}$, $a = (a_1, \dots, a_n) \in D_h$, és $i \in \{1, \dots, n\}$. Az $i$-edik változó szerinti **értelmezési tartomány-metszet**:

$$D^{(a)}_{h,i} := \{t \in \mathbb{R} : (a_1, \dots, a_{i-1}, t, a_{i+1}, \dots, a_n) \in D_h\}.$$

Ez sosem üres, hiszen $a_i \in D^{(a)}_{h,i}$. Az ezen értelmezett

$$h_{a,i}(t) := h(a_1, \dots, a_{i-1}, t, a_{i+1}, \dots, a_n) \qquad \bigl(t \in D^{(a)}_{h,i}\bigr)$$

egyváltozós valós függvény a $h$ **parciális függvénye**: $h_{a,i} \in \mathbb{R} \to \mathbb{R}$. ($n = 1$ esetén $h_{a,1} = h$.)

Geometriailag: $h$ leszűkítése az $a$-n átmenő, az $i$-edik koordinátatengellyel párhuzamos egyenesre.

### A definíció

A $h$ függvény az $a$-ban az **$i$-edik változó szerint parciálisan deriválható**, ha $h_{a,i} \in D\{a_i\}$, és ekkor

$$\partial_i h(a) := h_{a,i}'(a_i) = \lim_{t \to 0} \frac{h(a_1, \dots, a_{i-1}, a_i + t, a_{i+1}, \dots, a_n) - h(a)}{t}$$

a $h$ **$a$-beli, $i$-edik változó szerinti parciális deriváltja**.

Formálisan tehát: a többi komponenst konstansnak tekintjük, és csak az $i$-edik változótól való függést deriváljuk.

### A parciális deriváltfüggvény

Ha $D_{h,i} := \{a \in D_h : \exists\, \partial_i h(a)\} \ne \emptyset$, akkor a $D_{h,i} \ni x \mapsto \partial_i h(x)$ leképezés a $h$ **$i$-edik változó szerinti parciális deriváltfüggvénye**, jelölése $\partial_i h$.

### Példa

Legyen $n = 2$ és $h(x,y) := x^2 + 2xy^2 + x + 3y + 1$. Az $a = (u,v)$ pontban $D^{(a)}_{h,i} = \mathbb{R}$ ($i = 1,2$), és

$$h_{a,1}(t) = t^2 + 2tv^2 + t + 3v + 1, \qquad h_{a,2}(t) = u^2 + 2ut^2 + u + 3t + 1 .$$

Ezek differenciálhatók, $h_{a,1}'(t) = 2t + 2v^2 + 1$ és $h_{a,2}'(t) = 4ut + 3$, tehát

$$\partial_1 h(a) = 2u + 2v^2 + 1, \qquad \partial_2 h(a) = 4uv + 3 .$$

### Jelölésváltozatok

A $\partial_i h$, illetve $\partial_i h(a)$ mellett használatos a $\partial_{x_i} h$, $\partial_x h$, $\partial_y h$, illetve a klasszikus

$$\frac{\partial h}{\partial x},\ \frac{\partial h}{\partial y},\ \dots$$

írásmód. Például $f(x,y,z) := x^3 + y^2 z + z^3 + xyz$ esetén

$$\partial_x f = 3x^2 + yz, \qquad \partial_y f = 2yz + xz, \qquad \partial_z f = y^2 + 3z^2 + xy .$$

### Visszafelé: függvény a parciális deriváltjaiból

A parciális deriváltak nem tetszőlegesen adhatók meg — a rekonstruálhatóság kompatibilitási feltételt ró rájuk. Keressük azt az $f : \mathbb{R}^2 \to \mathbb{R}$ differenciálható függvényt, amelyre

$$\partial_x f(x,y) = x^2 y, \qquad \partial_y f(x,y) = \frac{x^3}{3} + 1 .$$

Az elsőt $x$ szerint integrálva $f(x,y) = \frac{x^3 y}{3} + \varphi(y)$, a másodikat $y$ szerint integrálva $f(x,y) = \frac{x^3 y}{3} + y + \psi(x)$. A kettő összevetéséből $\psi(x) = \varphi(y) - y$ minden $x, y$-ra, ami csak úgy lehet, ha mindkét oldal ugyanaz a $c$ konstans. Tehát

$$f(x,y) = \frac{x^3 y}{3} + y + c \qquad (c \in \mathbb{R}).$$

Ez a [[concepts/analiii/vektormezo-primitiv-fuggvenye|primitív függvény]] keresésének elemi esete.

## Kapocs

- [[concepts/analiii/gradiens-parcialis-derivaltakbol]] — differenciálhatóságból következik a parciális deriválhatóság, és $\operatorname{grad} h(a) = (\partial_1 h(a), \dots, \partial_n h(a))$.
- [[concepts/analiii/iranymenti-derivalt]] — a parciális derivált az egységvektor-irányú iránymenti derivált speciális esete.
- [[concepts/analiii/differencialhatosag-elegseges-feltetele]] — mikor elég a parciális deriválhatóság a differenciálhatósághoz.
- [[concepts/analiii/differencialhatosagi-fogalmak-hierarchiaja]] — a parciális derivált gyengesége: ellenpéldák.
- [[concepts/analiii/jacobi-matrix]] — a vektorváltozó szerinti (multiindexes) általánosítás.
- [[concepts/analii/derivalt-fogalma]] — az egyváltozós derivált, amelyre a definíció visszavezet.
