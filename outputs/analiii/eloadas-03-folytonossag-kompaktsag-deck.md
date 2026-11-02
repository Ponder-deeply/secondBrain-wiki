`button-fc-review` | `button-fc-cram`

#flashcards/analiii/eloadas-03-folytonossag-kompaktsag

## Mikor mondjuk, hogy egy normált térből normált térbe képező függvény folytonos egy pontban?
?
$f : X \to Y$ **folytonos** az $a \in D_f$-ben, ha minden $\varepsilon>0$-hoz van $\delta>0$, hogy $\|f(x)-f(a)\|_Y < \varepsilon$ minden $x \in D_f$, $\|x-a\|_X<\delta$ esetén. Ekvivalens (környezetes) alak: minden $K(f(a))$ környezethez van $k(a)$ környezet, hogy $f[k(a)\cap D_f] \subset K(f(a))$.
---

## Milyen kapcsolat van egy $\mathbb{R}^n \to \mathbb{R}^m$ típusú függvény folytonossága és a koordinátafüggvényei folytonossága között?
?
$f = (f_1,\dots,f_m)$ akkor és csak akkor folytonos az $a$-ban, ha minden $i=1,\dots,m$-re a $f_i$ koordinátafüggvény folytonos $a$-ban. (Az átviteli elv és a koordinátánkénti konvergencia tételének következménye.)
---

## Mondja ki az összetett függvény folytonosságára vonatkozó tételt normált terek közötti leképezésekre!
?
Ha $g : X \to Y$ folytonos $a$-ban és $f : Y \to Z$ folytonos $g(a)$-ban, akkor az $f \circ g : X \to Z$ összetett függvény folytonos $a$-ban. (Bizonyítás: az átviteli elv kétszeri alkalmazása — ha $x_n \to a$, akkor $g(x_n)\to g(a)$, majd $f(g(x_n)) \to f(g(a))$.)
---

## Definiálja a határérték fogalmát normált terek közötti függvényekre!
?
Legyen $a \in D_f'$ (torlódási pont). $A$ az $f$ **határértéke** $a$-ban, ha minden $K(A)$ környezethez van olyan $k(a)$ környezet, hogy $f\bigl[(k(a)\setminus\{a\})\cap D_f\bigr] \subset K(A)$. Az így egyértelműen létező $A$-t $\lim_a f$-fel jelöljük. Torlódási pontban $f$ folytonossága $a$-ban ekvivalens azzal, hogy $\lim_a f$ létezik és egyenlő $f(a)$-val.
---

## Jellemezze normált térbeli halmazok esetében a torlódási pont fogalmát sorozatok segítségével!
?
$\alpha$ akkor és csak akkor torlódási pontja $H\neq\emptyset$-nek, ha van olyan $(x_n) : \mathbb{N}\to H\setminus\{\alpha\}$ sorozat, amelyre $\lim(x_n)=\alpha$ — a sorozat ráadásul injektívnek is választható.
---

## Mi a kapcsolat normált térben a zárt halmazok és a torlódási pontok között?
?
$H$ zárt $\iff$ minden torlódási pontja $H$-ban van, azaz $H' \subset H$ (ekvivalensen $\operatorname{cl}H = H \cup H' = H$).
---

## Jellemezze a normált térbeli zárt halmazokat sorozatok segítségével!
?
$H$ zárt akkor és csak akkor, ha bármely $H$-beli konvergens pontsorozat limesze is $H$-ban van.
---

## Definiálja a kompakt halmaz fogalmát normált térben!
?
$K$ **kompakt**, ha minden nyílt fedéséből kiválasztható véges fedés: ha $K \subset \bigcup_{i\in I} G_i$ nyílt halmazokkal, akkor van véges $V\subset I$, hogy $K \subset \bigcup_{i\in V}G_i$. Ezzel ekvivalens a sorozatos definíció: minden $K$-beli sorozatnak van $K$-ban konvergáló részsorozata.
---

## Mi a kapcsolat normált térben a kompakt halmazok és a zárt halmazok között?
?
Minden kompakt halmaz zárt. (A megfordítás általában nem igaz.)
---

## Mi a kapcsolat normált térben a kompakt halmazok és a korlátos halmazok között?
?
Minden kompakt halmaz korlátos. (A megfordítás általában nem igaz.)
---

## Adjon példát olyan normált térre, és abban olyan korlátos és zárt halmazra, ami nem kompakt!
?
$\bigl(C[0,1], \|\cdot\|_\infty\bigr)$-ben a zárt egységgömb $\overline{B}(0,1)$ korlátos és zárt, de nem kompakt: végtelen dimenziós normált térben a zárt egységgömb sosem kompakt (nincs belőle véges $\varepsilon$-háló minden $\varepsilon$-ra).
---

## Mit állíthatunk $\mathbb{R}^n$-ben a kompakt, valamint a korlátos és zárt halmazok viszonyáról?
?
$\mathbb{R}^n$-ben egy halmaz akkor és csak akkor kompakt, ha korlátos és zárt (Heine–Borel-tétel). Véges dimenzióban tehát a két fogalom egybeesik — ellentétben a végtelen dimenziós esettel.
---

## Mit mondhatunk kompakt halmazon értelmezett folytonos függvény értékkészletéről?
?
Kompakt halmazon értelmezett folytonos $f: X\to Y$ függvény értékkészlete is kompakt (Weierstrass-tétel: kompakt halmaz folytonos képe kompakt).
---

## Mit állíthatunk kompakt halmazon értelmezett valós értékű folytonos függvények szélsőértékeiről?
?
$f: X \to \mathbb{R}$ folytonos, $D_f$ kompakt esetén $R_f$ kompakt (tehát korlátos és zárt), így $f$-nek van legkisebb és legnagyobb értéke — a szélsőértéket $f$ felveszi (klasszikus Weierstrass-tétel).
---
