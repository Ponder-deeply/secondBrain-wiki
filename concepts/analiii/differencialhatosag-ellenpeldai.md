---
tags: [concept]
sources: [Analizis-3-gyakorlati-jegyzet-ELTE-IK.pdf, An_III_Gyak_2022_tavasz.pdf, gyakorlat.pdf]
derivation: source
kind: pitfall
element: water
updated: 2026-10-22
---

# A differenciálhatóság klasszikus ellenpéldái

Gyűjtemény a leggyakoribb függvényekről, amelyek megmutatják, hogy a [[concepts/analiii/differencialhatosagi-fogalmak-hierarchiaja|hierarchia]] nyilai nem fordíthatók meg. Vizsgán gyakran ezek az "adjon példát" kérdések.

## Tartalom

### Folytonos, parciálisan deriválható, de nem differenciálható: $\sqrt{|xy|}$

$f(x,y)=\sqrt{|xy|}$. Az origóban folytonos ($\sqrt{|xy|}\le\tfrac12(|x|+|y|)$), a parciális deriváltak léteznek és $0$-k ($f(x,0)\equiv0$), ezért ha differenciálható volna, $f'(0,0)=(0,0)$ lenne. Viszont
$$\frac{\sqrt{|xy|}}{|x|+|y|}\Big|_{y=x}=\frac12\not\to0,$$
tehát $f\notin D\{(0,0)\}$. Ugyanez a függvény az $y=x$ irányban lineárisan viselkedik, de a gradiens nem tudja ezt leírni.

### Minden irányban deriválható, de nem differenciálható

$f=\dfrac{xy^2}{x^2+y^2}$, $f(0,0)=0$: folytonos az origóban, minden $e$ irányban létezik $\partial_ef(0,0)$ (mert $f(te)=t\,f(e)$), de $e\mapsto\partial_ef(0,0)$ nem lineáris, így nem lehet $\langle f'(0,0),e\rangle$ alakú; $f$ nem totálisan deriválható. Lásd [[concepts/analiii/iranymenti-derivalt]].

### Differenciálható, de a parciálisok nem folytonosak

$$f(x,y)=\begin{cases}(x^2+y^2)\sin\dfrac1{x^2+y^2}&(x,y)\ne0\\0&(x,y)=0\end{cases}$$
Az origóban $\partial_1f=\partial_2f=0$, és $\dfrac{|f(h)|}{\|h\|_2}=\|h\|_2\left|\sin\dfrac1{\|h\|^2}\right|\to0$, tehát $f\in D\{(0,0)\}$, $f'(0,0)=(0,0)$. A $\partial_1f=2x\sin\frac1{x^2+y^2}-\frac{2x}{x^2+y^2}\cos\frac1{x^2+y^2}$ viszont nem tart $0$-hoz (az $x$ tengelyen az $x_n=1/\sqrt{2n\pi}$ pontsorozaton $\partial_1f\to-\infty$), így $\partial_1f\notin C\{(0,0)\}$. Következmény: a [[concepts/analiii/differencialhatosag-elegseges-feltetele|folytonos parciálisokra vonatkozó feltétel]] elégséges, de nem szükséges. Nem szabad **ágankénti** deriválással dolgozni: az origóban a definíció kell, a két ágat nem lehet külön deriválni.

### Vegyes parciálisok eltérnek: $\partial_{12}f\ne\partial_{21}f$

$f=xy\dfrac{x^2-y^2}{x^2+y^2}$, $f(0,0)=0$. Az origóban $\partial_{12}f(0,0)=1$, $\partial_{21}f(0,0)=-1$. A [[concepts/analiii/young-tetel|Young-tétel]] feltétele (kétszeres differenciálhatóság) tehát nem hagyható el; a második parciálisok az origóban nem folytonosak.

### Folytonos norma, de nem differenciálható

A $\|x\|_2=\sqrt{x^2+y^2}$ az origóban folytonos (sőt $|\|x\|-\|t\||\le\|x-t\|$ miatt Lipschitz-1, azaz egyenletesen folytonos), de nem differenciálható: az iránymenti deriváltak $\partial_e f(0)=1$ minden irányra, ami nem lineáris függvénye $e$-nek. A kúp csúcsában nincs érintősík.

## Kapocs

- [[concepts/analiii/differencialhatosagi-fogalmak-hierarchiaja]] — az implikációk, amelyek megfordítására ezek az ellenpéldák szólnak.
- [[concepts/analiii/frechet-derivalt]] — a definíció, amelyet az ellenőrzések használnak.
- [[concepts/analiii/magasabbrendu-parcialis-derivaltak]] — a vegyes parciálisok sorrendje.
- [[concepts/analiii/differencialhatosag-igazolasa-definicioval]] — a pozitív oldal: hogyan igazoljuk a deriválhatóságot.
- [[concepts/analiii/tobbvaltozos-hatarertek-vizsgalata]] — a határérték-cáfolás technikái.
