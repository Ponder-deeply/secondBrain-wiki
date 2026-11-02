---
tags: [concept]
sources: [SimonP-Anal2.pdf, 04_ea_An3_2022_tavasz.pdf, An_III_Gyak_2022_tavasz.pdf, Analizis-3-gyakorlati-jegyzet-ELTE-IK.pdf, gyakorlat.pdf, RopzhKerdesek.pdf, ElozetesKerdesekMegajanlottVizsgajegyhez1.pdf, 05_gyak_An_III_2022_tavasz.pdf, 06_gyak_An_III_2022_tavasz.pdf]
references: ["Simon Péter: Analízis II., 3.1. szakasz és 3.2. xiii), xiv) megjegyzés"]
derivation: source
kind: definition
element: fire
updated: 2026-10-21
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

<!-- src: 04_ea_An3_2022_tavasz.pdf -->
**Második példa.** Legyen $f(x,y) := xe^{x^2+y^2} - 3y$ és $a=(a_1,a_2)\in\mathbb{R}^2$. A szekciófüggvényeket $x$-ben, illetve $y$-ban rögzítve és egyváltozóban deriválva:

$$\partial_x f(a_1,a_2) = \bigl(xe^{x^2+a_2^2} - 3a_2\bigr)'_{x=a_1} = \bigl(e^{x^2+a_2^2} + x\cdot 2xe^{x^2+a_2^2}\bigr)_{x=a_1} = (1+2a_1^2)\,e^{a_1^2+a_2^2},$$

$$\partial_y f(a_1,a_2) = \bigl(a_1 e^{a_1^2+y^2} - 3y\bigr)'_{y=a_2} = \bigl(a_1\cdot 2y e^{a_1^2+y^2} - 3\bigr)_{y=a_2} = 2a_1 a_2\, e^{a_1^2+a_2^2} - 3.$$

### Szekciófüggvény és a parciális deriváltfüggvény

A lap fenti $h_{a,i}$ jelölése mellett a gyakorlatban a $G_i(t) := f(a_1,\dots,a_{i-1},t,a_{i+1},\dots,a_n)$ **szekciófüggvény** elnevezés is használatos — ugyanaz az objektum, csak $t$-t az $i$-edik koordináta helyén futtatva. A $\partial_i f(a)$ éppen $G_i'(a_i)$.

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

### Feladatok

Módszer: a $k$-adik változó szerint a többit konstansnak tekintjük, és az egyváltozós szabályokkal deriválunk; az origó (vagy két ág találkozási pontja) környezetében a definícióból kell számolni.

- $f=\dfrac{x^2-y^3}{xy}=\dfrac xy-\dfrac{y^2}{x}$ ($x,y>0$): $\partial_xf=\dfrac1y+\dfrac{y^2}{x^2}$, $\partial_yf=-\dfrac{x}{y^2}-\dfrac{2y}{x}$.
- **Visszafelé.** $\partial_xf=x^2y$, $\partial_yf=1+\tfrac{x^3}{3}$: $f=\tfrac{x^3}{3}y+c(y)$, a másodikba helyettesítve $c'(y)=1$, tehát $f(x,y)=\tfrac{x^3y}{3}+y+c$ ($c\in\mathbb{R}$). A jegyzet kiemeli: nem csak „$+c$"; többváltozósnál az integrációs „állandó" a másik változó függvénye, és a végén ki kell esniük a megfelelő tagoknak.
- **Hely szerinti másodrendű.** $f=x^3y+x^2y^2+x+y^2$ az $(1,0)$-ban: $\partial_{xx}f=6xy+2y^2=0$, $\partial_{xy}f=\partial_{yx}f=3x^2+4xy=3$, $\partial_{yy}f=2x^2+2=4$.
- **Szakadási pont a képletben.** $\sqrt{xy}$-szerű ágaknál a $0$-beli parciálist a definícióból számoljuk: $f=\sqrt{|xy|}$-re $\partial_1f(0,0)=\lim\dfrac{f(x,0)-f(0,0)}{x}=0$, és $\partial_2f(0,0)=0$ is. A $\sqrt{3(x-1)^4+2y^2}$ függvénynek az $(1,0)$-ban $\partial_xf$ létezik ($=0$), de $\partial_yf$ nem ($\sim\sqrt2\,|y|$, csúcs).
- **Tipikus hiba:** ha a függvény ágankénti, a $0$ pontbeli deriváltat nem lehet a képlet deriválásával kapni, és a környezetet is értelmezni kell.
- **Parciálisok folytonossága.** $f=(x^2+y^2)\sin\tfrac1{x^2+y^2}$, $f(0,0)=0$: $\partial_1f=2x\sin\tfrac1{x^2+y^2}-\tfrac{2x}{x^2+y^2}\cos\tfrac1{x^2+y^2}$ ($\ne0$ pont), $\partial_1f(0,0)=\lim x\sin\tfrac1{x^2}=0$; az $y=0$ mentén az $x_n=1/\sqrt{2n\pi}$ sorozaton $\partial_1f(x_n,0)=-2\sqrt{2n\pi}\to-\infty$, tehát $\partial_1f\notin C\{(0,0)\}$ (és $\partial_2f$ is). Mégis $f$ differenciálható $0$-ban: [[concepts/analiii/differencialhatosagi-fogalmak-hierarchiaja]].

