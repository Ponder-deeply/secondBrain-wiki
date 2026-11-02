#flashcards/analiii/2-eloadas-konvergencia-teljesseg

## Hogyan definiáljuk a $(H,d)$ metrikus térben az $a$ körüli, $r>0$ sugarú nyílt és zárt gömböt?
?
$B(a,r)=\{x\in H: d(x,a)<r\}$ a nyílt gömb, $\overline{B}(a,r)=\{x\in H: d(x,a)\le r\}$ a zárt gömb.
---

## Miért egyértelmű a limesz normált térben?
?
Ha $\|x_k-\alpha\|<\varepsilon$ és $\|x_k-\beta\|<\varepsilon$ elég nagy $k$-ra, akkor a háromszög-egyenlőtlenség miatt $\|\alpha-\beta\|<2\varepsilon$. Ez minden $\varepsilon>0$-ra igaz, ezért $\alpha=\beta$.
---

## Hogyan viselkedik az $f_k(x)=x^k$ sorozat a $C[0,1]$ térben a $\|\cdot\|_\infty$ és az $\|\cdot\|_1$ normában?
?
$\|\cdot\|_\infty$-ben divergens, mert a pontonkénti limesz nem folytonos. $\|\cdot\|_1$-ben $0$-hoz tart, mert $\int_0^1 x^k\,dx=\frac1{k+1}\to0$.
---

## Milyen lépésekben vizsgáljuk egy függvénysorozat konvergenciáját $C[a,b]$-ben egy adott normában?
?
Először kiszámítjuk a $g$ pontonkénti limeszt, mert más limesz nem jöhet szóba. Utána megvizsgáljuk, hogy $\|f_k-g\|\to0$ teljesül-e: $\|\cdot\|_\infty$ esetén a szuprémumot számoljuk szélsőérték-kereséssel, $\|\cdot\|_1$ esetén az integrált.
---

## Konvergens-e $C[0,2]$-ben a $\|\cdot\|_\infty$ normában az $f_k(x)=\frac{kx}{1+k^2x^2}$ sorozat, és miért?
?
Nem, divergens. A pontonkénti limesz $0$, de $f_k$ maximuma $\tfrac12$, amit az $x=\tfrac1k$ pontban vesz fel, így $\|f_k-0\|_\infty=\tfrac12\not\to0$. Az $\|\cdot\|_1$ normában viszont $0$-hoz tart.
---

## Hogyan bizonyítjuk, hogy metrikus térben minden konvergens sorozat Cauchy-tulajdonságú?
?
Legyen $b=\lim a_n$, és válasszunk $n_0$-t úgy, hogy $n>n_0$ esetén $d(a_n,b)<\varepsilon/2$. Ekkor $m,n>n_0$ esetén $d(a_m,a_n)\le d(a_m,b)+d(a_n,b)<\varepsilon$.
---

## Melyek a lépései annak a bizonyításnak, hogy $\bigl(C[a,b],\|\cdot\|_\infty\bigr)$ teljes?
?
Egy Cauchy-sorozat minden rögzített $x$-ben Cauchy-számsorozatot ad, ezért létezik a $g$ pontonkénti limesz. Az $m\to\infty$ határátmenettel $\max_x|f_n(x)-g(x)|\le\varepsilon$, tehát a konvergencia egyenletes. Folytonos függvények egyenletes limesze folytonos, így $g\in C[a,b]$.
---

## Miért teljes a diszkrét metrikus tér?
?
Egy Cauchy-sorozathoz $\varepsilon<1$ mellett van olyan $k_0$, hogy $k,l>k_0$ esetén $\rho(x_k,x_l)<1$. Diszkrét metrikában ez azt jelenti, hogy $x_k=x_l$. A sorozat tehát kvázikonstans, így konvergens.
---
