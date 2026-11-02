`button-fc-review` | `button-fc-cram`

#flashcards/analiii/eloadas-05-derivalt-lancszabaly

## Adja meg a gradiens vektor fogalmát!
?
Ha $h \in \mathbb{R}^n \to \mathbb{R}$ és $h \in D\{a\}$, akkor a Jacobi-mátrix (deriváltmátrix) $\mathbb{R}^n$-beli vektornak tekinthető: $\operatorname{grad} h(a) := f'(a)$. Ha $h$ differenciálható $a$-ban, akkor minden $i$-re parciálisan is deriválható, és $\operatorname{grad} h(a) = \bigl(\partial_1 h(a), \dots, \partial_n h(a)\bigr)$.
---

## Legyen $f \in \mathbb{R}^n \to \mathbb{R}$ és $f \in D\{a\}$. Milyen $v \in \mathbb{R}^n$ irányban lesz a $\partial_v f(a)$ iránymenti derivált értéke a legnagyobb?
?
A $\operatorname{grad} f(a)$ irányában (ha $\operatorname{grad} f(a) \neq 0$), azaz $v = \dfrac{\operatorname{grad} f(a)}{\|\operatorname{grad} f(a)\|}$ mellett. Ekkor $\partial_v f(a) = \langle\operatorname{grad} f(a), v\rangle$ a Cauchy–Schwarz-egyenlőtlenség szerint maximális, és az értéke $\|\operatorname{grad} f(a)\|$.
---

## Legyen $f \in \mathbb{R}^n \to \mathbb{R}$ és $f \in D\{a\}$. Milyen $v \in \mathbb{R}^n$ irányban lesz a $\partial_v f(a)$ iránymenti derivált értéke nulla?
?
Azokban a $v$ irányokban, amelyek merőlegesek a gradiensre: $\partial_v f(a) = \langle\operatorname{grad} f(a), v\rangle = 0 \iff v \perp \operatorname{grad} f(a)$. Ez pontosan a szintfelület érintőhipersíkjának iránya.
---

## Mi a kapcsolat $\mathbb{R}^n \to \mathbb{R}^m$ típusú függvények esetén a differenciálhatóság és a folytonosság között?
?
Ha $f \in D\{a\}$, akkor $f$ folytonos is $a$-ban. Ez közvetlenül adódik a definícióból: $f(a+h)-f(a) = L(h)+\eta(h)\|h\| \to 0$, ha $h\to0$ ($L$ korlátos lineáris, tehát folytonos, és $\eta(h)\|h\|\to0$). A megfordítás nem igaz — folytonos, de nem differenciálható függvényre az $|x|$ az egyváltozós, ill. $\|x\|$ a többváltozós ellenpélda.
---

## Mi a kapcsolat $\mathbb{R}^n \to \mathbb{R}^m$ típusú függvények differenciálhatósága és a koordinátafüggvények differenciálhatósága között?
?
$f=(f_1,\dots,f_m)$ akkor és csak akkor differenciálható $a$-ban, ha minden $f_i$ koordinátafüggvény differenciálható $a$-ban, és ekkor $f'(a)$ sorai a $\operatorname{grad}f_i(a)$ vektorok: $f'(a) = (\operatorname{grad}f_1(a),\dots,\operatorname{grad}f_m(a))^\top$.
---

## Milyen feltételek mellett következik a parciális differenciálhatóságból a totális differenciálhatóság?
?
Ha valamely $i$ indexre $a$ egy környezetében léteznek a $\partial_j h$ ($j\neq i$) parciális deriváltfüggvények és ezek folytonosak $a$-ban, továbbá létezik a $\partial_i h(a)$ parciális derivált (ő maga elég, ha csak pontbeli), akkor $h \in D\{a\}$. A feltétel aszimmetrikus: egyetlen kitüntetett változónál elég a pontbeli parciális deriválhatóság, a többinél kell a környezetbeli létezés + pontbeli folytonosság.
---

## Mit mond az összetett függvény deriválási szabálya (láncszabály) többváltozós függvények esetén?
?
Ha $g\in\mathbb{R}^n\to\mathbb{R}^m$ differenciálható $a$-ban és $f\in\mathbb{R}^m\to\mathbb{R}^s$ differenciálható $g(a)$-ban, akkor $f\circ g$ differenciálható $a$-ban, és $(f\circ g)'(a) = f'(g(a))\cdot g'(a)$ — a két Jacobi-mátrix szorzata (a sorrend kötött, mert a mátrixszorzás nem kommutatív).
---
