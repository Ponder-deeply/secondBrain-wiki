`button-fc-review` | `button-fc-cram`

#flashcards/analiii/eloadas-02-konvergencia-teljesseg

## Definiálja a konvergens sorozat fogalmát normált térben!
?
Az $(a_n)$ sorozat **konvergens** és limesze $b$,
ha
 - $\forall \varepsilon>0\ \exists n_0\ \forall n>n_0:\ \|a_n-b\|<\varepsilon$,
 - azaz $a_n \in B(b,\varepsilon)$ véges sok kivétellel.
 - Ezzel ekvivalens: $\|a_n-b\|\to 0$ mint számsorozat. A limesz egyértelmű.
---
<!--SR:!2026-09-27,5,230-->

## Legyenek $\|\cdot\|_1, \|\cdot\|_2$ ekvivalens normák az $X$ lineáris téren. Mit állíthatunk a két norma által meghatározott konvergens sorozatok halmazáról?
?
Ugyanazok a sorozatok konvergensek mindkét normában, és ugyanaz a limeszük — az ekvivalencia $c\|x\|_1\le\|x\|_2\le C\|x\|_1$ becsléséből $\|a_n-b\|_1\to0 \iff \|a_n-b\|_2\to0$ közvetlenül adódik.
---
<!--SR:!2026-09-23,3,250-->

## Milyen kapcsolat van egy $\mathbb{R}^n$-beli sorozat konvergenciája és a koordinátasorozatainak konvergenciája között?
?
Ekvivalensek: $\mathbf{a}_n \to \mathbf{b}$ $\mathbb{R}^n$-ben $\iff$ minden $1\le i\le n$-re a koordinátasorozat konvergál, $a_{n,i}\to b_i$. A vektorsorozat konvergenciája tehát $n$ darab számsorozat konvergenciájára esik szét.
---
<!--SR:!2026-09-24,4,270-->

## Normált terekben milyen kapcsolat áll fenn a konvergens és a Cauchy-sorozatok között?
?
Minden konvergens sorozat Cauchy-tulajdonságú. Megfordítva ez általában nem igaz, de ha egy Cauchy-sorozatnak van konvergens **részsorozata**, akkor maga a sorozat is konvergens, ugyanoda.
---
<!--SR:!2026-09-24,4,270-->

## Mikor mondjuk, hogy egy normált tér teljes?
?
Ha érvényes benne a Cauchy-kritérium: minden Cauchy-sorozat konvergens.
A teljes normált vektorteret **Banach-térnek** nevezzük.
---
<!--SR:!2026-09-23,3,250-->

## Adjon példát nem teljes normált térre!
?
$\bigl(C[-1,1], \|\cdot\|_1\bigr)$: az $f_n(x) =$
- $-1$ ($x<-1/n$), 
- $nx$ ($-1/n\le x\le 1/n$), 
- $1$ ($x>1/n$) sorozat 
Cauchy az $L^1$-normában, de nincs folytonos limesze (a határ az előjelfüggvény lenne, ami nem folytonos).
---
<!--SR:!2026-09-21,1,210-->

## Adjon meg olyan normát a $C[0,1]$ lineáris téren, amellyel az Banach-tér lesz!
?
A maximumnorma $\|f\|_\infty = \max_{x\in[0,1]}|f(x)|$. $\bigl(C[a,b],\|\cdot\|_\infty\bigr)$ teljes:
- ha $(f_n)$ Cauchy, akkor pontonként konvergál egy $g$ függvényhez,
- és a Cauchy-becslésből $\|f_n-g\|_\infty\to0$ (egyenletes konvergencia),
- így $g$ folytonos, tehát $g \in C[a,b]$.
---
<!--SR:!2026-09-24,2,230-->

## Mit tudunk az $\mathbb{R}^n$-beli normák ekvivalenciájáról?
?
$\mathbb{R}^n$-en (véges dimenzióban) **minden** norma ekvivalens egymással. Ezért a konvergencia, a topológia (nyílt/zárt halmazok) és a kompaktság $\mathbb{R}^n$-ben normafüggetlen — szabadon dolgozhatunk $\|\cdot\|_1$, $\|\cdot\|_2$ vagy $\|\cdot\|_\infty$-nel.
---
<!--SR:!2026-09-24,4,270-->

## Mit állít a Bolzano-Weierstrass-féle kiválasztási tétel $\mathbb{R}^n$ euklideszi térre?
?
**Minden korlátos $\mathbb{R}^n$-beli sorozatnak van konvergens részsorozata**.
(A koordinátánkénti Bolzano–Weierstrass-tételből adódik:
- minden koordinátasorozat korlátos,
- így egymás után kiválasztva mind az $n$ koordinátára konvergens közös indexsorozat kapható.)
---
<!--SR:!2026-09-24,2,210-->
