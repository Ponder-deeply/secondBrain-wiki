#flashcards/analiii/3-eloadas-folytonossag-kompaktsag

## Miért legfeljebb egy határértéke lehet egy függvénynek egy torlódási pontban metrikus terek között?
?
Ha $B\ne A$ is határérték volna, akkor $0<r<\sigma(A,B)/2$ mellett $K_r(A)$ és $K_r(B)$ diszjunktak (háromszög-egyenlőtlenség). A két megfelelő $k(a)$ környezet metszetének $a$-tól különböző $D_f$-beli pontjaiban viszont $f(x)$-nek mindkét gömbben benne kellene lennie, ami ellentmondás.
---

## Mit jelent, hogy a határérték lokális tulajdonság?
?
Ha $f$ és $g$ megegyezik $a$ egy kipontozott környezetén (a $D$ közös, nemüres tartományon), akkor $a\in D_f'\cap D_g'$ esetén $\lim_a f$ pontosan akkor létezik, ha $\lim_a g$ létezik, és ekkor egyenlők. Az $f(a)$ értéke és az $a\in D_f$ kérdés érdektelen.
---

## Hogyan definiálható $\mathbb{R}^2\to\mathbb{R}$ esetben a határérték folytonos kiterjesztéssel?
?
$\lim_{(a_1,a_2)}f=A$, ha az az $\tilde f$ függvény, amely $D_f\setminus\{(a_1,a_2)\}$-n megegyezik $f$-fel, és amelyre $\tilde f(a_1,a_2)=A$, folytonos az $(a_1,a_2)$ pontban.
---

## Mikor létezik egy $f=(f_1,\dots,f_m)\in\mathbb{K}^s\to\mathbb{K}^m$ függvény határértéke, és mennyi?
?
Pontosan akkor, ha mindegyik $\lim_a f_i$ koordinátahatárérték létezik. Ekkor $\lim_a f=(\lim_a f_1,\dots,\lim_a f_m)$.
---

## Miért nem létezik $\lim_{(0,0,0)}\dfrac{xy+yz+zx}{x^2+y^2+z^2}$?
?
Az $x$-tengely mentén a függvény értéke $0$, az $x=y=z$ egyenes mentén $1$. Két úton két különböző érték adódik, a határérték viszont egyértelmű, ezért nem létezik.
---

## Mit mondanak az iterált határértékek az $f=\dfrac{x-y}{x+y}$ függvényről az origóban?
?
Mindkét iterált határérték létezik, de az egyik $1$, a másik $-1$. Mivel különböznek, a kétváltozós határérték nem létezik.
---

## Mennyi $\lim_{(0,0)}(x^2+y^2)^{x^2y^2}$, és miért?
?
$1$. A függvény $e^{x^2y^2\ln(x^2+y^2)}$ alakba írható, és $|x^2y^2\ln(x^2+y^2)|\le r^4|\ln r^2|\to0$, ezért a kitevő $0$-hoz tart, a határérték pedig $e^0=1$.
---

## Mennyi $\lim_{(1,2)}\dfrac{x^2+xy}{x+y^2}$, és miért szabad behelyettesíteni?
?
$\tfrac35$. A függvény racionális törtfüggvény, amelynek nevezője az $(1,2)$ pontban nem nulla, ezért ott folytonos, így a határérték megegyezik a függvényértékkel.
---
