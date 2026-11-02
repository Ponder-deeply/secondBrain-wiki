`button-fc-review` | `button-fc-cram`

#flashcards/analiii/eloadas-01-metrikus-normalt-terek


## Mi a metrikus tér definíciója?
?
Az $(M,d)$ pár, ahol $M \neq \emptyset$ és $d : M \times M \to [0,\infty)$ olyan függvény (**metrika**), 
amelyre minden $x,y,z \in M$-re:
- $d(x,y) \geq 0$ és $d(x,y)=0 \iff x=y$; 
- $d(x,y)=d(y,x)$ (szimmetria); 
- $d(x,y)+d(y,z) \geq d(x,z)$ (háromszög-egyenlőtlenség).

---

## Mi a normált tér definíciója?
?
A $(V,\|\cdot\|)$ pár, ahol $V$ valós vagy komplex vektortér, és $\|\cdot\| : V \to [0,\infty)$ olyan függvény (**norma**), amelyre:
- $\|x\|\geq 0$ és $\|x\|=0 \iff x=0$; 
- $\|cx\| = |c|\cdot\|x\|$ (homogenitás); 
- $\|x+y\| \leq \|x\|+\|y\|$ (háromszög-egyenlőtlenség).

---

## Mit nevezünk norma által indukált metrikának?
?
Ha $(V,\|\cdot\|)$ normált tér, akkor a $d(x,y) := \|y-x\|$ képlettel definiált $d$ metrika lesz $V$-n. 
Ezért minden normált vektortér egyben metrikus tér is,
de a megfordítás nem igaz (pl. a diszkrét metrika nem származik normából).

---

## Adjon meg három különböző normát $\mathbb{R}^n$-en!
?
$L^1$: $\|x\|_1 = \sum_{i=1}^n |x_i|$ (taxi-norma). 
$L^2$: $\|x\|_2 = \sqrt{\sum_{i=1}^n x_i^2}$ (euklideszi norma). 
$L^\infty$: $\|x\|_\infty = \max_{1\le i\le n}|x_i|$ (maximumnorma).
---

## Legyen $(X,\|\cdot\|)$ normált tér és $A \subset X$. Mikor mondjuk, hogy az $a \in X$ pont torlódási pontja $A$-nak?
?
Ha bármely $r>0$ esetén a $B(a,r)$ gömb $A$-val vett metszete végtelen sok pontot tartalmaz:
$|B(a,r) \cap A| = \infty$. Ezzel ekvivalens: van $A\setminus\{a\}$-beli, $a$-hoz tartó (akár injektív) sorozat.
---

## Legyen $(X,\|\cdot\|)$ normált tér és $A \subset X$. Mikor mondjuk, hogy az $a \in X$ pont belső pontja $A$-nak?
?
Ha van olyan $r>0$, hogy $B(a,r) \subset A$ azaz $A$ az $a$ egy környezete.

---

## Definiálja a nyílt halmaz fogalmát normált térben!
?
$H$ **nyílt**, ha minden pontja belső pont, azaz minden $a \in H$-hoz van olyan $r>0$, amelyre $B(a,r) \subset H$.
---

## Definiálja a zárt halmaz fogalmát normált térben!
?
$H$ **zárt**, ha a komplementere nyílt. 
Ezzel ekvivalens jellemzések: 
- $\partial H \subset H$; 
- $H = \operatorname{int}H \cup \partial H$; 
- bármely $H$-beli konvergens sorozat limesze is $H$-ban van.
---

## Legyen $X$ lineáris tér, $\|\cdot\|_1, \|\cdot\|_2$ két norma $X$-en. Mikor mondjuk, hogy ez a két norma ekvivalens?
?
Ha van olyan $c,C>0$, hogy minden $x \in X$-re $c\cdot\|x\|_1 \leq \|x\|_2 \leq C\cdot\|x\|_1$. 
Ekvivalens normák ugyanazokat a sorozatokat találják konvergensnek (ugyanazzal a limesszel), és ugyanazt a topológiát (nyílt/zárt/kompakt halmazok rendszerét) indukálják.

---

## Definiálja az euklideszi tér fogalmát!
?
Az $(X,\langle\cdot,\cdot\rangle)$ pár, ahol $X$ lineáris tér $\mathbb{K}$ felett, és 
$\langle\cdot,\cdot\rangle : X^2 \to \mathbb{K}$ **skaláris szorzat**: 
- hermitikus szimmetrikus ($\langle x,y\rangle = \overline{\langle y,x\rangle}$)
- pozitív definit ($\langle x,x\rangle>0$ ha $x\neq0$),
- és az első változóban lineáris (${}\langle \alpha x + \beta z, y \rangle = \alpha \langle x,y \rangle + \beta \langle z,y \rangle{}$).
---
<!--SR:!2026-09-14,0,230-->

## Mit nevez a skaláris szorzat által indukált normának?
?
Az $\|x\| := \sqrt{\langle x,x\rangle}$ képlettel definiált normát. 
Ez valóban norma (a háromszög-egyenlőtlenség a Cauchy–Bunyakovszkij-egyenlőtlenségből következik). 
A $(\mathbb{K}^n,\|\cdot\|_p)$ normák közül **pontosan** $p=2$ esetén származik a norma skaláris szorzatból (paralelogramma-szabály).

---
<!--SR:!2026-09-14,0,230-->

## Mit állít a Cauchy-Schwarz-egyenlőtlenség?
?
Tetszőleges $(X,\langle\cdot,\cdot\rangle)$ euklideszi térben 
$|\langle x,y\rangle| \leq \|x\|\cdot\|y\|$ minden $x,y \in X$-re, ahol $\|x\|=\sqrt{\langle x,x\rangle}$. $\mathbb{R}^n$-ben ez a $\bigl|\sum x_iy_i\bigr| \leq \sqrt{\sum x_i^2}\cdot\sqrt{\sum y_i^2}$ alakot ölti.
---