- **Geometria (5. gyak).** $f\in\mathbb{R}^2\to\mathbb{R}$ grafikonja a $z=f(x,y)$ felület; az $y=a_2$ síkkal ($xz$-síkkal párhuzamos) vett metszetgörbe az $F(t)=f(a_1+t,a_2)$ függvény grafikonja, és $\partial_xf(a)=F'(0)$. A másodrendű jelölés: $\partial_{ij}f(a):=\partial_j(\partial_if)(a)$, vagyis előbb $i$, aztán $j$ szerint deriválunk (gyak 5. lap).
- **Hányados és kimaradó változó (gyak 5. lap megoldása szerint).** A hányadosszabállyal $\partial_xf=\dfrac{x^2+y^3}{x^2y}$ és $\partial_yf=-\dfrac{x^2+2y^3}{xy^2}$ — ez egyezik a fenti $\tfrac1y+\tfrac{y^2}{x^2}$, ill. $-\tfrac x{y^2}-\tfrac{2y}x$ alakkal. Az origóban a második ($\sin$-os) példára a 6. gyakorlat ugyanezt a sorozatot $x_n=y_n=\tfrac1{2\sqrt{n\pi}}$-nel is használja: $\partial_xf(x_n,y_n)=-2\sqrt{n\pi}\to-\infty$ (gyak 6. lap).

## Kapocs

- [[concepts/analiii/gradiens-parcialis-derivaltakbol]] — differenciálhatóságból következik a parciális deriválhatóság, és $\operatorname{grad} h(a) = (\partial_1 h(a), \dots, \partial_n h(a))$.
- [[concepts/analiii/iranymenti-derivalt]] — a parciális derivált az egységvektor-irányú iránymenti derivált speciális esete.
- [[concepts/analiii/differencialhatosag-elegseges-feltetele]] — mikor elég a parciális deriválhatóság a differenciálhatósághoz.
- [[concepts/analiii/differencialhatosagi-fogalmak-hierarchiaja]] — a parciális derivált gyengesége: ellenpéldák.
- [[concepts/analiii/jacobi-matrix]] — a vektorváltozó szerinti (multiindexes) általánosítás.
- [[concepts/analii/derivalt-fogalma]] — az egyváltozós derivált, amelyre a definíció visszavezet.
- [[concepts/analiii/fuggvenygrafikon-erintosikja]] — a parciális deriváltak mint az érintősík normálvektorának koordinátái.
- [[concepts/analiii/vizsgakerdesek-es-bizonyitando-tetelek]] — a témához tartozó megajánlott vizsgajegy- és röpdolgozat-kérdések.
